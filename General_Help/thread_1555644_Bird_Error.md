---
title: "Bird Error"
date: 2010-08-18
forum: General Help
---

### Post by kakakhushi on 2010-08-18
This is the error I am getting on most installs


Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 bird

 bird6

---

### Post by Frogs Hair on 2010-08-18
Do you have Twitter ? The only thing I have found connected to this error is Twitter, but I can't find any resolutions yet.

---

### Post by conradin on 2010-08-18
What are you trying to do exactly? Bird and Bird6 are daemons for modems. Are you using networking with modems? Where you installing something which has a dependency for those programs?

---

### Post by kakakhushi on 2010-08-19
I am trying to install softwares like amsn or jut now I tried Emesene for IM this is the details:

installArchives() failed: Selecting previously deselected package emesene.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 244264 files and directories currently installed.)

Unpacking emesene (from .../emesene_1.5-1ubuntu1_all.deb) ...

Selecting previously deselected package python-pysqlite2.

Unpacking python-pysqlite2 (from .../python-pysqlite2_2.5.5-1ubuntu1_i386.deb) ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for man-db ...

Processing triggers for desktop-file-utils ...

Setting up bird (1.0.15-2) ...

/etc/init.d/bird: 134: Syntax error: ";" unexpected

invoke-rc.d: initscript bird, action "start" failed.

dpkg: error processing bird (--configure):

 subprocess installed post-installation script returned error exit status 2

Setting up bird6 (1.0.15-2) ...

bird: /etc/bird6.conf, line 20: syntax error

/etc/init.d/bird6: 134: Syntax error: ";" unexpected

invoke-rc.d: initscript bird6, action "start" failed.

dpkg: error processing bird6 (--configure):

 subprocess installed post-installation script returned error exit status 2

Setting up emesene (1.5-1ubuntu1) ...



Setting up python-pysqlite2 (2.5.5-1ubuntu1) ...



Errors were encountered while processing:

 bird

 bird6

---

### Post by kakakhushi on 2010-08-20
and the program is installed and working some how :rolleyes:

---

### Post by kakakhushi on 2010-08-23
waiting for a solution :popcorn:

---

