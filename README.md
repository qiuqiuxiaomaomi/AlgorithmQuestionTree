# AlgorithmQuestionTree
算法试题技术研究

<pre>
有几台机器存储着几亿淘宝搜索日志,你只有一台2g的电脑,怎么选出搜索热度最高的十个搜索关键词;

方案1：把日志以2G为单位拆分多份文件，每份文件选取命中率最高的10个关键词，最后排序所有文件
      选出的每个文件10个关键词，获取全部文件的搜索量最高的10个关键词。

方案2：
</pre>

<pre>
如何设计算法压缩一段URL;
</pre>

<pre>
有一个页面能同时展示两个广告,现在有五个广告,设计算法使五个广告展示概率为1:2:3:4:5;
方案1：
     数组：
         Array[0]  广告1
         Array[1]  广告2
         Array[2]  广告2
         Array[3]  广告3
         Array[4]  广告3
         Array[5]  广告3
         Array[6]  广告4
         Array[7]  广告4
         Array[8]  广告4
         Array[9]  广告4
         Array[10] 广告5
         Array[11] 广告5
         Array[12] 广告5
         Array[13] 广告5
         Array[14] 广告5
       
         Random 随机 0~14,随机数，概率满足1:2:3:4:5

方案2：
</pre>

<pre>
有25匹马,五个赛道,用最少比赛次数将25匹马排序;
      分段有序：

      一共有25匹马，有一个赛场，赛场有5个赛道，就是说最多同时可以有5匹马一起比赛。假设每匹马都跑的很稳定，不用任何其他工具，只通过
      马与马之间的比赛，试问，最少得比多少场才能知道跑得最快的5匹马？（不能使用撞大运的算法）

      很明显这是一个算法题，网上有很多贴子在讨论这个问题，不过都没有给出一个明确的答案。我想了想，想到下面的一个算法：

          1）分成5组A，B，C，D，E，比五场。然后根据每场结果分别给这五组内的五匹马排序（从快到慢）。
          2）每组的头名再赛一场，取走第一名，然后该组第二名顶上。
          3）重复第二步，直到选出前5名。

       这个算法是比较笨的算法，总计需要赛10次，这个算法应该是万无一失的。现在的问题的就，如何优化这个算法，想了想，的确是有优化的
       空间的。也就是说，是可以少于10次的。

       想了一想，上面的那个算法自从第6次开始就使用5个排序数组的头名做“冒泡法”，总是挑一个最优秀的出来，其实，在第6次以后除了挑出
       最优秀的，我们还可以在每次比赛后淘汰一些速度不行的，淘汰的马匹数自然会比选出的更多，所以，一方面在找，另一方面在淘汰，找出
       前5名的速度应该会更快。

       比如：我们假设比赛完第六场后，我们得到下面的排序：（每组排序是——快马从左到右，各组头名的排序是——快马从上到下）

            A组 A1 A2 A3 A4 A5
            B组 B1 B2 B3 B4 B5
            C组 C1 C2 C3 C4 C5
            D组 D1 D2 D3 D4 D5
            E组 E1 E2 E3 E4 E5

       这样，我们不但知道，A1是25匹马里最快的马，而且我们可以淘汰近一半的马，比如E2，E3，E4，E5就可以全部淘汰了，为什么呢，因为
       比E2快的马有A1,B1,C1,D1,E1这五匹马，所以，E2后面的马是无法进入前五名了；同理，D3和其后面的也进入不了前5；同理，C4，C5，
       B5都可以淘汰。

       于是，在第六轮后我们可以得知，除了A1外的Top 4必然在下面这些马中：

            A组  A2 A3 A4 A5
            B组 B1 B2 B3 B4 
            C组 C1 C2 C3 
            D组 D1 D2 
            E组 E1
</pre>

<pre>
电梯调度算法

   传统电梯调度算法：

      1) 先来先服务算法
         任何调度算法在请求队列长度为1时，请求速率极低或相邻请求的间隔为无穷大时使用先来先
         服务算法既对调度效率不会产生影响，而且实现这种算法极其简单。

      2）最短寻找楼层时间优先算法（SSTF）
         在重载荷的情况下，最短寻找楼层时间优先算法的平均响应时间较短，但响应时间的方差较
         大，原因是队列中的某些请求可能长时间得不到响应，出现所谓的“饿死”现象。

      3）扫描算法（SCAN）
         所有的与电梯运行方向相同的乘客的请求在一次电向上运行或向下运行的过程中完成，免去了
         电梯频繁的来回移动。

         扫描算法的平均响应时间比最短寻找楼层时间优先算法长，但是响应时间方差比最短寻找楼层
         时间优先算法小，从统计学角度来讲，扫描算法要比最短寻找楼层时间优先算法稳定。 

      5）LOOK 算法
         LOOK 算法是扫描算法（SCAN）的一种改进。对LOOK算法而言，电梯同样在最底层和最顶层之
         间运行。

         但当 LOOK 算法发现电梯所移动的方向上不再有请求时立即改变运行方向，而扫描算法则需
         要移动到最底层或者最顶层时才改变运行方向。

   实时电梯调度算法

      1）最早截止期优先调度算法
      
</pre>

<pre>
参考文章：

      算法应该怎么“玩”
      https://blog.csdn.net/GitChat/article/details/81703229
</pre>