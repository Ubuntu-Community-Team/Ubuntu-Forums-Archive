---
title: "How to get Grub1 instead of Grub2?"
date: 2009-10-31
forum: General Help
---

### Post by DeMus on 2009-10-31
I'm having problems with Grub 2and I don't want to use it any longer.
I have installed Karmic on 2 Raid arrays, one for / and one for /home.
I also have a separate partition for /boot, outside the Raids.
Since Grub2 also uses files in /etc they are in the Raid and therefore they can not be found.
So, I need to have Grub 1 again. When I uninstall Grub 2 and install Grub 1 I also get Grub-common which belongs to Grub 2.

How to completely switch over from Grub 2 to Grub 1?

---

### Post by grandtoubab on 2009-10-31
[]("https://wiki.ubuntu.com/Grub2")[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

look at section 12 [https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

:popcorn:

---

### Post by DeMus on 2009-10-31
> **grandtoubab said:**
> []("https://wiki.ubuntu.com/Grub2")[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

look at section 12 [https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

:popcorn:

Fantastic. At the moment I do not need it anymore since I have returned to Jaunty which has Grub1 by default.
Should I install Karmic again I will definitely use that site to get Grub1.
The problem I had is this:
I have set my disks like this:
```
sda1 /boot
sda2 + sdb2 RAID0 for /
sda3 + sdb3 Raid0 for /home

```
Since /boot can not be part of a RAID I put that onto a separate partition (sda1)
Now with Grub2 files are all over the place, like in /etc/default. These folders are all placed inside my Raid so Grub2 doesn't work the way it should:
[LIST=1]
[*]I got an error saying a disk is not there,
[*]I did not get a menu to choose from,
[*]plus it took ages to boot.
[/LIST]

Since I also had problems with kernel 2.6.31 I installed 2.6.30 which is good. Then the problems really started:
[LIST=1]
[*]How to tell Grub2 I want to boot into 2.6.30?
[*]I had no sound anymore. I had to install all kinds of stuff and activate it after stopping gdm - which did not work anymore since also there things have changed.
[/LIST]
No, I will use Jaunty for a while till the problems with Karmic are solved. Then maybe I will make the plunge again.

Thanks very much for your help.

---

### Post by grandtoubab on 2009-10-31
Doing 
**[Upgrading from Ubuntu 9.04]("http://www.ubuntu.com/getubuntu/upgrading")**


you will keep grub-legacy and ext3 files system

Refer to
[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

but maybe have a look on this [Grub won't install on software raid setup]("http://ubuntuforums.org/showthread.php?t=1305811")

---

