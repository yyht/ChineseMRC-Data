# ChineseMRC-Data
收集了目前为止中文领域的MRC抽取式数据集

## 1. WebQA
- [链接](https://spaces.ac.cn/archives/4338)
- 特点：**数据量：572.3K**；**问题类型：单片段抽取，包括不可回答负例**；百度于2016年开源的数据集，数据来自于**百度知道**；格式为一个问题多篇意思基本一致的文章，分为人为标注以及浏览器检索；数据**整体质量中**，因为混合了很多检索而来的文章；文章分为人工标注(**ANN**)和浏览器检索(**IR**)；问题和文章的答案分为可回答(**positive**)和不可回答(**other_negative**)；query-passage-answer三元组，**无答案索引**

|  |  | Annotated Evidence |  |  |
| :---: | :---: | :---: | :---: | :---: |
|  | Question | Positive | Negative | Retrieved Evidence |
| Training | 36,181 | 140,897 | 125,886 | 181,661 |
| Validation | 3,018 | 5,305 | // | 60,351 |
| Training | 3,024 | 5,315 | // | 60,465 |

- 示例：

|            Question            | source |      type      |   Answer  |                                                                                                           Passage                                                                                                           |
|:------------------------------:|:------:|:--------------:|:---------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 1945年国共重庆谈判签署的协议是 | IR     | other_negative | No Answer | 1945年抗日战争胜利后，为避免内战、争取和平，中囯共产党同国民党政府在重庆进行了为期43天的和平谈判，史称重庆谈判。                                                                                                            |
| 同上                           | ANN    | positive       | 双十      | 1945年抗日战争胜利后，为避免内战、争取和平，中囯共产党同国民党政府在重庆进行了为期43天的和平谈判，史称重庆谈判。整个事件过程从1945年8月29日开始，至10月10日结束，国共双方签订了《政府与中共代表会谈纪要》（即《双十协定》） |
## 2. SQuAD-zen
- [链接](https://github.com/pluto-junzeng/ChineseSquad)
- 特点：**数据量：125.9K**；**问题类型：单片段抽取，包括不可回答负例**；将英文数据集**SQuAD**翻译成中文加人工筛选而来；格式与SQuAD一致
- 示例：

|   title  | is_impossible |                       Question                       |       Answer       |                                                                                                                                                                                              Passage                                                                                                                                                                                              |
|:--------:|:-------------:|:----------------------------------------------------:|:------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 圣母大学 | false         | 据称，1858年，圣母玛利亚在法国卢尔德出现在谁的面前？ | 圣伯纳黛特苏比罗斯 | 在建筑上，这所学校是天主教的。在主楼的金色穹顶上是一座圣母玛利亚的金色雕像。紧靠着主楼的前面，面对着它，是一尊双臂高举的基督铜像，上面写着“威尼斯和我的天”。主楼旁边是圣心大教堂。紧跟在大教堂后面的是石窟，一个马里祈祷和思考的地方。这是法国卢尔德石窟的复制品，据说1858年圣母玛利亚在那里出现在圣伯纳黛特苏比罗斯。在主干道的尽头（通过3座雕像和金色穹顶直接连接），是一座简单的现代玛丽石像。 |

## 3. Sogou QA
- [链接](http://task.www.sogou.com/cips-sogou_qa/)
- 特点：**数据量：297.3K**；**问题类型：单片段抽取，包括不可回答负例**；2018年CIPS-SOGOU问答比赛数据；来自于**搜狗搜索引擎**真实用户提交的查询请求；含有事实类与非事实类数据

| 任务类型         | Factoid Q&A subtask                                      | Non-Factoid Q&A subtask（长答案）       |
|------------------|----------------------------------------------------------|-----------------------------------------|
| 问题类型         | 事实类                                                   | 非事实类                                |
| 问题数量         | 3万                                                      | 10万                                    |
| 候选篇章         | 每个问题10个候选篇章（提供来源网页URL）                  | 每个问题10个候选篇章（提供来源网页URL） |
| 标准答案数量     | 唯一答案                                                 | N个答案(N>=0)                           |
| 标准答案产生方式 | 完全从候选篇章中截取                                     | 完全从候选篇章中截取                    |
| 标准答案长度     | 20字以内                                                 | 500字以内                               |
| 参赛者提交答案   | 针对每个问题，从候选篇章中提取答案文本                   | 针对每个问题，从候选篇章中提取答案文本  |
| 评价指标         | Accuracy; Precision-Recall（F1）（最终成绩按平均值排列） | ROUGE-L; BLEU （最终成绩按平均值排列）  |

| Question                  | Answer   | Passage                                                                                                                      |
|:------------------------- |:---------- |:--------------------------------------------------------------------------------------------------------------------------------- |
| 中国最大的内 陆盆地是哪个 | 塔里木盆地 | 中国新疆的塔里木盆地，是世界上最大的内陆盆地，东西 长约1500公里，南北最宽处约600公里。盆地底部海拔 1000米左右，面积53万平方公里。 |


**非事实类**样例如下：

| Question | Answer | Passage |
|:---------------- |:-----------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 什么是活性水    |  活性水，就是将普通饮用水经过砂滤、炭滤、膜滤等多层过滤后，再经过具有纳米技术的电生离子交换设备，将水中对人体有害的酸性物质分离出去，而保留水中的矿物质离子，具有弱碱性、小分子团特征的新一代饮用水。   | 活性水，就是将普通饮用水经过砂滤、炭滤、膜滤等多层过滤后，再经过具有纳米技术的电生离子交换设备，将水中对人体有害的酸性物质分离出去，而保留水中的矿物质离子，具有弱碱性、小分子团特征的新一代饮用水。 活性水，是弱碱性水，符合人体弱碱性内环境要求，可以为细胞的生命运动提供良好的内部和外部环境，让细胞更具活力。 活性水，是小分子团水，它将13个左右水分子抱成一团的普通水改造成为6个水分子抱成一团的“六角水”，这种水运动速度快、渗透性好、溶解力强，喝下后能够快速被人体吸收，比大分子团水（如矿泉水、山泉水、自来水、纯净水等）更好地溶解代谢产物，起到有效清除体内垃圾的作用。体内垃圾少了，疾病自然就少了。|


## 4. 军事QA
- [链接](https://www.heywhale.com/home/competition/5d142d8cbb14e6002c04e14a/content/5)
- 特点：**数据量：50K**；**问题类型：单片段抽取**；来源于2019年“莱斯杯”第二届军事机器阅读理解挑战赛；为**军事**垂域

| Question | Answer | Passage |
|:---------------- |:-----------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|苏联把沙俄的"拉扎列夫海军上将"号改造后的重巡洋舰有多重？      |  @content3@8000多吨@content3@   | @content1@红色高加索号巡洋舰是苏联海军中的第一艘重巡洋舰，是沙俄1913年开工的"斯维兰那"级轻巡洋舰的后继舰"拉扎列夫海军上将"号改造而成。@content1@@content3@栋哥猜可能有些朋友看到我上面说“彼罗巴甫洛夫斯克”号是苏联唯一一艘重巡会有一些不同意见，争议的焦点应该就是上图的“红色高加索”号了。该舰是苏联以从沙俄手中继承的斯维特兰娜级半成品“海军上将拉扎列夫”号改进而成的。不得不说毛子就是狠，改进计划直接就准备给红色高加索上4座双联装200mm火炮，其8000多吨的小身材当然承受不住这么重的火炮，最后不得不换成了4座单联180mm火炮。按照当时伦敦条约的标准，即使是180mm火炮，红色高加索号也是妥妥的重巡标准了。@content3@|


## 5. Dureader系列
- [链接](https://github.com/baidu/DuReader)
- 特点：**数据量：831.3K**；**问题类型：单片段抽取，包括不可回答负例**；分为Dureader-checklist，Dureader-robust，Dureader-yes/no以及Dureader 2.0

### 5.1 Dureader-checklist
**粒度更细**；**数据量：54.1K = train(3K) + dev(1.1K) + test(50K：4.5K real)**

| Question         |  Answer   | Passage                                                                                                                                                                                       |
|:---------------- |:---------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 高铁站可以充电吗 | no answer | 高铁和动车上是可以充电的,充电插头就在座位下边或者是前边。高铁动车上的充电插座排布与车型新旧有关。有些车座位是每排座位两个电源插座,有些新型车比如说“复兴号”是每两个座位有一个电源。祝旅途愉快! |

### 5.2 Dureader-robust

| Dataset | len(p) | len(q) | len(a) | # |
| :--- | :---: | :---: | :---: | :---: |
| Train | 291.88 | 9.19 | 5.39 | 14,520 |
| Development | 288.16 | 9.38 | 6.66 | 1,417 |
| Test | 285.36 | 9.41 | 6.55 | 1,285 |
| Challenge | 132.09 | 11.97 | 7.33 | 3,556 |
| All |  |  |  | 20,778 |

第一个方面则是测试**模型对于改写后的query的鲁棒性**
![](https://github.com/sherlcok314159/ChineseMRC-Data/blob/main/Images/dureader_robust_1.png)

第二个方面则是会构造困惑度较大的样本，**将错误答案和问题的句式结合在一起**，如果模型类似于正则查找而没有理解语义的话，容易回答错误
![](https://github.com/sherlcok314159/ChineseMRC-Data/blob/main/Images/dureader_robust_2.png)

第三个方面则是从**泛化性**来评测模型
![](https://github.com/sherlcok314159/ChineseMRC-Data/blob/main/Images/dureader_robust_3.png)

### 5.3 Dureader-Yes/No
**观点型**，answer即为模型抽取的答案，标签分为Yes, No以及Depends；**数据量：91.4K = train(75K) + eval(5.4K) + test(11K)**

| Question             | Answer   | Yes-No Answer | Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|----------------------|----------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 吃完螃蟹可以吃西瓜吗 | 因人而异 | Depends       | 海鲜和水果一起吃会产生砒霜，这样搭配吃多了，会慢性中毒。\n同时有海鲜和水果的时候，吃两种东西中间间隔20分钟以上就可以。\n另外，海鲜和黄瓜，西红柿在一起也不合适。\n所以最好不要。", "西瓜和螃蟹皆属于寒性食物，同食容易引起腹泻，食物食用应间隔2小时以上。\n因为皆为凉性，过凉则败胃，伤胃气，如果有不良反应多为胃疼，不能按，此时应让肚子暖点。 如果你是风寒感冒，建议不要吃这么多凉性的东西。\n小贴士：1、患有慢性胃炎、排空延缓、消化不良等胃动力功能低下者，更不宜吃螃蟹、西瓜。\n2、螃蟹：性寒味咸，蟹肉有清热、散血结、续断伤、理经脉和滋阴等功用；其壳可清热解毒、破淤清积止痛。\n3、西瓜： 性质寒凉,胃寒、孕妇、身体略燥热底子寒虚之人不宜。\n螃蟹与芹菜相克：同食会引起蛋白质的吸收。\n螃蟹与南瓜相克：同食会引起中毒。\n螃蟹与地瓜相克：容易在体内凝成柿石。\n螃蟹与香瓜相克：易导致腹泻。\n螃蟹与石榴相克：刺激胃肠，出现腹痛、恶心、呕吐等症状。\n螃蟹与泥鳅相克：功能正好相反，不宜同吃。\n螃蟹与冷食相克：必导致腹泻。\n螃蟹与花生仁相克：易导致腹泻。\n螃蟹与茄子相克：二者同食，伤人肠胃。\n螃蟹与梨相克：二者同食，伤人肠胃。", "因人而异" |

### 5.4 Dureader2.0
数据分布如下：

|  | Question | Passage | Answer |
| :---: | :---: | :---: | :---: |
| Amount | 301,574 | 1,431,729 | 665,723 |
| Avglen | 26 | 1793 | 299 |

不同query类型分布如下：

|  Query Type | train set | dev set | test set |
|:-----------:|:---------:|:-------:|:--------:|
|     Total    |   271574  |  10000  |   20000  |
| Description |   170428  |   6378  |   12437  |
|    Entity   |   76686   |   2825  |   5786   |
|    Yes_No   |   24460   |   797   |   1777   |

- 示例：

| question_type | question                   | paragraphs                               | answers                                                                                                                                                                                                                                          | "yesno_answers"             |
|---------------|----------------------------|------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| YES_NO        | 上海迪士尼可以带吃的进去吗 | ["text paragraph 1", "text paragraph 2"] | ["完全密封的可以，其它不可以。","可以的，不限制的。只要不是易燃易爆的危险物品，一般都可以带进去的。","罐装婴儿食品、包装完好的果汁、水等饮料及包装完好的食物都可以带进乐园，但游客自己在家制作的食品是不能入园，因为自制食品有一定的安全隐患。"] | ["Depends","Yes","Depends"] |


## 6. CMRC系列
- 特点：**数据量：319.1K**；**问题类型：单片段抽取，包括不可回答负例**；哈工大与讯飞实验室发布；因为20和21年的数据均为法律领域，遂归在CAIL系列中

### 6.1 CMRC 2017
- [链接](https://hfl-rc.com/cmrc2017/)
**数据量：305K = train(300K) + eval(2K) + test(3K)**；取自于**儿童童话**，另外简体和繁体中文混杂

|            Question            | Answer |                                                                                                                                                                                    Passage                                                                                                                                                                                    |
|:------------------------------:|:------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 狐狸说自己的什么比老虎大一倍？ | 影子   | 有一隻狐狸很自大，大家都不喜歡他。有一天，狐狸走在夕陽下，遇到了老虎，看見自己的影子比老虎大。狐狸大吼了一聲：「讓開!瘦小的老虎。老虎張牙舞爪的說：「你活得不耐煩了。狐狸抖一抖身子，不客氣的說：「我的影子比你的大一倍。老虎看一看影子，覺得很生氣，向狐狸大吼一聲。狐狸面呲牙咧嘴繼續說：「我的影子比你的大，我也一定比你大。老虎聽了非常生氣，大吼一聲，一口就把狐狸吃了。 |

### 6.2 CMRC2018
- [链接](https://ymcui.com/cmrc2018/)
**数据量：14.1K= train(10.1K) + eval(3K) + trial(1K)**；取自于**维基百科**上的问题，然后人工标注

|   Question   |                                                                   Answer                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------:|:------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 锣鼓经是什么 | ["大陆传统器乐及戏曲里面常用的打击乐记谱方法", "大陆传统器乐及戏曲里面常用的打击乐记谱方法", "大陆传统器乐及戏曲里面常用的打击乐记谱方法"] | 锣鼓经是大陆传统器乐及戏曲里面常用的打击乐记谱方法，以中文字的声音模拟敲击乐的声音，纪录打击乐的各种不同的演奏方法。常用的节奏型称为「锣鼓点」。而锣鼓是戏曲节奏的支柱，除了加强演员身段动作的节奏感，也作为音乐的引子和尾声，提示音乐的板式和速度，以及作为唱腔和念白的伴奏，令诗句的韵律更加抑扬顿锉，段落分明。锣鼓的运用有约定俗成的程式，依照角色行当的身份、性格、情绪以及环境，配合相应的锣鼓点。锣鼓亦可以模仿大自然的音响效果，如雷电、波浪等等。戏曲锣鼓所运用的敲击乐器主要分为鼓、锣、钹和板四类型：鼓类包括有单皮鼓（板鼓）、大鼓、大堂鼓(唐鼓)、小堂鼓、怀鼓、花盆鼓等；锣类有大锣、小锣(手锣)、钲锣、筛锣、马锣、镗锣、云锣；钹类有铙钹、大钹、小钹、水钹、齐钹、镲钹、铰子、碰钟等；打拍子用的檀板、木鱼、梆子等。因为京剧的锣鼓通常由四位乐师负责，又称为四大件，领奏的师傅称为：「鼓佬」，其职责有如西方乐队的指挥，负责控制速度以及利用各种手势提示乐师演奏不同的锣鼓点。粤剧吸收了部份京剧的锣鼓，但以木鱼和沙的代替了京剧的板和鼓，作为打拍子的主要乐器。以下是京剧、昆剧和粤剧锣鼓中乐器对应的口诀用字： |
### 6.3 CMRC2019
这个数据集是**完形填空**型，这里就不多赘述了


## 7. CAIL系列
- 特点：**数据量：61.2K**；**问题类型：单片段与多片段抽取，包括不可回答负例**；围绕**法律**领域

### 7.1 CAIL 2018
第一年并无阅读理解任务，略过

### 7.2 CAIL 2019(CJRC)
**数据量：51K= train(39K) + eval(6K) + test(6K)**

|   Question   |      Answer      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------:|:----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 事故结果如何 | 两车不同程度损坏 | 经审查,原告提供的证据1-3、被告中华联合广东分公司提供的证据4-5、被告万友公司提供的证据6,各方对其真实性均没有异议,本院对其真实性予以确认综合本院采信的证据及当事人的陈述,本院认定以下事实:2015年6月1日,田x17驾驶粤A×××××号车辆与严x3驾驶的赣C×××××号重型仓栅式货车发生碰撞,造成两车不同程度损坏的交通事故交警部门作出事故认定书,认定严x3承担事故的全部责任,田x17不负事故责任粤A×××××号车辆在原告处投保了保险金额为908000元的机动车损失保险,事故发生在保险期间内事故发生后,粤A×××××号车辆的被保险人陈x18就该车辆的损失以财产保险合同纠纷起诉至佛山市禅城区人民法院案经审理,佛山市禅城区人民法院于2015年8月18日作出(2015)佛城法民二初字第1006号民事判决,查明粤A×××××号车辆经广州市华盟价格事务所有限公司评估,损失价格为241541元,陈x18支付了粤A×××××号车辆的维修费241541元、评估费9050元;本案原告在庭审中明确表示不申请重新对车辆损失进行评估鉴定并判决原告向陈x18支付粤A×××××号车辆损失保险理赔款250591元2015年10月11日,原告向陈x18赔付了250591元及诉讼费用2529元后原告提起本案之诉并查明,赣C×××××号车辆的所有人为被告万友公司,该车辆在被告中华联合广东分公司处投保了交强险,事故发生在保险期内事故发生后,被告中华联合广东分公司向该车辆的被保险人许x19赔付了2000元诉讼中,被告徐11确认其为该车辆的实际支配人,严x3是被告徐11雇请,是从事派遣工作过程中发生案涉交通事故被告徐11与被告万友公司签订《车辆挂靠合同书》,被告万友公司同意被告徐11就赣C×××××号车辆挂靠被告万友公司名下 |

### 7.3 CAIL 2020
**数据量：5K= train(5K)；**

|              Question              |   Answer   |                                                                                                                                                                                                                                                                                                                           Passage                                                                                                                                                                                                                                                                                                                          |
|:----------------------------------:|:----------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| 该案中的被害人除了杨x7之外还有谁？ | 黄x6、梁x8 | 另查明，2015年2月2日，被告人邱x1向被害人杨x7的家属赔付死者丧葬费29672.50元。以上事实，被告人邱x1在开庭审理过程中亦无异议，并有110警情信息表，受案登记表、立案决定书，被害人黄x6、梁x8的陈述，证人杨9、林某某、程某某的证言，道路交通事故现场勘查笔录、现场图、事故现场照片，强制措施（扣押）凭证，肇事车载重称量单，广东省汽车综合性能检测报告单，道路交通事故车辆技术鉴定书，肇事车行驶证、驾驶证复印件、机动车驾驶人信息查询结果单、涉案车保险单，伤者病情简介，交通事故尸体检验报告和尸检照片，法医学人体损伤程度鉴定书和伤情照片，道路交通事故认定书，到案（抓获）经过，常住人口信息表，支付丧葬费收据等证据予以证实，被告人邱x1亦供认在案，足以认定。 |

### 7.4 CAIL 2021
**数据量：5.2K= train1(1.2K) + train2(4K)**；

| Question                                     | Answer          | Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 
|----------------------------------------------|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 被同班同学打伤的人是谁及其住院医疗费是多少？ | 王x0、9646.66元 | 本院经审理认定事实如下:原告王x0与被告杨x3系同班同学。2016年10月13日是10时许,原告王x0与被告杨x3在上体育课时,因原告王x0用手打了一下被告杨x3的屁股,后被告杨x3将原告按倒在地并压在其身上,导致原告受伤。后原告被送往贺12县人民医院治疗,经诊断为:1.左肱骨外科颈骨折;2.左肩峰撕脱性骨折。原告住院治疗6天,期间原告因为治疗伤情支出住院医疗费9646.66元,出院后医嘱:1.每3天换药术后14天拆线;2.术后1.2.3.6.12月复查,1年取出钢板;3.3周后开始行左肩关节功能锻炼;4.门诊随诊。原告为了治疗病情共支出门诊治疗费944.72元。后经贺12县公安局城关派出所委托,贺12县公安局物证鉴定室于2016年11月22日作出贺公伤鉴字〔2016〕122号法医学人体损伤程度鉴定书鉴定原告王x0损伤程度系轻伤一级。对于原告营养、护理期限评定,经贺12县德胜法律服务所委托宁夏中天奥立升司法鉴定中心于2016年12月16日作出宁x13鉴司〔2016〕临鉴字第200号司法鉴定意见书进行了司法鉴定,经鉴定原告误工期270日、护理期90日、营养期90日,为此,原告支出鉴定费1050元。另查明,原告受伤后,被告杨x3家属已垫付医疗费4000元。上述事实,依据原告提交的询问笔录、诊断证明、住院病案、出院证、贺12县人民医院医疗费收据、门诊费收费票据、贺公伤鉴字〔2016〕122号法医学人体损伤程度鉴定书、宁x13鉴司〔2016〕临鉴字第200号司法鉴定意见书以及原、被告当庭陈述予以证实,本院予以采信。 | 

## 8. CHIP 2020
- [链接](https://tianchi.aliyun.com/competition/entrance/531826/introduction)
- 特点：**数据量：18.5K**；**问题类型：单片段抽取**；

| Question       | Answer                                                           | Passage                                                                                      |  
|----------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| 重实是指什么？ | 所谓重实，如大热病人，邪气甚热，而脉象又盛满，内外俱实，便叫重实 | 黄帝道：什麽叫重实？岐伯说：所谓重实，如大热病人，邪气甚热，而脉象又盛满，内外俱实，便叫重实 | 

## 9. 疫情问答
- [链接](https://www.datafountain.cn/competitions/424/datasets)
- 特点：**数据量：5K**；**问题类型：单片段抽取**；

| Question                             | Answer                                                                 | Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|--------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 在山西省，患者使用的药品哪些可报销？ | 符合卫生健康部门制定的新型冠状病毒感染肺炎诊疗方案的药品和医疗服务项目 | 【山西】省财政厅关于山西省确诊为新型冠状病毒感染的肺炎患者的医疗保障政策 一是对于患者发生的医疗费用，在基本医保、大病保险、医疗救助等按规定支付後，个人负担部分由财政给予全额补助，实施综合保障。二是对于其中的异地就医患者，先救治後备案，报销不执行异地转外就医支付比例调减规定。 三是患者使用的符合卫生健康部门制定的新型冠状病毒感染肺炎诊疗方案的药品和医疗服务项目，按甲类药品和项目纳入医保基金支付范围。 四是对收治患者较多的医疗机构预付部分医保资金，及时调整有关医疗机构的医保总额预算指标，对新型冠状病毒感染的肺炎患者医疗费用单独预算。 |

## 10. DRCD
- [链接](https://github.com/DRCKnowledgeTeam/DRCD)
- 特点：**数据量：30K**；**问题类型：单片段抽取**；台湾研究者从**维基**百科上爬取；**繁体**

| Question                                    | Answer   | Passage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|---------------------------------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 新教在教義上強調信徒皆祭司以及什麼樣的理念? | 因信稱義 | 基督新教與天主教均繼承普世教會歷史上許多傳統教義，如三位一體、聖經作為上帝的啟示、原罪、認罪、最後審判等等，但有別於天主教和東正教，新教在行政上沒有單一組織架構或領導，而且在教義上強調因信稱義、信徒皆祭司， 以聖經作為最高權威，亦因此否定以教宗為首的聖統制、拒絕天主教教條中關於聖傳與聖經具同等地位的教導。新教各宗派間教義不盡相同，但一致認同五個唯獨：唯獨恩典：人的靈魂得拯救唯獨是神的恩典，是上帝送給人的禮物。唯獨信心：人唯獨藉信心接受神的赦罪、拯救。唯獨基督：作為人類的代罪羔羊，耶穌基督是人與上帝之間唯一的調解者。唯獨聖經：唯有聖經是信仰的終極權威。唯獨上帝的榮耀：唯獨上帝配得讚美、榮耀 |
