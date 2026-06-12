---
title: "Recomended way of installing Oracle Java/JDK ?"
date: 2012-05-21
forum: General Help
---

### Post by bokopperud on 2012-05-21
After it was removed(?) from the main repository, what is the recommended way (or best hack) to install Oracle Java JDK and related packages (like plug-in for Mozilla)?  A way that actually work and preferably will make it possible to update later...

Alternatively, how is the best way to globally (not just for one user) install Oracle Java/JDK after downloading it from Oracle, preferably in a way that lets it co-exist with other Java-versions (e.g. via the alternatives-facility)?  Where should it be installed?  How?  Which configurations must be done?

---

### Post by raja.genupula on 2012-05-21
[http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/)

---

### Post by Cheesemill on 2012-05-21
I've found after much trial and error that the webupd8 PPA is the way to go:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by scouser73 on 2012-05-21
Following the instructions on the [[COLOR="Red"]**Easy Linux Tips Project - Install Java**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java") works perfectly.

---

