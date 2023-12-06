# Bigmart-sales-predictive-modeling-project-using-python
## Summary:
### 1. Conclusions:
For the numeric variables, Item MRP and Outlet Age (retrieved from Outlet establishment year) are most important to predicting target variable Item outlet sales. For the categorical variables, all the variables except Item fat content is not important. This is a regression problem and the best model to predict sales is CatBoost Regressor. More details about the analysis can be found in later parts and in the jupyter notebook attached.
### 2. Challengages:
- There are not many numeric variables (only 3) to use so we have to retrieve the outlet age from Outlet establishment year to have more input into the model training
- The data is not clean yet with missing values (6455 values out of 14204 rows) and outliers
- Most numeric variables are skewed
### 3. Cool techniques:
In this analysis, we use different methods to:
- Cleaning data and manipulation:
    - Treat missing values using imputation with a normal distribution
    - Creating new feature (Outlet Age)
- Data analytics:
    - Using statistical analysis for descriptive analysis
    - Machine learning techniques: linear regression, regression tree, KNN regressor, CatBoost regressor, etc.
- Data visualization: matplotlib, plotly express
### 4. Where to get the data:
Data source: https://www.kaggle.com/datasets/thedevastator/bigmart-product-sales-factors
The dataset is about 1559 products across 10 stores in different cities, collected in 2013 by data scientists at BigMart. By exploring and analyzing this dataset, we can understand which factors really drive product sales.

## Analysis: below is the brief of the analysis, more details in the jupyter notebook attached
### 1. Objective:
This is an academic project I worked with my group in Predictive modeling course. The goal of the project is to see what factors affect the sales of a grocery store and create a model to predict sales.
## 2. Data exploration & Data cleaning:
- Remove irrelevant variables:
  - 'Item_Identifier' and 'Outlet_Identifier' are not necessary for predicting sales so we removed them
- Creating new attribute:
  - To make the most out of column 'Outlet_Establishment_Year', we created a new metric named Outlet_Age = 2023 - Outlet_Establishment_Year
- Checking & Fixing missing values:
  - Item_Weight: mean and median of this variables are pretty much the same, we might use mean imputation in this case. However, the number of missing values is too large (2439), using mean imputation might cause spike in the distribution. To be safe, we treat missing values of this column using values generated randomly from a normal distribution with same mean and standard deviation as that of this column
  - Outlet_Size: in this categorical variable, we decided to just remove these missing values, the remaining is 10188 records which are still good enough for prediction
- Remove negative values and outliers: during exploration, we found some negative values in Item_Weight which doesnt make sense so we removed them. We also found outliers using IQR method so we also exluded them from the dataset.
- Visualization: helps us to see the distribution of the variables (histogram), any outliers (boxplot), and correlation among variables (scatter plot)
## 3. Feature Engineering:
- Numeric variables: using Pearson correlation, Selectkbest with the f_regression, Backward method using Ordinary Least Squares (OLS) regression, Lasso regression. We put ranking of significance for each variable in each method, then combine all into one table and summarize the ranking by each variable. The smaller the ranking, the more important. Being said that, as we have only 4 variables, we decided to go with all. 
- Categorical variables: using ANOVA and  eliminated Item_Fat_Content.
## 4. Data preparation:
- Correct skewness of Item_Visibility using log10 transformation, we only applied this method to only this variable because most variables dont have much skewness, and this method helps reduce skewness of this variable only, other variables were transformed from positively to negatively skewed with bigger magnitude of skewness.
- Scaling all numeric variables using MinMaxScaler
- Convert chosen categorical variables into dummies before modeling
## 5. Model training:
We use different models to train the dataset and get a table of all measurement metrics including R-squared, MSE (mean squared error), RMSE (root mean squared error) to compare the models.
At the end we chose the CatBoost Regressor as the best model. Below is the visualization of the comparison, and display of the predicted and actual values of the CatBoost:
![model comparison](https://github.com/thanhhoaph/Bigmart-sales-predictive-modeling-project-using-python/assets/133604339/089061cf-73dc-49e6-bf8a-02aa2f080fa9)

![CB model](https://github.com/thanhhoaph/Bigmart-sales-predictive-modeling-project-using-python/assets/133604339/67298f05-31e6-4146-9ffc-c8501b164626)

## 6. Model testing:
Using new data to test with the model CatBoost and see the prediction it makes.

## 7. Team acknowledgement:
Irving Alejandro Covarrubias Medina

Alejandra Parrilla Guzman

Thanh Tung Nguyen



