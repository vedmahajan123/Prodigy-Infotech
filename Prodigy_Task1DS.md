```python
!pip install pandas matplotlib seaborn
```

    Requirement already satisfied: pandas in c:\users\asus\miniconda3\lib\site-packages (2.3.1)
    Requirement already satisfied: matplotlib in c:\users\asus\miniconda3\lib\site-packages (3.10.3)
    Collecting seaborn
      Using cached seaborn-0.13.2-py3-none-any.whl.metadata (5.4 kB)
    Requirement already satisfied: numpy>=1.26.0 in c:\users\asus\miniconda3\lib\site-packages (from pandas) (2.3.1)
    Requirement already satisfied: python-dateutil>=2.8.2 in c:\users\asus\miniconda3\lib\site-packages (from pandas) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in c:\users\asus\miniconda3\lib\site-packages (from pandas) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in c:\users\asus\miniconda3\lib\site-packages (from pandas) (2025.2)
    Requirement already satisfied: contourpy>=1.0.1 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (1.3.2)
    Requirement already satisfied: cycler>=0.10 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (0.12.1)
    Requirement already satisfied: fonttools>=4.22.0 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (4.59.0)
    Requirement already satisfied: kiwisolver>=1.3.1 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (1.4.8)
    Requirement already satisfied: packaging>=20.0 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (24.2)
    Requirement already satisfied: pillow>=8 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (11.3.0)
    Requirement already satisfied: pyparsing>=2.3.1 in c:\users\asus\miniconda3\lib\site-packages (from matplotlib) (3.2.3)
    Requirement already satisfied: six>=1.5 in c:\users\asus\miniconda3\lib\site-packages (from python-dateutil>=2.8.2->pandas) (1.17.0)
    Using cached seaborn-0.13.2-py3-none-any.whl (294 kB)
    Installing collected packages: seaborn
    Successfully installed seaborn-0.13.2
    


```python

```


```python
# Import required libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Set Seaborn style for plots
sns.set(style="whitegrid")
```


```python
# Read the file and skip the first 4 rows which contain metadata
df = pd.read_csv("API_SP.POP.TOTL_DS2_en_csv_v2_38144.csv", skiprows=4)

# Show the first few rows
df.head()


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
      <th>2022</th>
      <th>2023</th>
      <th>2024</th>
      <th>Unnamed: 69</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Aruba</td>
      <td>ABW</td>
      <td>Population, total</td>
      <td>SP.POP.TOTL</td>
      <td>54922.0</td>
      <td>55578.0</td>
      <td>56320.0</td>
      <td>57002.0</td>
      <td>57619.0</td>
      <td>58190.0</td>
      <td>...</td>
      <td>108727.0</td>
      <td>108735.0</td>
      <td>108908.0</td>
      <td>109203.0</td>
      <td>108587.0</td>
      <td>107700.0</td>
      <td>107310.0</td>
      <td>107359.0</td>
      <td>107624.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Population, total</td>
      <td>SP.POP.TOTL</td>
      <td>130075728.0</td>
      <td>133534923.0</td>
      <td>137171659.0</td>
      <td>140945536.0</td>
      <td>144904094.0</td>
      <td>149033472.0</td>
      <td>...</td>
      <td>623369401.0</td>
      <td>640058741.0</td>
      <td>657801085.0</td>
      <td>675950189.0</td>
      <td>694446100.0</td>
      <td>713090928.0</td>
      <td>731821393.0</td>
      <td>750503764.0</td>
      <td>769294618.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>AFG</td>
      <td>Population, total</td>
      <td>SP.POP.TOTL</td>
      <td>9035043.0</td>
      <td>9214083.0</td>
      <td>9404406.0</td>
      <td>9604487.0</td>
      <td>9814318.0</td>
      <td>10036008.0</td>
      <td>...</td>
      <td>34700612.0</td>
      <td>35688935.0</td>
      <td>36743039.0</td>
      <td>37856121.0</td>
      <td>39068979.0</td>
      <td>40000412.0</td>
      <td>40578842.0</td>
      <td>41454761.0</td>
      <td>42647492.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Africa Western and Central</td>
      <td>AFW</td>
      <td>Population, total</td>
      <td>SP.POP.TOTL</td>
      <td>97630925.0</td>
      <td>99706674.0</td>
      <td>101854756.0</td>
      <td>104089175.0</td>
      <td>106388440.0</td>
      <td>108772632.0</td>
      <td>...</td>
      <td>429454743.0</td>
      <td>440882906.0</td>
      <td>452195915.0</td>
      <td>463365429.0</td>
      <td>474569351.0</td>
      <td>485920997.0</td>
      <td>497387180.0</td>
      <td>509398589.0</td>
      <td>521764076.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>AGO</td>
      <td>Population, total</td>
      <td>SP.POP.TOTL</td>
      <td>5231654.0</td>
      <td>5301583.0</td>
      <td>5354310.0</td>
      <td>5408320.0</td>
      <td>5464187.0</td>
      <td>5521981.0</td>
      <td>...</td>
      <td>29183070.0</td>
      <td>30234839.0</td>
      <td>31297155.0</td>
      <td>32375632.0</td>
      <td>33451132.0</td>
      <td>34532429.0</td>
      <td>35635029.0</td>
      <td>36749906.0</td>
      <td>37885849.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 70 columns</p>
</div>




```python
# Keep only the columns we need
df_simple = df[["Country Name", "2020"]].dropna()
df_simple.columns = ["Country", "Population"]

