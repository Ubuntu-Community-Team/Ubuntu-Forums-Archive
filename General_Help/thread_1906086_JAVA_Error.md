---
title: "JAVA Error"
date: 2012-01-08
forum: General Help
---

### Post by shashanksingh on 2012-01-08
I made a very simple java file t.
It compiles, but gives me the following exception on runtime

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: t : Unsupported major.minor version 51.0
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
Could not find the main class: t. Program will exit.

```

Is it because I have installed openjdk-7? I searched ol and it seems to be some version problem.

I have installed openjdk-7-jre and openjdk-7-jdk

---

