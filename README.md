# PulseShop Sales Analysis Dashboard

## Overview
This Power BI dashboard provides an interactive analysis of PulseShop's sales data from October 2022 to October 2024. It delivers actionable insights into sales performance, product categories, regional trends, and sales representative contributions, enabling data-driven decision-making. The project includes data preparation, transformation, modeling, DAX calculations, and four dashboard pages: Overview, Trends Analysis, Performance Details, and Insights & Recommendations. Key features include a dynamic date slicer with a bookmark, a parameter for toggling sales and profit visuals, and a dedicated Insights & Recommendations page with strategies to boost sales performance.

Key Highlights:
- **Total Sales**: $3.81M
- **Total Quantity Sold**: 10.82K
- **Total Profit**: $808,670
- **Average Order Size**: $35.15
- **MoM Sales Growth**: 87.14%
- **YoY Sales Growth**: -1.07%
- **Return Rate**: 19.45%

The dashboard is fully interactive, with slicers for dates, products, regions, and sales reps, supporting filters by year, month, time of day, and more.

## Data Source
- **Dataset**: PulseShop sales.xlsx (transactional and dimensional data covering ~thousands of records).
- **Key Columns**: Order ID, Date, Product ID, Region ID, Sales Rep ID, Total Sales, Profit, Quantity Sold, Returns Sales, Product Category, Region Name, Sales Rep Name.
- **Data Prep**: Imported via Excel connector; transformed in Power Query to split into Fact_Orders (transactions) and Dim tables (Date, Products, Regions, Sales Reps); created Dim_Date (Year, Month, Quarter, Week, Day) and Dim_Date_Time (Hour, Time of Day: Morning/Afternoon/Evening/Night).
- **Modeling**: Star schema with relationships on Order ID, Date, Product ID, Region ID, Sales Rep ID for optimal performance.
- **Sample Data Structure** (aggregated view):
  | Metric | Value | Description |
  |--------|-------|-------------|
  | Total Sales | $3.81M | SUM(Fact_Orders[Total_Sales]) |
  | Total Profit | $808K | SUM(Fact_Orders[Profit]) |
  | #Orders | Varies | COUNTROWS(Fact_Orders) |
  | Peak Hour | Hour 16 ($189K) | Hourly sales distribution |

- **Total Records**: Thousands of orders; cleaned for consistency (e.g., date format conversion).

## DAX Measures
Custom DAX measures power dynamic calculations:
- **#Customers**: DISTINCTCOUNT(Customers[Customer_ID])
- **#Orders**: COUNTROWS(Fact_Orders)
- **#Products**: DISTINCTCOUNT(Products[Product_ID])
- **Average_Order_Size**: DIVIDE([Total_Sales], SUM(Fact_Orders[Quantity_Sold]), 0)
- **MoM_Sales_Growth**: Month-over-month growth percentage
- **Profit_Margin**: DIVIDE(SUM(Fact_Orders[Profit]), SUM(Fact_Orders[Total_Sales]), 0)
- **Return_Rate**: DIVIDE(SUM(Fact_Orders[Returns_Sales]), SUM(Fact_Orders[Total_Sales]), 0)
- **Total_Profit**: SUM(Fact_Orders[Profit])
- **Total_Quantity**: SUM(Fact_Orders[Quantity_Sold])
- **Total_Sales**: SUM(Fact_Orders[Total_Sales])
- **Variance_Period_MoM**: Current vs. previous month variance
- **Variance_Period_YoY**: Current vs. previous year variance
- **YoY_Sales_Growth**: Year-over-year growth

These ensure accurate, real-time insights across visuals.

## Dashboard Structure
The dashboard features four pages for a comprehensive view:

### 1. Overview
- **Purpose**: High-level KPIs and sales summary.
- **Content**: KPI cards (Total Sales, Quantity, Profit, Average Order Size, Growth Rates, Return Rate); slicers (Date, Product Category, Region, Sales Rep, Year, Month, Time of Day).
- **Visuals**: Line charts for monthly/yearly sales trends (with MoM on secondary axis) and profit margin trends.

### 2. Trends Analysis
- **Purpose**: Time-based trends (hourly, daily, sales rep performance).
- **Content**: Ranked table for top sales reps (e.g., Cristian Popescu, Iulia Ionescu); line chart for hourly sales (peaks at Hour 4: $183K, Hour 16: $189K, Hour 22: $182K); bar charts for sales by time of day (Night: $1.26M) and day of week (Thursday: $0.59M).
- **Feature**: Parameter to toggle Total Sales/Profit visuals by Year, Month, or both (defaults to combined).

### 3. Performance Details
- **Purpose**: Breakdown by products, regions, customers, reps.
- **Content**: Cards (#Orders, #Products, #Customers, #Regions); funnel charts for top 2 products (Televisions, Air Fryer) and regions (Brăila, Târgu Mureș); stacked bar for sales vs. returns by region; pie chart for sales by category (Electronics: 60.06%).

### 4. Insights & Recommendations
- **Purpose**: Key findings and strategies.
- **Content**: Actionable insights (e.g., peak hours, Electronics dominance, Thursday peaks); recommendations (e.g., promotions in peak hours for 15% uplift, Thursday campaigns for 10% boost, promote high-margin products like Televisions).

## Dashboard Screenshots
Replace placeholders with actual image paths (e.g., `images/screenshot1.png`) when uploading to GitHub.

### 1. Overview Page
![Overview - KPIs, Sales Trends, Profit Margin](images/screenshot1.png)

### 2. Trends Analysis Page
![Trends - Sales Rep Performance, Hourly/Daily Sales](images/screenshot2.png)

### 3. Performance Details Page
![Performance - Top Products/Regions, Category Breakdown](images/screenshot3.png)

### 4. Insights & Recommendations Page
![Insights - Key Findings, Strategies](images/screenshot4.png)

## Key Insights
- **Time Trends**: Peak sales at Hour 16 ($189K); Night contributes $1.26M; Thursday highest day ($0.59M), Monday lowest ($0.45M).
- **Products**: Electronics drives 60.06% revenue; top performers: Televisions, Air Fryer.
- **Regions**: Brăila and Târgu Mureș lead sales; analyze returns for shipping optimization.
- **Sales Reps**: Cristian Popescu, Iulia Ionescu, Alina Georgescu as top contributors.
- **Recommendations**: Flash sales in peak hours (projected +15%, $28K/hour); loyalty campaigns on Thursdays (+10%, $59K); bundle high-profit products.

## How to Run
1. **Prerequisites**: Install Power BI Desktop (free from Microsoft).
2. **Load Data**:
   - Open Power BI Desktop.
   - Get Data > Excel > Select "PulseShop sales.xlsx".
   - Apply Power Query transformations (date conversion, table splitting).
3. **Import Dashboard**:
   - Open "PulseShop_Dashboard.pbix".
   - Use the date slicer bookmark (click calendar icon to toggle).
   - Toggle parameters for sales/profit views.
4. **Explore**:
   - Filter via slicers; navigate pages with buttons.
   - Refresh for updates.
5. **Publish (Optional)**: Publish to Power BI Service for sharing.

## Tech Stack
- **Tool**: Power BI Desktop
- **Data**: Excel (.xlsx)
- **Measures**: DAX (e.g., Total Sales = SUM(Fact_Orders[Total_Sales]))
- **Visuals**: Cards, Line Charts, Bar Charts, Funnel Charts, Pie Charts, Stacked Bars
- **Features**: Bookmarks, Parameters, Star Schema Modeling
- **Design**: Consistent gray/yellow palette; page navigation for UX.

