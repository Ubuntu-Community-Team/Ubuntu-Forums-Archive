---
title: "Java and font Arial"
date: 2011-05-25
forum: General Help
---

### Post by zajc on 2011-05-25
I would like to use Arial font in Java application in (X)ubuntu. In Windows it is working OK.

I installed Java and Arial font
```
sudo apt-get install sun-java6-jdk
sudo apt-get install msttcorefonts
```
I removed configuration files for Ubuntu
```
sudo rm /usr/lib/jvm/java-6-sun/jre/lib/fontconfig.Ubuntu.*
```
I edited
```
/etc/java-6-sun/fontconfig.properties
```
I have replaced all lucida fonts for arial and I included the path to arial.ttf. This instructions I have found on [this web site]("http://www.inductiveautomation.com/forum/viewtopic.php?f=64&t=4295").

But this doesn't work. Does anybody have any idea how to use Arial font in Java application in Linux OS?

---

