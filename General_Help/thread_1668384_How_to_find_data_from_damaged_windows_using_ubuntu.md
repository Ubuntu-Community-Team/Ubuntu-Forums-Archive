---
title: "How to find data from damaged windows using ubuntu cd live"
date: 2011-01-16
forum: General Help
---

### Post by krowka_smieszka on 2011-01-16
Hi,

I am new to ubuntu. Yesterday, my windows xp died and I can not do anything with that, but I would like to rescue my important files from hdd before format.  I open ubuntu trial version from cd but i can not access my hdd. I find my hdd in system->administration->disk utility but I can not go anywhere from there.  And need someone to help me get my old files. Please

When I solve this problem I would like to try ubuntu as my os but i am worried that some programs may  not work on it . Like for example my bamboo tablet, fm2010, adobe ilustrator, autocad.

---

### Post by TeoBigusGeekus on 2011-01-16
Have you tried in the Places menu?

---

### Post by krowka_smieszka on 2011-01-16
Yes and I do not see my hdd there, just examples and installubuntu

---

### Post by ronnielsen1 on 2011-01-16
Does disk utility see your hard drive? It might have died.

System > Administration > Disk Utility

---

### Post by TeoBigusGeekus on 2011-01-16
Open a terminal and give us the output of
```
sudo fdisk -l
```

---

### Post by krowka_smieszka on 2011-01-16
I can see my hdd there

---

### Post by krowka_smieszka on 2011-01-16
I am using my other laptop right now so do you want me to write everything down or you are just interested in specific line?

---

### Post by TeoBigusGeekus on 2011-01-16
I'm interested about whether the command lists any of your partitions.
The output of my system is this
```
$ sudo fdisk -l
Password: 

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1d42923

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   586099394   293049666   83  Linux

Disk /dev/sdc: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa634a634

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625137344   312568641   83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     1992059      995998+  83  Linux
/dev/sda2   *     1992060    59986709    28997325   83  Linux
/dev/sda3        59986710   156296384    48154837+  83  Linux
```
It should be something similar in your system.

---

### Post by krowka_smieszka on 2011-01-16
in first line say something like that 

fdisk: invalid option -- '1'

then  usage: and options:

---

### Post by JKyleOKC on 2011-01-16
That option should be a lower-case L, not the numeral one. It's a very easy mistake to make!

---

### Post by TeoBigusGeekus on 2011-01-16
> **JKyleOKC said:**
> That option should be a lower-case L, not the numeral one. It's a very easy mistake to make!
^This.

---

### Post by krowka_smieszka on 2011-01-16
nothing happen :/

---

### Post by TeoBigusGeekus on 2011-01-16
By your answer I presume that you've got a null output.
Seems like your problem is a hardware one.
Turn off your pc and take it out of power. Open your pc case and detach and reattach all the cables of your hard disk. Reassemble and try again.

---

### Post by joes7 on 2011-01-16
[LEFT][SIZE=2]This happened to me back in 2008 and was the reason I installed ubuntu for the first time. I did, however, find it extremely easy to recover data from my damaged Windows. Simply go to[/SIZE] Places on the top menu. There should be  a couple of disk options. Browse them and you will find what you need. Hope this helps!
Good luck!
[/LEFT]

---

