# springboot开发网站和小程序项目

## 复习所学知识
基本项目所要实现的功能：1.正常启动2.能对持久层数据进行CURD操作3.能访问当前项目的服务器4.能正常请求并获得响应
需要增加的一些功能：1.用lombok简化pojo层开发（@Data）2.设置拦截器、过滤器和监听器3.AOP切面日志打印4.简化service层开发（mybatisPlus提供的IService<T>接口和ServiceImpl<M,T>实现类）5.设置异常处理类6.设置模板引擎或视图对象或一般性结果对象/前后端分离，一般数据化处理7.rest模式开发
初建工程所需要做的事情：1.创建springboot工程，勾选必要依赖2.更改application配置文件为yml格式，并配好数据库的地址、用户名密码和驱动类3.新增好数据库，完成三层架构的代码4.设置mapping，并且创建视图解析器以方便返回视图或是直接返回静态资源
优化工程所需要做的事情：1.导入依赖加上注释2.复制粘贴一个实现HandlerInterceptor接口的类，并在实现了WebMvcConfigurer接口的类里面注册这个拦截器，后续在拦截器里完善拦截的逻辑3.给需要日志的类加上@sl4j即可用log对象打印日志了，在需要打印的地方实现逻辑（info,warn,debug,error）4.编写异常类继承Exception/RuntimeException类，重写构造函数，然后在特定的地方抛出该异常并传入相应的msg（自定义异常只起到一个名字的作用）5.（前后端分离）原本只需要写一个Result类即可返回数据（msg、data和code），但是更细分出DTO 、Entity和VO，所以用泛型类Result<T>，并泛型存储Data

## 一直想不起来的知识
前后端不分离开发：当客户端发送请求时，我们用控制器匹配请求并返回渲染好的视图，一是静态资源，直接返回逻辑视图的名称（“index.html”）它会自动在resources里面寻找static和templates下的资源（可以自己更改路径），二是动态资源，声明model实例，并将值传递进去，此时再返回静态页面，就会自动渲染之后再发给客户端。
前后端分离开发：前端自己做好了页面，然后用框架（vue）发送ajax请求，服务器再返回json格式的数据，这样前端就拿到数据再自行渲染。
spring的容器会在创建你的请求响应方法里声明的参数的实例，也就是@Mapping就有@Autowire的效果
用Thymeleaf返回视图的话，就要static和templates文件夹，以及配置好的prefix和suffix，再返回视图逻辑名称。
