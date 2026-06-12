---
title: "Wrong login screen an cant login"
date: 2010-11-16
forum: General Help
---

### Post by poordamnedfool on 2010-11-16
Last night I was changing some configuration settings with the network (DNS, SMB, etc.) and pulled some data off of a friends drive. I didnt think that I changed anything with the user configuration.  After I removed the HD I just started the computer up and went to bed.  This morning I tried logging in and it accepted the password and tried to load into gnome but stopped and kicked me back to the user select screen.  I rebooted and it brought up a different login screen.  Any ideas?

---

### Post by poordamnedfool on 2010-11-16
I think that I figured out the cause of the problem.  My root partition is 100% full.  /home and /boot are on their own partitions.  My root partition is ~= 30GB so I am wondering what is eating up this space.  My Trash folders and /tmp is empty.

---

### Post by dino99 on 2010-11-16
bleachbit & gtkorphan can make room on your system

---

