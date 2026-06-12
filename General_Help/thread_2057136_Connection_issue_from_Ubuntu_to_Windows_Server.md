---
title: "Connection issue from Ubuntu to Windows Server"
date: 2012-09-13
forum: General Help
---

### Post by rahuljha088 on 2012-09-13
Hi,
I am using Ubuntu 12 in Oracle VM which is installed in Windows Server. i have installed Mysql in Ubuntu and Mssql in Windows. There are two scripts. one is basically creating table in Mysql(which is successfully executing right now)while executing another script which should create table in MSSQL in windows it is giving following error:
-------------------------------------------------------------------------------
An exception occurred.  Please see the following for details:
-------------------------------------------------------------------------------
java.net.ConnectException: Connection timed out
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
    at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
    at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
    at java.net.Socket.connect(Socket.java:546)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at net.sourceforge.jtds.jdbc.SharedSocket.createSocketForJDBC3(SharedSocket.java:305)
    at net.sourceforge.jtds.jdbc.SharedSocket.<init>(SharedSocket.java:255)
    at net.sourceforge.jtds.jdbc.ConnectionJDBC2.<init>(ConnectionJDBC2.java:323)
 [wrapped] java.sql.SQLException: Network error IOException: Connection timed out
    at net.sourceforge.jtds.jdbc.ConnectionJDBC2.<init>(ConnectionJDBC2.java:395)
    at net.sourceforge.jtds.jdbc.ConnectionJDBC3.<init>(ConnectionJDBC3.java:50)
    at net.sourceforge.jtds.jdbc.Driver.connect(Driver.java:184)
    at org.apache.commons.dbcp.DriverConnectionFactory.createConnection(DriverConnectionFactory.java:38)
    at org.apache.commons.dbcp.PoolableConnectionFactory.makeObject(PoolableConnectionFactory.java:582)
    at org.apache.commons.dbcp.BasicDataSource.validateConnectionFactory(BasicDataSource.java:1556)
    at org.apache.commons.dbcp.BasicDataSource.createPoolableConnectionFactory(BasicDataSource.java:1545)
 [wrapped] org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (Network error IOException: Connection timed out)
    at org.apache.commons.dbcp.BasicDataSource.createPoolableConnectionFactory(BasicDataSource.java:1549)
    at org.apache.commons.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:1388)
    at org.apache.commons.dbcp.BasicDataSource.getConnection(BasicDataSource.java:1044)
    at org.jumpmind.symmetric.AbstractCommandLauncher.testConnection(AbstractCommandLauncher.java:325)
 [wrapped] java.lang.RuntimeException: org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (Network error IOException: Connection timed out)
    at org.jumpmind.symmetric.AbstractCommandLauncher.testConnection(AbstractCommandLauncher.java:329)
    at org.jumpmind.symmetric.AbstractCommandLauncher.getDatabasePlatform(AbstractCommandLauncher.java:336)
    at org.jumpmind.symmetric.DbImportCommand.executeWithOptions(DbImportCommand.java:104)
    at org.jumpmind.symmetric.AbstractCommandLauncher.execute(AbstractCommandLauncher.java:130)
    at org.jumpmind.symmetric.DbImportCommand.main(DbImportCommand.java:65)
-------------------------------------------------------------------------------
    


Kindly Help!!

---

