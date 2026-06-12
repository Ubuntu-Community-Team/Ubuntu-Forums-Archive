---
title: "Help with format"
date: 2010-09-11
forum: General Help
---

### Post by SoAb on 2010-09-11
Hello....not before long time i was windows user...as many windows users i had endless problems and i sweared that if i ll have one more problem i will never log in in windows again,so...i got a virus and the windows dont boot up anymore.In my pc i had installed
windows xp and ubuntu 9.0.4 as dualboot.My question is can i format
the partition of windows?i have 2 hds 1 250gb and 1 80 gb i have installed windows in a 108 gb partition,ubuntu at a 40gb partition and i have made one last 82 gb partition for storage. The problem is that in 108 file system i see an ubuntu installation file and i dont know if a format will delete ubuntu too,plus ubuntu doesnt appear as 40gb filesystem ,only as filesystem.So pls help me to "break" those f^%7ing windows and free my hdd :P here are some screenshots (in greek sorry)
[http://img821.imageshack.us/img821/5679/mycomputer.png](http://img821.imageshack.us/img821/5679/mycomputer.png)
[http://img834.imageshack.us/img834/1649/108filesystem.png](http://img834.imageshack.us/img834/1649/108filesystem.png)

---

### Post by Lukas666 on 2010-09-11
I'm sorry but your problem is not clear.

To see all partitions run GParted (System->Administration->GParted)
and from there you can format partitions individually (WHICH WILL OF COURSE DELETE ALL DATA ON A GIVEN PARTITION).

If in doubt, ask here!

---

### Post by Lateralis on 2010-09-11
Hi Soab.  You are quite free and able to delete and remove the Windows partition without doing a thing to the Ubuntu partitions. 

What you will need is gparted.  I don't think it is installed by default with Ubuntu, so you will need to install it (if you haven't installed it already).  

```

sudo aptitude install gparted

```

Once it is installed, you can start up gparted going 

```

sudo gparted

```

If you're unclear as to which hard drive is which, type 

```

sudo blkid

```

into the command line.  The output will tell you what partitions you have, what format they're in and any labels they might have (such as Windows or w/e). It will help you identify the IDs (/dev/sdXY, X will be a lowercase letter and Y a number starting from 1) of the partitions you can wipe using gparted. 

I'd also at this point like to echo Lukas and say that editing the partition tables of a hard drive carries a certain amount of risk.  You will obviously be deleting all of the data on the disk you partition, but you should backup *all* essential and important data you have on that entire hard disk just in case something goes wrong, e.g. you accidentally delete the wrong partition.  

Oh, as a postscript, can you resize the pictures or attach them to your post?

---

### Post by SoAb on 2010-09-11
[http://img821.imageshack.us/img821/8591/screenshot2eq.png](http://img821.imageshack.us/img821/8591/screenshot2eq.png)


i m worried that if i format 108 ntfs file system,ubuntu will fail because there is that file in there (you can see it at the screenshot).So depenting on what you see can i format 108 gb ntfs system?pls tell me
if you ne me to post anything else

---

### Post by Lateralis on 2010-09-11
Hi Soab. 

How did you install Ubuntu?  Did you boot into the LiveCD and then install from there, or did you install using Wubi?

---

### Post by SoAb on 2010-09-11
From live cd

---

### Post by Lateralis on 2010-09-11
OK, so if you did not install using Wubi under Windows, and did not install Ubuntu into a directory in Windows, then you should be OK to remove the parition.  

Just to check though, can you type in open up a terminal and type in:

```

sudo fdisk -l

```

and post the output.

---

### Post by SoAb on 2010-09-11
```
jim@jim-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cc8935e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13134   105498823+   7  HPFS/NTFS
/dev/sda2           13135       30400   138689145    f  W95 Ext'd (LBA)
/dev/sda5           20398       30400    80349066    7  HPFS/NTFS
/dev/sda6           13135       20095    55914169+  83  Linux
/dev/sda7           20096       20397     2425783+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8877d88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

```

i dont think i need gparted 9.10 have a tool called palimpsest

---

### Post by SoAb on 2010-09-11
Ok i deleted the partition tried to create ntfs but it failed and i chose ext3, it created it and now there is one file called lost and found O.o with an "x" and a locker on it O.o

---

### Post by cgroza on 2010-09-11
Its normal, you can ignore that. Its on my hard drive too.

---

### Post by Lateralis on 2010-09-11
OK, I hope that everything went OK with the partition changes.  =)  


Also, just to point out, NTFS support in Linux isn't actually all that good, despite what it seems like.  Now you've deleted your Windows operating system you should really stick with native Linux file systems such as ext4.  Steer clear of NTFS as much as possible.   

As for Lost+Found... every Linux partition will have this directory.  In the event of an unclean shutdown - power loss, crash, or some unexpected event - fsck will scan the partition(s) at the next book looking for corrupt data.  It will attempt to recover these data, the results of which are placed in this directory.  Not all files recovered in this way will make much sense or can even be used, but there is a chance that something useful and worthwhile will have been recovered.

---

