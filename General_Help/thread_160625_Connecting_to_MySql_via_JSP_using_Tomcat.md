---
title: "Connecting to MySql via JSP using Tomcat"
date: 2006-04-15
forum: General Help
---

### Post by joe343 on 2006-04-15
Hi ! I have a problem connecting to MySql from a JSP page.  Here's my situation:

Using Ubuntu 5.10.  

Installed MySql 4.1.12 and it's working fine because a created a database using MySql Administrator and I've created a user for this database with the appropriate rights.  

Installed Tomcat 5.5.16 and it's working fine because when a got to [http://localhost/](http://localhost/) the default JSP page appears and the examples are working.  

Then I've downloaded the MySql Connector/J 3.1.12 and copied the mysql-connector-java-3.1.12-bin.jar file to my /usr/local/tomcat/common/lib/ and restarted tomcat (sudo /etc/init.d/tomcat restart).

I created a test page that looks like this:
```

<%@ page import="java.sql.*" %>
<%
	try {
		Class.forName("com.mysql.jdbc.Driver");
	} catch(ClassNotFoundException msg) {
		out.println("Error loading driver:" + msg.getMessage());
	}

	Connection ocon = null;
	int pages;

	ocon = DriverManager.getConnection("jdbc:mysql:3306//localhost/MYDB","MYUSER","MYPASS"); 
	Statement stmtt = ocon.createStatement();
	ResultSet rc = stmtt.executeQuery("Select count(*) from tblusers ");

	rc.next();
	pages = rc.getInt(1);
	out.println("Count of Records : " + pages + "<br>");

%>

```

Where MYDB, MYUSER and MYPASS are set correctly (same values I use with MySql Query Browser)

I've put the test.jsp there:
/usr/local/tomcat/webapps/root/test.jsp


And when I go to [http://localhost/test.jsp](http://localhost/test.jsp) I get this error:
```

HTTP Status 500 -

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

org.apache.jasper.JasperException: Exception in JSP: /test.jsp:12

9: 	Connection ocon = null;
10: 	int pages;
11: 
12: 	ocon = DriverManager.getConnection("jdbc:mysql:3306//localhost/MYDB","MYUSER","MYPASS"); 
13: 	Statement stmtt = ocon.createStatement();
14: 	ResultSet rc = stmtt.executeQuery("Select count(*) from tblusers ");
15: 


Stacktrace:
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:504)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:375)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

root cause

javax.servlet.ServletException: No suitable driver
	org.apache.jasper.runtime.PageContextImpl.doHandlePageException(PageContextImpl.java:858)
	org.apache.jasper.runtime.PageContextImpl.handlePageException(PageContextImpl.java:791)
	org.apache.jsp.test_jsp._jspService(test_jsp.java:69)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

root cause

java.sql.SQLException: No suitable driver
	java.sql.DriverManager.getConnection(DriverManager.java:545)
	java.sql.DriverManager.getConnection(DriverManager.java:171)
	org.apache.jsp.test_jsp._jspService(test_jsp.java:54)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

note The full stack trace of the root cause is available in the Apache Tomcat/5.5.16 logs.

```

Any help would be appreciated.
Thanks

---

### Post by rodonea on 2006-09-09
Copy the driver in the folder:

/usr/lib/j2sdk1.5-sun/jre/lib/ext/

---

