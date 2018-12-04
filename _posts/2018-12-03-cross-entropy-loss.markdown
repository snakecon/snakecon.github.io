---
layout: post
date:   2018-12-03 19:50:00 +0800
categories: jekyll update
---

# 结论先行

交叉熵的公式:

$$ J(\theta)=-\frac{1}{m}\sum_{i=1}^{m}y^{(i)}\log(h_\theta(x^{(i)}))+(1-y^{(i)})\log(1-h_\theta(x^{(i)})) $$

$J(\theta)$对$\theta$的求导结果为:

$$ \frac{\partial}{\partial\theta_{j}}J(\theta) =\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)} $$

# 推导细节

交叉熵损失函数为： 

$$ J(\theta)=-\frac{1}{m}\sum_{i=1}^{m}y^{(i)}\log(h_\theta(x^{(i)}))+(1-y^{(i)})\log(1-h_\theta(x^{(i)})) $$

其中，
 
$$ \log h_\theta(x^{(i)})=\log\frac{1}{1+e^{-\theta^T x^{(i)}} }=-\log ( 1+e^{-\theta^T x^{(i)}} )\ ,\\ \log(1- h_\theta(x^{(i)}))=\log(1-\frac{1}{1+e^{-\theta^T x^{(i)}} })=\log(\frac{e^{-\theta^T x^{(i)}}}{1+e^{-\theta^T x^{(i)}} })\\=\log (e^{-\theta^T x^{(i)}} )-\log ( 1+e^{-\theta^T x^{(i)}} )=-\theta^T x^{(i)}-\log ( 1+e^{-\theta^T x^{(i)}} ) \ . $$

由此，得到 

$$\small
{
J(\theta) =-\frac{1}{m}\sum_{i=1}^m \left[-y^{(i)}(\log ( 1+e^{-\theta^T x^{(i)}})) + (1-y^{(i)})(-\theta^T x^{(i)}-\log ( 1+e^{-\theta^T x^{(i)}} ))\right]\\
=-\frac{1}{m}\sum_{i=1}^m \left[y^{(i)}\theta^T x^{(i)}-\theta^T x^{(i)}-\log(1+e^{-\theta^T x^{(i)}})\right]\\
=-\frac{1}{m}\sum_{i=1}^m \left[y^{(i)}\theta^T x^{(i)}-\log e^{\theta^T x^{(i)}}-\log(1+e^{-\theta^T x^{(i)}})\right]_{③}\\
=-\frac{1}{m}\sum_{i=1}^m \left[y^{(i)}\theta^T x^{(i)}-\left(\log e^{\theta^T x^{(i)}}+\log(1+e^{-\theta^T x^{(i)}})\right)\right] _②\\
=-\frac{1}{m}\sum_{i=1}^m \left[y^{(i)}\theta^T x^{(i)}-\log(1+e^{\theta^T x^{(i)}})\right] 
}$$

这次再计算$J(\theta)$对第$j$个参数分量$\theta_j$求偏导: 

$$ \frac{\partial}{\partial\theta_{j}}J(\theta) =\frac{\partial}{\partial\theta_{j}}\left(\frac{1}{m}\sum_{i=1}^m \left[\log(1+e^{\theta^T x^{(i)}})-y^{(i)}\theta^T x^{(i)}\right]\right)\\
=\frac{1}{m}\sum_{i=1}^m \left[\frac{\partial}{\partial\theta_{j}}\log(1+e^{\theta^T x^{(i)}})-\frac{\partial}{\partial\theta_{j}}\left(y^{(i)}\theta^T x^{(i)}\right)\right]\\
=\frac{1}{m}\sum_{i=1}^m \left(\frac{x^{(i)}_je^{\theta^T x^{(i)}}}{1+e^{\theta^T x^{(i)}}}-y^{(i)}x^{(i)}_j\right)\\
=\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)} $$

这就是交叉熵对参数的导数： 

$$ \frac{\partial}{\partial\theta_{j}}J(\theta) =\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)} $$

# Ref.
[交叉熵代价函数(损失函数)及其求导推导][csdn-blog] 

[csdn-blog]:  https://blog.csdn.net/jasonzzj/article/details/52017438