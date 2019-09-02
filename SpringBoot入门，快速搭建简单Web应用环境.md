- **SpringBoot入门，快速搭建简单Web应用环境**

- **1.基本环境（自行下载安装）**

- JDK:1.8

- Intellij IDEA:2018.1.6 （免费注册码地址http://idea.lanyus.com/）

- Maven:3.5.3

- **2.开始搭建**

- 使用idea创建Springboot应用非常简单，废话不多说，搞起。

- 打开idea，点击新建项目：

- ![img](file:///11.png)

- 选择Spring Initializr，点击next：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image002.png)

-  

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image003.png)

- 上面的信息可自行修改，其他默认就行，之后next：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image004.png)

- 如图所示，添加web依赖，右上角Springboot版本号可自行选择，我这里默认没动。之后点击next：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image005.png)

- 点击Finish完成项目创建。进入到主界面后，maven会下载一些依赖包，可能会需要一段时间，整体目录如下：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image006.png)

- 至此，springboot工程已经创建完毕，下面开始测试。

- **3.测试**

- 每个springboot项目都会有一个命名为xxApplication.java的入口程序，我们只需要启动它就行。效果如下图所示：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image007.png)

- 由于我们在创建项目的时候，添加了web组件，程序启动后会开启服务器，默认端口8080。

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image008.png)

- 现在我们打开浏览器，输入[http://localhost:8080](http://localhost:8080/)进行查看，结果如下图：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image009.png)

- 由于我们什么也写，所以界面显示报错，下面我们在java/com.example下新建一个controller包，然后创建一个HelloController类：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image010.png)

- @RestController注解是@Controller和@ResponseBody注解的合体。之后我们再次启动入口程序，在浏览器中输入http://localhost:8080/hello查看效果。

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image011.png)

- 可以看到，页面已经正确返回我们想要的东西，那么如何跳转到我们想要的界面呢，springboot不推荐jsp开发，推荐使用thymeleaf模版引擎进行web页面开发，所以我们需要在pom.xml添加thymeleaf依赖：

-  

- 1. <dependency>
  2. <groupId>org.springframework.boot</groupId>
  3. <artifactId>spring-boot-starter-thymeleaf</artifactId>
  4. </dependency>

- 然后打开springboot配置文件application.properties，添加下面两个配置信息，用来指定跳转页面的存放路径和页面的格式信息：

-  

- 1. spring.thymeleaf.prefix=classpath:/templates/
  2. spring.thymeleaf.suffix=.html

- **classpath:指向的是resources目录**。然后我们在新建一个HiController类：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image012.png)

- **注意，这里用的是@Controller注解，不是@RestController**

- 可以看到我们返回的是"index"，根据配置文件，即返回/templates/index.html页面，所以我们需要在templates目录下新建一个index.html页面。

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image013.png)

- 准备工作完成，启动入口程序，在浏览器中输入http://localhost:8080/hi查看效果：

- ![img](file:///C:/Users/donsp/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image014.png)

- ok，大功告成，返回的是我们执指定的页面。一个简单的基于springboot的web应用就搭建完成。

- **4.总结**

- 博主也是刚刚开始学习springboot，感觉用起来十分方便，之前也学过搭建SSM框架，各种配置文件根本记不住。。使用springboot就完全不用担心那些繁琐的配置步骤了，是不是很爽。下一篇，我将继续使用这个项目，整合mybatis。有什么问题欢迎大家批评指正。

-  

- 来自 <https://blog.csdn.net/qq_27317475/article/details/81119098> 