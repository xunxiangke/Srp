# 【python软件开发】物流运输网络优化

# **题目：办公用品销售企业SD公司的物流网络设计**

请根据办公用品销售企业SD公司的历史销售数据、物流成本和区域划分等背景资料，为公司设计出最低物流成本的物流网络，并撰写出备忘录。



## **一、背景介绍**

### **1. SD公司概况**

SD公司总部位于美国宾夕法尼亚州Blawnox，是一家定制纸制品和办公用品的销售企业，客户以小型企业为主，旗下现有400多家独立分销商（每一个分销商负责某一固定区域的产品销售和上门配送服务），业务范围覆盖美国全境。

### **2. SD公司的营销网络现状**

SD公司在Blawnox拥有一家文具加工厂，产品原料来自传统的办公用品制造商，公司根据客户订单安排生产计划，然后按照客户需求进行定制化加工，如客户的企业徽标和地址的印刷。

当分销商与客户签订销售协议后，即将订单发送至公司总部，由总部向加工厂下达生产任务，集中安排生产，完成加工后的产品再从Blawnox运送至分销商，由分销商上门配送至客户。

### **3. SD公司的物流现状**

目前，SD公司从Blawnox至各分销商的全部货物运输由第三方物流企业USPE公司承担，依照合约规定，只有当USPE公司的运输能力无法满足SD公司的需求时，SD公司才可以选择与其他物流企业合作。

根据商业环境和自身运营情况，USPE公司一般每12-18个月修改一次运输费率。本年度由于受运输能力限制，USPE公司与SD公司的合约提高了从Blawnox至各区域的运输费率，部分地区的收费甚至高于USPE的非合约用户。调整后的各区域运输费率见表1。

`表1 USPE公司向SD公司收取的各区域运输费率（调整后）`

| 区域 | 每磅费率 | 最低收费 |
| :--: | :------: | :------: |
|  2   |  \$0.28  |  \$4.00  |
|  3   |  \$0.32  |  \$4.30  |
|  4   |  \$0.35  |  \$4.65  |
|  5   |  \$0.40  |  \$5.00  |
|  6   |  \$0.45  |  \$5.45  |
|  7   |  \$0.58  |  \$6.30  |
|  8   |  \$0.70  |\$7.40|

### **4. SD公司的跨区（Zone-skipping）运输策略**

为了在维护与USPE公司长期战略合作伙伴关系的同时，降低由于运输费率调整对企业经营带来的负面影响，SD公司的运输部门提出了跨区运输策略，即在与USPE公司续约的同时，私下与另一家物流企业DJ公司合作，通过类似于越库（crossdocking）作业方式，降低物流成本。

上述跨区运输策略需要利用DJ公司在美国西海岸的部分仓库设置若干物流分拨中心（pool point），由每个分拨中心集中处理附近几家分销商的货物。然后通过与Blawnox当地另一企业共享卡车的方式，将货物先从Blawnox集中运输至物流分拨中心拆包，再通过USPE转运至各分销商。

为了避免被USPE公司收取合同约定的运输费用，所有经由物流分拨中心处理的货物不得不增加了外包装，并以个人名义向各分销商发货，以USPE非合约用户的收费标准支付运输费用。

可用于跨区运输策略的DJ公司仓库分布图，如图1所示。

尽管由于跨区运输造成的延迟运输时间影响仍在SD公司客户的可接受范围之内，但采用跨区运输策略增加的物流成本却难以忽略。因为对于每一个被SD公司作为物流分拨中心的仓库，DJ公司将收取固定的使用费和维护费，二者合计为$40,000/仓库/年。与此同时，DJ公司还对每一个包裹征收处理费用，根据仓库（物流分拨中心）的存储能力和繁忙程度，对包裹收取的处理费率有所不同，见表2。

`图1  DJ公司的仓库相对于宾夕法尼亚州Blawnox的地理位置`

