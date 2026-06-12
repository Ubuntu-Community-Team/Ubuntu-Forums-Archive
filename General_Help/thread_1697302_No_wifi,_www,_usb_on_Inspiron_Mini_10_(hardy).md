---
title: "No wifi, www, usb on Inspiron Mini 10 (hardy)"
date: 2011-02-28
forum: General Help
---

### Post by serioussurfer on 2011-02-28
Hi all

A few problems have occurred with my Dell netbook:

It can't see my wifi network (or any of the neighbours' normally visible).

When connected by ethernet the Dell can log into my router but not connect to the www.  Other machines on the network can.

USB memory sticks fail to mount when plugged in.

Can anyone help with some first steps, pointers?

Thanks

Inspiron Mini 10
1Gb memory
1.6GHz Atoms
Ubuntu 8.04
Kernel 2.6.24-27-lpia
Gnome 2.22.3
ADSL Sky Broadband router
Firmware 2.8Sky

---

### Post by thesavager on 2011-02-28
Did you made a fresh install from CD ?
the more info u give , the better we can help

---

### Post by serioussurfer on 2011-03-01
> **thesavager said:**
> Did you made a fresh install from CD ?


No, it's not a new install.  The user at the time isn't aware of doing anything but normal surfing and word processing.

What more info can I give?

If I put "91.189.94.12" into Firefox it returns "Firefox Can't find the server at www.canonical.com".

When I plug in a usb stick it says

 "Cannot mount volume.
 Unable to mount the volume.
 mount: can't open /etc/mtab for writing: No such file or directory"

Thanks.

---

### Post by thesavager on 2011-03-06
> **serioussurfer said:**
> 
If I put "91.189.94.12" into Firefox it returns "Firefox Can't find the server at www.canonical.com".
Strange ...its no dns problem ..cos the ip-adres gets resolved. 

do command:   ifconfig   and view if there are collisions.

In some cases you need to clone the MAC-adres of the router you are using.
in that case install macchanger.

sudo apt-get install macchanger

then (example):

ifconfig eth0 down
macchanger -m 00:3E:11:00:10:01 eth0 
ifconfig eth0 up
dhclient eth0

change 00:3E:11:00:10:01 to MAC adres router.
change "eth0" to whatever interface you are using

> 
When I plug in a usb stick it says.


 "Cannot mount volume.
 Unable to mount the volume.
 mount: can't open /etc/mtab for writing: No such file or directory"


There are some few steps you need to take care of , in the BIOS before your pc starts reading the USB stick.

1)turn on USB-legacy if not already done, save and exit and restart pc
2)back into BIOS again
3)set your USB stick as first boot device, save and exit , now restart pc with USB stick in place.

---

