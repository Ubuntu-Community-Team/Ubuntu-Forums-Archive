---
title: "How insall eclipse 3.6.2 classic (lastest version) on ubuntu 11.04"
date: 2011-04-30
forum: General Help
---

### Post by hightech20 on 2011-04-30
Hi I am beginner . 
How can I install eclipse 3.6.2 classic .
What additional step need to write java program ?
 By the way I installed sun-java6-jre and sun-java6-jdk through Synaptic Package Manager . 

thanks

---

### Post by lovinglinux on 2011-04-30
You can simply download it from Eclipse site, extract it somewhere in your home directory and execute the eclipse file inside it.

---

### Post by superchair on 2011-05-15
FYI I had issues with Eclipse 3.6 and Ubuntu 11.04; none of the menus worked.  Either a java bug or an eclipse bug.  Anyway, to fix it, you gotta write a script:

```
#!/bin/bash
unset UBUNTU_MENUPROXY
path/to/eclipse/here
```

Props to this blog that told me about it: [http://blog.matto1990.com/2011/04/using-eclipse-under-ubuntu-11-04-natty/](http://blog.matto1990.com/2011/04/using-eclipse-under-ubuntu-11-04-natty/)

---

### Post by dniMretsaM on 2011-05-15
I was going to install the latest (Helios?) but I just decided to install the one from the repos. Less work. And for Java, use the Eclipse IDE for Java developers (that's what the one in the repos is I think). But if you want to install Classic, you need the Java plugin (JDE I think).

---

