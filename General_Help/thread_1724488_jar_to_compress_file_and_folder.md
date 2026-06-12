---
title: "jar to compress file and folder"
date: 2011-04-08
forum: General Help
---

### Post by cucucur on 2011-04-08
hi! I have some files and folders to compress, and I have no idea how to do it!!

The folders have some subfolders, there are all of them in the same folder:

```

ubuntu@ubuntu:/var/www/bridge/java$ ls
bridge           database.jar                         pruebaLog.class
bridge.jar       database.java                        pruebaLog.jar
com              log.log                              pruebaLog.java
database2.class  META-INF                             tocaDB.class
database2.java   mysql-connector-java-5.1.15-bin.jar  tocaDB.java
database.class   org


```

I want to compress in a jar file, META-INF, com, org and pruebaLog.class, how can I do it??

thank you so much!!!

---

### Post by randallecook on 2011-04-08
The jar man page should have information (execute 'man jar' on the command line), or you could read this:

[http://download.oracle.com/javase/1.4.2/docs/tooldocs/windows/jar.html](http://download.oracle.com/javase/1.4.2/docs/tooldocs/windows/jar.html)

I am guessing that some combination of 'jar c...' or 'jar u...' will do what you want. use 'jar t...' to verify the resulting jar file.

---

