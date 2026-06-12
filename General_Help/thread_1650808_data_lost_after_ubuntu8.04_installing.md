---
title: "data lost after ubuntu8.04 installing"
date: 2010-12-22
forum: General Help
---

### Post by problemes on 2010-12-22
Hey every one, i installed win XP month ago, after that i have installed ubuntu 8.04. i didn't choose manual configuration while selecting partitions. NOW all the data LOST !!! :(:(

and after typing sudo fdisk -lu

the result is as following 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11aa10aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   310327604   155163771   83  Linux
/dev/sda2       310327605   312576704     1124550    5  Extended
/dev/sda5       310327668   312576704     1124518+  82  Linux swap / Solaris
 

i tried teseDisk and gparted and nothing happened

plz i need help if there is any thing i can do to get back my DATA

---

### Post by Hippytaff on 2010-12-22
Did you remove windows (ie installed ubuntu over windows)?
 
Can you post the output of the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") and post the results in code tags # so we can see exatly whats what :-)

---

