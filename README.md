# https-username.github.io-uju_priscilla
Financial Analysis SQL Project

-- 10 SQL Queries for Stock Market Analysis
-- Data source: Kaggle
-- Table name: sp500_financials
-- ============================================

-- Query 1: Show all data (first 10 rows)
SELECT * FROM sp500_financials LIMIT 10;

-- Query 2: Count total companies
SELECT COUNT(Name) AS total_companies FROM sp500_financials;

-- Query 3: List companies by sector
SELECT Sector, COUNT(Name) AS company_count
FROM sp500_financials
GROUP BY Sector
ORDER BY company_count DESC;

-- Query 4: Top 10 most expensive stocks
SELECT Symbol, Name, Price
FROM sp500_financials
ORDER BY Price DESC
LIMIT 10;

-- Query 5: Stocks with highest dividend yield
SELECT Symbol, Name, `Dividend Yield`
FROM sp500_financials
WHERE `Dividend Yield` > 3
ORDER BY `Dividend Yield` DESC
LIMIT 10;

-- Query 6: Average price by sector
SELECT Sector, ROUND(AVG(Price), 2) AS average_price
FROM sp500_financials
GROUP BY Sector
ORDER BY average_price DESC;

-- Query 7: Find cheap stocks (under $50)
SELECT Symbol, Name, Price, Sector
FROM sp500_financials
WHERE Price < 50
ORDER BY Price;

-- Query 8: Technology sector analysis
SELECT Symbol, Name, Price, `Price/Earnings`
FROM sp500_financials
WHERE Sector = 'Information Technology'
ORDER BY Price DESC;

-- Query 9: High earnings per share
SELECT Symbol, Name, `Earnings/Share`
FROM sp500_financials
WHERE `Earnings/Share` > 10
ORDER BY `Earnings/Share` DESC;

-- Query 10: Companies near 52-week high
SELECT Symbol, Name, Price, `52 Week High`
FROM sp500_financials
WHERE Price > `52 Week High` * 0.9  -- Within 10% of high
ORDER BY Price DESC;
