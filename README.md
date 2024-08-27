# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

## READ CSV FILE HERE
```
df= pd.read_csv('Data_set.csv')
```
## DISPLAY THE INFORMATION ABOUT CSV AND RUN THE BASIC DATA ANALYSIS FUNCTIONS
```
print(df.describe())
```
## OUTPUT
![image](https://github.com/user-attachments/assets/fe6924ad-892d-4ffa-aa7a-3bf892d9c567)

## CHECK OUT NULL VALUES IN DATA SET USING FUNCTION
```
print(df.isnull().sum())
```
## OUTPUT
![image](https://github.com/user-attachments/assets/c7af01a4-2063-4b18-b88d-1d09be8d353c)

## DISPLAY THE SUM ON NULL VALUES IN EACH ROWS
```
print(df.isnull().sum(axis=1))
```
## OUTPUT
![image](https://github.com/user-attachments/assets/29bbad32-ac8b-4461-aedd-cdeb7fc00f36)

## DROP NULL VALUES
```
df.dropna()
```
## OUTPUT
![image](https://github.com/user-attachments/assets/c46e57ff-5a91-4535-8335-020b8b24fd27)

## FILL NULL VALUES WITH CONSTANT VALUE "O"
```
df.fillna("O")
```
## OUTPUT
![image](https://github.com/user-attachments/assets/79ef680d-42b1-4ef9-ac06-d34d0cb508fd)
 
## FILL NULL VALUES WITH ffill or bfill METHOD
```
df.fillna(method="ffill")
```
## OUTPUT
![image](https://github.com/user-attachments/assets/e17638f4-d882-493f-85b8-99851416740a)

## CALCULATE MEAN VALUE OF A COLUMN AND FILL IT WITH NULL VALUES
```
mean=df['num_episodes'].mean()
df.fillna(mean)
```
## OUT{UT
![image](https://github.com/user-attachments/assets/c8eda060-dbc2-4060-81ca-75cfcb33288c)

## DROP NULL VALUES
```
df.dropna()
```
## OUTPUT
![image](https://github.com/user-attachments/assets/73d5bc09-57d1-49a2-82b5-ffc1c4934116)

### NEXT DATA SET
```
import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
## USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```
sns.boxplot(af)
```
## OUTPUT
![download](https://github.com/user-attachments/assets/37bad882-136a-4e55-b667-e9526e50eb5b)
## PERFORM IQR METHOD AND DETECT OUTLIER VALUES
```
Q1=af.quantile(0.25)
Q3=af.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```
## OUTPUT
![image](https://github.com/user-attachments/assets/f87a74a6-88fe-4ed5-98fa-b3c046c3692a)

## REMOVE OUTLIERS
```
af=af[~((af<(Q1-1.5*IQR))|(af>(Q3+1.5*IQR))).any(axis=1)]
af
```
## OUTPUT
![image](https://github.com/user-attachments/assets/e02e720f-81ae-4287-b357-c5907c870137)

## USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```
sns.boxplot(af)
```
## OUTPUT
![download](https://github.com/user-attachments/assets/479792b0-d1c0-4baf-a943-2df2d4523d70)

## STATS METHOD IS USED TO IMPLEMENT Z SCORE METHOD
```
from scipy import stats
data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
```
## USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```
sns.boxplot(df)
```
## OUTPUT
![download](https://github.com/user-attachments/assets/49a7124d-7e88-410b-ad76-87da6d47c2d8)
## PERFORM Z SCORE METHOD AND DETECT OUTLIER VALUES
```
z=np.abs(stats.zscore(df))
print(z)
```
## OUTPUT
![image](https://github.com/user-attachments/assets/6cb021d7-21a3-431d-ae8c-45f0a3d18202)
## REMOVE OUTLIERS
```
df=df[(z<3).all(axis=1)]
df
```
## OUTPUT
![image](https://github.com/user-attachments/assets/dd381e33-9b30-4e9a-9a9f-8c5227524dc9)

## USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```
sns.boxplot(df)
```
## OUTPUT
![download](https://github.com/user-attachments/assets/d77e4151-4b95-44fb-9378-da5b958d1e07)

# Result
 thus the program to perform data cleaning and save the cleaned data to a file is successfully executed

