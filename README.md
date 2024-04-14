# <p align="center"> Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset </p>

# <p align="center"> ![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/d04d2145-18c7-4542-a76e-a8a6eb504e3a)
 
 </p>
 

## Overview

The Exploratory Data Analysis (EDA) and Visualization on Airbnb Dataset is a comprehensive examination of Airbnb data aimed at extracting meaningful insights and patterns. Airbnb is a popular platform for short-term lodging rentals, offering a vast array of properties worldwide. This dataset typically contains various attributes such as property type, location, price, availability, and host information.

**Tools:-** Excel,Python

[Datasets Used](Airbnb_Excel.xls)

[Python Script (Code)](Python_Project.ipynb)

## Requirements

- Python 3

- Libraries: NumPy, pandas, Sklearn, etc.

- Jupyter Lab


## Exploratory-Data-Analysis

```py
#To show the Attribotes and it's Datatype
a.info()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/630a408c-b25b-4e54-a947-ccdd1d9e6d08)

</p>

```py
#To show the Statistical Summary of a Dataset
a.describe()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/4bd99aa5-3f20-473a-ac8e-280824c4e8dd)


</p>

```py
#To check for Duplicates
b = a.duplicated().sum()
print("The total number of Duplicate values : ",b)
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/13b7f265-a6aa-4cdb-97e6-2d630abb4065)

</p>

```py
#To remove the ir-relevant Attributes column
e = a.drop(['license'],axis=1,inplace=True)
f = a.drop(['house_rules'],axis=1,inplace=True)
a.info()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/398282c6-5c26-464b-aa82-bbb1ffe90435)

</p>

```py
#To check for Null values
d = a.isnull().sum()
print("The total number of Null values : \n",d)
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/1a95b6fc-3074-4260-ad9f-43181776496b)

</p>

```py
#To Replace the Null values
a['NAME'].fillna(a['NAME'].mode().iloc[0],inplace=True)
a['host_identity_verified'].fillna(a['host_identity_verified'].mode().iloc[0],inplace=True)
a['host name'].fillna(a['host name'].mode().iloc[0],inplace=True)
a['neighbourhood group'].fillna(a['neighbourhood group'].mode().iloc[0],inplace=True)
a['neighbourhood'].fillna(a['neighbourhood'].mode().iloc[0],inplace=True)
a['country'].fillna(a['country'].mode().iloc[0],inplace=True)
a['country code'].fillna(a['country code'].mode().iloc[0],inplace=True)
a['instant_bookable'].fillna(a['instant_bookable'].mode().iloc[0],inplace=True)
a['cancellation_policy'].fillna(a['cancellation_policy'].mode().iloc[0],inplace=True)
a['Construction year'].fillna(a['Construction year'].mode().iloc[0],inplace=True)
a['minimum nights'].fillna(a['minimum nights'].mode().iloc[0],inplace=True)
#To rename the column  
a['service fee'] = a['service fee'].str.replace('$','')
a['price'] = a['price'].str.replace('$','')
a = a.rename(columns={'price':'price in dollars','service fee':'service fee in dollars'})
#To change the datatype
a['price in dollars'] = pd.to_numeric(a['price in dollars'], errors='coerce')
a['service fee in dollars'] = pd.to_numeric(a['service fee in dollars'], errors='coerce')
a['price in dollars'].fillna(a['price in dollars'].mean(),inplace =True)
a['service fee in dollars'].fillna(a['service fee in dollars'].mean(),inplace =True)
a['number of reviews'].fillna(a['number of reviews'].mode().iloc[0],inplace=True)
a['last review'].fillna(a['last review'].mode().iloc[0],inplace=True)
a['reviews per month'].fillna(a['reviews per month'].mean(),inplace=True)
a['review rate number'].fillna(a['review rate number'].mode().iloc[0],inplace=True)
a['calculated host listings count'].fillna(a['calculated host listings count'].mode().iloc[0],inplace=True)
a['availability 365'].fillna(a['availability 365'].mode().iloc[0],inplace=True)
```
```py
#a.isnull().sum()
a.isnull().sum()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/ba53d4a4-9efb-4f3a-9af7-753167c65ab8)

