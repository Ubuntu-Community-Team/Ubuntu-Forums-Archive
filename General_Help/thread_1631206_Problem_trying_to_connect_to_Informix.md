---
title: "Problem trying to connect to Informix"
date: 2010-11-26
forum: General Help
---

### Post by maxonico on 2010-11-26
Dear all, I've been fighting for quite a long time with this and I can't figure out what I'm doing wrong.

I've installed Ubuntu Server 8.04 (with gnome desktop), and also installed using Synaptic; Informix Dynamic Server Demo and OpenAdmin Tools; but I can't access the DB server, I get this message in OAT:

> 
SQLSTATE=08004, SQLDriverConnect: -908 [Informix][Informix ODBC  Driver][Informix]Attempt to connect to database server (demo_on) failed.
Everything has been installed with default settings (OAT, IDS, CSDK, etc), I've only changed the password for the user Informix, but AFTER the installation, I had to reboot the machine.

Any help is appreciated, thanks!

---

### Post by dino99 on 2010-11-26
might be of some help:

[http://anjusaksena.blogspot.com/2009/08/installing-informix-115-on-ubuntu.html](http://anjusaksena.blogspot.com/2009/08/installing-informix-115-on-ubuntu.html)

by the way 8.04 is no more maintained, you might installed 10.04 instead

---

### Post by maxonico on 2010-11-26
Hi, thanks for your answer, in theory Synaptic have made all the steps required (the same described in the link, creating a group, user, setting permissions, etc). By default, using Synaptic, IDS should be working? or is there something else to do? or by rebooting the machine after the installation  something got lost?

Thanks!

---

### Post by dino99 on 2010-11-26
" theory" is like "dreaming", better to really check if the necessary packages are installed (respect the order) into synaptic.

then reboot and watch logs, maybe there are usefull errors logged to get around.

---

