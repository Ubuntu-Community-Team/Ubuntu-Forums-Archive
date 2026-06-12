---
title: "Cannot boot into Wondows Vista and Ubuntu"
date: 2011-01-08
forum: General Help
---

### Post by fEast91 on 2011-01-08
Hi, I don't know where to post this, so here goes.

I have been planning to dual-boot Ubuntu and Vista for quite a long time, so tonight I took the leap after a lot of research. Using a LiveCD of Ubuntu 10.04 LTS, I've successfully installed it.
But after reboot, and choosing Windows Vista loader, I got a blank, black screen, only with the words 
"error: no such partition
grub rescue>  "

Now I'm using the "Try Ubuntu" option on the LiveCD, as I cannot boot into either Ubuntu or Vista. First thing I checked was that the files in my Vista side are still there.
What to do now?

---

### Post by dcstar on 2011-01-09
> **fEast91 said:**
> Hi, I don't know where to post this, so here goes.

I have been planning to dual-boot Ubuntu and Vista for quite a long time, so tonight I took the leap after a lot of research. Using a LiveCD of Ubuntu 10.04 LTS, I've successfully installed it.
But after reboot, and choosing Windows Vista loader, I got a blank, black screen, only with the words 
"error: no such partition
grub rescue>  "

Now I'm using the "Try Ubuntu" option on the LiveCD, as I cannot boot into either Ubuntu or Vista. First thing I checked was that the files in my Vista side are still there.
What to do now?

Reinstall and overwrite the first Ubuntu partition created during the first install - use the manual partitioning option.

Pay attention and make sure that no error messages appear during the whole Ubuntu installation process.

---

### Post by fEast91 on 2011-01-09
> **dcstar said:**
> Reinstall and overwrite the first Ubuntu partition created during the first install - use the manual partitioning option.

Pay attention and make sure that no error messages appear during the whole Ubuntu installation process.

There are 3 sda things in there, and some free space.
sda1 and sda2 are Windows Vista, and sda5 I think had developer written, but I don't see any ubuntu partition. Does this indicate a failed install the first time I tried?
I tried the slider during step 3, (the second coloured bar, there seems to be a slider just right beside sda2 coloured bar) but as I don't know what I'm doing I didn't proceed. It seems to resize the sda2 portion, although it can size up to a volume more than my hard disk though.

Also, if this helps the situation, I'm doing the dual-boot on my laptop. It has 2 partition in it, 1 is the main VistaOS partition, the other is non-OS one (no OS install, just free space, used for backup and storage). If I remember correctly, the hard disk is 320 GB, and the non-OS partition is 147 GB. During the "Choose partition" option in the Ubuntu install, sda5 is also the same size. Is that (sda5) the other partition?

---

### Post by fEast91 on 2011-01-09
Something that I found interesting.
I've been doing some digging around, so to check the drives' names I've done that sudo fdisk -l command and found this:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       15559   112685523+   7  HPFS/NTFS
/dev/sda3           15559       38913   187592545+   f  W95 Ext'd (LBA)
/dev/sda5           20987       38913   143998596    7  HPFS/NTFS

```So, does this mean the Ubuntu install was a failure?

---

### Post by fEast91 on 2011-01-09
Well as it turns out, I just need to reinstall it again. Maybe the last time I picked the wrong Vista loader.
Thank you for your help dcstar.

---

