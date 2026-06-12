---
title: "Tomcat6 and Permission problems"
date: 2010-10-13
forum: General Help
---

### Post by UltraLord on 2010-10-13
Hi, I'm a complete Linux n00by so please bear with me as I try best explain the problem.

1) I've installed Ubuntu 10.10 Server Edition on a new VM Machine so that I can start running tests again a Grails app I'm developing.

This is what I've done so far :
I've set the JAVA_HOME to that Java Path
I've installed Tomcat6 using the following [https://help.ubuntu.com/10.04/serverguide/C/tomcat.html](https://help.ubuntu.com/10.04/serverguide/C/tomcat.html)
I've also installed mysql and Webmin.

I have access to Tomcat Web Application Manager and all the example files work.

When I try to deploy ANY grails war (even wars that have been generated with no additional code)

I get the following in Catalina.out :
og4j:ERROR setFile(null,true) call failed.
java.io.FileNotFoundException: stacktrace.log (Permission denied)
{Can supply more info}

2010-10-13 12:18:30,336 [http-8080-1] ERROR context.ContextLoader  - Context initialization failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'messageSource': Initialization of bean failed; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'transactionManager': Cannot resolve reference to bean 'sessionFactory' while setting bean property 'sessionFactory'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'sessionFactory': Cannot resolve reference to bean 'hibernateProperties' while setting bean property 'hibernateProperties'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'hibernateProperties': Cannot resolve reference to bean 'dialectDetector' while setting bean property 'properties' with key [hibernate.dialect]; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dialectDetector': Invocation of init method failed; nested exception is org.springframework.jdbc.support.MetaDataAccessException: Error while extracting DatabaseMetaData; nested exception is org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (File input/output error prodDb.properties java.io.FileNotFoundException: prodDb.properties.new (Permission denied))
	at java.lang.Thread.run(Thread.java:636)
{Can supply more info}

Caused by: java.sql.SQLException: File input/output error prodDb.properties java.io.FileNotFoundException: prodDb.properties.new (Permission denied)
{Can supply more info}

13 Oct 2010 12:18:30 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
13 Oct 2010 12:18:30 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/TestDeployment-0.1] startup failed due to previous errors

It seems I've having permission issues.. Anybody have any idea how to fix this?

P.s. I've attached Catalina.out to the post

---

