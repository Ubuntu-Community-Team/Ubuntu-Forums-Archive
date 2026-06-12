---
title: "JDK runtime not working?"
date: 2012-02-21
forum: General Help
---

### Post by test_tube_baby on 2012-02-21
Hello,

I am trying to play this java applet here [http://www.chess.com/play/computer.html]("http://www.chess.com/play/computer.html")

However, the page always fails to load. It just crashes.

This is a java problem, and the same problem persists with firefox and google-chrome and chromium browser.

Anybody know a fix for this?

I have java/jdk installed. my ```
dpkg -l |grep jdk
``` command returns:
```
ii  default-jdk                                   1:1.6-42ubuntu2                             Standard Java or Java compatible Development Kit
ii  default-jdk-doc                               0.42ubuntu2                                 Standard Java or Java compatible Development Kit (documentation)
ii  gcj-4.6-jdk                                   4.6.1-4ubuntu2                              gcj and classpath development tools for Java(TM)
ii  gcj-jdk                                       4:4.6.1-2ubuntu5                            gcj and classpath development tools for Java(TM)
ii  openjdk-6-dbg                                 6b23~pre11-0ubuntu1.11.10.1                 Java runtime based on OpenJDK (debugging symbols)
ii  openjdk-6-demo                                6b23~pre11-0ubuntu1.11.10.1                 Java runtime based on OpenJDK (demos and examples)
ii  openjdk-6-doc                                 6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Development Kit (JDK) documentation
ii  openjdk-6-jdk                                 6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Development Kit (JDK)
ii  openjdk-6-jre                                 6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                        6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                             6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Java runtime (architecture independent libraries)
ii  openjdk-6-jre-zero                            6b23~pre11-0ubuntu1.11.10.1                 Alternative JVM for OpenJDK, using Zero/Shark
ii  openjdk-6-source                              6b23~pre11-0ubuntu1.11.10.1                 OpenJDK Development Kit (JDK) source files
ii  openjdk-7-dbg                                 7~b147-2.0-0ubuntu0.11.10.1                 Java runtime based on OpenJDK (debugging symbols)
ii  openjdk-7-demo                                7~b147-2.0-0ubuntu0.11.10.1                 Java runtime based on OpenJDK (demos and examples)
ii  openjdk-7-doc                                 7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Development Kit (JDK) documentation
ii  openjdk-7-jdk                                 7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Development Kit (JDK)
ii  openjdk-7-jre                                 7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless                        7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                             7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Java runtime (architecture independent libraries)
ii  openjdk-7-jre-zero                            7~b147-2.0-0ubuntu0.11.10.1                 Alternative JVM for OpenJDK, using Zero/Shark
ii  openjdk-7-source                              7~b147-2.0-0ubuntu0.11.10.1                 OpenJDK Development Kit (JDK) source files
ii  uwsgi-plugin-jvm-openjdk-6                    0.9.8.1-1                                   Java plugin for uWSGI (OpenJDK 6)
ii  uwsgi-plugin-jwsgi-openjdk-6                  0.9.8.1-1                                   JWSGI plugin for uWSGI (OpenJDK 6)

```

---

### Post by HeroOfCanton on 2012-02-21
I can't see it either. I write/run Java on this computer with no problem. Maybe the app has a problem with the open JRE?

Have you tried another Java app to make sure it's not just that particular one?

---

### Post by test_tube_baby on 2012-02-22
It used to work fine on my ubuntu machine, and it works fine on my windows virtual machine. just lately, it doesn't work.

---

### Post by raja.genupula on 2012-02-22
> **test_tube_baby said:**
> It used to work fine on my ubuntu machine, and it works fine on my windows virtual machine. just lately, it doesn't work.
have you gone through any updates recently ?

---

### Post by test_tube_baby on 2012-02-22
This worked on Natty. It stopped working when I moved to 11.10

---

### Post by raja.genupula on 2012-02-23
Ok , try it by reinstalling . we need to do  purging uninstall  before install . 

all the best .

---

### Post by zeljkojagust on 2012-02-23
Try to install Oracle's (ex Sun) version, here is a guide how you can do it in Ubuntu: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by test_tube_baby on 2012-02-25
> **zeljkojagust said:**
> Try to install Oracle's (ex Sun) version, here is a guide how you can do it in Ubuntu: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

It works! thanks :)

---

