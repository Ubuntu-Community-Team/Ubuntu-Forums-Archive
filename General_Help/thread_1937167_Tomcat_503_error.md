---
title: "Tomcat 503 error"
date: 2012-03-07
forum: General Help
---

### Post by anand1298 on 2012-03-07
Hello,

I installed tomcat in ubuntu using "sudo apt-get install tomcat6".
I installed examples also. I am trying to create my own servlet now. I installed openjdk6 using "sudo apt-get install openjdk-6-jdk". I create a "HelloWorld.java" file, whose contents are below and compiled it to "HelloWorld.class". I created a directory structure in "/usr/share" directory as follows:
testing
|----index.html
|----WEB-INF
      |----web.xml
      |----classes
              |----HelloWorld.class
And created a "testing.xml" in "/etc/tomcat6/Catalina/localhost" folder.

Contents of Files:
"HelloWorld.java"
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;
public class HelloWorld extends HttpServlet
{
public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException
{
response.setContentType("text/html;charset=\"UTF-8\"");
PrintWriter out = response.getWriter();
out.println("<html>");
out.println("<body><p>Hello World...</p></body>");
out.println("/<html>");
out.close();
}
}

"index.html"
<html>
<body>
<p>Testing index.html</p>
</body>
</html>

"web.xml"
<web-app>
<servlet>
<servlet-name>HelloWorldExample</servlet-name>
<servlet-class>HelloWorld</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>HelloWorldExample</servlet-name>
<url-pattern>/HelloWorld</url-pattern>
</servlet-mapping>
</web-app>

"testing.xml"
<Context path="/testing" docBase="/usr/share/testing" />

The problem is, when i try to browse to "http://localhost:8080/testing" using firefox, i get a "503 Service Temporarily Unavailable" error. Sometimes, after restarting tomcat using "sudo /etc/init.d/tomcat6 restart" command, i get the output of "index.html" alone and when i browse to "http://localhost:8080/testing/HelloWorld" i get "404 page Not Found" error. Any idea what's wrong? Or else, can you give me a simpler way to deploy servlets?

Regards,
M.Anand

---

