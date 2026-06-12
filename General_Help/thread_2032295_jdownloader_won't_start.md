---
title: "jdownloader won't start"
date: 2012-07-23
forum: General Help
---

### Post by kill o matic on 2012-07-23
When I try to run jdownloader from the terminal, I get this.

```
------------------------  Thread: 10  -----------------------
10 12-7-23 23:25:18 - INFO [jd.Main(main)] -> Start JDownloader
Exception in thread "main" java.lang.ExceptionInInitializerError
    at jd.Main.main(Main.java:368)
Caused by: java.lang.SecurityException: class "org.appwork.utils.event.DefaultEvent"'s signer information does not match signer information of other classes in the same package
    at java.lang.ClassLoader.checkCerts(ClassLoader.java:787)
    at java.lang.ClassLoader.preDefineClass(ClassLoader.java:502)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:628)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at jd.controlling.JDController.<init>(JDController.java:201)
    at jd.controlling.JDController.<clinit>(JDController.java:193)
    ... 1 more
```Any help would be appreciated.

---

