---
title: "Current Java VM installation doesn't work correctly :("
date: 2009-11-01
forum: General Help
---

### Post by cthlhu1987 on 2009-11-01
Every time i try to run a programm more sophisticated than "hello world" or similar, the jvm gives me the following;(:
```
Exception in thread "main" java.lang.NoClassDefFoundError: jd.update.Main
   at java.lang.Class.initializeClass(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: com.sun.java.swing.plaf.windows.WindowsLookAndFeel not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jdupdate.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)

```

I have downloaded and installed the recent Sun JVM as a parallelly installed JVM and it worked without any problems.

Does anybody know how to solve this problem or how to "switch" the system to use the parallelly installed JVM? TIA

---

### Post by morningboat on 2009-11-05
You'd better to use Sun JDK rather than the GCJ for the Java environment. Currently your problem is caused by that Windows L&F is not available in GCJ environment.

---

