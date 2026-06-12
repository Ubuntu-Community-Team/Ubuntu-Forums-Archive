---
title: "JDK 6 from apt-get"
date: 2010-09-01
forum: General Help
---

### Post by HAcland on 2010-09-01
Hi - how do I install Java JDK 6 from apt-get?

thanks

---

### Post by dino99 on 2010-09-01
sudo apt-get install openjdk-6-jdk

or for Sun:

[http://beeznest.wordpress.com/2010/04/23/howto-install-suns-java-on-ubuntu-lucid-lynx-10-04/](http://beeznest.wordpress.com/2010/04/23/howto-install-suns-java-on-ubuntu-lucid-lynx-10-04/)

---

### Post by surfer on 2010-09-01
try [this]("http://ubuntuforums.org/showthread.php?t=1517979").

---

### Post by PaulReaver on 2010-09-01
to install the proper sun java dev kit you'll need to enable the canonical partner repo 

go to System/Administration/Software Sources then the "Other Software" Tab and make sure that  "http://archive.canonical.com/ubuntu lucid partner" is ticked.  it'll update the package lists

then install it via the ubuntu software center.  :D

---

