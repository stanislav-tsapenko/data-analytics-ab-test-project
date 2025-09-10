# A/B Test for E-commerce Platform

This project's Jupyter Notebook (`AB_test_e_commerce.ipynb`) calculates the statistical significance of key metrics from an A/B test on an e-commerce platform. The results are prepared for further visualization in Tableau.

---

## Project Goals
The main objective is to analyze the statistical significance of the differences between two test groups (A and B) for the following key metrics:

- **add_payment_info / session**  
- **add_shipping_info / session**  
- **begin_checkout / session**  
- **new_accounts / session**

The analysis uses a **Z-test for proportions** to determine if the observed differences are statistically significant (**p-value < 0.05**).

---

## Methodology

1. **Data Retrieval**  
   - The notebook connects to **Google BigQuery** using the `google-cloud-bigquery` library to fetch data from the `data-analytics-mate` project.

2. **SQL Query**  
   - A complex SQL query joins multiple tables (`ab_test`, `session`, `session_params`, `order`, `event_params`, `account_session`) to prepare the dataset.

3. **Data Cleaning**  
   - Data is loaded into a **Pandas DataFrame**.  
   - Performed cleaning steps: date format conversion, trimming text fields, and converting text to lowercase.

4. **Statistical Analysis**  
   - A loop iterates through test cases and metrics to calculate conversion rates for groups **A** and **B**.  
   - **Z-Test for proportions** (`statsmodels.stats.proportion.proportions_ztest`) is applied to compute Z-statistics and p-values.

5. **Results**  
   - Final results are returned as a dictionary, including:  
     - metric name  
     - conversion rates for groups A and B  
     - Z-statistic  
     - p-value  
     - significance flag (True if **p-value < 0.05**)  
   - The structured output is ready for further visualization in **Tableau**.

---

## Tools and Libraries

- **Python**  
- **Jupyter Notebook**  
- **Google BigQuery Client**  
- **Pandas**  
- **statsmodels.stats.proportion**  
- **SQL**

---
