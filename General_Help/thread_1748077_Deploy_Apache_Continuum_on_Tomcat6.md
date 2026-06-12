---
title: "Deploy Apache Continuum on Tomcat6"
date: 2011-05-03
forum: General Help
---

### Post by continuum1 on 2011-05-03
Hi,

I have ubuntu 10.04LTS server.
Open jdk and tomcat6 installed from synaptic package manager.
I run different war files on tomcat6.
I downloaded apache-continuum-1.3.7.war.
I followed the instructions on apache continuum web site.
[http://continuum.apache.org/docs/1.3...on/tomcat.html]("http://continuum.apache.org/docs/1.3.7/installation/tomcat.html")

1)I wrote /etc/init.d/tomcat6 this commands:
CONTINUUM_HOME=/var/lib/tomcat6
JAVA_OPTS="-Dappserver.home=$CONTINUUM_HOME -Dappserver.base=$CONTINUUM_HOME"
2)I put jar files to /var/lib/tomcat6/webapps/apache-continuum-1.3.7/WEB-INF/lib and /var/lib/tomcat6/common/lib also
3)I installed postfix as a smtp server
4)I created context.xml file /var/lib/tomcat6/webapps/apache-continuum-1.3.7/META-INF/context.xml

<Context path="/apache-continuum-1.3.7"
         docBase="/var/lib/tomcat6/webapps/apache-continuum-1.3.7.war">

  <Resource name="jdbc/users"
            auth="Container"
            type="javax.sql.DataSource"
            username="sa"
            password=""
            driverClassName="org.apache.derby.jdbc.EmbeddedDriver"
            url="jdbc:derby:database/users;create=true" />

  <Resource name="jdbc/continuum"
            auth="Container"
            type="javax.sql.DataSource"
            username="sa"
            password=""
            driverClassName="org.apache.derby.jdbc.EmbeddedDriver"
            url="jdbc:derby:database/continuum;create=true" />

  <Resource name="mail/Session"
            auth="Container"
            type="javax.mail.Session"
            mail.smtp.host="localhost"/>
</Context>

5) But I can't run continuum. I have these error in my log file. (catalina.out)
It creates continuum.log also.

May 3, 2011 5:24:05 AM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
May 3, 2011 5:24:05 AM org.apache.catalina.core.StandardContext start
SEVERE: Context [/apache-continuum-1.3.7] startup failed due to previous errors
May 3, 2011 5:24:05 AM org.apache.catalina.loader.WebappClassLoader clearReferencesThreads
SEVERE: A web application appears to have started a thread named [Store  url-failures-cache Spool Thread] but has failed to stop it. This is very  likely to create a memory leak.
May 3, 2011 5:24:05 AM org.apache.catalina.loader.WebappClassLoader clearThreadLocalMap
SEVERE: A web application created a ThreadLocal with key of type  [org.springframework.core.NamedThreadLocal] (value [Prototype beans  currently in creation]) and a value of type [null] (value [null]) but  failed to remove it when the web application was stopped. To prevent a  memory leak, the ThreadLocal has been forcibly removed.
May 3, 2011 5:24:05 AM org.apache.catalina.loader.WebappClassLoader clearThreadLocalMap
SEVERE: A web application created a ThreadLocal with key of type  [org.springframework.core.NamedThreadLocal] (value [XML bean definition  resources currently being loaded]) and a value of type [null] (value  [null]) but failed to remove it when the web application was stopped. To  prevent a memory leak, the ThreadLocal has been forcibly removed.

continuum.log:

2011-05-03 05:24:04,998 [http-8080-1] ERROR org.springframework.web.context.ContextLoader  - Context initialization failed
org.springframework.beans.factory.BeanCreationException: Error creating  bean with name 'workingDirectoryService#chrootJail': Injection of  resource fields failed; nested exception is  org.springframework.beans.factory.BeanCreationException: Error creating  bean with name 'configurationService' defined in URL  [jar:file:/var/lib/tomcat6/webapps/apache-continuum-1.3.7/WEB-INF/lib/continuum-commons-1.3.7.jar!/META-INF/spring-context.xml]:  Invocation of init method failed; nested exception is  javax.jdo.JDODataStoreException: Failed initialising database. Please  check that your database JDBC driver is accessible, and the database URL  and username/password are correct. Exception : Cannot create JDBC  driver of class '' for connect URL 'null'
org.apache.commons.dbcp.SQLNestedException: Cannot create JDBC driver of class '' for connect URL 'null'

---

### Post by dragonfly41 on 2011-05-03
Try here ..

[http://blog.jteam.nl/2011/03/18/debugging-the-dreaded-severe-error-listenerstart-and-severe-error-filterstart-tomcat-error-messages/](http://blog.jteam.nl/2011/03/18/debugging-the-dreaded-severe-error-listenerstart-and-severe-error-filterstart-tomcat-error-messages/)

---

