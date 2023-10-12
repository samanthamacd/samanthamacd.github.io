---
layout: post
title:  "The Basics of Pandas Data Visualization"
author: Samantha MacDonald 
description: (description coming soon) 
image: /assets/images/blog-image.jpg
---

# Data Visualization  

In the vast world of data analysis, the ability to effectively present results is paramount. Enter the world of data visualization, where Python and its tools shine brightly! Whether you're a data scientist, analyst, or enthusiast, mastering the art of visualization is essential. Here, I am to guide you through fundamental techniques that lay the foundation for impactful visualization. Buckle up and put away the graph paper and rulers, it's typing time! 


# Three Steps 
Here are the three key steps in visualizing data in python: 
1. Importing any necessary packages 
2. Importing your data (and potentially cleaning it) 
3. Create the appropriate visualizations 


# Step 1 - Import Packages 

There's a wide variety of packages that can assist you in your visualizations, but the primary packages include Pandas (for data processing), Matplotlib (for basic visuals), Numpy (for calculations), and Seaborn (for advanced visuals). 

``````
import pandas as pd 
import matplotlib.pyplot as plt 
import numpy as np 
import seaborn as sns 

from matplotlib import style 
style.use('ggplot') 
``````
Here, not only did I import the neccessary packages, but I set the graph style to 'ggplot', although there's a variety of styles available. 

# Step 2 - Import the Data 

``````
data = sns.load_dataset('iris')
``````

For simplicity's sake, I'm using data that comes loaded in Seaborn. In certain cases, you may need to take further steps to clean and arrange your data in a way that makes it more usable. This could include renaming columns or rows, getting rid of missing values, adding or removing columns, and other procesudes that makes the data more accessible. 

# Step 3 - Visualizations  
There are many charts that you can create to visualize your data. Here, I'm mentioning the three that I believe fit my data set best. 

1. Histogram 

The histogram is quite possibly the most popular way to observe the frequency of a certain variable. Here, I also included a curve that can give a better idea of what the distribution is like for those variables. 

``````
sns.distplot(df_iris['petal_length'], color = 'darkorchid', label = 'Petal Length')
sns.distplot(df_iris['petal_width'], color = 'skyblue', label = 'Petal Width')
plt.legend(fontsize = 12)
plt.xlabel('Petal Width', color = 'black')
plt.ylabel('Frequency', color = 'black')
plt.xticks(color = 'black')
plt.yticks(color = 'black')
plt.savefig('histogram.png')
``````
![Figure](/assets/images/histogram.jpg)

2. Grouped Bar Chart

A grouped bar chart is also a great way to exhibbit a lot of information at once. There can be any number of categories on the x-axis, and each category will  have a set number of variables whose frequencies are displayed with the bars.

``````
iris_melted = pd.melt(data, id_vars=['species'], value_vars=['sepal_length', 'sepal_width'])

plt.figure(figsize=(12, 6))
sns.barplot(x='species', y='value', hue='variable', data=iris_melted, palette='muted')

plt.xlabel('Species')
plt.ylabel('Measurement (cm)')
plt.title('Comparison of Sepal Length and Width for Two Iris Species')

plt.legend(title='Variable')

plt.show()
plt.savefig('barchart.jpg')
``````
Here, I used 'pd.melt' to reshape the data from a wide to a long format, making it easier to visualize. 

![Figure](/assets/images/barchart.jpg)

5. Scatterplot

A scatterplot is a visual representation of two variables, and is typically used to asses any potential relationships between those variables. 

``````
sns.scatterplot(x='sepal_length', y='sepal_width', data=df_iris, color = 'darkgreen', s=100, linewidth=1, edgecolor='lightgreen')

plt.title('Scatter Plot Sample', color='black', fontsize=18)
plt.savefig('scatter.png')

plt.show()
``````
![Figure](/assets/images/scatter.png) 

# Wrapping it Up! 

I truly just scratched the surface with the three visualization methods I showed in this post. There are many more such as single or multiple line graphs, box plots, heat maps, pie charts, and so on. I hope that this was enough to pique your interest in data visualization tactics, and implore you to continue practicing and researching the methods that best suit your data's needs! 
