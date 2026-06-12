---
title: "Limit Size"
date: 2011-07-27
forum: General Help
---

### Post by Aceofspades138 on 2011-07-27
Hi im a noob and ubuntu its taking up like 30 somthing gibs and i wanna lower that.

I also has vista installed so i want more space on my actual hard drive and less on the linux virtual disk.

---

### Post by Frogs Hair on 2011-07-27
Is this a Wubi installation or Virtual box ? If it is Wubi you would have had an option during installation the max being 30Gb and you would have had to select that . I think the default option is 17Gb or less . (been a while) I have not used Virtual Box .

---

### Post by Aceofspades138 on 2011-07-27
Sorry for long reply but i installed off of a cd and so neither i think lol.

---

### Post by Mark Phelps on 2011-07-27
A CD can be used to install either using Wubi or as a separate partition.  If you were running Windows and launched it from there, it was probably a Wubi installation.

One way to tell is to open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.  If all you see are NTFS or FAT partitions, it was a Wubi install.

---

### Post by Aceofspades138 on 2011-07-27
Heres output

```

xxxxx:~$ sudo fdisk -lu
[sudo] password for xxxxx: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   380524248   190262093    7  HPFS/NTFS
/dev/sda2       464792580   488392064    11799742+   7  HPFS/NTFS
/dev/sda3       380524542   464791551    42133505    5  Extended
/dev/sda5       380524544   458504191    38989824   83  Linux
/dev/sda6       458506240   464791551     3142656   82  Linux swap / Solaris

Partition table entries are not in disk order
xxxxxxx~$ 

```

---

### Post by Kira_Belka on 2011-07-27
so dual boot installation) easiest way to solve your problem it's to resize patitions from Ubuntu Live-CD.. gparted utility does it very well.. but mmmm.. you do it on your own risk! you can lose you data.

---

### Post by wildmanne39 on 2011-07-28
Hi, here is a guide to help with resizing partitions read it carefully and please be very careful when you start to resize your partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

