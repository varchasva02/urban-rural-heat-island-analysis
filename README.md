
# 🌡️ Urban Heat Island Analysis — Delhi 2023

A data science project analysing the **Urban Heat Island (UHI) effect** in Delhi using Landsat 8 satellite data sourced from **Google Earth Engine**. The project explores how Land Surface Temperature (LST) varies across different land use zones throughout the year.

---

## 📌 Overview

Urban Heat Islands occur when cities experience significantly higher temperatures than surrounding rural areas due to human activity and infrastructure. This project quantifies that effect across 5 land use zones in Delhi using real satellite imagery data from 2023.

---

## 📁 Project Structure

```
Urban-Heat-Island-Delhi/
│
├── Urban_rural_island.ipynb   # Main analysis notebook
├── Delhi_UHI_LST_Data.csv     # Raw dataset (Landsat 8 via GEE)
├── Delhi_UHI_Cleaned.csv      # Cleaned & preprocessed dataset
│
├── graphs/
│   ├── graph1_bar_zone_temp.png        # Avg LST by zone
│   ├── graph2_line_monthly_trend.png   # Monthly LST trend
│   ├── graph3_uhi_season.png           # UHI intensity by season
│   ├── graph4_scatterplot.png          # Urbanisation vs LST
│   └── graph5_correlation_heatmap.png  # Correlation matrix
│
└── README.md
```

---

## 🗂️ Dataset

- **Source**: Landsat 8 Surface Temperature — Google Earth Engine
- **Location**: Delhi, India
- **Year**: 2023
- **Zones**: `green_space`, `rural`, `peri_urban`, `suburban`, `urban_core`
- **Key columns**: `date`, `name`, `zone`, `LST_Celsius`, `cloud_cover`

---

## 🔬 Methodology

### 1. Data Cleaning
- Renamed `mean` → `LST_Celsius`
- Dropped irrelevant GEE columns (`system:index`, `.geo`)
- Converted `date` to proper datetime format
- Filled missing LST values using **zone-wise mean imputation**
- Removed duplicate rows

### 2. Preprocessing
- Extracted `month` and `season` (Summer / Monsoon / Post Monsoon / Winter)
- Encoded zones numerically (`zone_code`: 0 = green_space → 4 = urban_core)
- Computed `UHI_intensity` = LST − rural zone mean (baseline)

### 3. Visualisation
Five plots were created using `matplotlib` and `seaborn`:

| # | Chart Type | What it shows |
|---|-----------|---------------|
| 1 | Bar chart | Average LST per zone |
| 2 | Line chart | Monthly LST trend per zone |
| 3 | Grouped bar | UHI intensity by season & zone |
| 4 | Scatterplot | Urbanisation level vs LST with regression line |
| 5 | Heatmap | Correlation matrix of key variables |

---

## 📊 Key Findings

- 🔥 **All zones peak in June (~38–40°C)**, Delhi's hottest month
- 🌧️ **Monsoon shows the strongest UHI effect** — urban core reaches **+4°C** above the rural baseline
- 🌳 **Green spaces** consistently record the lowest temperatures
- ☁️ **Cloud cover and temperature** have a moderate negative correlation (–0.32), confirming monsoon cooling
- 📉 LST vs zone_code correlation is nearly flat (–0.05), confirming UHI is **seasonal, not constant**

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core language |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib | Visualisation |
| Seaborn | Statistical plots |
| Google Colab | Development environment |
| Google Earth Engine | Satellite data source |

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/varchasva02/Urban-Heat-Island-Delhi.git
   cd Urban-Heat-Island-Delhi
   ```

2. **Open in Google Colab**
   - Upload `Urban_rural_island.ipynb` to [colab.research.google.com](https://colab.research.google.com)
   - Mount your Google Drive and update the dataset path in Cell 1:
     ```python
     df = pd.read_csv('/content/drive/MyDrive/your-folder/Delhi_UHI_LST_Data.csv')
     ```

3. **Run all cells** sequentially (Runtime → Run all)

> Alternatively, if running locally, install dependencies:
> ```bash
> pip install pandas numpy matplotlib seaborn
> ```

---



## 🎓 Context

This project was developed as part of a **Computer Science Engineering** coursework assignment focusing on data analysis and environmental data science.

---
