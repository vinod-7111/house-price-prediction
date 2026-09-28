# House Price Prediction Using Machine Learning 🏠

A Machine Learning regression project that predicts residential house prices based on property characteristics such as bedrooms, bathrooms, living area, lot size, floors, condition, location, construction year, and other property-related features.

This project demonstrates a complete Machine Learning workflow, starting from data loading and exploratory data analysis to data cleaning, feature engineering, feature selection, preprocessing, model training, evaluation, and model comparison.

---

## 📌 Project Overview

House price prediction is a regression problem where the objective is to estimate the price of a property based on its characteristics.

In this project, multiple regression algorithms are trained and evaluated to understand how different Machine Learning models perform on the house price dataset.

The project covers:

- Data Loading
- Data Inspection
- Exploratory Data Analysis
- Data Cleaning
- Feature Engineering
- Feature Selection
- Target Leakage Prevention
- Feature Type Identification
- Data Preprocessing
- Train-Test Split
- Machine Learning Pipeline
- Model Training
- Prediction
- Model Evaluation
- Model Comparison
- Visualization

---

# 📂 Dataset

The dataset contains **4,600 records** and **18 original columns** related to residential properties.

## Original Features

| Feature | Description |
|---|---|
| `date` | Date associated with the property record |
| `price` | Target variable representing the house price |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `sqft_living` | Living area in square feet |
| `sqft_lot` | Lot area in square feet |
| `floors` | Number of floors |
| `waterfront` | Indicates whether the property has waterfront access |
| `view` | View quality rating |
| `condition` | Overall condition of the property |
| `sqft_above` | Square footage above ground |
| `sqft_basement` | Square footage of basement |
| `yr_built` | Year the property was built |
| `yr_renovated` | Year the property was renovated |
| `street` | Street address |
| `city` | City where the property is located |
| `statezip` | State and ZIP code |
| `price_per_sqft` | Price per square foot |

---

# 🎯 Target Variable

The target variable for this project is:

**`price`**

The Machine Learning models are trained to predict the residential property price based on the available property features.

---

# 🔍 Data Loading and Inspection

The dataset was loaded and inspected to understand:

- Number of rows and columns
- Data types
- Missing values
- Duplicate records
- Statistical summary
- Numerical features
- Categorical features
- Target variable distribution

Initial dataset size:

**4,600 rows × 18 columns**

---

# 📊 Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the relationships between property characteristics and house prices.

The analysis included:

- Distribution of house prices
- Distribution of numerical features
- Correlation analysis
- Price relationships with property characteristics
- Categorical feature analysis
- Identification of potential data quality issues

### Important Correlations with Price

Some features showed stronger relationships with the target variable, including:

- `sqft_living`
- `sqft_above`
- `bathrooms`
- `view`
- `sqft_basement`
- `bedrooms`
- `floors`
- `waterfront`
- `sqft_lot`
- `condition`

These relationships were analyzed during the exploratory analysis stage.

---

# 🧹 Data Cleaning

Data cleaning was performed before model training.

The dataset contained invalid target values where the house price was zero.

These invalid records were removed because a zero house price is not a valid target value for this prediction problem.

After removing invalid price records, the cleaned dataset contained approximately:

**4,551 valid records**

The cleaned dataset was then used for feature preparation and model training.

---

# ⚙️ Feature Engineering

Feature engineering was performed to extract useful information from the existing features.

The `date` feature was converted into a proper date format and separated into:

- `year`
- `month`
- `day`

The original `date` column was then removed after extracting these useful components.

This allows the Machine Learning models to use meaningful numerical representations of the date information.

---

# 🎯 Feature Selection

Feature selection was performed to avoid unnecessary or potentially problematic variables.

The following columns were excluded from model training:

### `price`

This is the target variable and therefore cannot be used as an input feature.

### `price_per_sqft`

This feature was excluded because it is directly derived from the house price and could introduce **target leakage** into the Machine Learning model.

### `street`

The street address was excluded because it is a high-cardinality location feature and would create a large number of unique categorical values without providing an efficient representation for the selected models.

---

# 🔤 Feature Type Identification

The remaining features were separated into numerical and categorical variables.

## Numerical Features

Examples include:

- `bedrooms`
- `bathrooms`
- `sqft_living`
- `sqft_lot`
- `floors`
- `waterfront`
- `view`
- `condition`
- `sqft_above`
- `sqft_basement`
- `yr_built`
- `yr_renovated`
- `year`
- `month`
- `day`

## Categorical Features

The main categorical features include:

- `city`
- `statezip`

Identifying feature types allows the appropriate preprocessing technique to be applied to each group.

---

# 🛠️ Data Preprocessing

Different preprocessing techniques were applied to numerical and categorical features.

## Numerical Features

Numerical features were standardized using:

**StandardScaler**

This transforms numerical variables to a common scale.

## Categorical Features

Categorical features were converted into numerical representations using:

**OneHotEncoder**

The encoder was configured to:

- Handle previously unseen categories
- Drop the first category to reduce redundant encoded variables

---

# 🔗 Preprocessing Pipeline

A Scikit-learn `ColumnTransformer` was used to apply different preprocessing operations to numerical and categorical features.

The preprocessing stage was combined with each Machine Learning model using a Machine Learning pipeline.

This ensures that the same preprocessing steps are consistently applied during both training and prediction.

---

# ✂️ Train-Test Split

The cleaned dataset was divided into training and testing sets.

The split used:

- **80% Training Data**
- **20% Testing Data**
- **Random State: 42**

The training dataset was used to train the Machine Learning models, while the testing dataset was used to evaluate their performance on unseen data.

---

# 🤖 Machine Learning Models

Four regression algorithms were implemented and compared.

## 1. Linear Regression

