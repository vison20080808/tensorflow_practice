《统计学习方法》李航

CART算法（分类与回归树 classification and regression tree）：1984年提出
同样由特征选择、树的生成及剪枝，三部分组成。

特征选择的标准：基尼指数（Gini index）最小化准则。（ID3算法-信息增益最大化；C4.5算法-信息增益比最大化）

树的生成：
回归树：用平方误差最小化准则
分类树：用基尼指数（Gini index）最小化准则

问题：怎样对输入空间进行划分？
启发式的方法，选择切分变量（splitting variable）和切分点（point）

最小二乘回归树（least squares regression tree）：
递归地将每个区域划分为两个子区域，选择使"残差平方和最小"的切分点。

分类树，用基尼指数选择最优特征，同时决定该特征的最优二值切分点。

基尼指数：
对于二分类问题，概率分布的 Gini(p) = 2p(1 - p)
对于给定的样本集合D，其基尼指数 Gini(D)表示集合D的不确定性
在特征A的条件下，集合D的基尼指数 Gini(D, A) 表示经A = a分割后集合D的不确定性。

基尼指数、熵之半，接近分类误差率，可以近似表示。

CART剪枝：
简化树，解决过拟合问题。从树的底端开始，自下而上，减掉一些叶节点或叶节点以上的子树，并将其父节点or根节点作为新的叶节点：
1、剪枝，形成一个子树序列；
2、通过交叉验证选取最优子树T。



《机器学习实战 Machine Learning in Action》

ID3算法：数据按某个特征切分后，该特征后续将不再起作用，切分过于迅速；而且不能直接处理连续型特征。

回归树：每个叶节点包含单个值；
模型树：每个叶节点包含一个线性方程。

构建树：
chooseBestSplit()：找到数据集切分的最佳位置，遍历所有特征及其可能的取值，找到使误差最小化的切分阈值。
三个提前终止条件：
1、特征所有值相等，即剩余特征值数目为1；
2、误差减少不大（小于用户定义的tolS）；
3、切分出的数据集很小（小于用户定义的参数tolN）

树剪枝：
预剪枝（prepruning）操作：chooseBestSplit()中提前终止条件；然后不断修改停止条件，并不是很好的方法
后剪枝（postpruning）：
将数据集分为测试集和训练集；
从上而下找到叶节点，用测试集判断将当前两个叶节点合并，是否能降低测试误差。

模型树：
分段线性：模型由多个线性片段组成。
可解释性，优于回归树。

比较哪一种模型好？(回归树、模型树、标准线性回归)
计算相关系数 R2值（预测值与实际值之间）：Numpy的corrcoef(yHat, y)；越接近1.0越好







