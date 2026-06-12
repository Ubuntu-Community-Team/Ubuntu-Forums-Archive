---
title: "[WARNING] Some problems with the latest updates ? (with auto-login for example)"
date: 2006-06-16
forum: General Help
---

### Post by frodon on 2006-06-16
Many of you got some problems with the latest updates especially with automatic login :

[http://ubuntuforums.org/showthread.php?t=197484](http://ubuntuforums.org/showthread.php?t=197484)
[http://ubuntuforums.org/showthread.php?t=197421](http://ubuntuforums.org/showthread.php?t=197421)
[http://ubuntuforums.org/showthread.php?t=197738](http://ubuntuforums.org/showthread.php?t=197738)

This has been reported and will be surely fixed soon through the repository updates :
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49964](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49964)
[https://launchpad.net/distros/ubuntu/+source/shadow/+bug/49976](https://launchpad.net/distros/ubuntu/+source/shadow/+bug/49976)
[https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49973](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49973)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031)

For nvidia cards you will find useful informations there:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

Feel free to report there other bugs or post some workarounds.
[SIZE="3"][COLOR="Red"]
**The auto-login bug is now under control :**[/COLOR][/SIZE]
[https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940)

Frodon

---

### Post by Jucato on 2006-06-16
May I add something for those using restricted kernel modules?

To those using linux-restricted-modules, please make sure that the *restricted* component of *dapper-security* is added and/or enabled, since the restricted modules are downloaded from that section.

Seems like no bug has been filed yet about non-working mice after upgrading. Could it be that it's an isolated problem? I'll try to file a bug report, but I don't know how or if it's worth filing...

EDIT:
Filed a bug report about the mouse not working. Sorry for the "unprofessional" report, it's my first time...

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49996](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49996)

---

### Post by siriusnova on 2006-06-17
There are also problems with thinkpads not being able to suspend or hibernate correctly. It's a known bug that affects a multitude of thinkpads, so please revert back to the kernel version "23" till it gets fixed if you are a thinkpad user and are having such problems..

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031)

---

### Post by homersbrain on 2006-06-17
The latest updates have caused several breakages:

See this thread:

[http://www.ubuntuforums.org/showthread.php?t=198021&highlight=gnome+update](http://www.ubuntuforums.org/showthread.php?t=198021&highlight=gnome+update)

and

[http://ubuntuforums.org/showthread.php?t=198585&highlight=broke](http://ubuntuforums.org/showthread.php?t=198585&highlight=broke)

Anyone know how to resolve these issues?

---

### Post by homersbrain on 2006-06-19
Bug reports now merged to here:

[https://launchpad.net/bugs/50150](https://launchpad.net/bugs/50150)

Please describe similar problems there.

---

### Post by Fnx on 2006-06-26
Hello,
I am reporting a bug encounter for both new installation from the Dapper 6.06 liveCD and (dist-) upgrading from a fully functionnal Breezy install.
 After upgrade, the computer is unable to start again. It boots but the system crash during mount of the local partitions.
My system (Athlon XP [686] on a Asus Abit NF-7S motherboard) has three hard drives connected through an inboard IDE controller and a PCI Silicon Graphic 680 IDE controller.
 Before installation and for other linux distro the disc enumeration is as follow
[INDENT] Grub    Dapper    Disk
 hd0    /dev/hda          WD (onboard IDE0)
 hd1    /dev/hde          Maxtor (PCI Sil680 IDE0)
 hd2    /dev/hdg          IBM (PCI Sil680 IDE1)
.....      /dev/hdc           DVD Drive (onboard IDE1)
 [/INDENT] 

For Dapper 6.06, my system is recognized as follow
[INDENT] Grub    Dapper     Disk
hd0    /dev/hde        WD (onboard IDE0)
hd1    /dev/hda        Maxtor (PCI Sil680 IDE0)
hd2    /dev/hdc        IBM (PCI Sil680 IDE1)
... ..     /dev/hdg DVD Drive (onboard IDE1)
[/INDENT]
Problem seems to be related with kernel 2.6.15, and udev.
It is not fixed to date (end of june 2006).

---

