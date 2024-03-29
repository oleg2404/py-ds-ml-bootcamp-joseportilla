
___

<a href='http://www.pieriandata.com'> <img src='../Pierian_Data_Logo.png' /></a>
___
# Pandas Built-in Data Visualization

In this lecture we will learn about pandas built-in capabilities for data visualization! It's built-off of matplotlib, but it baked into pandas for easier usage!  

Let's take a look!

## Imports


```python
import numpy as np
import pandas as pd
%matplotlib inline
```

## The Data

There are some fake data csv files you can read in as dataframes:


```python
df1 = pd.read_csv('df1',index_col=0)
df2 = pd.read_csv('df2')
```

## Style Sheets

Matplotlib has [style sheets](http://matplotlib.org/gallery.html#style_sheets) you can use to make your plots look a little nicer. These style sheets include plot_bmh,plot_fivethirtyeight,plot_ggplot and more. They basically create a set of style rules that your plots follow. I recommend using them, they make all your plots have the same look and feel more professional. You can even create your own if you want your company's plots to all have the same look (it is a bit tedious to create on though).

Here is how to use them.

**Before plt.style.use() your plots look like this:**


```python
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x125853940>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_6_1.png)


Call the style:


```python
import matplotlib.pyplot as plt
plt.style.use('ggplot')
```

Now your plots look like this:


```python
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12588d358>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_10_1.png)



```python
plt.style.use('bmh')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x125bec080>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_11_1.png)



```python
plt.style.use('dark_background')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1259eb780>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_12_1.png)



```python
plt.style.use('fivethirtyeight')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x125fad2b0>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_13_1.png)



```python
plt.style.use('ggplot')
```

Let's stick with the ggplot style and actually show you how to utilize pandas built-in plotting capabilities!

# Plot Types

There are several plot types built-in to pandas, most of them statistical plots by nature:

* df.plot.area     
* df.plot.barh     
* df.plot.density  
* df.plot.hist     
* df.plot.line     
* df.plot.scatter
* df.plot.bar      
* df.plot.box      
* df.plot.hexbin   
* df.plot.kde      
* df.plot.pie

You can also just call df.plot(kind='hist') or replace that kind argument with any of the key terms shown in the list above (e.g. 'box','barh', etc..)
___

Let's start going through them!

## Area


```python
df2.plot.area(alpha=0.4)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x126222978>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_18_1.png)


## Barplots


```python
df2.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.039762</td>
      <td>0.218517</td>
      <td>0.103423</td>
      <td>0.957904</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.937288</td>
      <td>0.041567</td>
      <td>0.899125</td>
      <td>0.977680</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.780504</td>
      <td>0.008948</td>
      <td>0.557808</td>
      <td>0.797510</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.672717</td>
      <td>0.247870</td>
      <td>0.264071</td>
      <td>0.444358</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.053829</td>
      <td>0.520124</td>
      <td>0.552264</td>
      <td>0.190008</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.plot.bar()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x126388630>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_21_1.png)



```python
df2.plot.bar(stacked=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12657bb38>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_22_1.png)


## Histograms


```python
df1['A'].plot.hist(bins=50)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x12685e9b0>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_24_1.png)


## Line Plots


```python
df1.plot.line(x=df1.index,y='B',figsize=(12,3),lw=1)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1243875f8>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_26_1.png)


## Scatter Plots


```python
df1.plot.scatter(x='A',y='B')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x126b90fd0>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_28_1.png)


You can use c to color based off another column value
Use cmap to indicate colormap to use. 
For all the colormaps, check out: http://matplotlib.org/users/colormaps.html


```python
df1.plot.scatter(x='A',y='B',c='C',cmap='coolwarm')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x126f7b400>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_30_1.png)


Or use s to indicate size based off another column. s parameter needs to be an array, not just the name of a column:


```python
df1.plot.scatter(x='A',y='B',s=df1['C']*200)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x126f94c18>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_32_1.png)


## BoxPlots


```python
df2.plot.box() # Can also pass a by= argument for groupby
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1271fa198>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_34_1.png)


## Hexagonal Bin Plot

Useful for Bivariate Data, alternative to scatterplot:


```python
df = pd.DataFrame(np.random.randn(1000, 2), columns=['a', 'b'])
df.plot.hexbin(x='a',y='b',gridsize=25,cmap='Oranges')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x127413358>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_36_1.png)


____

## Kernel Density Estimation plot (KDE)


```python
df2['a'].plot.kde()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1276d9160>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_39_1.png)



```python
df2.plot.density()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1276f7940>




![png](01-Pandas%20Built-in%20Data%20Visualization_files/01-Pandas%20Built-in%20Data%20Visualization_40_1.png)


That's it! Hopefully you can see why this method of plotting will be a lot easier to use than full-on matplotlib, it balances ease of use with control over the figure. A lot of the plot calls also accept additional arguments of their parent matplotlib plt. call. 

Next we will learn about seaborn, which is a statistical visualization library designed to work with pandas dataframes well.

Before that though, we'll have a quick exercise for you!

# Great Job!
