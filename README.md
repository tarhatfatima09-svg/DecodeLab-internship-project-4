# E-Commerce Order Analytics

Exploratory data analysis of a 1,200-row e-commerce orders dataset — built as part of a data analytics internship project (Project 4).

**[View the interactive dashboard](dashboard.html)** · **[Download the Excel workbook](Ecommerce_Analysis.xlsx)**

---

## Overview

This project analyzes order-level e-commerce data covering products, payments, shipping status, coupons, and referral sources, to surface revenue patterns, customer behavior, and operational risk (cancellations/returns).

| | |
|---|---|
| **Rows** | 1,200 orders |
| **Columns** | 14 (order, customer, product, pricing, payment, status, coupon, referral, etc.) |
| **Date range** | Jan 2023 – Jun 2025 |
| **Tools** | Python (pandas, openpyxl), Excel, Chart.js |

## Key findings

- **Total revenue:** $1.26M across 1,200 orders, averaging **$1,054** per order.
- **Customer base is mostly one-time buyers:** of 1,189 unique customers, only **11** placed more than one order.
- **One outlier customer:** `C38840` spent $5,723 — about 66% more than the next-highest customer ($3,456). Worth flagging for a closer look (bulk order vs. multiple orders vs. possible data entry issue).
- **Coupons are heavily used** (74% of orders) but barely move average order value (~$1,058 with a coupon vs. ~$1,043 without) — suggests coupons aren't driving larger basket sizes in this dataset.
- **Cancellation + return rates** sit around 39–44% across all products, with Monitor and Tablet slightly higher than the rest.
- **No real seasonality or trend:** monthly revenue swings between roughly $28K and $68K with no sustained growth or decline.

### A note on data quality

Revenue, order counts, and order status are distributed almost evenly across every category — products, payment methods, referral sources, and statuses all fall within a few percentage points of each other, and the monthly trend is flat. This is a strong signal that the dataset is **synthetic / generated for practice**, rather than real transaction history. The analysis below treats it accordingly — as a structured way to practice the analytics workflow, not as a real business signal.

## What's in this repo

| File | Description |
|---|---|
| `dashboard.html` | Self-contained interactive dashboard (open directly in a browser, no install needed) |
| `Ecommerce_Analysis.xlsx` | Excel workbook — raw data + 8 pivot/summary sheets, all formula-driven |
| `Dataset_for_Data_Analytics.xlsx` | Original source dataset |
| `README.md` | This file |

## Dashboard

The dashboard (`dashboard.html`) is a single static HTML file — no server or build step required. Open it directly in any browser, or enable **GitHub Pages** on this repo to host it live.

It includes:
- Top-line KPIs (revenue, orders, AOV, customers, repeat rate)
- Monthly revenue trend
- Revenue by product
- Cancellation + return rate by product
- Revenue by payment method and referral source
- Coupon usage breakdown
- Top 10 customers by spend

## Excel workbook

`Ecommerce_Analysis.xlsx` contains:

1. **Data** – cleaned raw dataset
2. **Summary** – top-line KPIs
3. **Monthly Trend** – revenue by month, with chart
4. **By Product** – revenue/orders/units by product, with chart
5. **By Payment Method** – revenue/orders by payment type, with chart
6. **By Order Status** – revenue/orders by status, with chart
7. **By Referral Source** – revenue/orders by channel, with chart
8. **Coupon Impact** – revenue/orders by coupon code
9. **Top Customers** – top 10 spenders, with chart

Every number in the workbook is a live formula referencing the Data sheet (`SUMIF`, `COUNTIF`, `SUMPRODUCT`, etc.) — edit the raw data and every sheet recalculates automatically. No values are hardcoded.

## Methodology

1. Loaded and inspected the dataset for missing values, duplicates, and data types (pandas).
2. Computed summary statistics and grouped aggregations across product, payment method, order status, referral source, and coupon code.
3. Checked for trend/seasonality in monthly revenue.
4. Identified top customers and repeat-purchase rate.
5. Cross-tabulated order status against product to estimate cancellation/return risk by category.
6. Flagged the dataset's uniform distribution as a likely sign of synthetic data, rather than presenting it as a real business trend.
7. Built a formula-driven Excel workbook and a lightweight HTML/Chart.js dashboard to present findings.

## How to run

No setup needed to view results — just open `dashboard.html` in a browser or download the Excel file.

To reproduce the analysis from the raw data:

```bash
pip install pandas openpyxl
python analysis.py   # if included, or see methodology above
```

---

*Built as part of a data analytics internship project. Feedback welcome.*
