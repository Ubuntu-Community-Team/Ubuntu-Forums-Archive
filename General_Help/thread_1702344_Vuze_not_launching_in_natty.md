---
title: "Vuze not launching in natty"
date: 2011-03-07
forum: General Help
---

### Post by gaurav.chandiramani on 2011-03-07
Hi, i was using ubuntu 10.10 and vuze as the default bit-torrent client. I upgraded to natty alpha 3 a couple of days ago and after that vuze doesn't even launch...i don't see any errors, when you click on the icon absolutely nothing happens...
I tried removing vuze and then installing it again, but it didn't help.

---

### Post by shantiq on 2011-03-22
```

```hi there i found the repository was useless for vuze so went this route



1.  **Beforehand** as i seem to remember it needs that


```
 sudo add-apt-repository ppa:sun-java-community-team/sun-java6

```

```
sudo apt-get update

```

```
 sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk

```

===========================================

**THEN**


[** ==> download**]("http://cf1.vuze.com/files/Vuze_Installer.tar.bz2") to home folder

then create a launcher on desktop  (right-click create launcher) 

Go to where you have stored your download and use the commandline instruction  ```
./azureus
```   see attached

---

