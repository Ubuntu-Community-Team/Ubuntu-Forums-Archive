---
title: "MySQL connector not found"
date: 2011-06-20
forum: General Help
---

### Post by Newbie2011 on 2011-06-20
Hi,

I am quite new to Ubuntu and struggle with Tomcat and the MySQL connector.

I installed Tomcat (apt-get install tomcat6 tomcat6-admin tomcat6-common tomcat6-user tomcat6-docs tomcat6-examples) and it runs without problems.

I installed MySQL (apt-get install mysql-server) and it seems to run without problems too.

I changed the default JRE (update-java-alternatives -s java-6-sun).

The weird thing is - if I put the connector-jar into my web application (WEB-INF/lib), the connection works. If I put the connector-jar into usr/share/java, it does not work. If I write the jar location into the CLASSPATH and try "java com.mysql.jdbc.Driver", I get a NoSuchMethodError:Main, which means, that the jar is found?!

The datasource in the tomcat context.xml is: 

<Resource name="jdbc/myresource" auth="Container" type="javax.sql.DataSource" maxActive="100" maxIdle="30" maxWait="10000" username="username" password="password" driverClassName="com.mysql.jdbc.Driver" url="jdbc:mysql://localhost:3306/myschema" />

How can I make the database connection work without putting the jar into the WEB-INF/lib folder of the web application?

---

### Post by _0R10N on 2011-06-20
Hi! it looks like a typical case of environment variables problem. You could try installing libmysql-java. That will install the connector you require at make it known across your system.

---

### Post by Newbie2011 on 2011-06-22
Hi, thanks for the reply. I installed the connector with libmysql-java, but it was still not found by Tomcat.

---

