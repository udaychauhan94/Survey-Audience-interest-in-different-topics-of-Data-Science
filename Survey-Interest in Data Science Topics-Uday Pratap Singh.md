

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
df = pd.read_csv('https://cocl.us/datascience_survey_data', index_col=0)
```


```python
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
      <th>Very interested</th>
      <th>Somewhat interested</th>
      <th>Not interested</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Big Data (Spark / Hadoop)</th>
      <td>1332</td>
      <td>729</td>
      <td>127</td>
    </tr>
    <tr>
      <th>Data Analysis / Statistics</th>
      <td>1688</td>
      <td>444</td>
      <td>60</td>
    </tr>
    <tr>
      <th>Data Journalism</th>
      <td>429</td>
      <td>1081</td>
      <td>610</td>
    </tr>
    <tr>
      <th>Data Visualization</th>
      <td>1340</td>
      <td>734</td>
      <td>102</td>
    </tr>
    <tr>
      <th>Deep Learning</th>
      <td>1263</td>
      <td>770</td>
      <td>136</td>
    </tr>
  </tbody>
</table>
</div>




```python
result = result.sort_index(axis=1, ascending=False)
result = df.sort_values('Very interested', ascending=False)
result
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
      <th>Very interested</th>
      <th>Somewhat interested</th>
      <th>Not interested</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Data Analysis / Statistics</th>
      <td>1688</td>
      <td>444</td>
      <td>60</td>
    </tr>
    <tr>
      <th>Machine Learning</th>
      <td>1629</td>
      <td>477</td>
      <td>74</td>
    </tr>
    <tr>
      <th>Data Visualization</th>
      <td>1340</td>
      <td>734</td>
      <td>102</td>
    </tr>
    <tr>
      <th>Big Data (Spark / Hadoop)</th>
      <td>1332</td>
      <td>729</td>
      <td>127</td>
    </tr>
    <tr>
      <th>Deep Learning</th>
      <td>1263</td>
      <td>770</td>
      <td>136</td>
    </tr>
    <tr>
      <th>Data Journalism</th>
      <td>429</td>
      <td>1081</td>
      <td>610</td>
    </tr>
  </tbody>
</table>
</div>




```python
#convert into percentage

result = (result/2233 )*100
result.round(2)
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
      <th>Very interested</th>
      <th>Somewhat interested</th>
      <th>Not interested</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Data Analysis / Statistics</th>
      <td>75.59</td>
      <td>19.88</td>
      <td>2.69</td>
    </tr>
    <tr>
      <th>Machine Learning</th>
      <td>72.95</td>
      <td>21.36</td>
      <td>3.31</td>
    </tr>
    <tr>
      <th>Data Visualization</th>
      <td>60.01</td>
      <td>32.87</td>
      <td>4.57</td>
    </tr>
    <tr>
      <th>Big Data (Spark / Hadoop)</th>
      <td>59.65</td>
      <td>32.65</td>
      <td>5.69</td>
    </tr>
    <tr>
      <th>Deep Learning</th>
      <td>56.56</td>
      <td>34.48</td>
      <td>6.09</td>
    </tr>
    <tr>
      <th>Data Journalism</th>
      <td>19.21</td>
      <td>48.41</td>
      <td>27.32</td>
    </tr>
  </tbody>
</table>
</div>




```python
ax = result.plot(kind='bar', 
            figsize=(20, 8), 
            width=0.8, 
            color=['#5cb85c', '#5bc0de', '#d9534f'],
           )

ax.spines['left'].set_visible(False)
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)
ax.axes.get_yaxis().set_visible(False)
ax.tick_params(labelsize=14)
ax.legend(fontsize=14)
ax.set_title("Percentage of Respondents' Interest in Data Science Area", fontsize=16)
for p in ax.patches:
    ax.annotate(np.round(p.get_height(),decimals=2), 
                (p.get_x()+p.get_width()/2., p.get_height()), 
                ha='center', 
                va='center', 
                xytext=(0, 10), 
                textcoords='offset points',
                fontsize = 14
               )
plt.show()
```


![png](output_5_0.png)



```python

```
