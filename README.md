# Online_retail_SQLAnalysis
**Sales Data Sample SQL Analysis**
This repository contains SQL queries to analyze the sales data from the sales_data_sample table.


**Getting Started**
To run these SQL queries and reproduce the analysis, you'll need access to a database containing the sales_data_sample table. The database should have appropriate permissions to execute SQL queries.

**Queries**
**1. View Order Quantity, Price, Sales, and Deal Size**
 SELECT QUANTITYORDERED, PRICEEACH, SALES, DEALSIZE
FROM sales_data_sample;

**2. Change Datatype for Quantity Ordered, Price Each, and Sales**
ALTER TABLE sales_data_sample
ALTER COLUMN QUANTITYORDERED INT;

ALTER TABLE sales_data_sample
ALTER COLUMN PRICEEACH NUMERIC;

ALTER TABLE sales_data_sample
ALTER COLUMN SALES NUMERIC;

**3. View Total Quantity Ordered, Sales, and Price**
SELECT SUM(QUANTITYORDERED) AS TOTALORDERS, SUM(PRICEEACH) AS TOTALCOST, SUM(SALES) AS TOTALSALES
FROM sales_data_sample;

**4. Profit Percentage**
SELECT SUM(QUANTITYORDERED) AS TOTALORDERS, SUM(PRICEEACH) AS TOTALCOST, SUM(SALES) AS TOTALSALES, (SUM(SALES)-SUM(PRICEEACH)) AS PROFIT
FROM sales_data_sample;

**5. Highest Orders City-wise**
SELECT CITY, COUNT(ORDERNUMBER) AS TOTALORDERS
FROM sales_data_sample
GROUP BY CITY;

**6. Highest Orders Country-wise**
SELECT COUNTRY, COUNT(ORDERNUMBER) AS TOTALORDERS
FROM sales_data_sample
GROUP BY COUNTRY;

**7. Average Sales**
SELECT AVG(SALES) FROM sales_data_sample;

**8. Customer Name with Max Sales**
SELECT CUSTOMERNAME, MAX(SALES) AS MAXIMUMSALES
FROM sales_data_sample
GROUP BY CUSTOMERNAME
ORDER BY MAXIMUMSALES DESC;

**9. Sales Year-wise**
SELECT YEAR_ID, COUNT(QUANTITYORDERED) AS TOTALORDERS
FROM sales_data_sample
GROUP BY YEAR_ID;

**10. Orders as per the Deal Size**
SELECT DEALSIZE, COUNT(QUANTITYORDERED) AS TOTALORDERS
FROM sales_data_sample
GROUP BY DEALSIZE
ORDER BY TOTALORDERS DESC;

**11. Profit Percentage as per Deal Size**
SELECT
    DEALSIZE,
    SUM(SALES) AS TOTAL_SALES,
    SUM(QUANTITYORDERED * PRICEEACH) AS TOTAL_COST,
    ((SUM(SALES) - SUM(QUANTITYORDERED * PRICEEACH)) / SUM(QUANTITYORDERED * PRICEEACH)) * 100 AS PROFIT_PERCENTAGE
FROM
    sales_data_sample
GROUP BY
    DEALSIZE;
**12. Total Profit and Sales**
SELECT SUM(SALES) AS TOTAL_SALES,
    SUM(QUANTITYORDERED * PRICEEACH) AS TOTAL_COST,
    ((SUM(SALES) - SUM(QUANTITYORDERED * PRICEEACH)) / SUM(QUANTITYORDERED * PRICEEACH)) * 100 AS PROFIT_PERCENTAGE,
    SUM(QUANTITYORDERED) AS TOTALORDERS
FROM sales_data_sample;

**License**
Feel free to use, modify, and distribute the code as you need.

**Acknowledgments**
Thank you for using this SQL analysis! If you have any questions or suggestions, please feel free to contact me. Happy analyzing!
