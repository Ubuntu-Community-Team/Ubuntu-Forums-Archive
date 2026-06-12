---
title: "Can't run .java"
date: 2010-08-26
forum: General Help
---

### Post by phase constant on 2010-08-26
Like the title says. 

I'm trying to install Open Rocket : [http://openrocket.sourceforge.net/download.html](http://openrocket.sourceforge.net/download.html)

I don't think I have java installed.

I went to software center and trie to install "OpenJDK Java 6 runtime" and it says package dependencies cannot be resolved.

I tried doing sudo apt-get install through terminal and it was dependent on a long list of things:

openjdk-6-jre
openjdk-6-jre-headless
tzdata-java
tzdata

I tried to sudo apt-get each one and it led me down the list like that to a dead end.  

What can I do?

---

### Post by mthalis on 2010-08-26
Read this

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by Sef on 2010-08-26
What os are you running?

---

### Post by phase constant on 2010-08-26
> **sef said:**
> what os are you running?

10.04 lts

---

### Post by phase constant on 2010-08-26
> **mthalis said:**
> Read this

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

Thanks

---

### Post by phase constant on 2010-08-26
I've got it installed. I verified like that article said.

Now how do I run a file with extension .java?

---

### Post by mthalis on 2010-08-26
If you want to compile java files you have to intall JDK also

**apt-get install sun-java6-jdk** 

Comile java file using -  javac youfile.java
Run that file          -  java youfile
Run jar file           -  java -jar yourjarfile.jar

---

