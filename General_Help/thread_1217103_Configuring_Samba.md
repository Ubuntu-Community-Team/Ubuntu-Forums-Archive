---
title: "Configuring Samba"
date: 2009-07-19
forum: General Help
---

### Post by DeMus on 2009-07-19
Hi,

I just read the threads about Samba and started to install and configure it also. Well, parts are working, parts are not.

I can connect from within Ubuntu to my XP laptop, open folders, edit textfiles, start an MP3, whatever. This way (Ubuntu to Windows) works fine.

From within Windows I can see the printer which is connected to my Ubuntu machine. I can not install it since the HP driver needs some registry entries which I don't have (but that's another story). I can see the printer so the connection Windows to Ubuntu is made.

I can however not see any shared folders in my Ubuntu machine. Reason: I can not share anything. When I right-click on a folder within my own home folder I do not get the possibility to share it. It is not there.

What do I need to install or configure to be able to share a folder?

---

### Post by Charlietje on 2009-07-19
Hi,


What did you install?

The config file to share a directory is in:
/etc/samba/smb.conf



Regards,
Carl

---

### Post by swerdna on 2009-07-20
Looks like some of the Samba files are installed and some not. Looks sus for the package nautilus-share not being installed. The full list for Ubuntu 9.04 is smbclient, libsmbclient, samba-common, nautilus-share and samba. All except package samba are installed by default, but something missed out for you, so check them all. There's more on that here, including tweaking samba to make it talk nicely with windows:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

