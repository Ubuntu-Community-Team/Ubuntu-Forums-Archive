---
title: "Wacom Bamboo Connect tab setup for GIMP"
date: 2012-03-27
forum: General Help
---

### Post by gychang on 2012-03-27
Just bought the hardware for my photo touchup work.  Am on the latest xubuntu machine and trying to get it setup.  Can someone give me how to?  I am told the model works well in linux and gimp although company does not officially support it.

gychang

---

### Post by Favux on 2012-03-27
Hi gychang,

So Xubuntu Oneiric?

See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  You need to compile input-wacom for a new wacom.ko with the Connect in it.

---

### Post by fragos on 2012-03-27
Bamboo Connect is a newer version than the Bamboo Pen/Touch. I'm using it with Ubuntu Unity. The following PPA is my source of a workable Wacom driver.
[http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu](http://ppa.launchpad.net/lekensteyn/wacom-tablet/ubuntu)

Gimp itself also has some issues with Wacom. The following PPA gives you a correctly functioning Gimp 2.6 for the Wacom. If you look around you'll find PPAs for 2.7 but avoid them. 2.7 is a development release that will cause no end of dependency issues with your system.
[http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu)

---

