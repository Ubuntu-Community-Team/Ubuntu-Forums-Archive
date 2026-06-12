---
title: "bluej refusing to install"
date: 2009-08-25
forum: General Help
---

### Post by pythonscript on 2009-08-25
I looked around in the bluej support forum and couldn't find anything, so I figured I'd post this here. I just downloaded the newest version of bluej because a class I'm a TA for only uses it (intro to java programming). So... I downloaded the jar file, ran 

```
java -jar bluej-252.jar
``` but instead of starting the install wizard, the installation dialog pops up blank and the entire process freezes. Any ideas? I've tried installing bluej as me and as sudo, but neither one seems to work. Also, I've installed the sun-java6-jdk and the sun-java6-jre (former depends on the latter, so the jre came along anyways) and all my other java apps, including those that I've coded myself, work fine. Thanks for the help!

---

### Post by pythonscript on 2009-09-03
bump. Anyone have any ideas? I just installed a completely fresh copy of ubuntu, ran 

```
sudo apt-get install sun-java6-jdk sun-java6-bin sun-java6-jre
``` then

```
sudo java -jar bluej.jar
```. I've tried to install bluej both as sudo and non-root users, and nothing works! It opens the frame of the installation window, then crashes. Any ideas here? I really need to get this working for class...

---

### Post by P4man on 2009-09-03
thats weird.. I just dl-ed  it from here:

[http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html)

and it works just fine for me? No need for sudo either.

FWIW:

```
bob@bob-desktop:~/Desktop$java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)
```

---

### Post by pythonscript on 2009-09-03
That is weird... This is the second installation of ubuntu that I can't get this to work on. One's a default installation, and the other's a command line only with icewm installed on top (which is my primary installation). 

Any one else have any ideas?

```
pythonscript@gradteach-t24:~/Desktop$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

```

EDIT: Ok... I just ran it again, and it worked under my default gnome installation. However, it didn't install this morning on my icewm installation, so I'll get the java -version output from that once I boot into it (it's a dual boot installation on my laptop). Thanks!

---

### Post by pythonscript on 2009-09-03
I ran java -version on my icewm machine, and after I set the right jre:

```
sudo update-alternatives --config java
```

I get the same output. bluej still freezes when I go to install. I'll try again once I'm finished teaching.

---

### Post by pythonscript on 2009-09-04
bluej seems to be working on both boots now. I appreciate the help. Not sure what caused it, but it seems to have rectified itself, so for now, I'm content. Thanks!

---