Linear Regression was used as a baseline regression model for predicting house prices.

It attempts to model the relationship between the input features and the target price using a linear relationship.

---

## 2. Random Forest Regression

Random Forest Regression combines multiple decision trees to produce predictions.

It can capture nonlinear relationships between property characteristics and house prices.

Configuration used:

- 200 estimators
- Random state: 42
- Parallel processing enabled

---

## 3. Gradient Boosting Regression

Gradient Boosting Regression builds multiple models sequentially, with each new model attempting to improve the errors made by previous models.

Configuration used:

- 200 estimators
- Learning rate: 0.05
- Maximum depth: 5
- Random state: 42

---

## 4. Decision Tree Regression

Decision Tree Regression predicts house prices by learning a series of decision rules from the training data.

Configuration used:

- Maximum depth: 15
- Random state: 42

---

# 📈 Model Evaluation

The trained models were evaluated using the following regression metrics:

## R² Score

R² Score measures how much of the variation in the target variable is explained by the model.

A higher R² value indicates that the model explains more variance in the target data.

---

## R² Percentage

R² Percentage represents the R² score as a percentage for easier interpretation.

---

## MAE

Mean Absolute Error measures the average absolute difference between actual and predicted house prices.

Lower MAE indicates smaller average prediction errors.

---

## MSE

Mean Squared Error measures the average squared difference between actual and predicted values.

Larger errors receive greater weight because the errors are squared.

---

## RMSE

Root Mean Squared Error is the square root of MSE.

It represents prediction error in the same unit as the target variable.

Lower RMSE indicates smaller prediction errors.

---

# 📌 Model Evaluation Observations

Based on the test-set results:

- Linear Regression achieved an R² Score of **0.691039**.
- Linear Regression explained approximately **69.10%** of the variance in the test data.
- Linear Regression recorded an MAE of approximately **121,516.15**.
- Random Forest produced an R² Score of **-0.470101**.
- Gradient Boosting produced an R² Score of **-2.629812**.
- Decision Tree produced an R² Score of **-9.922804**.

The negative R² values for the tree-based models indicate that, under the evaluated configuration and test split, their predictions performed worse than the baseline represented by predicting the mean target value.

---

# 📊 Visualization

Several visualizations were created to understand the dataset and model performance.

The project includes visualizations for:

- House price distribution
- Feature distributions
- Correlation analysis
- Model R² comparison
- Model RMSE comparison
- Model MAE comparison
- Actual vs Predicted Prices
- Actual and Predicted Price Comparison

These visualizations help interpret the performance of the regression models.

---

# 🔄 Complete Machine Learning Workflow

The complete project workflow can be summarized as:

**Data Loading**

↓

**Data Inspection**

↓

**Exploratory Data Analysis**

↓

**Data Cleaning**

↓

**Feature Engineering**

↓

**Feature Selection**

↓

**Feature Type Identification**

↓

**Data Preprocessing**

↓

**Train-Test Split**

↓

**Machine Learning Pipeline**

↓

**Model Training**

↓

**Prediction**

↓

**Model Evaluation**

↓

**Model Comparison**

↓

**Visualization**

---

# 🧰 Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- VS Code
- Git
- GitHub

---

# 📦 Project Requirements

The main Python libraries used in this project include:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter

The required dependencies are listed in the `requirements.txt` file.

---

# 📁 Project Structure

- `Data/`
  - `house_price_data.csv`
- `Notebook/`
  - `House_Price_Prediction.ipynb`
- `README.md`
- `requirements.txt`
- `.gitignore`

---

# ▶️ How to Run the Project

1. Clone or download the repository.
2. Open the project folder in VS Code, Jupyter Notebook, Google Colab.
3. Install the dependencies listed in `requirements.txt`.
4. Open the Jupyter Notebook located inside the `Notebook` folder.
5. Run the notebook cells sequentially.
6. The dataset will be loaded from the `Data` folder.
7. Review the EDA, preprocessing, model training, evaluation, and visualization results.

---

# 🎓 Key Learning Outcomes

Through this project, I gained practical experience in:

- Understanding regression problems
- Performing exploratory data analysis
- Cleaning real-world datasets
- Handling invalid target values
- Creating features from date information
- Selecting relevant features
- Identifying target leakage
- Handling numerical and categorical features
- Scaling numerical variables
- Encoding categorical variables
- Building Scikit-learn preprocessing pipelines
- Training multiple regression models
- Evaluating Machine Learning models
- Comparing regression performance
- Visualizing model predictions
- Using Git and GitHub for project version control

---

# ⭐ Project Highlights

- End-to-end Machine Learning regression project
- Real-world house price dataset
- Complete EDA workflow
- Data cleaning and validation
- Date-based feature engineering
- Target leakage prevention
- Numerical feature scaling
- Categorical feature encoding
- ColumnTransformer preprocessing
- Scikit-learn Machine Learning pipelines
- Multiple regression algorithms
- Multiple evaluation metrics
- Model comparison
- Prediction visualization
- GitHub-ready project structure

---

# 🚀 Future Improvements

Future versions of this project could include:

- Hyperparameter tuning
- Cross-validation
- Feature importance analysis
- Advanced ensemble models
- XGBoost or other boosting algorithms
- Log transformation of the target variable
- Outlier treatment
- Advanced location-based feature engineering
- Additional feature selection techniques
- Model deployment using Streamlit or Flask
- Interactive house price prediction interface

---

# 🎯 Project Purpose

The main purpose of this project is to demonstrate the complete workflow of building a Machine Learning regression solution, from raw data preparation through model evaluation and visualization.

It is designed as a practical Machine Learning portfolio project demonstrating data analysis, feature engineering, preprocessing, model development, and evaluation skills.

---
