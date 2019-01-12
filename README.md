# pyswip_tutorial
pyswip的使用教程

> 与[sudoku_pyswip](https://github.com/yaopenglalala/sudoku_pyswip)简单案例一起食用更佳

## 第一步：安装SWI-Prolog

首先你需要安装自己对应平台的[SWI-Prolog](http://www.swi-prolog.org/Download.html)。切记[pyswip](https://github.com/yuce/pyswip)只是连接你的python程序与SWI-Prolog之间的桥梁，本身并不自带Prolog推理功能。调用使用了电脑的注册表项，所用不安装SWI-Prolog根本无法导入pyswip包。

## 第二步：安装pyswip
```
pip install pyswip
```
## 第三步：使用pyswip
1. 从pyswip导入Prolog
    ```
    from pyswip import Prolog
    ```
2. 运行外部prolog文件：consult函数  
    例如：
    ```
    solution_pl = Prolog()
    solution_pl.consult("sudoku_solution.pl")
    ```
3. 执行查询：query函数  
    例如：
    ```
    result = solution_pl.query(“solution(X,Y)”)
    ```
4. 查询返回值：一个字典（dictionary）的list  
    此处引用[官方示例](https://github.com/tjvr/pyswip)：
    ```
    >>> from pyswip import Prolog
    >>> prolog = Prolog()
    >>> prolog.assertz("father(michael,john)")
    >>> prolog.assertz("father(michael,gina)")
    >>> list(prolog.query("father(michael,X)"))
    [{'X': 'john'}, {'X': 'gina'}]
    >>> for soln in prolog.query("father(X,Y)"):
    ...     print soln["X"], "is the father of", soln["Y"]
    ...
    michael is the father of john
    michael is the father of gina
    ```
    可以看到，在每一个dict中，key都是query函数中所写的prolog查询语句中的变量。

## 其他
1. 其他常用函数：  
    assertz()：向prolog系统中添加事实或规则。
2. 学习链接：  
    [pyswip官方github主页](https://github.com/tjvr/pyswip)  
    [SWI-Prolog下载链接](http://www.swi-prolog.org/Download.html)  
    [SWI-Prolog官方教程](http://www.swi-prolog.org/pldoc/man?section=quickstart)