</p>

```py
#List the count of various room types available in the Dataset
g = a.groupby(['room type']).size()
g
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/9d8e6532-a266-488b-b620-3398c574dcd1)
</p>


```py
#Which room type has strict cancellation policy
h = a[a['cancellation_policy'] == 'strict']
i = h.groupby('room type').size()
i.sort_values().tail(1)
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/c9b247f3-8fa6-4025-8775-82babe735edc)

</p>

```py
#List the average price per neighborhood group
j = a.groupby('neighbourhood group')['price in dollars'].mean()
j
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/22902ff3-3cb5-42c3-96ad-520de536b999)

</p>

```py
#Most expensive neighborhood to rent from
k = a.groupby('neighbourhood group')['price in dollars'].mean()
k
k.sort_values().tail(1)
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/e6101ad9-c2e2-4568-b904-28c2689ea61d)

</p>

```py
#DATA VISUALIZATION
#List the count of various room types avaliable with Airnb
l = a.groupby('room type').size()
m = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(l,labels = m,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/d73bfce4-4936-4190-8841-dac679df0e70)

</p>

```py
#Which room type adheres to more strict cancellation policy
n = a[a['cancellation_policy'] == 'strict']
o = h.groupby('room type').size()
p = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(o,labels = p,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">!![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/10c515b2-ef89-4c66-a28b-5df4245d921a)

</p>

```py
#List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals
q = a.groupby('neighbourhood group')['price in dollars'].mean()
r = ['Bronx','Brooklyn','Manhattan','Queens','Staten Island','brookln','manhatan']
plt.pie(q,labels=r,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">!![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/b571eac4-481c-46d9-96b1-54987d48003e)

</p>


```py
#List the top 10 neighborhoods in the increasing order of their price with the help of a horizontal bar graph. Which is the cheapest neighborhood.
s = a.groupby('neighbourhood')['price in dollars'].mean().sort_values().head(10)
s.plot(kind='barh',color ='Red')
plt.show()
print("The cheapest neighborhood is :", s.sort_values().head(1))
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/d73e111e-3073-41b4-861a-f0c25dcc6408)

</p>

```py
#List the neighborhoods which offer short term rentals within 10 days.Illustrate with a bar graph
f = a.groupby('neighbourhood')['minimum nights'].mean().sort_values()
g = f.head(196)
plt.figure(figsize=(30, 6))
g.plot(kind='bar',color ='Red')
plt.title('neighborhoods which offer short term rentals within 10 days')
plt.xlabel('Neighbourhood')
plt.ylabel('minimum nights')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/440224d7-896b-4b15-b7e2-140b263a7ed6)

</p>

```py
#List the prices with respect to room type using a bar graph and also state your inferences.
d = a.groupby('room type')['price in dollars'].mean()
d.plot(kind='bar',color ='Red')
plt.title('prices with respect to room type')
plt.xlabel('room type')
plt.ylabel('prices')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/aa1473cd-630c-42b2-8bbf-9b0c051d1a13)

</p>

```py
#Create a pie chart that shows distribution of booked days for each neighborhood group 
x = a.groupby('neighbourhood group')['availability 365'].size()
y = ['Brooklyn','Bronx','Manhattan','Staten Island','Queens','brookln','manhatan']
plt.pie(x,labels = y,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/6b8cc643-cf10-41d2-bdc5-0109f4f27980)

</p>

```py
#Which neighborhood has the highest booking percentage
a.groupby('neighbourhood')['availability 365'].mean().sort_values().head(1)
```
Result : 
# <p align="center">![image](https://github.com/surajbisht06/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158066824/93b71d31-e387-49ed-a48f-ab03fa4fd7f0)

</p>
