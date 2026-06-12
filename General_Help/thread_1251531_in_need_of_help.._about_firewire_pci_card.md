---
title: "in need of help.. about firewire pci card"
date: 2009-08-27
forum: General Help
---

### Post by publicladykilla on 2009-08-27
it is not recognizing my dv camera.. it is being connected by a firewire pci card i installed a while back. and now its just not recognizing.... doesnt even say uknown  device.
anyone got any ideas??

---

### Post by P4man on 2009-08-28
Have a look here, maybe that helps:
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

### Post by Icebear on 2009-08-28
try this might help

[http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how](http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how)

---

### Post by publicladykilla on 2009-08-28
ok i have kdenlive whihc has the dv grab in it.. but i connect my camcorder and hit connect and it still says not connected... what do i do?

---

### Post by Icebear on 2009-08-28
in the terminal copy and past the following 

sudo gedit /lib/udev/rules.d/50-udev-default.rules

then scroll through the text and dind the firewire section

and add the following line
KERNEL=="raw1394", GROUP="video

---

### Post by publicladykilla on 2009-08-29
i already added that line.. it still wont recognize

---

