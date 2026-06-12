---
title: "unable to boot Ubuntu 9.10."
date: 2010-01-02
forum: General Help
---

### Post by roghov on 2010-01-02
guys i got into deep trouble today. in my ubuntu installation i had allocated about 15 GB for the /home folder. today i was trying to increase the memory in my system and so using the disk utility program of the 9.10 release, i formatted the /home part of the drive and gave it another name and started using it as just another ext3 partition to store my files. when i restarted the system, ubuntu wouldn't start and it takes me to the maintenance shell. 

i have no idea how to solve this problem from the maintenance shell. i also have win XP in my system along with 9.10. i can't afford to lose either of them. i've got many expensive applications installed in both OS. so i can't reinstall Ubuntu in my system. is there any way to override mounting the /home part and start ubuntu. 

its urgent. please help me.

---

### Post by zey on 2010-01-02
Try to override with the ubuntu installation CD.
Maybe it can help you..

[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by Leppie on 2010-01-02
> **roghov said:**
> guys i got into deep trouble today. in my ubuntu installation i had allocated about 15 GB for the /home folder. today i was trying to increase the memory in my system and so using the disk utility program of the 9.10 release, i formatted the /home part of the drive and gave it another name and started using it as just another ext3 partition to store my files. when i restarted the system, ubuntu wouldn't start and it takes me to the maintenance shell. 

i have no idea how to solve this problem from the maintenance shell. i also have win XP in my system along with 9.10. i can't afford to lose either of them. i've got many expensive applications installed in both OS. so i can't reinstall Ubuntu in my system. is there any way to override mounting the /home part and start ubuntu. 

its urgent. please help me.

did you format the /home partition without creating and assigning a new one and copying the data from the old one to the new one?
/home is where all the userpaces are saved (desktop settings, application settings, etc.)

---

### Post by Sef on 2010-01-02
From the Live CD:

Applications > Accessories > Terminal

the copy and paste this command:

```
sudo fdisk -l
```

Then copy and paste the results here.

---

### Post by roghov on 2010-01-03
thanx for the quick reply guys.

@ sef

i typed sudo fdisk -l and got this :


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe448e448

Device  Boot    Start    End     Blocks         Id     System
/dev/sda1 *       1       2550    20482843+  c      W95  FAT32 (LBA)
/dev/sda2       2551    6974    35535780     f      W95 Ext'd (LBA)
/dev/sda3       6975    7119    1164712+    82    Linux swap / Solaris
/dev/sda4       7120    9729    20964825     83    Linux
/dev/sda5       2551    5151    20892501     7      HPFS/NTFS
/dev/sda6       5152    6974    14643216     83    Linux


sda6 is the partition that was mounted as /home. this is the partition i formatted. sda4 is the partition in which linux system files are installed. it is my / partition. sda1 and sda5 have windows files. in sda6 i have 4 GB worth of files they are all mp3, avi, pdf,.c,.cc or .java files. can i copy all its contents to some other partition and remount it as /home?

---

### Post by Leppie on 2010-01-03
> **roghov said:**
> can i copy all its contents to some other partition and remount it as /home?
did you copy all of the /home folders to sda6? in that case you can mount sda6 as your /home partition.
otherwise you may have to recreate the /home folder structure.

---

### Post by roghov on 2010-01-03
no i did not copy any of the /home files to sda6. all the /home files are gone now.
so i was wondering if i can somehow transfer all the contents of sda6 to a windows partition using the maintenance shell and then reassigning the sda6 partition for /home as it was before. can i do all this without having to re-install the entire OS again?

---

### Post by Leppie on 2010-01-03
i suppose you can.
but i think you will have to recreate the user accounts. i'm no expert at this though, so there might be a way to restore your accounts without removing and re-adding all of them.

you can try changing the reference to the /home partition in your /etc/fstab to point it to sda6

---

### Post by Sef on 2010-01-03
> Device  Boot    Start    End     Blocks         Id     System
/dev/sda1 *       1       2550    20482843+  c      W95  FAT32 (LBA)
/dev/sda2       2551    6974    35535780     f      W95 Ext'd (LBA)
/dev/sda3       6975    7119    1164712+    82    Linux swap / Solaris
/dev/sda4       7120    9729    20964825     83    Linux
/dev/sda5       2551    5151    20892501     7      HPFS/NTFS
/dev/sda6       5152    6974    14643216     83    Linux

What's on sda1 and sda 5?

> guys i got into deep trouble today. in my ubuntu installation i had allocated about 15 GB for the /home folder. today i was trying to increase the memory in my system and so using the disk utility program of the 9.10 release, i formatted the /home part of the drive and gave it another name and started using it as just another ext3 partition to store my files
 
So you enlarged sda 6 by reformatting it?   If so, then you may be able to get stuff back by using [photorec]("http://www.cgsecurity.org/wiki/PhotoRec").  Also see [Data Recovery]("https://help.ubuntu.com/community/DataRecovery") in the Community Docs.

---