**![img](https://s1.ax1x.com/2022/09/07/vHjZT0.png)**



`表2 可用于跨区运输策略的DJ公司各仓库运输费率和处理费用`

|                **位置**                | **邮政编码** | **货车费率（\$/mile）** | **送货服务成本（\$）** |
| :------------------------------------: | :----------: | :---------------------: | :--------------------: |
| City of Industry, CA  加利福尼亚工业市 |    91789     |         \$1.10          |         \$1.14         |
|       Coos Bay, OR  俄勒冈库斯湾       |    97420     |         \$1.10          |         \$1.27         |
|      Laughlin, NV  内华达州拉芙琳      |    89029     |         \$1.40          |         \$1.23         |
|     Preston, ID  爱达荷州普雷斯顿      |    83263     |         \$1.35          |         \$1.30         |
|     Tuba City, AZ  亚利桑那图巴市      |    86045     |         \$1.25          |         \$1.19         |
|   Vacaville, CA  加利福尼亚瓦卡维尔    |    95687     |         \$1.10          |         \$1.36         |
|    Walla Walla, WA  华盛顿瓦拉瓦拉     |    99362     |         \$1.10          |         \$1.08         |



## **二、需求分析**

### **1.** **企业需求分析**

请结合跨区运输策略，为SD公司设计物流网络，决策范围涵盖以下两方面内容：

1）使用DJ公司的哪些仓库作为物流分拨中心；

2）每一个物流分拨中心负责哪些分销商的货物转运。

### **2.** **物流网络设计要求**

1) 对于某些地理位置偏远或所需货物运输规模极小的分销商，可保持原运输策略，即可以不经过物流分拨中心转运。

2. 每一个分销商的货物运输路径固定且唯一，即某一分销商的所有货物均由某一家物流分拨中心处理，或所有货物均直接从Blawnox通过USPE运输至分销商所在地。

3. SD公司的产品销售不受季节和流行趋势的影响，市场需求稳定。因此，附件中提供的一周销售数据可以作为年度市场需求计算依据（即假设当年度每周的出货量相同）。

4. 基于SD公司的产品特性，运输费用按照货物重量收取，且运费与货物重量满足线性关系。

## **3.** **数据参考**

1. “SD公司历史销售数据.xlsx”中包含了具有代表性的某一周的包裹发货历史数据，所有货物均由Blawnox发出。

2.  “区域划分.xlsx”中包含UPSE的区域划分及每个独立经销商所在的区域，同时还包括DJ公司位于美国西海岸的7个可用于设置物流分拨中心的仓库位置。同时，此Excel文档中还包含本文中表1至表3中的数据，它们分别保存在单独的工作表中。

3. DJ公司货车的最大载重量为40,000磅；SD公司与另一家企业共享卡车，另一家企业占用卡车最大载重量的一半，即每辆卡车实际可供SD公司使用的载重量上限为20,000磅。但无论实际容量分布如何，卡车运输成本将在两家公司之间平均分配。

4. 计算卡车成本时，以Blawnox作为起点。

5. 表3为USPE公司面向非合约客户的运输费率报价，如果SD公司通过物流分拨中心向分销商发货，则USPE将使用表3中的价格向SD公司收取费用。

6. Blawnox的邮编为15238，Blawnox至物流分拨中心的运输里程，以及单位车辆的运输成本可以据此计算。

   

`表3 USPE在各区域的运输费率(适用于非合约用户)`

| 区域 | 每磅费率 | 最低收费 |
| :--: | :------: | :------: |
|  2   |  \$0.33  |  \$4.20  |
|  3   |  \$0.37  |  \$4.65  |
|  4   |  \$0.41  |  \$5.00  |
|  5   |  \$0.46  |  \$5.40  |
|  6   |  \$0.50  |  \$5.85  |
|  7   |  \$0.54  |  \$6.10  |
|  8   |  \$0.59  |\$6.45|



## **三、具体要求**

**1.** **请评估当前物流网络设计下SD公司的年度总分销成本**，即所有发货均通过USPE从Blawnox直接发往各分销商。

**2.** **请为SD公司设计一个结合跨区运输策略的物流网络**，确定在DJ公司的哪些仓库设立物流分拨中心，并安排由Blawnox至每一个分销商的运输方案（是否采用跨区运输），同时计算所涉及的新物流网络的年度总分销成本。

**3.** **请为SD公司撰写一份备忘录，主要内容包括：**

1. 识别SD公司物流网络设计决策中的利益相关者

2. 针对USPE公司公布的调整后的运输费率，SD公司可以采取的应对措施

3. 分析SD公司可能采取的每一项应对措施对每一位利益相关者的潜在影响

4. 结合上述对利益相关者的潜在影响，判断影响SD公司决策的关键因素

5. 为SD公司的物流网络重新规划推荐一些措施

6. 阐述其他可行应对措施未入选的理由

 

### **附件1 SD公司的历史销售数据（周销售额）**

参见文件：SD公司历史销售数据.xlsx

### **附件2 区域划分**

参见文件：区域划分.xlsx

 


