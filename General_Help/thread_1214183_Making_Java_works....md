---
title: "Making Java works..."
date: 2009-07-15
forum: General Help
---

### Post by Shinka.S on 2009-07-15
I'm having a hard time making Java works witouth openJDK. sun-java6-jdk and sun-java6-jre are installed, but for some reason if I remove openJDK a java program like NetBeans will refuse to open.

The result of **sudo update-alternatives --config java;**

```
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
          3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java
```

---

