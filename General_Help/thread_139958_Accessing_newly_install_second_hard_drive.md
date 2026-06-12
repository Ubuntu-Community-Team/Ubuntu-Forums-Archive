---
title: "Accessing newly install second hard drive"
date: 2006-03-05
forum: General Help
---

### Post by madtinkerer on 2006-03-05
Hi Everyone,

I've just installed a second hard drive in my system.  I've got the drive formatted and mounted, but how can I make it accessible by the average user?  I have it (/dev/hdb1) mounted in /media/titus.  I'm assuming I have to change something in /etc/fstab, but I don't know what setting to modify.  Thanks for the help.

---

### Post by akiro.yamamoto on 2006-03-05
Depending on the type of file system used, the fstab entry will be a little different.
But a few suggestions from my own /ets/fstab file might help :)

Reiserfs?
/dev/hda4       /media/data               reiserfs notail          0       1

Ext3?
/dev/hdb1       /media/old-home ext3    defaults        0       2

---

