# Java学习笔记
![JDK version](https://camo.githubusercontent.com/f59a54da103da23eb40c2bc323aee9c8104266c3/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4a444b2d312e382d627269676874677265656e2e737667)

## Java平台
整体蓝图
![java蓝图](https://github.com/sgzilv/javaLearning/blob/master/img/java%E5%B9%B3%E5%8F%B0.jpg)

JVM通过类加载器（class_loader）加载字节码**解释**或者**编译**执行。
* 解释：class文件经过JVM内嵌的解释器解释执行
* 编译：在JIT编译器（Just In Time Compile）把经常运行的代码作为**热点代码**编译与本地平台相关的机器码，并进行各种层次的优化
* AOT编译器： Java 9提供的直接将所有代码编译成机器码执行

## Error && Exception
两者都继承了Throwable类（才可被抛出（throw）或捕获（catch））
![继承关系图](https://github.com/sgzilv/javaLearning/blob/master/img/error_exception.png)
* 尽量不要捕获类似Exception这样的通用异常，而是应该捕获特定异常
* 不要生吞（swallow）异常
```sh 
try {
  // 业务代码
  // …
  Thread.sleep(1000L);
} catch (Exception e) {
  // Ignore it
}
```
自定义异常，除了保证需要提供足够的信息，还有2点需要考虑：
* 1.是否需要定义成Checked Exception, 因为类型设计的初衷更是为了从异常情况恢复，作为异常设计者，我们往往有充足信息进行分类
* 2.在保证诊断信息充足的同时，也要考虑避免包含敏感信息，因为那样可能会导致潜在的安全问题

## String && StringBuffer && StringBuilder
### String
* Immutable类，被声明为final class, value属性也是final.
* String str0 = "123" ->通过直接赋值方式，放入字符串常量池
  String str1 = new String("123") ->不会放入字符串常量池
* intern() 方法
* Java 9中，存储方式由char数组变为byte数组加上一个标识编码的所谓coder

### StringBuffer && StringBuilder
* 二者都继承了AbstractStringBuilder，区别在于最终的方法是否加了sychronized,初始长度均为16