# Convert population to integer
df_simple["Population"] = df_simple["Population"].astype(int)

```

# 1. Bar Chart: Top 10 populous countries


```python
top10 = df_simple.sort_values(by="Population", ascending=False).head(10)
plt.figure(figsize=(10,5))
plt.bar(top10["Country"], top10["Population"], color='skyblue')
plt.title("Top 10 Most Populous Countries (2020)")
plt.xticks(rotation=45)
plt.ylabel("Population")
plt.show()
```


    
![png](output_6_0.png)
    


# 2. Histogram: Distribution of country populations


```python
plt.figure(figsize=(10,5))
plt.hist(df_simple["Population"], bins=20, color='orange')
plt.title("Histogram of Population of Countries (2020)")
plt.xlabel("Population")
plt.ylabel("Number of Countries")
plt.show()
```


    
![png](output_8_0.png)
    


# 3. Bar Chart: Bottom 10 least populous countries


```python
bottom10 = df_simple.sort_values(by="Population").head(10)
plt.figure(figsize=(10,5))
plt.bar(bottom10["Country"], bottom10["Population"], color='lightcoral')
plt.title("Bottom 10 Least Populous Countries (2020)")
plt.xticks(rotation=45)
plt.ylabel("Population")
plt.show()

```


    
![png](output_10_0.png)
    


# 4. Histogram: Countries with population < 100 million


```python
small_pop = df_simple[df_simple["Population"] < 100_000_000]
plt.figure(figsize=(10,5))
plt.hist(small_pop["Population"], bins=15, color='lightgreen')
plt.title("Histogram for Countries with Population < 100 Million")
plt.xlabel("Population")
plt.ylabel("Count")
plt.show()
```


    
![png](output_12_0.png)
    


# 5. Bar Chart: Countries with ~50 million population


```python
mid_pop = df_simple[(df_simple["Population"] > 40_000_000) & (df_simple["Population"] < 60_000_000)]
plt.figure(figsize=(10,5))
plt.bar(mid_pop["Country"], mid_pop["Population"], color='violet')
plt.title("Countries Around 50 Million Population")
plt.xticks(rotation=45)
plt.ylabel("Population")
plt.show()

```


    
![png](output_14_0.png)
    


# 6. Bar Chart: Top 10 countries with population between 10M and 30M


```python
range_pop = df_simple[(df_simple["Population"] >= 10_000_000) & (df_simple["Population"] <= 30_000_000)]
top10_range = range_pop.sort_values(by="Population", ascending=False).head(10)
plt.figure(figsize=(10,5))
plt.bar(top10_range["Country"], top10_range["Population"], color='teal')
plt.title("Top 10 Countries with Population Between 10M and 30M")
plt.xticks(rotation=45)
plt.ylabel("Population")
plt.show()
```


    
![png](output_16_0.png)
    


# 7. Histogram: Countries with < 5 million population


```python
low_pop = df_simple[df_simple["Population"] < 5_000_000]
plt.figure(figsize=(10,5))
plt.hist(low_pop["Population"], bins=10, color='salmon')
plt.title("Histogram for Countries with Population < 5 Million")
plt.xlabel("Population")
plt.ylabel("Number of Countries")
plt.show()
```


    
![png](output_18_0.png)
    


# 8. Bar Chart: Random 10 countries' populations


```python
# 8. Histogram: Countries with population between 10 million and 200 million
pop_filtered = df_simple[(df_simple["Population"] >= 10_000_000) & (df_simple["Population"] <= 200_000_000)]

plt.figure(figsize=(10, 5))
plt.hist(pop_filtered["Population"], bins=10, color='cyan', edgecolor='black')
plt.title("Histogram for Countries with Population Between 10M and 200M (2020)")
plt.xlabel("Population")
plt.ylabel("Number of Countries")
plt.grid(True)
plt.tight_layout()
plt.show()
```


    
![png](output_20_0.png)
    


# 9. Histogram: Log-scale population to show global spread clearly


```python
import numpy as np
plt.figure(figsize=(10,5))
plt.hist(np.log10(df_simple["Population"]), bins=15, color='gold')
plt.title("Log-Scale Histogram of Country Populations (log10)")
plt.xlabel("Log10(Population)")
plt.ylabel("Number of Countries")
plt.show()
```

    C:\Users\ASUS\AppData\Local\Programs\Python\Python312\Lib\site-packages\pandas\core\arraylike.py:399: RuntimeWarning: invalid value encountered in log10
      result = getattr(ufunc, method)(*inputs, **kwargs)
    


    
![png](output_22_1.png)
    


# 10. Bar Chart: 5 countries closest to median population


```python
median_val = df_simple["Population"].median()
df_simple["diff_from_median"] = abs(df_simple["Population"] - median_val)
closest_to_median = df_simple.sort_values(by="diff_from_median").head(5)
plt.figure(figsize=(10,5))
plt.bar(closest_to_median["Country"], closest_to_median["Population"], color='skyblue')
plt.title("5 Countries Closest to Median Population")
plt.xticks(rotation=45)
plt.ylabel("Population")
plt.show()
```


    
![png](output_24_0.png)
    

