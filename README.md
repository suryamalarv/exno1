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

# Coding
# Data Cleaning
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/95514552-11c7-4030-aa36-9bb8e601772d)
```
 df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/e2625724-7c7e-459f-b146-fb7110da92d6)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/18bd7834-80d5-49a5-bd42-dd524c45b251)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/54194795-4cdc-4fae-a020-f055b305dcf3)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/e7909869-121b-4995-a3a3-506c604be789)
```
df.fillna(method = 'ffill')
```

![image](https://github.com/user-attachments/assets/8b25be75-4ef3-4018-82b7-45e98b1996c4)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/8d0ad56d-83d5-48bf-9028-e7e4c98cf6cb)
```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/2f59a7bf-b58c-4901-a39a-1ceef1864f61)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/c739f4c9-27f9-4506-bc5b-71e732ae51b9)
```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/e560bd91-97c2-409d-a930-f0e440859867)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/c96e28c3-c7d7-4d26-aaa3-1cf12c1bedd8)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/532f93bd-f53e-4682-a15b-bc528d2ef485)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/c1fe2342-e047-4b35-a6aa-6f5c83fa3c47)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/9cdc9eda-cbc8-4c50-a034-99d2fc8af7c1)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/63b54423-592a-454c-af9f-7e13ae706b79)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/bc4277ec-0a72-4666-83e7-e32fcc33325c)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/23f4c4fa-749e-489d-851d-4f200d043631)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/a3b93ac2-b7cc-49c5-b882-5182f463b31b)
```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/38099042-9979-46c9-97be-c6a69c4fdb67)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f7c2cb17-2406-472a-b282-64bfb2990424)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/764048e6-4bbb-40f9-8fbd-6cc301417f41)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/413491a2-1cfe-40a5-9fca-eb7de1ab6a9a)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/7afe68bf-b838-4f0e-ba9d-56afadac0ca1)

# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
     
