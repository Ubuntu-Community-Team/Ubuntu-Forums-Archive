---
title: "Help running iDiet"
date: 2009-06-28
forum: General Help
---

### Post by edpatterson on 2009-06-28
I am trying to use iDiet on Ubunto 9.04. It is a Java app with a .jar file. I tried java iDiet.jar and got the following errors
```

Exception in thread "main" java.lang.NoClassDefFoundError: iDiet/jar
Caused by: java.lang.ClassNotFoundException: iDiet.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: iDiet.jar.  Program will exit.

```

Ideas? I do not know beans about java, but this app looks like what I am looking for.

---

### Post by edpatterson on 2009-06-28
I posted to quickly, the correct command line is:

jave -jar "iDiet.jar"

---

