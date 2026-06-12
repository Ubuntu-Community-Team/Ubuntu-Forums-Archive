---
title: "Problem with Java"
date: 2011-03-20
forum: General Help
---

### Post by tomarmstrong on 2011-03-20
Hello, when i try to check my version of java I get this

```
tom@tom-laptop:~$ java versions
Exception in thread "main" java.lang.NoClassDefFoundError: versions
Caused by: java.lang.ClassNotFoundException: versions
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: versions. Program will exit.

```
Could you try and help me fix this :/

---

### Post by lykeion on 2011-03-20
Maybe this:
```
java -version
```
To show usage of java command:
```
java -?
```

---

### Post by Script Warlock on 2011-03-20
he forgot the dash and omit the s

---

