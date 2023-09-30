# Power-BI-Project(Credit Card Transactions)
This is a Project on Power BI for my internship on Advanced Data Science at Indo-Euro Synchronization
# Data Preperation
I used ChatGpt as a medium to create a sample data for this project according to my needs so the data here is fictional but can be used for the project
When creating a CSV file for credit card transaction data to use in your Power BI project, it's essential to include relevant information that allows for meaningful analysis and anomaly detection. Here's a list of common fields you should consider including in your credit card CSV dataset:

1. **Transaction Date and Time:** Include a timestamp for each transaction. This allows for time-series analysis and the identification of temporal patterns.

2. **Transaction Amount:** Include the amount of each transaction, as this is a critical factor in anomaly detection.

3. **Cardholder Name:** For a realistic dataset, you can include cardholder names. However, ensure that you maintain privacy and compliance with data protection regulations. Anonymize or pseudonymize real cardholder names if necessary.

4. **Card Number (Tokenized):** For privacy and security reasons, never include real card numbers in your dataset. Instead, use tokenized or masked card numbers.

5. **Merchant Information:** Include details about the merchant, such as merchant ID, merchant name, and merchant category code (MCC). This helps analyze transaction patterns based on merchant types.

6. **Transaction Type:** Indicate whether the transaction is a purchase, withdrawal, refund, or other transaction type. This can be valuable for distinguishing different transaction categories.

7. **Location Information:** Include the location or geographical data, such as city, state, and country, where the transaction occurred. Geospatial analysis can be helpful for identifying anomalies related to transaction locations.

8. **Currency:** Specify the currency used for each transaction. This is important for cross-currency analysis if your dataset involves international transactions.

9. **Payment Status:** Indicate whether the payment was approved, declined, or resulted in other outcomes. This helps in identifying potentially fraudulent transactions.
10. **Exploratory Data Analysis (EDA):
EDA is a crucial step in the data analysis process that involves visually and statistically examining your dataset. It aims to uncover patterns, relationships, and insights within the data. By creating visualizations, calculating summary statistics, and identifying anomalies, EDA provides a deeper understanding of the dataset's characteristics, helping inform subsequent analytical decisions and hypotheses. In this project, we leverage Power BI's EDA capabilities to gain valuable insights into credit card transactions, enabling better-informed fraud detection and decision-making.

11. **Transaction ID or Reference:** Include a unique identifier for each transaction. This can help track and refer to specific transactions.

12. **Additional Transaction Metadata:** Depending on the nature of your dataset and analysis goals, you may include additional fields such as transaction authorization codes, transaction source, or any other relevant metadata.

13. **Fraud Indicator (Optional):** If you have access to historical fraud data, you can include a field indicating whether a transaction was flagged as potentially fraudulent. This can be used for supervised learning and model evaluation.

Remember to anonymize or pseudonymize sensitive information like cardholder names and card numbers to protect privacy and comply with data protection regulations like GDPR and HIPAA. Additionally, consider the size of your dataset and ensure it contains a sufficient number of normal and anomaly cases to train and evaluate your anomaly detection algorithms effectively.

Lastly, you can generate synthetic data or use publicly available datasets with realistic credit card transaction information while ensuring that sensitive information is appropriately anonymized or masked.
# Exploratory Data Analysis (EDA):
EDA is a crucial step in the data analysis process that involves visually and statistically examining your dataset. It aims to uncover patterns, relationships, and insights within the data. By creating visualizations, calculating summary statistics, and identifying anomalies, EDA provides a deeper understanding of the dataset's characteristics, helping inform subsequent analytical decisions and hypotheses. In this project, we leverage Power BI's EDA capabilities to gain valuable insights into credit card transactions, enabling better-informed fraud detection and decision-making.

**Average Transaction Amount Calculation**
DAX QUERY:
 ```DAX
Average Transaction Amount = AVERAGE('creditcardtransaction'[Transaction_Amount])
 ```
