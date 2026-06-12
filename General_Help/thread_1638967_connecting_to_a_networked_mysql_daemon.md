---
title: "connecting to a networked mysql daemon"
date: 2010-12-06
forum: General Help
---

### Post by emonti on 2010-12-06
Hi,

I have two machines each running lucid and they are on a home network.

I have installed Tomcat on one machine and MySQL on another. When I run tomcat on the same machine as Mysql and use 'localhost' in the jdbc url, I have no problem accessing mysql through jdbc. So my problem is accessing a remote mysql instance.

I have granted privileges in the following way from the MySQL prompt:[INDENT]GRANT ALL PRIVILEGES ON mydatabase.* TO myusername @192.168.0.103  IDENTIFIED BY 'mypassword';

FLUSH PRIVILEGES;
[/INDENT]Still I get :

com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Access denied for user 'myusername'@'192.168.0.103' to database 'mydatabase'
    sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    com.mysql.jdbc.Util.handleNewInstance(Util.java:409)
    com.mysql.jdbc.Util.getInstance(Util.java:384)
    com.mysql.jdbc.SQLError.createSQLException(SQLError.java:1054)
    com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3566)
    com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3498)
    com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:919)
    com.mysql.jdbc.MysqlIO.secureAuth411(MysqlIO.java:4004)
    com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1284)
    com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2312)
    com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2122)
    com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:774)
    com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:49)
    sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    com.mysql.jdbc.Util.handleNewInstance(Util.java:409)
    com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:375)
    com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:289)
    org.apache.commons.dbcp.DriverConnectionFactory.createConnection(DriverConnectionFactory.java:38)
    org.apache.commons.dbcp.PoolableConnectionFactory.makeObject(PoolableConnectionFactory.java:582)
    org.apache.commons.dbcp.BasicDataSource.validateConnectionFactory(BasicDataSource.java:1556)
    org.apache.commons.dbcp.BasicDataSource.createPoolableConnectionFactory(BasicDataSource.java:1545)
    org.apache.commons.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:1388)
    org.apache.commons.dbcp.BasicDataSource.getConnection(BasicDataSource.java:1044)
    org.springframework.jdbc.datasource.DataSourceUtils.doGetConnection(DataSourceUtils.java:113)
    org.springframework.jdbc.datasource.DataSourceUtils.getConnection(DataSourceUtils.java:79)
    org.springframework.jdbc.core.JdbcTemplate.execute(JdbcTemplate.java:572)
    org.springframework.jdbc.core.JdbcTemplate.query(JdbcTemplate.java:636)
    org.springframework.jdbc.core.JdbcTemplate.query(JdbcTemplate.java:665)
    org.springframework.jdbc.core.JdbcTemplate.query(JdbcTemplate.java:673)
    org.springframework.jdbc.core.JdbcTemplate.query(JdbcTemplate.java:713)
    org.springframework.jdbc.core.simple.SimpleJdbcTemplate.query(SimpleJdbcTemplate.java:200)
    org.springframework.jdbc.core.simple.SimpleJdbcTemplate.query(SimpleJdbcTemplate.java:205)
....
        sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    java.lang.reflect.Method.invoke(Method.java:616)
    org.springframework.web.bind.annotation.support.HandlerMethodInvoker.doInvokeMethod(HandlerMethodInvoker.java:710)
    org.springframework.web.bind.annotation.support.HandlerMethodInvoker.invokeHandlerMethod(HandlerMethodInvoker.java:167)
    org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter.invokeHandlerMethod(AnnotationMethodHandlerAdapter.java:414)
    org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter.handle(AnnotationMethodHandlerAdapter.java:402)
    org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:771)
    org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:716)
    org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:647)
    org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:552)
    javax.servlet.http.HttpServlet.service(HttpServlet.java:617)
    javax.servlet.http.HttpServlet.service(HttpServlet.java:717)

I have no idea whether this is a problem at the operating system level i.e. allowing networked hosts, or whether it is something to do with MySQL. I have commented out bindaddress and, on this version, there is no 'skip-networking' line to comment out.

Any advice will be much appreciated.

---

### Post by surfer on 2010-12-06
did you change the bind-address in /etc/mysql/my.cnf on the server?

by default the mysql server will only listen to 127.0.0.1. if you want to connect from any other machine, you have to comment out that line (all machines will be allowed to access the server) or edit the address there.

---

### Post by lukeiamyourfather on 2010-12-06
> **surfer said:**
> did you change the bind-address in /etc/mysql/my.cnf on the server?

by default the mysql server will only listen to 127.0.0.1. if you want to connect from any other machine, you have to comment out that line (all machines will be allowed to access the server) or edit the address there.

+1

I recently discovered this after many hours of troubleshooting. This issue can be confirmed with the netstat command. Any service bound to 0.0.0.0 means a host from any IP can connect. If a service is bound to 127.0.0.1 means that only the localhost can use that service (default of MySQL).

---

### Post by emonti on 2010-12-06
Hi guys,

I commented out that line in my.cnf so that's not the problem. 

Thanks for the suggestion, tho'.

```
sudo netstat -lnp | grep mysql
``` gives me:

```
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      7032/mysqld     
unix  2      [ ACC ]     STREAM     LISTENING     738008   7032/mysqld         /var/run/mysqld/mysqld.sock
```

---

### Post by emonti on 2010-12-06
I have moved the mysql db onto the same machine as tomcat for the time being.

What I did find out tho', is that by putting 'mysqld 192.168.0.103' into hosts.allow and restarting the daemon, I can access the remote mysql daemon using the cmd line tool. i.e. mysql -h 192.168.0.100 -myusername -p mypasswd

 So I'd be surprised if that didn't work from jdbc now.

Thanks for the help ;)

---

