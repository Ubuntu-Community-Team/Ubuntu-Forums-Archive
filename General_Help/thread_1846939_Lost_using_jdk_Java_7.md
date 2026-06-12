---
title: "Lost: using jdk Java 7"
date: 2011-09-19
forum: General Help
---

### Post by Steviedallas on 2011-09-19
I just installed Java 7 on my natty server using this guide:

[http://brunoreis.com/tech/intalling-java-ubuntu-natty/](http://brunoreis.com/tech/intalling-java-ubuntu-natty/)

I'm trying to teach myself java, but i'm not getting far because the .class file will not execute. I've typed up the code for my "hello world" java file, successfully compiled it using **javac**, then I try to run it, but I get this error:

```
root@server:~/Desktop/Test$ java hw
Exception in thread "main" java.lang.UnsupportedClassVersionError: hw : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: hw. Program will exit.
```

I figured there might be something wrong with the code I typed up, so I went to 2 diff websites, copied their code into the file, recompiled, etc... but the same error.

Any ideas?

---

