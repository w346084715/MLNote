
# DAY4-6 逻辑回归

目标 ： 解决因变量是定型变量的问题。 

概述 ： 逻辑回归（Logistic Regression）是用于处理因变量为分类变量的回归问题，常见的是二分类或二项分布问题，也可以处理多分类问题，它实际上是属于一种分类方法。
二分类问题的概率与自变量之间的关系图形往往是一个S型曲线，如图所示，采用的Sigmoid函数实现。

线性回归和Logistic回归都是广义线性模型的特例。

假设有一个因变量y和一组自变量x1, x2, x3, ... , xn，其中y为连续变量，我们可以拟合一个线性方程：

y =β0 +β1*x1 +β2*x2 +β3*x3 +...+βn*xn

并通过最小二乘法估计各个β系数的值。

如果y为二分类变量，只能取值0或1，那么线性回归方程就会遇到困难: 方程右侧是一个连续的值，取值为负无穷到正无穷，而左侧只能取值[0,1]，无法对应。为了继续使用线性回归的思想，统计学家想到了一个变换方法，就是将方程右边的取值变换为[0,1]。最后选中了Logistic函数：

y = 1 / (1+e-x)

这是一个S型函数，值域为(0,1)，能将任何数值映射到(0,1)，且具有无限阶可导等优良数学性质。

我们将线性回归方程改写为：

y = 1 / (1+e-z),

其中，z =β0 +β1*x1 +β2*x2 +β3*x3 +...+βn*xn

此时方程两边的取值都在0和1之间。

进一步数学变换，可以写为：

Ln(y/(1-y)) =β0 +β1*x1 +β2*x2 +β3*x3 +...+βn*xn

Ln(y/(1-y))称为Logit变换。我们再将y视为y取值为1的概率p(y=1)，因此，1-y就是y取值为0的概率p(y=0)，所以上式改写为：

p(y=1) = ez/(1+ez),

p(y=0) = 1/(1+ez),

其中，z =β0 +β1*x1 +β2*x2 +β3*x3 +...+βn*xn.

接下来就可以使用”最大似然法”估计出各个系数β。

[参考资料: 深入理解logit回归](http://blog.sina.com.cn/s/blog_44befaf60102vznn.html)

[逻辑回归详解](https://blog.csdn.net/bitcarmanlee/article/details/51154481)

[logistic回归详解(二）：损失函数（cost function）详解](https://blog.csdn.net/bitcarmanlee/article/details/51165444)

## 步骤


## 相关数据类型及函数

- sigmoid 函数 ： 见image 文件夹
- 损失函数：
 
  1. 0-1损失函数 （0-1 loss function） L(Y,f(X))={1,0,Y ≠ f(X)Y = f(X)
  2. 平方损失函数（quadratic loss function)  L(Y,f(X))=(Y−f(x))2
  3. 绝对值损失函数(absolute loss function)  L(Y,f(x))=|Y−f(X)|
  4. 对数损失函数（logarithmic loss function) 或对数似然损失函数(log-likehood loss function)  L(Y,P(Y|X))=−logP(Y|X)
  

逻辑回归中一般采用的损失函数一般为对数损失函数 ： 
cost(hθ(x),y)= 

{
- −log(hθ(x))    if y = 1 
- -log(1−hθ(x))  if y = 0

}


y表示真实值，hθ(x)表示预测值， hθ(x)被变换到0-1的范围。 


