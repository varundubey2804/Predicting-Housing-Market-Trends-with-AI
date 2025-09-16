# Predicting-Housing-Market-Trends-with-AI
This project builds and evaluates regression models to predict house prices using the Kaggle competition dataset "House Prices: Advanced Regression Techniques".

Project Overview

The goal is to predict the final sale price of homes based on various features such as overall quality, year built, total square footage, and neighborhood characteristics.
The pipeline includes:

Data loading and preprocessing

Handling missing values

Feature engineering

Encoding categorical variables

Model training and evaluation (Linear Regression and XGBoost)

Generating predictions for submission to Kaggle

Steps
1. Setup Kaggle API

Download kaggle.json from your Kaggle account (under Account Settings > API > Create New API Token).

Upload it in Colab and configure permissions to access Kaggle datasets.

2. Dataset Download

The dataset is pulled directly from Kaggle:

Competition: house-prices-advanced-regression-techniques

Files: train.csv, test.csv

3. Data Preprocessing

Set Id column as index.

Handle missing values:

Fill numerical columns with 0 or median values by neighborhood.

Fill categorical columns with None or mode values.

Special handling for GarageYrBlt.

Create new features:

TotalSF = total square footage of basement + first and second floors.

TotalBath = total bathrooms including basement baths.

Age = age of the house at sale.

Log-transform the target variable SalePrice to reduce skewness.

4. Feature Encoding and Scaling

One-hot encode categorical variables.

Scale numerical features using StandardScaler for Linear Regression.

5. Model Training

Linear Regression: Trained on scaled data (but showed limited performance).

XGBoost Regressor: Trained on unscaled data with tuned hyperparameters:

n_estimators=1000

learning_rate=0.05

max_depth=3

subsample=0.8

colsample_bytree=0.8

6. Model Evaluation

Metrics used:

RMSE (Root Mean Squared Error)

MAE (Mean Absolute Error)

R-squared

7. Prediction and Submission

Predictions generated on the test set using XGBoost.

Reverse log transformation applied using np.expm1.

Submission file submission.csv created with columns:

Id

SalePrice

Results

XGBoost performed significantly better than Linear Regression.

Final predictions were formatted for Kaggle submission.
