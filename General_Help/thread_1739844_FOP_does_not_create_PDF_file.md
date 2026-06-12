---
title: "FOP does not create PDF file"
date: 2011-04-26
forum: General Help
---

### Post by code_expert on 2011-04-26
Hi Guys,

I have installed fop 0.95 and I am trying to use it within an application to create pdf files. I get the following error message though. I appreciate any help or idea, as I am not sure what causes this and how to fix it.

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/fop/cli/Main Caused by: 
java.lang.ClassNotFoundException: org.apache.fop.cli.Main     at 
java.net.URLClassLoader$1.run(URLClassLoader.java:217)     at 
java.security.AccessController.doPrivileged(Native Method)     at 
java.net.URLClassLoader.findClass(URLClassLoader.java:205)     at 
java.lang.ClassLoader.loadClass(ClassLoader.java:321)     at 
sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)     at 
java.lang.ClassLoader.loadClass(ClassLoader.java:266) Could not find the main class: 
org.apache.fop.cli.Main. Program will exit. 

Thanks,

---