**Anomaly Detection (Z-score):**
Anomaly detection is a critical component of this project, focused on identifying irregular or suspicious patterns within credit card transactions. We employ the Z-score method, a statistical approach, to pinpoint transactions that significantly deviate from the mean. By calculating the Z-scores for transaction amounts, we can highlight potential anomalies, allowing for enhanced fraud detection capabilities and informed decision-making.
**CALCULATING Z-score Transaction Amount**
DAX QUERY:
 ```DAX
Z-score Transaction Amount = 
VAR AvgAmount = AVERAGE('CreditCardTransaction'[Transaction_Amount])
VAR StdDevAmount = STDEV.P('creditcardtransaction'[Transaction_Amount])
RETURN ('creditcardtransaction'[Transaction_Amount] - AvgAmount) / StdDevAmount
 ```
# How to Set up alert rules in Power BI based on predefined thresholds ??
Certainly, here are step-by-step instructions for setting up alert rules in Power BI based on predefined thresholds:

**Step 1: Open Your Power BI Report**
- Launch Power BI Desktop and open the report you want to set up alert rules for.

**Step 2: Define the Metric to Monitor**
- Identify the specific metric or measure in your report that you want to monitor for anomalies or exceedance of thresholds. This could be, for example, the "Transaction Amount."

**Step 3: Create a Measure for the Threshold**
- If you don't already have a measure that represents the threshold value, create one. This measure will be used to define the threshold for triggering alerts.
- In Power BI Desktop, go to the "Model" view.
- Click "New Measure" from the Modeling tab.
- Create a measure like this (replace `1000` with your desired threshold value):
- 
  ```DAX
  Threshold Amount = 1000  // Replace with your desired threshold value
  ```

**Step 4: Create a Measure to Check Against the Threshold**
- Create a measure that calculates the metric you want to monitor. For example, to monitor the total transaction amount, create a measure like this:
- 
  ```DAX
  Total Transaction Amount = SUM('creditcardtransaction'[Transaction_Amount])
  ```

**Step 5: Set Up the Alert Rule in Power BI Service**
- Publish your report to the Power BI Service platform (https://app.powerbi.com/).
- Open the published report in Power BI Service.

**Step 6: Configure the Alert Rule**
- Click on the visual (chart or table) that represents the metric you want to set the alert for.
- In the right-hand pane, under "Visualizations," expand the "Alerts" section.
- Click "New Alert."

**Step 7: Configure Alert Settings**
- Configure the alert rule settings:
  - Set the condition (e.g., "Above").
  - Select the measure representing the metric to monitor (e.g., "Total Transaction Amount").
  - Choose the threshold measure (e.g., "Threshold Amount").
  - Set the alert sensitivity and frequency.
  - Provide a name and description for the alert.
  - Define the notification recipients (email addresses).

**Step 8: Save and Activate the Alert**
- Save the alert rule configuration.
- Activate the alert rule to start monitoring the metric based on the predefined threshold.

**Step 9: Test the Alert (Optional)**
- To test the alert, you can intentionally create or modify data in your dataset that triggers the alert condition you've set. You should receive email notifications when the alert condition is met.

**Step 10: Monitor and Manage Alerts**
- You can view, manage, and edit your alert rules in the Power BI Service platform. This allows you to fine-tune your alerting system as needed.

By following these step-by-step instructions, you can effectively set up alert rules in Power BI to receive notifications when predefined thresholds are exceeded or specific conditions are met in your data, enhancing your monitoring and decision-making capabilities.
---
----

## Conclusion

- Explored credit card transaction analysis using Power BI.
- Key components: data preparation, exploratory data analysis (EDA), and Z-score-based anomaly detection.
- EDA revealed transaction patterns and trends.
- Anomaly detection helps detect suspicious transactions.
- Future enhancements: advanced algorithms, continuous monitoring for improved fraud detection.

---

















