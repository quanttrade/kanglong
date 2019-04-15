## kanglong

#### 降龙四式之亢龙有悔

> 这一招叫作‘亢龙有悔’，掌法的精要不在‘亢’字而在‘悔”字。倘若只求刚猛狠辣，亢奋凌厉，只要有几百斤蛮力，谁都会使了。这招又怎能教黄药师佩服？‘亢龙有悔，盈不可久’，因此有发必须有收。打出去的力道有十分，留在自身的力道却还有二十分。哪一天你领会到了这‘悔’的味道，这一招就算是学会了三成。好比陈年美酒，上口不辣，后劲却是醇厚无比，那便在于这个‘悔’字。” --洪帮主

这是一个根据PE、PB在指数历史低估区间时买入，长期持有，然后在PE、PB处于历史高位时卖出的策略。

* 这个策略极其简单，适用于大部分宽基指数；
* 这个策略是跑不赢指数的，但是能让你极其安心的长期持有；

* 谨记：一切回测有效的策略都是看后视镜开车。回测仅仅是参考，不能预测未来。
* 谨记：成功概率不能预测，失败风险无法回避，历史周期不断重复，时刻抱有敬畏之心。

#### 指数特点

* 背靠国运，不死鸟
* 长期上涨
* 成本低
* 不择股
* 容易量化
* 大道至简

## 低估不定期不定额策略

我们的策略制定原则：

1. 可复现、可回测
2. 排除人工干扰，机器拯救人类
3. 落子无悔，买定离手
4. 低估买，高估卖，没有机会不动
5. 资金分为100份分批投入

### 买入条件

1. 市场出现系统性低估机会可以买入
2. 单一标的PE、PB 处于历史30%以下可以买入
4. PB处于历史30%以下，且PE<10 或 1/PE<十年期国债利率X2，可以买入

### 卖出条件

1. 市场出现系统性高估机会可以卖出
2. 单一标的PE、PB 处于历史70%以上可以卖出
5. 1/PE<市场能找到的最小无风险收益率，可以卖出置换

### 简单持有

不符合买入，也不符合卖出条件，简单持有即可。

若市场利率缓慢下行，可简单买入短债基金持有，其他情况不动。

### 半凯利公式控制仓位

采用[银行螺丝钉](https://xueqiu.com/3079173340/62032246)的方法计算仓位；

其盈利增长率我们替换为10年ROE中位值，因为长远来看，PEG会趋近于ROE；用ROE更加保险

以恒生指数为例。

* 恒生指数过去10年的ROE中位值10%左右
* 我们期望5年年化15%的收益率
* PE历史30%大概为12，配合我们上面要求的条件，我们需要在10PE买入

#### 凯利公式

```
F =（bp - q）/ b
```

其中b代表赔率，p代表获胜率，q代表落败率，q = 1-p

#### 投资指数基金的赔率

```
赔率b =（卖出时估值/买入时估值）*【1+指数盈利增长率】^持有年数 =（1+你要求的年复合收益率）^持有年数

b = （卖出时估值/买入时估值）* 1.1^5 = 1.15^5

卖出时估值PE/10 ≈ 1.25

要求卖出时估值 ≈ 12.5

```

这样就把我们的投资行为固化为了这样一个事件：

假如未来恒生指数能保持平均10%的ROE，我们在10PE买入恒生指数，要求有15%的年复合收益率，那我们“需要在5年的时间里，至少有一次机会在12.5倍以上市盈率卖出”。


#### 投资指数基金的胜率

```
胜率 = 期望卖出PE的历史估值概率
```

5年时间里，12.5PE是大概率事件，事实上，我们要求在70%的PE上方卖出，这个值大概是15PE。

12.5PE在历史上大概处于 60%的位置， 所以我们的条件还是非常宽松的。

按照我们前面制定的的边界卖出条件 PE估值百分位 > 70%，所以如果能买到10PE以下的恒生指数，并且期望5年内年化收益15%的话，只要能持有不动，胜率>60%；

#### 计算仓位

通过凯利公式计算出来的仓位， X0.5；成为半凯利公式

胜率60%，赔率2；

```
F =（bp-q）/b = (2 * 60% - 40%)/2 = 40%

F * 0.5 = 20%
```
根据半凯利公式推出，推荐仓位为20%。


#### 一些推论

* 预期收益越低，胜率就会越高，仓位也会越高。如果预期收益过高，甚至仓位会是负数（也就是无法实现）
* 买入估值越低，胜率就会越高，仓位也会越高。如果买入估值过高，甚至仓位会是负数（无法赚取估值差收益）
* 指数的盈利增长率越高，对应的胜率也会越高
* 买入时不要求每次都能赢，但是一定要在赢面大的时候下大注

#### 多指数组合计算仓位

对组合中的每个指数设定 买入PE，卖出PE，持有年数，要求年复合增长率， 分别计算仓位

全部仓位相加，便可以决定总仓位。

#### 定投

每次的总仓位即 定投总额 / 定投次数；比如5年计划投入60w，每月定投一次，那么每次总仓位1w；

每次计算卖出PE点大于历史估值70%即可盈利的品种，并决定仓位；然后所有仓位相加。

如果定投不定额， 每次仓位可以超过100%；

如果定投定额，每个品种的仓位比例再等分平均，最后达到100%

如果没有符合条件的品种或者总仓位<100%，买入短债基金代替；

达到卖出条件分批减仓，减仓可以逆运算，也可以简单的用一个网格策略逐步卖出。

#### 不定期不定额

如果我们有一个量化策略，可以直接把投入资金分为50份，在某个品种达到极高的胜率的时候计算仓位一把买入；然后在此之上， 采用价值平均策略定投，长期持有；

