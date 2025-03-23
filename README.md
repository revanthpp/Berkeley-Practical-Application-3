# Berkeley-Practical-Application-3

**Business Problem Understanding**
A Portuguese bank seeks to improve the efficiency of its telemarketing campaigns for term deposit subscriptions. The goal is to predict whether a client will subscribe to a term deposit (y = yes/no) using historical campaign and client data. Accurately predicting this outcome allows the bank to:
1. Reduce wasted outreach on uninterested leads
2. Prioritize high-probability clients
3. Increase campaign ROI and customer satisfaction



**Data Understanding and Preparation**
**Dataset Overview**
The dataset was obtained from the UCI Machine Learning Repository and includes:
41,188 records and 20 features
Client demographic info (e.g. age, job, marital status)
Campaign-specific info (e.g. call duration, number of contacts)
Economic indicators (e.g. euribor3m, employment variation rate)

**Data Preparation Steps:**
1. Encoded categorical variables
2. Converted target y to binary (1 for yes, 0 for no)
3. Standardized features using StandardScaler
4. Split data (70% training, 30% test)


Four classifiers were trained and compared:

![image](https://github.com/user-attachments/assets/148ee756-91e5-4f68-8f0f-ac71f2ea661e)


Model	Accuracy	Precision (Class 1)	Recall (Class 1)	F1-score (Class 1)	ROC-AUC
Logistic Regression	0.91	0.68	0.40	0.50	0.93
Support Vector Machine	0.91	0.69	0.38	0.49	0.91
K-Nearest Neighbors	0.90	0.59	0.39	0.47	0.86
Decision Tree	0.89	0.49	0.52	0.50	0.72

**Key Findings:**
Logistic Regression had the highest AUC (0.93), indicating the strongest ability to distinguish between classes.
SVM performed similarly but was slightly more computationally intensive.
k-NN and Decision Tree struggled, especially with false positives and class imbalance.
Recall was low across all models, suggesting the bank should consider alternative threshold tuning or resampling techniques for minority class detection.

**Statistical Insights & Feature Importance**
**Correlation Analysis (Inferential Statistics):**
Top variables positively correlated with subscriptions:
1. duration (0.41): Longer calls lead to more conversions
2. previous (0.23): Previous campaign contacts matter
3. poutcome (0.13): Successful past outcomes are good predictors
4. education (0.06)
5. confidence index (0.05)

**Feature Importance from Logistic Regression:**
Top drivers of positive predictions:
emp.var.rate, duration, euribor3m, nr.employed
Surprisingly, some economic indicators had negative coefficients — indicating inverse relationships worth exploring further


 **Actionable Business Insights**
1. Agent Training Focus: Since duration strongly correlates with success, invest in better call scripting and coaching for agents to create meaningful conversations.
2. Target Warm Leads: Re-contacting clients with past positive outcomes (poutcome) or recent engagement (previous, pdays) is more likely to yield conversions.
3. Economic Awareness: Features like emp.var.rate and euribor3m indicate that external economic conditions impact client decisions. Consider aligning campaign timing with favorable economic trends.


**Recommendations & Next Steps**
1. Deploy Logistic Regression for lead scoring due to its accuracy and interpretability.
2. Tune model thresholds or apply SMOTE to improve recall on subscribed class.
3. Incorporate real-time data into predictions (e.g. recent contact updates).
4. A/B test campaign strategies with and without model-based prioritization to measure impact.
5. Periodically retrain the model to adapt to evolving client behavior and economic conditions.
