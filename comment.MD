#论文查漏补空
* 以四叉树结构对栅格数据集合进行索引，呈影像金字塔状。而矢量数据集合支持分层存储，同层次的数据以图的形式表示。
* 影像金字塔（Pyramid）地理信息系统导论 P3291
* 二维矢量数据可视化的一般流程 地理信息系统导论
* 考虑下百度的路由服务怎么使用
* 拓扑关系矩阵 1111
* 瓦片点图的地图分辨率公式在服务器端提供？还是由UI层负责换算？基于Rest的瓦片地图Web服务研究。



* 开头可以加上企业私有云（数据安全性，专题图层等个性化）和公有云（成本低）  
  * 商业GIS组件不支持公有云（公有云服务的自我封闭和组件不支持）
  * 消费GIS SDK不支持私有云


* 最终方案——
  * 采用mapABC企业服务（国家偏移和企业服务偏移，造成不能获得百度地图数据反转）
  * 采用mapABC公开API （在企业外，显示业务信息和采集）
  * 图形界面和切片地图采用mapABC SDK
  * （剪裁和扩展）企业自我数据采用通用模块的存储和收集，以及某些专题数据和特殊矢量图形。


* 论文模块划分按照矢量数据处理，栅格数据处理，位置服务，地图UI四大子系统划分

* OGIS提出的空间几何体的基本构件 P1094
* 高清屏对于加载瓦皮地图的影响
* 对于多瓦片图层的支持

* 在基于REST的瓦片地图Web服务研究总有 **客户端瓦片数据的预提取**

*A tiled layer links to its tile matrix set through a tileMatrixSet URI that points to a TileMatrixSet section that completely defines it as previously explained. A layer can use a specific TileMatrixSet that describes a region adjusted to the actual content of this layer. In this case, the optional tileMatrixSetLimits section will not be used and changes in spatial extension of the layer can affect the minimum bounding box of the layer forcing to redefine the TopLeftCorner of each TileMatrix and that will end up changing the TileCol,TileRow indices thereby invalidating any previously cached tile. To
在OGC的文档中提到瓦片矩阵

* Each tile matrix set defines its own set of scale levels corresponding with the contained tile matrices. Each layer references one or more tile matrix sets. Although each layer could reference a different tile matrix set, it is likely that a server will offer many layers with the same tile matrix set reference.
A tile matrix set is composed of a collection of tile matrices, each one with a resolution optimized for a particular scale and identified by a tile matrix identifier (see figure 3). Each tile matrix set has an optional approximated bounding box but each tile matrix has an exact bounding box that is deduced indirectly from other parameters. Tile matrix bounding boxes at each scale will usually vary slightly due to pixel alignment, and it is important for the client and server to take this variation into account. Given the top left point of the tile matrix in CRS coordinates (tileMatrixMinX, tileMatrixMaxY), the width and height of the tile matrix in tile units (matrixWidth, matrixHeight), the width and height of a tile in pixels (tileWidth, tileHeight), the coefficient to convert the coordinate reference system (CRS) units into meters (metersPerUnit) and the scale (1:scaleDenominator), the bottom right corner of the bounding box of a tile matrix (tileMatrixMaxX, tileMatrixMinY) can be calculated as follows:

* 用户故事：A快递公司某分部发现因为限号等原因，自己负责区域的交通状况每日不同，
同时因为收发件需求的实时变化，以往快递员按照固定路线巡视的方案已经不能满足公司业务的
需要。公司希望有一套移动GIS系统，可以实时传递快递员的位置，每次收发件时间及路上的交通情况，以及经常
不在办公桌前的经理可以通过移动设备实时收取这些信息，并且通过统计数据发现业务热点，通过调派
快递人员的方式实现利益最大化。  
实际使用中发现，快递人员和经理的使用场景有明显边界，可以转化成为两个app来实现数据的安全性。  
经过一段时间的数据积累，A公司已经按照开始按照每日的交通业务预测来分上下午排班，未来的期望是
