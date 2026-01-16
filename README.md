# 🛒 Zepto-Business-Data-Analysis-Using-SQL-Project

## 📌 Project Overview

This project simulates real-world work done by data analysts in the e-commerce and retail industries using SQL. The goal is to analyze a messy, realistic inventory dataset from a quick-commerce grocery platform (Zepto) and extract meaningful business insights.

Key objectives include:

* Setting up a real-world e-commerce inventory database
* Performing Exploratory Data Analysis (EDA)
* Cleaning and transforming raw data for accuracy
* Writing business-focused SQL queries to generate insights on pricing, inventory, revenue, and stock availability

---

## 📁 Dataset Overview

The dataset was sourced from *Kaggle* and originally scraped from *Zepto’s official product listings*. It closely reflects real-world e-commerce catalog data.

* Each row represents a unique *SKU (Stock Keeping Unit)*
* Duplicate product names exist due to different package sizes, weights, discounts, or categories

### 🧾 Columns

* *sku_id* – Unique identifier for each product (Synthetic Primary Key)
* *name* – Product name as listed on the app
* *category* – Product category (Fruits, Snacks, Beverages, etc.)
* *mrp* – Maximum Retail Price (converted from paise to ₹)
* *discountPercent* – Discount applied on MRP
* *discountedSellingPrice* – Final selling price after discount (₹)
* *availableQuantity* – Units available in inventory
* *weightInGms* – Product weight in grams
* *outOfStock* – Boolean flag for stock availability
* *quantity* – Units per package (mixed with grams for loose items)

---

## 🔧 Project Workflow

### 1️⃣ Database & Table Creation

A PostgreSQL table is created with appropriate data types:

sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);


---

### 2️⃣ Data Import

* Dataset loaded using *pgAdmin CSV Import*
* UTF-8 encoding issues were resolved by re-saving the CSV file in *CSV UTF-8* format

Alternative import method:

sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');


---

### 3️⃣ 🔍 Data Exploration (EDA)

* Counted total records
* Viewed sample records
* Checked null values across columns
* Identified distinct product categories
* Compared in-stock vs out-of-stock products
* Detected duplicate product names representing multiple SKUs

---

### 4️⃣ 🧹 Data Cleaning

* Removed records where MRP or selling price was zero
* Converted prices from *paise to rupees* for consistency

---

### 5️⃣ 📊 Business Insights

Using SQL queries, the following insights were derived:

* Top 10 best-value products based on highest discounts
* High-MRP products currently out of stock
* Estimated potential revenue by product category
* Expensive products (MRP > ₹500) with minimal discounts
* Top 5 categories offering the highest average discounts
* Price-per-gram analysis to find value-for-money products
* Product segmentation by weight (Low, Medium, Bulk)
* Total inventory weight per category

---

## 🛠️ How to Use This Project

### 2️⃣ Run the SQL File

* Open zepto_SQL_data_analysis.sql
* Create a PostgreSQL database
* Execute the SQL file
* Import the dataset (ensure UTF-8 encoding)

### 3️⃣ Learn Along

Follow the YouTube walkthrough for a step-by-step explanation of the project.

---

## 🧑‍💼 Skills Demonstrated

* SQL (Joins, Aggregations, Subqueries, CASE statements)
* Data Cleaning & Validation
* Exploratory Data Analysis (EDA)
* Business Insight Generation
* Real-world E-commerce Data Handling

---

## 📜 License

MIT License — Feel free to fork, star ⭐, and use this project in your portfolio.

---

### 🚀 This project is ideal for:

* Data Analyst / SQL Fresher portfolios
* Interview preparation
* Hands-on SQL practice with real-world data
