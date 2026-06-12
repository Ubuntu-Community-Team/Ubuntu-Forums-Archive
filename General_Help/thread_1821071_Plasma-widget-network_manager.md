---
title: "Plasma-widget-network manager"
date: 2011-08-08
forum: General Help
---

### Post by geoaraujo on 2011-08-08
Hello. Earlier today, I've updated some kde components that were prompted  by Kpackagekit. Now, the applet for Network is displaying wrongly, it  shows the icon for a wired connection (I'm connect through wi-fi) and I  can't enable wi-fi when I click on it. When I pass the mouse over it, it  says "wi-fi disable by hardware". Help, please?:(

---

### Post by Ric_NYC on 2011-08-08
Yes. 

This:

[[IMG]http://img97.imageshack.us/img97/8062/wifi1.png[/IMG]](http://imageshack.us/photo/my-images/97/wifi1.png/)

---

### Post by picharras on 2011-08-08
I also same thing happens, after upgrading not connect me back to let, only connecting cable. The WICD me not working, Help!

The problem apparently is in the package: plasma-widget-networkmanagement-dbg_0.9 ~ ~ natty1 svngit20110728-0ubuntu3 ~ ppa5_i386.deb or equivalent

---

### Post by picharras on 2011-08-08
New updates are available to correct the error. just do the following:

sudo aptitude update
sudo aptitude dist-upgrade or sudo aptitude upgrade

---

### Post by geoaraujo on 2011-08-08
> **picharras said:**
> New updates are available to correct the error. just do the following:

sudo aptitude update
sudo aptitude dist-upgrade or sudo aptitude upgrade
Solved with latest update! :)

Edit: With normal *sudo apt-get update && sudo apt-get upgrade*

---

