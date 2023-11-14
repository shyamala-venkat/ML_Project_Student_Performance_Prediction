##  ML Project - Student Performance Prediction

The goal is to predict the math score of students (Regression Analysis).

There are 7 independent variables:

1. gender - Male/ Female
2. race/ethnicity	- Group division from A to E
3. parental level of education	- Details of parental education varying from high school to master's degree
4. lunch	- Type of lunch selected
5. test preparation course	- Course details
6. reading score	- Marks secured by a student in Reading
7. writing score	- Marks secured by a student in Writing

Target variable:

math score	- Marks secured by a student in Mathematics

Dataset Source Link : https://www.kaggle.com/datasets/spscientist/students-performance-in-exams/data

## Steps followed in the project:

Data Ingestion :

The input data is read as csv file and the data is split into training and testing sets and saved as csv files.

Data Transformation :

Different transformations are applied depending on the nature of variables: Numerical, Categorical, Ordinal

Numeric variables: SimpleImputer transformation (with strategy = median) is applied to impute the missing values with median value and StandardScaler is applied to scale the values with 0 mean and unit standard deviation.
Categorical Variables SimpleImputer transformation (with strategy = most_frequent) is applied to impute the missing values with the most frequent values, OneHotEncoder,StandardScaler is applied.

These transformations are applied over the numerical and categorical variables and passed in a pipeline created using ColumnTransformer class.

This preprocessor object is saved as a pickle file for future use.

Model Training :

GridSearchCV is used to find the optimal values of the hyperparameters of different mdoels like Linear regression, Decision Tree, Random Forest, AdaBoost, CatBoost. 
The best model is selected which gave the highest r2_score and was used to predict the target value.
This model object is saved as a pickle file for future use.

Prediction Pipeline :

This pipeline is used to get the input user data, convert data to dataframe and make prediction using preprocessor and model pickle files.

Flask App creation :

A simple Flask app is created with UI to get the input user data and predict the final math score.
