---
title: "Tomcat on Ubuntu Server"
date: 2010-08-13
forum: General Help
---

### Post by zombie_ on 2010-08-13
Hello everyone, 

I got a tomcat 6.0 on my Ubuntu server and wondering how I could use it with already developed WAR file. 

Thanks in advance,

---

### Post by moonport on 2010-08-13
Drop the test.war (the real name of your app instead of test)  into $CATALINA_HOME\webapps. A context called test will be created automatically. You can access the web application via URL [http://host:port/test](http://host:port/test).

Best

---

### Post by zombie_ on 2010-08-13
> **moonport said:**
> Drop the test.war (the real name of your app instead of test)  into $CATALINA_HOME\webapps. A context called test will be created automatically. You can access the web application via URL [http://host:port/test](http://host:port/test).

Best
I dont have the webApps folder inside Tomcat folder. 
> 
/etc/tomcat6$ ls
Catalina  catalina.properties  context.xml  logging.properties  policy.d  server.xml  tomcat-users.xml  web.xml

1) Should I create it?. 

2) Do I need to change any other config file?

---

### Post by moonport on 2010-08-17
Usually,there is a default folder schema,eg: /home/moonport/apache-tomcat-6.0.26/webapps.
Try: [http://localhost:8080/manager/html](http://localhost:8080/manager/html)
This is the Tomcat's management console, and you can deploy a .war file fron this.
Remenber before that, you need a manager-level-user credentials (check tomcat-users.xml file).

---

### Post by zombie_ on 2010-08-18
> **moonport said:**
> Usually,there is a default folder schema,eg: /home/moonport/apache-tomcat-6.0.26/webapps.
Try: [http://localhost:8080/manager/html](http://localhost:8080/manager/html)
This is the Tomcat's management console, and you can deploy a .war file fron this.
Remenber before that, you need a manager-level-user credentials (check tomcat-users.xml file).
The situation is Im using a Ubuntu server . So let say I can see my server via internet browser as : yourserver.mycompany.com

Now the Tomcat6.0 Is already installed. And when I go inside the folder I dont see the webapps so I create a folder webapps. 

Then, I put the  test.WAR file inside the webapps folder. 

Questions is: 

1. How to access it?
2. When I Start the tomcat on the server it doesnt deploy the test.war. 

Thanks in advance,

---

### Post by moonport on 2010-08-20
Check this: [http://oreilly.com/java/archive/tomcat-tips.html](http://oreilly.com/java/archive/tomcat-tips.html)

May be help.

---

