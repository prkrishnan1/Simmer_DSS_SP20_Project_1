# DSS-SP20-Project1-Churn Prediction
Developing models to predict churn and increase user retention at Simmer using MixPanel app usage dataset. More information about Simmer can be found at https://usesimmer.com/. All of the iPython notebooks in this repository are cleaned and well documented for easy implementation.

## Repository Outline
The following files comprise our finished work of Simmer's Dish Churn Prediction project.

`/Simmer Data`

Input dataset pulled from MixPanel using JQL interfacing. Includes both Mixpanel events and People datasets.

`EDA.ipynb`

Merges the people and events datasets. Each column is cleaning and processed appropriately. This is then sent to our labeling and metric development notebooks. 

`Session_Labeling.ipynb`

Assigns unique session identifier numbers to each session in our events dataset. This will be used for labeling and metric development purposes. Assumes `cleaned_AllPeople.csv` is a correctly structured merged Mixpanel events-people dataset. Outputs the equivalent CSV `Cleaned_Events_With_SessionID.csv` which includes a sessionID column.

`cleaned_labeling.ipynb`

Assigns labels to each user in the dataset based on churn definition. Outputs a dataset with each row having a user id, user information, and a label. 

`Churn_Metrics.ipynb`

Develops member behavior metrics for each user in our people dataset. Calculates multiple metrics including Session Quality Score (SQS), Average Session Trends, # of ratings, etc. Assumes `Cleaned_Events_With_SessionID.csv` and `labeled_data.csv` have been correctly created. Outputs a new CSV, `labeled_data_with_metrics.csv`, which attaches columns for each metric indicating a user's score for the respective metric. This is the equivalent of `labeled_data.csv` with `# of metrics` columns attached.

`Modeling - Decision Trees + XGBoost.ipynb`

Includes any modeling using Decision Trees, Random Forest, XGBoost, and stacking previous models. Assumes `labeled_data_with_metrics.csv` has been correctly written to and splits this dataset for training and testing purposes. Any hyperparameter tuning functions and visualizations have also been included. Outputs `decision_tree.png`, a visualization of generated decision tree model as well as `RandomForest_Predicted_Churned.csv`, and `XGBoost_Predicted_Churned.csv` containing users which our model has predicted to have churned (indicated by `predicted_churned` column based off a 70/30 train-test split).

`Modeling - Logistic.ipynb`

Includes modeling using Logistic Regression and Support Vector Machines. Uses `labeled_data_with_metrics.csv`. Models are packaged implementations from Python's sklearn module. 



Compressed version of our end product. This dataset contains all original rows from `simmer_dish_data.csv`. All dishes are accompanied with boolean columns for each protein indicating whether the dish contains a specific protein and a final label column indicating all proteins that are contained in the respective dish. This was generated by `Dish Data Processing.ipynb` and manually compressed.

## Workflow

The following are the steps necessary to run through our data pipelining process:

1. Create necessary input datasets from MixPanel using JQL

2. Feed into `EDA.ipynb` for cleaning and merging. Outputs `cleaned_AllPeople.csv`.

3. Feed `cleaned_AllPeople.csv` into `Session_Labeling.ipynb` to generate session labels. Outputs `Cleaned_Events_With_SessionID.csv`.

4. Feed `Cleaned_Events_With_SessionID.csv` into `cleaned_labeling.ipynb` to generate churn labels. Outputs `labeled_data.csv`.

5. Feed `labeled_data.csv` and `Cleaned_Events_With_SessionID.csv` into `Churn_Metrics.ipynb` to generate member behavior metrics for each user. Our data, `labeled_data_with_metrics.csv`, is now ready to be modeled.

## Instructions for Consultants

Step 1: Clone the repo to your local computer 

Step 2: Create your own branch off of master 

Step 3: Create an iPython notebook with your labeling code inside. Name your iPython notebook with your labeling method and write down whoever worked on the notebook at the top of the notebook in a markdown cell.

Step 4: Add, commit, and push to your own branch 

Step 5: Make a pull request, and add Pranav and Rick as reviewers

## Properties

Authors: 
* [Pranav Krishnan](), 
* [Rick Zhang](https://github.com/wsxdrorange), 
* [Erica Zhu](https://github.com/zhuerica), 
* [Anna Waldorf](https://github.com/annawaldorf), 
* [Grace Qiu](https://github.com/graqiu), 
* [Jake Mercer](https://github.com/goldenscribe), 
* [Henry Cheong](https://github.com/heneong),
* [Charles Van](https://github.com/ccharlesvan)

This repository was created by the Data Science Society at Berkeley's (https://www.dssberkeley.com/) Simmer project team in Spring 2020. All work can be transferred to Simmer for implementation.
