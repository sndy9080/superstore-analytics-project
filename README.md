# SuperStore Sales & Delivery Analytics

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat-square&logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
[![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat-square&logo=tableau&logoColor=white)](https://public.tableau.com/views/SuperStoreSalesDeliveryAnalytics/Dashboard1)

An end-to-end analytics project that turns raw SuperStore order data into an interactive Tableau dashboard covering revenue growth, product profitability, and shipping efficiency.

[![Open the interactive dashboard](https://img.shields.io/badge/Tableau%20Public-View%20Interactive%20Dashboard-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/views/SuperStoreSalesDeliveryAnalytics/Dashboard1)

## Dashboard

[![SuperStore Dashboard Preview](images/dashboard_preview.png)](https://public.tableau.com/views/SuperStoreSalesDeliveryAnalytics/Dashboard1)

*Click the preview to open the fully interactive version on Tableau Public. Use the Order Date range filter to drill down into specific periods.*

## Project Objective

Analyze the historical sales data of a retail SuperStore to uncover actionable insights on revenue growth, product profitability, and supply chain efficiency, and give management clear, data-driven recommendations to reduce losses in underperforming product segments.

## Dataset

| Item | Detail |
|---|---|
| Source | SuperStore Global retail dataset (sample) |
| Size | 51,290 rows, 21 columns (22 after cleaning) |
| Period | January 2011 - December 2014 |
| Coverage | 7 markets, 147 countries |
| Key attributes | Order Date, Ship Date, Ship Mode, Segment, Category, Sub-Category, Sales, Quantity, Discount, Profit |

## Business Questions

1. What is the Year-over-Year (YoY) trend for sales?
2. Which categories and sub-categories drive the most profit, and which operate at a loss?
3. How do shipping modes compare in average delivery time?
4. What actions can management take to improve margins in loss-making segments?

## Process

1. **Data cleaning and preprocessing (Python / Pandas, Google Colab)**
   - Audited the raw data: checked dimensions, data types, missing values (none found), and duplicate rows (none found).
   - Converted `sales` from text to numeric.
   - Standardized the date columns. The raw data mixes `dd/mm/yyyy` and `dd-mm-yyyy` formats, so both are parsed day-first with an explicit format and validated to have zero failed conversions.
   - Engineered `delivery_time_days` (ship date minus order date).
2. **Exploratory data analysis (Python)**
   - Aggregated sales and profit by product category and visualized the results with Matplotlib and Seaborn.
3. **Dashboard (Tableau)**
   - Connected the cleaned dataset to Tableau and built an interactive dashboard with a sales trend, a profit-by-sub-category chart, a shipping efficiency chart, executive KPIs, and an order date range filter.

## Key Findings

| Metric (2011-2014) | Value |
|---|---|
| Total sales | 12,642,905 |
| Total profit | 1,469,035 (11.6% margin) |
| Total quantity sold | 178,312 units |

- **Sales growth:** Sales grew every year, from 2.26M in 2011 to 4.30M in 2014. Annual growth was about 18.5% (2012), 27.2% (2013), and 26.3% (2014).
- **Profit drivers:** Technology is the most profitable category (663,779 profit), led by Copiers (258,568) and Phones (216,717).
- **Loss-maker:** Tables is the only loss-making sub-category, at -64,083 profit (an -8.5% margin) on 757,034 in sales.
- **Discounts drive the Tables loss:** Tables carry an average discount of 29% versus 14% across all products, and 75% of Tables orders are discounted by 20% or more. Those orders lost 125,326 combined, while Tables orders with smaller or no discounts earned 61,242.
- **Logistics:** Average delivery time is about 0 days for Same Day, 2.2 days for First Class, 3.2 days for Second Class, and 5.0 days for Standard Class. Standard Class handles 60% of all orders.

## Recommendations

1. **Rework the Tables discount policy.** Cap discounts on Tables (for example below 20%) and review supplier costs. The data shows the losses come from heavily discounted orders, not from the sub-category as a whole.
2. **Use Standard Class volume as leverage.** With 60% of orders shipping Standard Class, negotiate better SLA and rate terms with logistics vendors, aiming to cut shipping cost without lengthening the 5-day average.
3. **Protect the profit engine.** Keep Copiers and Phones well stocked and avoid deep discounting on them.

## Repository Structure

```text
SuperStore-Analytics-Project/
│
├── data/
│   ├── raw_superstore.csv            # Raw dataset before processing
│   └── Cleaned_SuperStoreOrders.csv  # Clean dataset produced by the Python pipeline
│
├── notebooks/
│   └── Superstore_EDA_Cleaning.ipynb # Cleaning and EDA (Pandas) from Google Colab
│
├── images/
│   └── dashboard_preview.png         # Screenshot of the Tableau dashboard
│
├── requirements.txt                  # Python libraries
└── README.md                         # Project documentation
```

## How to Reproduce

1. Open `notebooks/Superstore_EDA_Cleaning.ipynb` in [Google Colab](https://colab.research.google.com/), or run it locally after `pip install -r requirements.txt`.
2. Upload `data/raw_superstore.csv` (or change the path in the first code cell) and run all cells to generate `Cleaned_SuperStoreOrders.csv`.
3. Connect the cleaned CSV to Tableau to rebuild or refresh the dashboard.

## Author

**Sendy Tegar Mahendra** · [LinkedIn](https://www.linkedin.com/in/sendytegar) · [Email](mailto:sndy9080@gmail.com)
