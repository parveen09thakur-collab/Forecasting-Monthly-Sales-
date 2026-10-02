# FreshMart Monthly Sales Forecasting

A time series forecasting project that predicts monthly sales for **FreshMart**, a retail chain selling groceries and household products. The goal is to help management plan inventory, reduce stockouts and improve supply chain efficiency.

## Dataset
- Monthly sales in INR lakhs from **January 2020 to December 2024** (60 months)
- Columns: `Month`, `Sales`
- Split: first 48 months for training, last 12 months (2024) for testing

## Methods Used
| Task | Method |
|------|--------|
| 1 | Moving Average (3, 6 and 12 months) |
| 2 | Simple, Double and Triple Exponential Smoothing |
| 3 | Autoregressive models AR(1), AR(2), AR(3) with ACF/PACF |
| 4 | ARIMA using the Box-Jenkins method (ADF test, differencing, residual check) |
| 5 | SARIMA with grid search over 144 parameter combinations |
| 6 | Holt-Winters additive and multiplicative |

## Results
Models were compared on the 2024 test data using MAE, RMSE and MAPE.

| Model | MAE | RMSE | MAPE (%) |
|-------|-----|------|----------|
| **SARIMA(2,1,0)(1,0,0)[12]** | 1.012 | 1.338 | 1.394 |
| Holt-Winters Additive | 1.644 | 1.968 | 2.224 |
| Holt-Winters Multiplicative | 1.738 | 1.970 | 2.383 |
| ARIMA(3,1,3) | 2.434 | 2.928 | 3.374 |
| SES | 3.318 | 4.101 | 4.651 |
| Double Exponential | 4.011 | 4.605 | 5.572 |
| AR(1) | 5.134 | 6.417 | 6.862 |

**Best model: SARIMA(2,1,0)(1,0,0)[12]**, with an average error of about 1.4%. Models that capture both trend and yearly seasonality performed best.

## Key Insights
- Sales show a steady upward trend and a clear yearly seasonal pattern
- Peak months: November-December. Weakest months: August-October
- The 12-month forecast for 2025 can be used to stock up before peaks and run promotions in slow months

## Repository Contents
- `FreshMart_Forecasting.ipynb` – full Python notebook
- `FreshMart_Monthly_Sales.csv` – dataset
- `FreshMart_Task1_Moving_Averages.xlsx` – moving average output
- `FreshMart_12_Month_Forecast.xlsx` – forecast for 2025
- `FreshMart_Model_Comparison.xlsx` – error metrics for all models
- `FreshMart_Notebook_Explanation_Report.docx` – step-by-step explanation of the notebook with graphs

## Tools and Libraries
Python, pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels

## How to Run
```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn openpyxl
jupyter notebook FreshMart_Forecasting.ipynb
```
Keep the CSV file in the same folder as the notebook.
