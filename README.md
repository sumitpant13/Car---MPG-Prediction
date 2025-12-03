# Car Fuel Efficiency Prediction (MPG) — Linear Regression & Feature Selection

## Project Overview
The objective of this project is to predict a car’s fuel efficiency (Miles Per Gallon - MPG) based on its characteristics such as horsepower, weight, displacement, cylinders, etc. This is a regression problem where we apply feature engineering, outlier treatment, dimensionality checks, multicollinearity analysis, and model comparison across Linear, Ridge, Lasso, and ElasticNet regression.

## Dataset Summary
- Total Records: 398  
- Final usable records after cleaning: 392  
- Features: 8 predictors + 1 target  
- Target variable: `mpg` (float)

### Features:
- cyl (number of cylinders)  
- disp (engine displacement)  
- hp (horsepower)  
- wt (vehicle weight)  
- acc (acceleration)  
- yr (model year)  
- origin (country of manufacture)  
- car_name (removed due to high cardinality)  

## Data Cleaning & Preparation
- Corrected datatype of `hp` (from object → float)  
- Replaced '?' values with NaN  
- Removed rows with missing horsepower  
- Checked and removed outliers using IQR capping  
- Confirmed no duplicate rows  
- Dropped `car_name` column as non-informative  
- Standardized numeric features for stable regression  
- Verified feature correlations and VIF values  

## Exploratory Data Analysis
- Histograms to check distribution of each numeric feature  
- Boxplots to visually identify outliers  
- Heatmap for correlation  
- Scatter plots for mpg vs hp / mpg vs wt / mpg vs cyl  
- Observations:
  - mpg increases in newer model years  
  - heavier cars have worse fuel efficiency  
  - higher horsepower reduces mpg  
  - 4-cylinder vehicles are more fuel-efficient  

## Feature Selection
Applied:
- SelectKBest  
- RFE (Recursive Feature Elimination)  
- VIF (Variance Inflation Factor)

### Most informative features:
- wt  
- disp  
- hp  
- yr  
- origin  

Final selected feature set used for modelling:  
`origin`, `yr`, `wt`, `acc`

## Models Applied
- Linear Regression  
- Ridge Regression  
- Lasso Regression  
- ElasticNet Regression  
- Hyperparameter tuning using GridSearchCV for all regularized models  

## Model Performance Summary

| Model | Train R² | Test R² | Train RMSE | Test RMSE |
|------|---------|--------|-----------|-----------|
| Linear Regression | 0.8216 | 0.7794 | 3.15 | 4.04 |
| Ridge | 0.8216 | 0.7787 | 3.15 | 4.05 |
| Lasso | 0.7828 | 0.7109 | 3.47 | 4.63 |
| ElasticNet | 0.7397 | 0.6309 | 3.80 | 5.23 |
| Ridge (tuned) | 0.8216 | 0.7794 | 3.15 | 4.04 |
| Lasso (tuned) | 0.8216 | 0.7790 | 3.15 | 4.05 |
| ElasticNet (tuned) | 0.8216 | 0.7788 | 3.15 | 4.05 |

## Final Model Choice
**Linear Regression** was selected as the best performing model due to:
- Highest R² on test data (~0.78)  
- Lowest error (RMSE ≈ 4.04 mpg)  
- Stable generalization  
- No unnecessary regularization penalties required  
- Simple and interpretable  

## Model Interpretation
From coefficients:
- Heavier cars → lower MPG  
- Higher horsepower → lower MPG  
- Newer model year → higher MPG  
- Origin (country) influences fuel efficiency trends  

## Tools & Technologies Used
- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- Statsmodels  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

## Repository Structure
car-mpg.csv  
car_mpg_analysis.ipynb  
README.md  

## Conclusion
This project demonstrates regression modelling on automotive fuel efficiency with appropriate feature engineering and model comparison. The Linear Regression model provides the best balance of interpretability and predictive performance, making it suitable for estimating fuel efficiency from vehicle specifications.

## Author
**Sumit Pant**  
Email: sumitpant2004@gmail.com  
GitHub: https://github.com/sumitpant13  
LinkedIn: https://linkedin.com/in/sumitpant13
