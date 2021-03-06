---
layout:     post
title:      正则化
category: blog
description: 在学习模型中，常常会出现过拟合的现象，通常可以使用正则化的方法尽量避免过拟合。当模型出现过拟合时，主要是因为模型过于复杂，正则化就是降低模型的复杂度。
---

在模型过于复杂的情况下，模型会学习到很多特征，从而导致将所有的训练样本都拟合到，这样就导致了过拟合。解决过拟合一般从两个方面入手，一是减少模型复杂度，二是增加训练样本个数。而正则化是降低模型复杂度的一种方法。即以最小化损失和复杂度为目标（结构风险最小化）：

$$ J(w)=Loss(x,w)+\lambda Complexity(w) $$

比如在逻辑回归中，通常在目标函数（经验风险）中添加一个正则项
$$ \Phi(w) $$
,即：

$$ J(w)=-\frac{1}{m}[\sum_{i=1}^{m}y_{i}logh_{w}(x_{i})+(1-y_{i})log(i-h_{w}(x_{i}))]+\lambda \Phi (w) $$

这个正则化项一般采用L1范数或者L2范数，其形式为
$$ \Phi (w)=\left \| w \right \|_{1} $$
和
$$ \Phi (w)=\left \| w \right \|_{2}^{2} $$
,以L2正则项为例，

$$ L_{2}\,  regularization\, term =\left \| w \right \|_{2}^{2}=w_{1}^{2}+w_{2}^{2}+\cdots +w_{n}^{2} $$

* 复杂度等于权重的平方和
* 可以减少非常大的权重
* 对线性模型来说首选比较平滑的斜率
* 贝叶斯先验概率：权重应以0为中心，并呈正态分布

上文中的标量
$$ \lambda $$
是正则化率，用来调整正则化项的整体影响，平衡模型简单化和训练数据的拟合，增大
$$ \lambda $$
将增强正则化项的效果，但过高的
$$ \lambda $$
会导致欠拟合风险，
$$ \lambda $$
时可以取消正则化。

注意：较低的学习速率通常会产生和强
$$ \lambda $$
类似的效果，但是不建议同时调整两个参数。
