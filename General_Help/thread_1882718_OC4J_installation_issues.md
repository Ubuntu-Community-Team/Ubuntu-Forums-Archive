---
title: "OC4J installation issues"
date: 2011-11-17
forum: General Help
---

### Post by powerisall on 2011-11-17
Hey I'm trying to run OC4J for the Oracle Forms builder as a class project, and I've been fighting ubuntu (an OS I'm not entirely familiar with, but know enough to get in trouble) and I finally got to this problem which I cannot solve.

Whenever I use any of the commands (*$oc4j -start*, and *$java -jar $ORACLE_HOME/j2ee/home/oc4j.jar -install*) to run the OC4J instance, I get the following error message:

```

Exception in thread "main" java.lang.NoClassDefFoundError: oracle/core/ojdl/logging/LoggingConfigurationException
Caused by: java.lang.ClassNotFoundException: oracle.core.ojdl.logging.LoggingConfigurationException
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: com.evermind.server.OC4JServer. Program will exit
```I can't for the life of me find anybody who has had a similar problem via google, so as of now, I'm clueless.  Any suggestions?

---

