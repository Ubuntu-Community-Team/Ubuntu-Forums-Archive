---
title: "Local Site not working on Tomcat 6"
date: 2009-09-19
forum: General Help
---

### Post by tomcatProb on 2009-09-19
Hi,
I am new to Ubuntu, and having problem in porting a site with Tomcat 6. Site was initially made and tested on Windows XP with Apache and Tomcat 6 installed, it worked perfectly there. but when i tried to port it on Ubuntu, its not working. In the site i have a login page, when i try to login Tomact throughs Java Null Exception. I have all the Java files (servlets) which are attached to my site's JSP pages in the WEB-INF/classs/projectName folder with respective compiled java class files. All the required settings like JAVA_HOME, CATALINA_HOME are set.
Pls help.

---

### Post by nikhilbhardwaj on 2009-09-19
which database do you use
if you use an access database 
then you may have troubles connecting unless you have unix-odbc

---

### Post by tomcatProb on 2009-09-19
Hi, Thanx for the reply.  I am using MySQL and its working correctly i can access database tables. But i think issue is related to some java files, as files included in JSP pages are not loaded and printf statements in Java files are not shown on command prompt.

---

