---
layout: post
title: 深入浅出之 Factorization Machines
tags:  [machine learning,fm]
status: publish
type: post
published: true
---

Factorization Machines 由日本 Osaka University 的 Steffen Rendle [1] 在 2010 年提出。它是一种利用交叉项解决推荐问题的模型。

$$\hat y:= w_0 + \sum_{i=1}^{n} w_ix_i + \sum_{i=1}^n \sum_{j=i+1}^n \left \langle v_i,v_j \right \rangle x_iy_i$$

$$W_{i,j}=\left \langle v_i,v_j \right \rangle = \sum_{f=1}^kv_{i,f} \cdot v_{j,f}$$

$$\sum_{i=1}^n \sum_{j=i+1}^n \left \langle v_i,v_j \right \rangle x_iy_i = \frac{1}{2}\sum^k_{f=1} \left( \left(\sum_{i=1}^nv_{i,f}x_i \right)^2 - \sum^n_{i=1} v^2_{i,f} x_i^2 \right)$$


$$
\frac{\partial}{\partial \theta} \hat y \left( x \right) =
\begin{cases}
1, & \text{ if $\theta$ is $w_0$} \\
x_i, & \text{ if $\theta$ is ${w_i}$} \\
x_i\sum^n_{j=1} v_{j,f}x_j - v_{i,f}x_i^2, &\text{if $\theta$ is ${v_{i,f}}$}  
\end{cases} $$

##  Reference

1. Rendle, Steffen. “Factorization Machines,” 995–1000, IEEE, 2010. doi:10.1109/icdm.2010.127.


3. [深入浅出Factorization Machines系列](http://kubicode.me/2018/02/23/Deep%20Learning/Deep-in-out-Factorization-Machines-Series/)
4. [因子机深入解析](https://tracholar.github.io/machine-learning/2017/03/10/factorization-machine.html)
