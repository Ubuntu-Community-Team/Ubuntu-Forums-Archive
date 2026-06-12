---
title: "Java problem"
date: 2011-06-26
forum: General Help
---

### Post by tarciokk on 2011-06-26
Hi, I install ubuntu server amd64bit. And  configured everything   normal. Phpmyadmin, user, ftp, putty, internet,raid... perfect work!
 But no Java ... : (


 I'm trying to start L2 server, and I get this error.

 root @: / lineage / login #. / startLoginServer.sh
 Exception in thread "main" java.lang.NoClassDefFoundError: version
 Caused by: java.lang.ClassNotFoundException: version
         at java.net.URLClassLoader $ 1.run (URLClassLoader.java: 202)
         at java.security.AccessController.doPrivileged (Native Method)
         at java.net.URLClassLoader.findClass (URLClassLoader.java: 190)
         at java.lang.ClassLoader.loadClass (ClassLoader.java: 307)
         at sun.misc.Launcher $ AppClassLoader.loadClass (Launcher.java: 301)
         at java.lang.ClassLoader.loadClass (ClassLoader.java: 24:cool:
 Could not find the main class: version. Program will exit.

 

 Java install by this tuturial  [http://www.how-to.lt/viewtopic.php?f=6&t=82](http://www.how-to.lt/viewtopic.php?f=6&t=82)
 ```
 apt-get install sun-java6-jdk 
```
 I later Tring
 ```
 apt-get install sun-java * 
``` ITS did not help.

 Maybe someone can help for my Resolve this problem? My Skype: rayne.lt or post your answer there, thanks!


 [SIZE=150] ** [COLOR=PaleTurquoise]Maybe I need first start  java ? or configure somewhere? [/COLOR]** [/SIZE]

---

### Post by YesWeCan on 2011-06-26
What is the output of
java -version

---

### Post by tarciokk on 2011-06-27
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)



[Solved]Problem was bad server files. Thanks for help.

---

