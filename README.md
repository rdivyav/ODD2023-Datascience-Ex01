# Ex-01_DS_Data_Cleansing


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file
### STEP 5
Remove outliers using IQR
### STEP 6
Use zscore of to remove outliers
# CODE and OUTPUT
### import pandas as pd
### df=pd.read_csv("/content/SAMPLEIDS.csv")
### df

![Screenshot 2024-08-20 105954](https://github.com/user-attachments/assets/5312dd4a-8966-433b-867c-bc49f5a64be3)

### df.isnull().sum()

![Screenshot 2024-08-20 110159](https://github.com/user-attachments/assets/130faa65-8d48-44b5-8190-9b933352184b)

### df.isnull().any()

![Screenshot 2024-08-20 110307](https://github.com/user-attachments/assets/cf0ddd1f-bb95-4a8d-ae9d-b12dcc960675)

### df.dropna()

![Screenshot 2024-08-20 110423](https://github.com/user-attachments/assets/81a26686-a26d-4c47-b5c9-5bdba2986663)

### df.fillna(0)

![Screenshot 2024-08-20 110536](https://github.com/user-attachments/assets/5f1a6307-70cd-435e-8a97-6ddbedb2c7dd)

### df.fillna(method="ffill")

![Screenshot 2024-08-20 111041](https://github.com/user-attachments/assets/610b6cb7-d7ed-47a3-b3c7-adcc99442249)

### df.fillna(method='bfill')

![Screenshot 2024-08-20 111148](https://github.com/user-attachments/assets/ee22c617-303f-4b78-8746-8c3ffa18ddb9)

### df_dropped = df.dropna()
### df_dropped

![Screenshot 2024-08-20 111244](https://github.com/user-attachments/assets/c13740c5-84a4-4429-8adb-56e635977473)

### df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

![Screenshot 2024-08-20 111342](https://github.com/user-attachments/assets/9d8a3958-491e-4136-83f3-d097aa17a2d9)

### import pandas as pd
### ir=pd.read_csv('/content/iris.csv')
### ir

![Screenshot 2024-08-20 111435](https://github.com/user-attachments/assets/9dc572ac-d9dc-4e7c-8c6a-c1338e853f5f)

### ir.describe()

![Screenshot 2024-08-20 111520](https://github.com/user-attachments/assets/92661bd8-3909-4a40-9963-fd626df5833d)

### import seaborn as sns
### sns.boxplot(x='sepal_width',data=ir)

![Screenshot 2024-08-20 111610](https://github.com/user-attachments/assets/c5b558a9-f3ac-4104-b5aa-876f0e9b7f40)

### c1=ir.sepal_width.quantile(0.25)
### c3=ir.sepal_width.quantile(0.75)
### iq=c3-c1
### print(c3)

3.3

### rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
### rid['sepal_width']

![Screenshot 2024-08-20 111734](https://github.com/user-attachments/assets/d91c2361-a5dd-433e-9c4a-7891dcfb9996)

### delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
### delid

![Screenshot 2024-08-20 111823](https://github.com/user-attachments/assets/f27609ea-4d60-4339-bf3f-7e17648019b0)

### sns.boxplot(x='sepal_width',data=delid)

![Screenshot 2024-08-20 111911](https://github.com/user-attachments/assets/79c797a5-fd59-4810-b692-46fda54c5f49)

### import matplotlib.pyplot as plt
### import pandas as pd
### import numpy as np
### import scipy.stats as stats

### dataset = pd.read_csv('/content/heights.csv')
### dataset

![Screenshot 2024-08-20 112020](https://github.com/user-attachments/assets/1f543ad9-d45f-4d24-9883-185ff4f4eb9b)

### df = pd.read_csv('/content/heights.csv')
### q1=df['height'].quantile(0.25)
### q2=df['height'].quantile(0.5)
### q3=df['height'].quantile(0.75)
### iqr=q3-q1
### iqr

0.9249999999999998

### low=q1-1.5*iqr
### print(low)

3.8625000000000003

### high= q3+1.5*iqr
### print(high)

7.5625

### df1=df[(df['height']>=low) & (df['height']<=high)]
### df1

![Screenshot 2024-08-20 112508](https://github.com/user-attachments/assets/266570f1-86a8-4c4e-a006-4047b4c4fafc)

### z = np.abs(stats.zscore(df['height']))
### z

![Screenshot 2024-08-20 112708](https://github.com/user-attachments/assets/71b41ec3-3545-4333-997b-bc6750279e4b)

### df1=df[z<3]
### df1

![Screenshot 2024-08-20 112833](https://github.com/user-attachments/assets/eea34a6d-5aba-4fbe-aade-a5246b37495e)

### RESULT 
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method. 






