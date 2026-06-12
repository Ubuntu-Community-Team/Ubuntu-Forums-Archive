---
title: "Configure Eclipse for Java"
date: 2010-01-07
forum: General Help
---

### Post by conte_matthew on 2010-01-07
Hi everyone. I just installed Eclipse and I'm trying to configure it to be able to edit/compile Java code. I followed the official Ubuntu help for Eclipse  [http://help.ubuntu.com/community/EclipseIDE](http://help.ubuntu.com/community/EclipseIDE) Everything went well until I had to run this code in the terminal:

gksudo gedit /etc/eclipse/java_home

Apparently, this file doesn't exist which is why, I assume, I can't get Eclipse to create a Java project, compile Java code, etc. I'm fairly new to Linux so is it possible I just followed the above tutorial wrong?

---

### Post by Crafty Kisses on 2010-01-08
I would suggest you download Eclipse from the official Eclipse website. Have you installed OpenJDK? In some cases you have to point Eclipse to the JDK, which remember depending on where you have it stored the command would be different obviously, so for example you would do something like this:
```
echo "/usr/lib/jvm/sun-6-java" >> /etc/eclipse/java_home
```
I think the easiest way to install Eclipse and OpenJDK would be from the official websites, that's probably the easiest way. It also looks like you're using the **"Ubuntu 8.04 - Hardy Heron"** install instructions, so those might be obsolete if you're using a newer version of Ubuntu.

---

