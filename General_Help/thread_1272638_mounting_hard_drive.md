---
title: "mounting hard drive"
date: 2009-09-22
forum: General Help
---

### Post by kjv161147201 on 2009-09-22
Good day! In xubuntu how to I get the hard drive to show up under 'Places' so I can mount it and have the icon on my desktop?

---

### Post by rbc on 2009-09-22
What shows up under Places are partitions on hard drives that can be mounted, so.....is there a formatted partition? Go to terminal and type:
sudo fdisk -l
Then post back with the results. Does the desired partition show up on those results?

---

### Post by kjv161147201 on 2009-09-24
Thanks for the reply...Here are the results of sudo fdisk

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa730e7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4777    38371221   83  Linux
/dev/sda2            4778        4865      706860    5  Extended
/dev/sda5            4778        4865      706828+  82  Linux swap / Solaris

---

### Post by tcturner on 2009-09-24
I had a similar problem with ubuntu 8.04. I have a primary hdd of 80 Gb and a secondary drive of 40 Gb. Here is my sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006d4a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9480    76148068+  83  Linux
/dev/sda2            9481        9729     2000092+   5  Extended
/dev/sda5            9481        9729     2000061   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d936

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

The 80 Gb is listed as sda and the 40 Gb is listed as sdb. It looks like your other drive is not partitioned and formatted. I found this tutorial on psychocats This is the url for psychocats [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)   I used this because I never could figure out how to change permissions so I could write to the disk. This tutorial shows you how. To list the new disk in Places menu open nautilus fioe browser to file system and drag and drop the new folder you created (whatever you named it) into the bottom left hand pane of nautilus where Documents Music Pictures and Video are. Make sure when using the tutorial that in certain places you use your username instead of marie as thry do. (username you use to log into your system on boot). Also you don't have to name the disk storage as they do name it whatever you want just don't name it the same as any other folder in your file system. Hope this helps.

---

### Post by tcturner on 2009-09-24
Sorry one more thing the tutorial is only if your drive is formatted to ext3. the tutorial shows you how to install gparted which you can use to partition and format the drive. Also your file browser isn't nautilus it is thunar so adding the folder to places may be different.

---

### Post by kjv161147201 on 2009-09-24
Thanks for the great info! Will study it...

---

