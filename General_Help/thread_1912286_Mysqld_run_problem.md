---
title: "Mysqld run problem"
date: 2012-01-20
forum: General Help
---

### Post by Idiotji on 2012-01-20
Hi, 

I am using Connector/MXJ 5.0.12 to embed mysql and run some test cases in java. It works fine on Windows machine. But it fails on Linux (Ubuntu 11). The code I have used is 

File ourAppDir = new File(System.getProperty("java.io.tmpdir")); 
File databaseDir = new File(ourAppDir, "mysql-mxj"); 
int port = Integer.parseInt(System.getProperty("c-mxj_test_port", "3336")); 
String userName = "alice"; 
String password = "q93uti0opwhkd"; 

mysqldResource = new MysqldResource(databaseDir); 
Map options = new HashMap(); 
options.put("port", port); 
options.put(MysqldResourceI.INITIALIZE_USER, "true"); 
options.put(MysqldResourceI.INITIALIZE_USER_NAME, userName); 
options.put(MysqldResourceI.INITIALIZE_PASSWORD, password); 
String threadName = "OurApp MySQL"; 
mysqldResource.start(threadName, options); 

It fails at the line 'mysqldResource.start(threadName, options);' with the message 'please check the security manual to run mysqld as root!'. 

I have also tried this without providing a username and password but it still fails. 

Any help will be appreciated!!!

---

### Post by nothingspecial on 2012-01-20
Thread moved to General Help.

---

### Post by SeijiSensei on 2012-01-20
Is mysqld already running, or is it being invoked by this application?  The error you get suggests the latter.  If so, just let the OS manage mysqld and write your app to be a client.

---

