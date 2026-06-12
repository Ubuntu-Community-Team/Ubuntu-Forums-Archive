---
title: "install Qt  on ubuntu 10.04"
date: 2010-08-24
forum: General Help
---

### Post by dato1989 on 2010-08-24
hello everybody   i am using ubuntu 10.04 can anybody tell me how install Qt on ubuntu? i am c++ user and i need it   to learn please help

---

### Post by gavinjb on 2010-08-24
Hi,

From this post it looks like you need to install libqt3-mt

[http://ubuntuforums.org/showthread.php?t=312690]("http://ubuntuforums.org/showthread.php?t=312690")

or possibly libqt4-core for non gui runtime libraries, best thing is to do a apt-cache search libqt4 and you will get a list of packages and you will need to have a look to see which looks right for your needs.

---

### Post by lykwydchykyn on 2010-08-24
Just install qt-sdk.  That should get you everything you need.

libqt3-mt is old old old stuff.

---

### Post by Vaphell on 2010-08-24
and qt4 provides legacy classes of qt3 just in case someone really needed them

---

