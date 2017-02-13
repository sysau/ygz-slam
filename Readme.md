ygz-slam  一锅粥－SLAM

# 日志
- 17.2.13 
增加了初始化部分代码，主要来自ORB-SLAM，见include/ygz/Initializer.h和src/Algorithm/Initializer.cpp文件。
测试文件为test/test_initializer.cpp，使用仿真数据。
结论：初始化H部分对噪声表现较好，但分解F的结果比较受噪声影响，需要增加一个后续的BA处理。

- 2017.2.11
调整Sparse Feature Alignment中的代码，将原有的8维误差改成了1维，提高了匹配速度. 3层金字塔，200个特征时，耗时约16ms。
算法见include/ygz/Ceres/CeresReprojSparseDirectError.h。由Matcher::SparseImageAlignment负责调用。
结论：
用FEJ会有少许速度提升，大约1到2ms，在alignment中并不明显。
深度值的误差会对alignment产生较大影响。

- 17.1 正在重构
小写开头的文件是旧文件，重构之后都以大写开头。
SVO和ORB的基本元素已经加入到本程序中。

# 依赖
- FAST
git clone https://github.com/uzh-rpg/fast.git

- Eigen
sudo apt-get install libeigen3-dev

- OpenCV 3.1 or higher 
see opencv.org

- Sophus 非模板类版本
git clone https://github.com/strasdat/Sophus.git
cd Sophus
git checkout a621ff

- glog 
sudo apt-get install libgoogle-glog-dev

- boost
sudo apt-get install libboost-all-dev

- ceres solver
https://github.com/ceres-solver/ceres-solver

- pangolin 
https://github.com/stevenlovegrove/Pangolin

- DBoW3
see 3rdparty

# 说明
一锅粥库由基础数据、算法和应用三层组成
数据类见src/Basic，是组成SLAM系统的基本数据结构
算法类见src/Algorithm，操作基本数据构成算法。
应用类使用数据和算法构成SLAM中各大模块，以及SLAM本身。

# 任务分工
请在此加入您想做的事情，然后提交到此工程。

## gaoxiang12 17.1.15 添加SVO的光流跟踪和初始化代码