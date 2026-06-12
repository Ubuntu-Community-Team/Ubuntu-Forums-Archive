---
title: "OpenOffice.org Languagetool"
date: 2010-10-06
forum: General Help
---

### Post by Mukoi on 2010-10-06
Hi,

Am quite new to OpenOffice.org and Linux.

Having problems in installing the language tool into OpenOffice 3.2.

Have tried to follow the instructions from their website, but I am obviously doing something wrong.

Am using Ubuntu 10.04 LTS.

Have downloaded the file to my downloads and when when I use the OpenOffice Extension Manager to get the extension I get a java error message.

---

### Post by viralmeme on 2010-10-06
> **Mukoi said:**
> Have downloaded the file to my downloads and when when I use the OpenOffice Extension Manager to get the extension I get a java error message.
What's the exact text of the Java error message?

---

### Post by Mukoi on 2010-10-06
It's quite long:

(com.sun.star.uno.RuntimeException) { { Message = "[jni_uno bridge  error] UNO calling java method writeRegistryInfo: non-UNO exception  occurred: java.lang.NoClassDefFoundError:  com/star/task/XJobExecutor\X000a\X009at  java.lang.ClassLoader.defineclass1(Native Method)\X000a\X0009at  java.lang.ClassLoader.defineClass(ClassLoader.java:634)\X000a\X0009at
java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)\X000a\X0009at
java.net.URLClassLoader.defineClass(URLClassLoader.java:277)\X000a\X0009at
java.net.URLClassLoader.access$000(URLClassLoader.java:73)\X000a\0009at
java.net.URLClassLoader$1.run(URLClassLoader.java:212)\X000a\0009at  java.security.AccessController.doPrivileged(Native Method)\X000a\0009at
java.net.URLClassLoader.findClass(URLClassLoader.java:205)\X000a\0009at
java.lang.ClassLoader.loadClass(ClassLoader.java:321)\X000a\0009at
java.lang.ClassLoader.loadClass(ClassLoader.java:314)\X000a\0009at
java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:615)\X000a\0009at
java.lang.ClassLoader.loadClass(ClassLoader.java:266)\X000a\0009at
com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:67)\X000a\0009at
com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:421)\X000aCaused  by: java.lang.ClassNotFoundException:  com.sun.star.task.XJobExecutor\X000a\X009at
java.net.URLClassLoader$1.run(URLClassLoader.java:217)\X000a\X0009at  java.security.AccessController.doPrivileged(Native Method)\X000a\X0009at
java.net.URLClassLoader.findClass(URLClassLoader.java:205)\X000a\X0009at
java.lang.ClassLoader.loadClass(ClassLoader.java:321)\X000a\X0009at
java.lang.ClassLoader.load.loadClass(ClassLoader.java:266)\X000a\X0009
... 14 more\X000a\X0009a", Context = (com.sun.star.uno.XInterface) @0 } }

---

### Post by zzzisgood on 2010-10-06
I got exactly the same error. My configuration are also Ubuntu 10.04, open office 3.2.  The extension did work a short while ago on another machine with ubuntu Karmic and open office 3.2.

---

### Post by viralmeme on 2010-10-07
> **Mukoi said:**
> UNO calling java method writeRegistryInfo: non-UNO exception  occurred:

[it is a Ubuntu problem. Installing the package openoffice.org-java-common resolves the issue!]("http://web.archiveorange.com/archive/v/LLXmL7jzaZWeEEfmK8d3")

---

### Post by Mukoi on 2010-10-07
Thank you.  The extension has now been installed.  Have tested it and it seems to work OK.

---

