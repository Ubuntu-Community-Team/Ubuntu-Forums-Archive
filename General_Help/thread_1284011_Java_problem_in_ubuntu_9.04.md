---
title: "Java problem in ubuntu 9.04"
date: 2009-10-06
forum: General Help
---

### Post by gaurav sontakke on 2009-10-06
Hi I am using ubuntu 9.04 .I have some question
 
1) Is there java version is differant for ubuntu
2) If yes where to download this version 
3) If no I am facing problem in java softwares like sqldeveloper 
when I move mouse cursor on blank field I get symbolic character and blured characters.

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.

> 1) Is there java version is differant for ubuntu
There is no ubuntu java, you have to use sun jdk (unless you want to use some free implementation: openjdk, etc)
> 2) If yes where to download this version 
To install sun jdk, you can use the ubuntu repositories:
sudo apg-get install sun-java6-jdk
Then, in a terminal, make sure you use sun jdk (you should get an output like the one below):
java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)
> 3) If no I am facing problem in java softwares like sqldeveloper 
when I move mouse cursor on blank field I get symbolic character and blured characters
I use oracle sqldeveloper with sun jdk 1.6, and have no problems...
Let me know if it is working for you.
Bogdan

---

### Post by credobyte on 2009-10-06
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by bogdan.veringioiu on 2009-10-06
Yes, better jre as pointed by credobyte.
I use jdk, also for development.
Bogdan

---

### Post by bigboy_pdb on 2009-10-06
It's already been mentioned how you can install Java as a runtime environment, but you can do a search in Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) to find out what programs are available.

Typing "java" in the quick search field brings up different packages that are affiliated with Java, including the JDK, plugins, and the runtime environment.

---

