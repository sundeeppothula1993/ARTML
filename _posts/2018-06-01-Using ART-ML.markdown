---
layout: post
title: How to Execute ART-ML
date: {}
published: true
---


<style>body {text-align: justify;}</style>
<div class="body">
<p class="intro"><span class="dropcap">C</span>onventionally, Machine Learning algorithms interact directly with the whole dataset. Even in the Real time learning models it should somehow accommodate the impact of whole data (new + old data), changes in attributes (variables), etc. to improve the existing models.</p>
In Adaptive real time machine learning method, data is summarized in the Basic Elements Table (BET) which is a relatively small table. BET summarizes the whole dataset and can be updated in real-time by only using the newly generated data. As shown in Figure, In ART-ML modeling process is split into four separate components: Learner, Explorer, Modeler and Predictor defining the total workflow. </div>
<figure>
	<img src="{{ '/assets/img/BET.PNG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig1. - Adaptive Real Time Learning Machine (ART-ML) </figcaption>
</figure>

The tasks assigned to each of the four real time components are as follows: 
- **Learner**: updates (incrementally or decrementally) the Basic Elements Table utilizing the data in real time. 
- **Explorer**: does univariate and bivariate statistical data analysis using the Basic Elements Table in real time. 
- **Modeler**: constructs models using the Basic Elements Table in real time. 
- **Predictor**: uses the models for prediction in real time.


### Basic Elements Table:

The Basic Elements Table building block includes two attributes, 𝑋𝑖, 𝑋𝑗 and one or more basic elements 𝐵𝑖𝑗:
<figure>
	<img src="{{ '/assets/img/Table.JPG' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig2. - Building block of the Basic Elements Table (BET) </figcaption>
</figure>

All of the equations for Data exploration or for generating models use combination of Basic elements like Σ𝑋𝑖 -Σ𝑋𝑖𝑋𝑗 -Σ𝑋𝑖2 - Σ(𝑋𝑖𝑋𝑗)2 etc. Hence, 𝐵𝑖𝑗 consists of one or more of following basic elements which can be used for calculations of all real time equations:  
- 𝑁𝑖𝑗 : Total number of joint occurrence of two attributes 
- Σ𝑋𝑖 and Σ𝑋𝑗 : Sum of data 
- Σ𝑋𝑖𝑋𝑗 : Sum of multiplication 
- Σ𝑋𝑖2 and Σ𝑋𝑗2 : Sum of squared data 
- Σ(𝑋𝑖𝑋𝑗)2 : Sum of squared multiplication

All above basic elements can be update in real time (incrementally or decrementally), using the following basic general real time equation.

{% highlight ruby %} 
𝐵𝑖𝑗∶=𝐵𝑖𝑗±𝐵𝑖𝑗𝑛𝑒𝑤
where: 
- 𝐵𝑖𝑗=𝐵𝑗𝑖 
- (+) represents incremental and (-) decremental change of the basic elements.
{% endhighlight %}

The number of attributes can also be updated in real time (incrementally or decrementally), simply by adding corresponding rows and columns and the related basic elements to the BET table. This simple Basic Element Table (BET) is the key factor which differntiates ART-ML approach from all the existing complex methods. BET can learn/ Forget with data or Grow/Shrink with features. BET with the basic atomic nature can be directly used for Data exploration and modeling.
