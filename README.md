# Data-Driven Marketing Strategy: From ROI Analysis to Revenue Forecasting

## Executive Summary
This project is a comprehensive Power BI decision-support tool designed to connect Marketing Expenditure with Sales Performance. Rather than merely visualizing historical data, this dashboard serves as an analytical engine to calculate accurate Return on Ad Spend (ROAS) and simulate future revenue/net gain based on dynamic budget allocations.

## Tech Stack & Skills Demonstrated
* **Tool:** Power BI (Desktop & Service)
* **Technical Skills:** Advanced DAX, Relational Data Modeling, What-If Parameters, Cost Allocation Algorithms.
* **Business Skills:** Financial Sanity Checks, ROI Analysis, Top-Down Analytical Approach, Data Storytelling.

## Key Challenges & Technical Solutions

### 1. The "Double Counting" Trap (Overlapping Campaigns)
* **Problem:** Marketing campaigns frequently overlapped in time and regions. Using standard `SUMX` aggregation caused a massive Cartesian Join issue, falsely inflating "Influenced Revenue" by 21x due to single orders being counted across multiple simultaneous campaigns.
* **Solution:** Engineered a robust DAX solution using `CROSSJOIN` and `FILTER(ALL())` to iterate through time and space strictly once, guaranteeing that each dollar of revenue was attributed correctly without duplication.

### 2. The Granularity Conflict (Cost Allocation)
* **Problem:** Advertising Spend was recorded at the *Strategy* level, while Revenue was tracked at the *Channel* level. Attempting to view Net Gain by combining both dimensions caused massive negative outliers as the system forced entire corporate budgets onto single channels.
* **Solution:** Designed a dynamic weighted-allocation algorithm in DAX. The model automatically calculates the revenue contribution percentage of each channel and distributes the Ad Spend proportionally, resulting in highly accurate, drill-down capable Net Gain projections.

## Dashboard Architecture
The report is structured using a Top-Down philosophy:
1.  **Executive Summary:** A high-level overview of corporate financial health (Total Revenue, Gross Margin), highlighting strict seasonality (Q1 dips) and identifying "Wholesale" as the primary cash cow.
2.  **Marketing ROI:** Deep-dive into campaign efficiency, proving that the "New Customers" strategy yields the highest ROAS and serves as the core growth engine.
3.  **Forecasting Engine:** An interactive "What-If" matrix. Users can simulate budget increases (e.g., +20%) to instantly project future Ad Spend, Revenue, and precise Net Gain across any specific strategy and channel.

## Strategic Recommendations
* Prioritize budget scaling for the "New Customers" strategy, specifically targeting the Wholesale channel to maximize Net Gain.
* Audit and reallocate budgets from underperforming legacy campaigns with ROAS < 1.0.
* *Future Iteration:* Integrate Macroeconomic indicators and model "Diminishing Returns" into the forecasting algorithm for enhanced precision.
