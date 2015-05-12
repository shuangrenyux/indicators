Indicators
==========

Trading indicators used in technical analysis of stock prices.

Implemented indicators in Python:

[EMA](http://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average): Exponential Moving Average

```Python
def getEMAList(inlist,num):
    k = 2.0/(num+1.0)
    ema = inlist[0]
    emaList = [ema]
    for item in inlist:
        ema = item*k+ema*(1-k)
        emaList.append(ema)
    return emaList
```

[MACD](http://en.wikipedia.org/wiki/MACD): Moving Average Convergence/Divergence `note:(Need getEMAList())`

```Python
def getMACDList(inList,short,long,mid):
    shortEMAList = getEMAList(inList,short)
    longEMAList = getEMAList(inList,long)
    macdList =[]
    diffList =[]
    for i in range(0,len(inList)+1):
        diff= shortEMAList[i]-longEMAList[i]
        diffList.append(diff)
        dea = getEMAList(diffList,mid)[-1]
        macd = [diffList[i],dea,(diffList[i]-dea)*2]
        macdList.append(macd)
    return macdList;
```
