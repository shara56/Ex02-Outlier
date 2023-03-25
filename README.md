# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
## ALGORITHM:
# STEP 1
Read the given Data.

# STEP 2
Get the information about the data.

# STEP 3
Detect the Outliers using IQR method and Z score.

# STEP 4
Remove the outliers.

# STEP 5
Plot the datas using Box Plot.

## PROGRAM:
```
DEVELOPED BY: SHARANGINI T K
REGISTER NUMBER: 212222230143
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT:
bhp.csv IQR METHOD

## df.head()
![image](https://user-images.githubusercontent.com/113497104/227721872-2a3fd2fa-4fce-4e7d-8e45-0eea1a9af2ee.png)

## df.describe()
![image](https://user-images.githubusercontent.com/113497104/227722423-ee2be566-2f53-4dbb-bae2-f83848126fab.png)

## df.info()
![image](https://user-images.githubusercontent.com/113497104/227722553-e8ba3f89-9f0d-4dbf-9228-f57ed6ad63e5.png)

## df.shape
![image](https://user-images.githubusercontent.com/113497104/227722568-712a8577-c37f-462b-ba08-5eea023b0191.png)

## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722581-45f77e77-a325-4b0c-bcb3-6eb2f308e00e.png)

## NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/113497104/227722596-62a13dd3-7d0e-4457-95dd-1b0f755620e7.png)

## OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722609-2ae09efe-1191-415b-81ba-25c6f53a43c0.png)

## newdata.shape
![image](https://user-images.githubusercontent.com/113497104/227722627-6a7a2a42-a61c-4125-a930-42a5f73ddc94.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/113497104/227722645-0eadc7d6-c2be-4001-8615-675e5b5eccfa.png)

## Zscore of 3

## NEWDATA USING Zscore
![image](https://user-images.githubusercontent.com/113497104/227722657-fd770d10-b55d-48ea-823f-14119f35d244.png)

## OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722667-40c67c46-6408-461a-bf61-d7a63a8d1e6d.png)

## newdata2.shape
![image](https://user-images.githubusercontent.com/113497104/227722677-45a89355-828f-40d1-8ff7-e1e6e36b3f6a.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://user-images.githubusercontent.com/113497104/227722686-50fe72aa-ddc2-40e7-8359-898dad7e868d.png)

## height_weight.csv
dataset.shape![image](https://user-images.githubusercontent.com/113497104/227722753-83a7ccfd-d637-458e-8f94-9e2cb3b626c1.png)

## dataset.describe()
![image](https://user-images.githubusercontent.com/113497104/227722827-02bc9c53-5d40-469c-8686-3c077da76f92.png)

## dataset.info()
![image](https://user-images.githubusercontent.com/113497104/227722843-24d870b3-2f69-41b8-b2a1-d55c79955d63.png)

## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722852-17c2945a-dacd-474c-8741-fae6ab46739e.png)

## HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722868-91910a90-c4ff-4a68-9e38-1dd735f183bb.png)

## DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722883-239bf0bb-b08a-41ae-8071-c3baf31e66d8.png)

## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722961-3ae76cd1-fbc1-45bc-806b-506714799e6d.png)

## WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722978-2ee00cb5-01c6-4063-96e2-dc40a371318f.png)

## DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227722992-68d5d5a7-d61d-4af9-93f0-8f0e0cac74ce.png)

## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497104/227723006-eb7addc5-62f3-4aa0-bded-3195085e1dc9.png)

## RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.

