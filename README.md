# Customer Churn Prediction

## Overview

Customer churn is one of the biggest challenges faced by subscription-based businesses. Losing existing customers is often more expensive than acquiring new ones. This project builds a machine learning model that predicts whether a customer is likely to churn based on demographic information, account details, and service usage patterns.

The project follows a complete end-to-end machine learning pipeline, starting from data exploration and preprocessing to model evaluation and deployment using Streamlit.

---

## Objectives

* Analyze customer behavior and identify factors contributing to churn.
* Build multiple machine learning models for churn prediction.
* Compare models using appropriate evaluation metrics.
* Select the best-performing model for deployment.
* Develop an interactive web application for real-time predictions.

---

## Dataset

The dataset contains customer information such as:

* Customer demographics
* Contract type
* Internet service
* Payment method
* Monthly charges
* Total charges
* Tenure
* Additional subscribed services
* Churn status (Target Variable)

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)

Before training any model, exploratory data analysis was performed to understand the dataset.

The following analyses were carried out:

* Missing value analysis
* Duplicate record checking
* Data type inspection
* Target variable distribution
* Numerical feature distributions
* Categorical feature analysis
* Correlation analysis
* Feature relationships with churn
* Outlier inspection

Visualizations included:

* Count plots
* Histograms
* Heatmaps
* Bar charts

These analyses helped understand customer behavior and identify important patterns before preprocessing.

---

### 2. Data Preprocessing

The following preprocessing steps were applied:

* Removed unnecessary columns (e.g., Customer ID)
* Converted appropriate columns to numerical format
* Handled missing values
* Encoded categorical variables using Label Encoding
* Split the dataset into training and testing sets

---

### 3. Feature Engineering

Feature engineering was performed to improve the predictive capability of the models.

This included:

* Encoding categorical variables
* Creating machine-learning-friendly features
* Selecting meaningful predictors
* Preparing the dataset for different algorithms

For Logistic Regression, numerical features were standardized using StandardScaler because the algorithm is sensitive to feature scale.

Random Forest and XGBoost were trained on the original feature scale since tree-based algorithms do not require feature scaling.

---

### 4. Handling Class Imbalance

The dataset exhibited class imbalance, with significantly fewer churned customers than retained customers.

To address this, SMOTE (Synthetic Minority Over-sampling Technique) was applied to the training data for Classification, enabling the model to learn equally from both classes.

---

## Models Evaluated

Three machine learning algorithms were trained and compared:

### Logistic Regression

Used as the baseline model.

Advantages:

* Simple and interpretable
* Fast training
* Good baseline for binary classification

Limitations:

* Assumes a linear relationship
* Lower capability for capturing complex interactions

---

### Random Forest Classifier

A bagging ensemble algorithm that builds multiple decision trees and combines their predictions.

Advantages:

* Captures nonlinear relationships
* Robust to overfitting
* Handles mixed feature types well
* No feature scaling required

Hyperparameter tuning was performed to improve performance.

---

### XGBoost Classifier

A boosting algorithm that sequentially improves weak learners by correcting previous errors.

Advantages:

* Excellent predictive performance
* Handles complex relationships
* Strong regularization
* Efficient for structured/tabular datasets

Hyperparameter tuning was performed to improve performance.

---

## Model Evaluation

Instead of relying only on accuracy, multiple evaluation metrics were used:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix
* ROC-AUC Score
* ROC Curve

Since customer churn prediction is an imbalanced classification problem, ROC-AUC was treated as the primary evaluation metric because it measures how effectively a model distinguishes churning customers from non-churning customers across different classification thresholds.

---

## Model Comparison

All three models were evaluated on the same test dataset.

Although each model produced competitive accuracy, Random Forest achieved the strongest balance across evaluation metrics and produced the highest ROC-AUC score.

Because ROC-AUC is particularly important for churn prediction, Random Forest was selected as the final model for deployment.

---

## Final Model

**Selected Model:** Random Forest Classifier

Reasons for selection:

* Highest ROC-AUC score
* Strong overall classification performance
* Better balance between Precision and Recall
* Robust against overfitting
* Handles nonlinear relationships effectively
* Does not require feature scaling

The trained model was serialized using Joblib and integrated into a Streamlit application for real-time customer churn prediction.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Plotly
* Scikit-learn
* XGBoost
* Joblib
* Streamlit

---

## Future Improvements

Possible enhancements include:

* Hyperparameter optimization using Bayesian Optimization or Optuna
* Probability calibration for better confidence estimates
* Feature importance analysis using SHAP values
* Cost-sensitive learning for highly imbalanced datasets
* Cross-validation with additional datasets
* Model monitoring and periodic retraining
* Deployment on cloud platforms such as Streamlit Community Cloud, Render, or AWS

---

## Conclusion

This project demonstrates a complete machine learning workflow for customer churn prediction, from exploratory data analysis and preprocessing to model comparison and deployment. Multiple algorithms were evaluated using comprehensive performance metrics rather than accuracy alone. Based on the experimental results, Random Forest was selected as the final model due to its superior ROC-AUC score and balanced classification performance, making it well-suited for identifying customers at risk of churn.

ROC Curve Comparision
<img width="862" height="677" alt="Screenshot (265)" src="https://github.com/user-attachments/assets/d26eb5df-914f-49df-8777-66e6070ac21e" />

Streamlit app interface
<img width="1920" height="910" alt="Screenshot (272)" src="https://github.com/user-attachments/assets/b10201e0-12dc-456c-9851-b33861692e18" />
<img width="1920" height="914" alt="Screenshot (273)" src="https://github.com/user-attachments/assets/1de01cdb-a38f-415a-9e1f-c31ac660ba40" />
