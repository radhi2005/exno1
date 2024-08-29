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
```
        REGISTRATION NUMBER:212223040159
         NAME: RADHIMEENA M
```
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/ccc5856c-39d8-4529-933f-fef5f0aa1460)

```
df.head(6)
```
![image](https://github.com/user-attachments/assets/166900e9-0583-4381-9e5e-d488a5ab455d)

```
df.tail(6)
```
![image](https://github.com/user-attachments/assets/12147aad-085d-4ebf-b0be-d1cbe7328174)

```
df.isnull()
```
![image](https://github.com/user-attachments/assets/a4880b35-384b-4648-9833-e1f1fafce4db)
```
df.notnull()
```
![image](https://github.com/user-attachments/assets/ca628573-0823-4419-a064-cdbf51db51a1)
```
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/d91d4744-45a1-4322-a1e1-6f453e64fc56)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/15e35531-3bdd-4c01-a6d5-d4635e3641b0)

```
print(df.shape)
```
![image](https://github.com/user-attachments/assets/127100d9-9afa-4735-9fec-f492c09bbdd2)

```
df.describe()
```
![image](https://github.com/user-attachments/assets/9fa08721-3485-40f5-8e24-05859a834f13)
<h2>IQR</h2>
```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/288d1c69-471c-4cdd-9e1b-9a04ffcb27ba)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/7185fe39-576d-4560-8e80-ff7598aad662)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/5645c857-1f81-4eed-b2c5-4d287f2a870e)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/df65fcbc-6cf2-40fe-a59d-9368fc95e09d)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/b54d6f33-ec4e-448d-bb4e-068618c3c424)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/559d8b1f-1ea9-43d6-9a1e-7fc7ab509869)
<h2>Z_SCORE</h2>
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv('/content/heights.csv')
dataset
```
```
![image](https://github.com/user-attachments/assets/72827648-2330-40f3-bd00-c9b3f8bb9b42)
```
df=pd.read_csv('/content/heights.csv')
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)

iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/20901f26-01de-4880-bb3b-16377a272d88)

```
low=q1-1.4*iqr
low
```
![image](https://github.com/user-attachments/assets/26a6eee9-c191-48af-bb86-61523c8eb3f4)
```
high=q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/5c9fbed9-6584-4b48-ba93-1d8dc11c9413)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/bd5aa64d-fe94-4937-82b5-faae8507d714)
```
z=np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/ebb4fd90-6aa3-480b-bada-24422d6dbadc)

```
df1=df[z<3]
df
```
![image](https://github.com/user-attachments/assets/17547928-c444-4a23-8238-5747936a3771)



# Result
    Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
