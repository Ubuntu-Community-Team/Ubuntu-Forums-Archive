---
title: "Need help converting *.bat to *.sh"
date: 2010-08-09
forum: General Help
---

### Post by hhhzzzarn on 2010-08-09
Solution: i was missing "deps/" before the last .jar.
Hello,
I converted the following .bat file:
```
@echo off 
title Oqra 
java -Xmx512m -cp bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server 
pause
```To:
```
#!/bin/bash 
java -Xmx512m -cp bin:deps/poi.jar:deps/mysql.jar:deps/mina.jar:deps/slf4j.jar:deps/slf4j-nop.jar:deps/jython.jar:log4j-1.2.15.jar: server.Server
```However, I am getting the following error after I did **chmod 777 Run.sh** then **sh Run.sh**:
```
Exception in thread "main" java.lang.NoClassDefFoundError: server/Server
Caused by: java.lang.ClassNotFoundException: server.Server
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
. Program will exit.ain class: server.Server

```The file "Server.class" is inside bin/server/Server.class.

---

### Post by nmaster on 2010-08-09
> **hhhzzzarn said:**
> Hello,
I converted the following .bat file:
```
@echo off 
title Oqra 
java -Xmx512m -cp bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server 
pause
```To:
```
#!/bin/bash 
java -Xmx512m -cp bin:deps/poi.jar:deps/mysql.jar:deps/mina.jar:deps/slf4j.jar:deps/slf4j-nop.jar:deps/jython.jar:log4j-1.2.15.jar: server.Server
```However, I am getting the following error after I did **chmod 777 Run.sh** then **sh Run.sh**:
```
Exception in thread "main" java.lang.NoClassDefFoundError: server/Server
Caused by: java.lang.ClassNotFoundException: server.Server
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
. Program will exit.ain class: server.Server

```The file "Server.class" is inside bin/server/Server.class.

i'm not sure what the answer is, but it seems like your real problem is with figuring out java packaging.  you might want to rename the thread and/or change the tags accordingly.

---

