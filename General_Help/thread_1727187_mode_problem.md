---
title: "mode problem?"
date: 2011-04-12
forum: General Help
---

### Post by cucucur on 2011-04-12
hi! I'm trying to do a log file with Java, but it doesn't work as I want to. 

I write in a new folder /log (this is the exact route):

```

drwxr-xr-x   2 tomcat6 tomcat6     4096 2011-04-12 12:50 log

```

tomcat6 is supossed who writes. 

when I execute the java code, it writes the log file, but it creates a new one:

```

ubuntu@ubuntu:/log$ ls -l
total 60
-rwxrwxrwx 1 tomcat6 tomcat6    3 2011-04-12 12:30 log.log
-rw-r--r-- 1 tomcat6 tomcat6 3120 2011-04-12 12:34 log.log.38
-rw-r--r-- 1 tomcat6 tomcat6    0 2011-04-12 12:33 log.log.38.lck


```

could it be a permission problem? I tried the same code in Windows and it works fine!

Thand yo so much!!!

---

