---
title: "tomcat wont start"
date: 2009-08-19
forum: General Help
---

### Post by abazoskib on 2009-08-19
im pretty sure i installed everything correctly. here's what i see after running./startup.sh from within the $CATALINA_HOME dir:

```
Using CATALINA_BASE:   /usr/local/tomcat/apache-tomcat-6.0.20
Using CATALINA_HOME:   /usr/local/tomcat/apache-tomcat-6.0.20
Using CATALINA_TMPDIR: /usr/local/tomcat/apache-tomcat-6.0.20/temp
Using JRE_HOME:       /usr/java/jdk1.6.0_16/bin/java

```

However the tomcat server does not start. I used chmod +x on the startup and shutdown scripts.

---

### Post by abazoskib on 2009-08-19
still looking at it, and everything seems fine

---

### Post by abazoskib on 2009-08-19
ok so i got this error now:

```
Starting tomcat5: /usr/bin/rebuild-jar-repository: error: JVM_LIBDIR /usr/lib/jvm-exports/java does not exist or is not a directory
/usr/bin/rebuild-jar-repository: error: JVM_LIBDIR /usr/lib/jvm-exports/java does not exist or is not a directory
/usr/bin/rebuild-jar-repository: error: JVM_LIBDIR /usr/lib/jvm-exports/java does not exist or is not a directory
/usr/bin/rebuild-jar-repository: error: JVM_LIBDIR /usr/lib/jvm-exports/java does not exist or is not a directory
                                                           [  OK  ]

```

what does that mean?

---

