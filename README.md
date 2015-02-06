# NMShortPath
@Keywords(NMShortPath,Graph,Vertex,Edge)

@Author(明月朗照之)

@CreatedDay(2015-01-23)

NM-最短路径算法，网络图中明确定义了起点和终点，求解前面至多N个最短路径并且所有不同顶点路径组合数目最多有M条(N <= M)。N和M 需要明确两个概念：<br/>
<b>N最短路径ShortPath：</b>指从起点到终点累计距离最短的前面至多N个路径，实际每个这样的路径可能有1条或多条不同的顶点序列走法。每个这样的路径就叫一个 ShortPath<br/>
<b>M顶点路径VertexPath：</b>指所有的至多N个路径的所有不同顶点序列走法总共至多有M条。每条这样的顶点序列就叫一条顶点序列路径，或顶点路径，或 VertexPath。

当N==1时，就是一般化的求解动态规划问题最短距离问题。

最初叫 N-最短路径，后来还是修改成 NM-最短路径最贴切。这里涉及到为什么有了N，还有个M的限制问题：M 的根本目的是为了压制问题求解产生的规模爆炸问题，
因为无穷多的顶点路径组合实际没有什么意义，我们应该限制成只需要前面求解出的至多M条顶点路径即可。
很容易构造一个当顶点数目和边的数目很多时，哪怕 N == 1 时也会产生求解爆炸的篱笆型动态规划用例：<b>所有边的距离相等</b>。当然，这是一种退化的极特殊境况，
但此时如果没有M的压制，实际等同于把所有顶点路径组合全部列举出来，那么程序在求解过程中把前面步骤的结果全部保存下来，导致内存占用爆炸! 而且真正应用中，
太多的顶点路径组合实际也没有什么意义。所以这里本程序专门提出一个M的参数来调节内存占用情况，而且还有一个特别的好处，就是大大加快超大规模问题程序求解的速度，
这里的超大规模指的是顶点的数目极大，边的数目也极大。当然，如果不限制M，也就是把M设置的很大，那么就完全等价于原来的 N-最短路径了。

所有编辑文件都是UTF-8编码格式。
