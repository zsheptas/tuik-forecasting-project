# TÜİK Forecasting Project

## 1. Project Overview
This project forecasts Turkey's Export Unit Value Index [2015=100] using monthly data from the TÜİK Data Portal, accessed via the tuikr R package.

## 2. Data Source and TÜİK Connection
- TÜİK data set name: Foreign Trade Indices
- TÜİK theme/category: International Trade (Theme 17)
- TÜİK table name: Foreign Trade Indices
- TÜİK dataflow ID: istab type (URL via tuikr)
- Selected variable: Export Unit Value Index [2015=100]
- Data frequency: Monthly
- Time coverage: 2013-01 to 2026-03
- Latest available observation: March 2026
- Forecast target period: April 2026
- Date of data access: 2026-05-23
- R package used: tuikr (https://github.com/emraher/tuikr)

## 3. Research Objective
Forecast the Export Unit Value Index for April 2026 using 10 quantitative forecasting methods.

## 4. Use of TÜİK Data in R
Data accessed via tuikr::statistical_tables('17'). TÜİK SDMX API returned HTTP 401/403 from Posit Cloud due to IP restrictions. The file URL was obtained through tuikr and downloaded via browser. No manual editing was performed.

## 5. Exploratory Time Series Analysis
- Upward trend from 2020 onward
- Mild seasonal fluctuations
- No missing values after 2013
- Structural break visible around 2020 (COVID-19)

## 6. Forecasting Methods Applied
- Naive Forecasting
- Moving Average (k=3)
- Weighted Moving Average
- Exponential Smoothing (alpha=0.3)
- Trend-Adjusted Exponential Smoothing
- Linear Trend Projection
- Seasonal Indices
- Additive Decomposition
- Multiplicative Decomposition
- Regression with Trend and Seasonal Dummy Variables

## 7. Forecast Accuracy Comparison
| Method | MAPE | MAD | Next Forecast |
|--------|------|-----|---------------|
| Weighted MA | 0.6278 | 0.6688 | 130.09 |
| Moving Average | 0.9068 | 0.9661 | 129.90 |
| Naive | 1.1175 | 1.1902 | 130.54 |
| Additive Decomp | 1.0518 | 1.1109 | 112.00 |

## 8. Selection of the Superior Method
Weighted Moving Average was selected as the superior method based on lowest MAPE (0.6278%) and MAD (0.6688). The series shows a smooth recent upward trend without strong seasonality, making WMA appropriate.

## 9. Final Next-Period Forecast
- Selected superior method: Weighted Moving Average
- Date of data access: 2026-05-23
- Latest available TÜİK observation: March 2026
- Forecast target period: April 2026
- Forecasted value: 130.09

## 10. Interpretation of Results
The Export Unit Value Index is forecast to be approximately 130.09 in April 2026, indicating continued upward pressure on Turkish export prices relative to the 2015 base year.

## 11. Limitations
- TÜİK API IP restrictions required browser-based file download using URL obtained via tuikr
- Structural breaks (COVID-19, exchange rate volatility) may affect accuracy
- External variables (exchange rates, commodity prices) not included

## 12. Reproducibility
1. Install R (>=4.0) and RStudio
2. Run: devtools::install_github('emraher/tuikr')
3. Install: install.packages(c('readxl','httr','forecast','ggplot2','tidyr','lubridate','knitr'))
4. Place Foreign Trade Indices.xls in project root
5. Knit forecasting_project.Rmd

## 13. Repository Structure
tuik-forecasting-project/
├── README.md
├── forecasting_project.Rmd
├── forecasting_project.html
├── Foreign Trade Indices.xls
├── outputs/
│   ├── tables/
│   │   ├── accuracy_comparison.csv
│   │   └── final_forecast.csv
│   └── figures/
│       └── (all method plots)

## 14. Author
- Student name: Zeynep Sena Heptaş
- Course name: Quantitative Analysis for Decision Making
