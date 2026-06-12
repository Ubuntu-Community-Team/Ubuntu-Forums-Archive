---
title: "Installed Ubuntu onto a windows partition"
date: 2011-12-27
forum: General Help
---

### Post by greyluver on 2011-12-27
Hello
I have a laptop with windows 7 already on it and I have had it for a year. Recently, I wanted to dualboot Ubuntu with it, so I put 11.04 on with a CD.  When I put the CD in, three options came up, and I chose share with windows thinking it would make another partition.  It installed just fine, so I rebooted and Ubuntu came up along with windows 7. Both operating systems boot and function correctly but they are kinda slow, which makes me think I put Ubuntu on the same partition.

Now, I want to take Ubuntu off and put it on a separate partition, leaving windows as it is (without having to restore it to factory settings)

Any help would be appreciated.

---

### Post by collisionystm on 2011-12-27
> **greyluver said:**
> Hello
I have a laptop with windows 7 already on it and I have had it for a year. Recently, I wanted to dualboot Ubuntu with it, so I put 11.04 on with a CD.  When I put the CD in, three options came up, and I chose share with windows thinking it would make another partition.  It installed just fine, so I rebooted and Ubuntu came up along with windows 7. Both operating systems boot and function correctly but they are kinda slow, which makes me think I put Ubuntu on the same partition.

Now, I want to take Ubuntu off and put it on a separate partition, leaving windows as it is (without having to restore it to factory settings)

Any help would be appreciated.


Did you do the WUBI install? You were in windows, put in the cd, and chose install ubuntu

or did you reboot with the cd, let it load, choose install ubuntu and then choose, install next to windows 7

---

### Post by greyluver on 2011-12-27
I did the WUBI install

---

### Post by collisionystm on 2011-12-27
> **greyluver said:**
> I did the WUBI install

okay so this is pretty much what happened 

you did NOT do seperate partitions. Ubuntu is living on your windows drive and accessing a file manipulated as a virtual hard drive.
This should make Ubuntu slow, not windows.
If your windows is going slow you should check task manager is see if anything is pinning the CPU at a high rate, and check to make sure your C: drive is not getting full.

---

### Post by greyluver on 2011-12-27
How do I remove Ubuntu?

---

### Post by collisionystm on 2011-12-27
> **greyluver said:**
> How do I remove Ubuntu?

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by greyluver on 2011-12-27
Thanks! Now I feel pretty dumb...

---

### Post by collisionystm on 2011-12-27
> **greyluver said:**
> Thanks! Now I feel pretty dumb...

ehh... dont worry about it. been there. done that lol.

---

