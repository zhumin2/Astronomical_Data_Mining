天池天文数据挖掘比赛——天体光谱智能分类
====
# 引言
138亿年前，一个时间与空间的奇点产生了不可想象的大爆发，宇宙万物由一碗粒子“热汤”不断演化，在接下来的时间里变得越发丰富多彩；138亿年后的今天，
科学家打造各种先进望远镜，在每一个晴朗夜空将目标对准神秘的夜空，寻找并解读光带来的宇宙信息，试图回答一个简单而又困难的问题：宇宙中到底有什么？

天文学是一门历史悠久的观测科学，随着科学技术的发展，观测设备不断升级，人类对宇宙的认识由近到远逐步扩展，从地球到太阳系，从恒星到银河系，再到河
外星系，天文学中的许多神秘而有趣的问题等待着我们探索发现。先进的观测设备使我们能够望向宇宙更深处，同时也带来了天文数据爆炸式的增长。如今，人工
智能（AI）技术能够辅助天文学家们处理分析海量天文数据，进而从中发现新的天体和物理规律。

郭守敬望远镜（LAMOST，大天区面积多目标光纤光谱天文望远镜）是一架新类型的大视场兼备大口径望远镜，在大规模光学光谱观测和大视场天文学研究方面，居
于国际领先的地位。作为世界上光谱获取率最高的望远镜，LAMOST 每个观测夜晚能采集万余条光谱，使得传统的人工或半人工的利用模板匹配的方式不能很好应对，
需要高效而准确的天体光谱智能识别分类算法。

阿里云联合中国科学院国家天文台举办天文数据挖掘大赛，希望让大众参与到天文科学探索中，用人工智能的方法分析望远镜收集的真实的天文数据，进一步了解宇宙。
本次大赛要求参赛者对LAMOST 光谱进行分类（STAR/ GALAXY/QSO/ UNKNOWN），设计高效高准确率的算法来解决这个天文学研究中的实际问题。
# 竞赛题目
赛题数据包括索引文件（index.csv）和波段文件（id.txt集合的zip）两部分：

1）索引文件的第一行是字段名，之后每一行代表一个天体。索引文件的第一个字段为波段文件id号。训练集的索引文件记录了波段文件id号以及分类信息，测试集
的索引文件记录了波段文件id号，需要预测分类信息。

2）波段文件是txt后缀的文本文件，存储的是已经插值采样好的波段数据，以逗号分隔。所有波段文件的波段区间和采样点都相同，采样点个数都是2600个。

3）带 train 为训练集；带 test 为第一阶段测试集；带 rank 为第二阶段测试集。
Unknown数据补充说明：
1）LAMOST数据集中的unknown类别是由于光谱质量（信噪比低）等原因，未能够给出确切的分类的天体；
2）Unknown分类目前由程序给出，其中不排除有恒星、星系和类星体。
# 评估指标
考虑到imbalance data的特性和易计算性，用marco f1 score作为评分规则。

* marco f1 score是每一类算出的 f1 score的算术平均。

以四类分类为例：每一类以oneVSall计算各类的f1 score
![image](https://raw.githubusercontent.com/liangxiao940517/Astronomical_Data_Mining/master/Image_folder/%E8%AF%84%E4%BC%B0%E6%8C%87%E6%A0%87.png)
