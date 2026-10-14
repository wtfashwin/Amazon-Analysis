# Amazon Analysis

A sales analytics practice project for exploring synthetic commerce data with Python, MySQL, Power BI, and Prophet.

## What it does

- Generates customers, products, orders, and order details as CSV files.
- Defines a MySQL schema and queries for revenue, profit, products, customers, regions, and payment methods.
- Forecasts monthly revenue for 12 additional months with Prophet.
- Includes a Power BI report, `Amazon.Insights_Dashboards.pbix`.

## Project status

This is a collection of scripts, data files, SQL queries, and a dashboard. `Amazon.py` generates synthetic data; this is not a connection to Amazon's sales systems. Database import and dashboard refresh are manual steps.

## Getting started

Use Python with pip. MySQL 8 or later is needed for the SQL queries that use window functions; Power BI Desktop is needed to open the report.

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

On Windows, activate the environment with `.venv\Scripts\activate`.

The repository already includes CSV files. To generate a new dataset, run:

```bash
python Amazon.py
```

This overwrites `customers.csv`, `products.csv`, `orders.csv`, and `order_details.csv` in the current directory. Generation is random and has no fixed seed.

Create the tables from the opening section of `Sql.sql`, then import the four CSVs into their matching tables. Load customers and products before orders and order details because the schema has foreign keys. The remaining statements provide the analysis queries; the file does not import CSVs for you.

## Forecast workflow

Use the included `monthly_revenue.csv`, or export the final monthly revenue query in `Sql.sql` with the columns `Month` and `Monthly_Revenue`. From the repository root, run:

```bash
python forcast.py
```

The script writes `forecast.csv` and opens forecast and component plots. Open the PBIX file in Power BI Desktop and review its data connections before refreshing.

## Files

| File | Purpose |
| --- | --- |
| `Amazon.py` | Synthetic dataset generator |
| `Sql.sql` | Schema and analysis queries |
| `forcast.py` | Prophet forecast and plots |
| `monthly_revenue.csv` | Forecast input |
| `Amazon.Insights_Dashboards.pbix` | Power BI report |
| `requirements.txt` | Python dependencies |

## Available checks and limitations

No automated test suite is included. Dependency versions are unpinned, and no model evaluation or forecast accuracy claim is provided.

Existing dashboard previews: [sales performance](https://github.com/user-attachments/assets/a8c13592-9354-45ab-92f8-d958c71ca5e6), [forecast](https://github.com/user-attachments/assets/1e0f69bc-02ef-4443-abef-7cd139c4db79), [product performance](https://github.com/user-attachments/assets/49cc8f9e-e85d-45f5-8219-39ef798136db), and [growth](https://github.com/user-attachments/assets/12e65499-7688-4644-8ae8-a500327ac1ca). These are existing images, not current validation results.

## License

No license file is included.
