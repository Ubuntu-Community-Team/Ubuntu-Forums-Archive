---
title: "Unable to rescue files in root partition(Karmic)"
date: 2011-03-09
forum: General Help
---

### Post by bulbus on 2011-03-09
Hello,

I'm unable to boot from hard disk. when booting from hard disk it says
```
Loading Grub.
File not found.
```Tried fixing grub,  by booting from Live CD.
But I'm unable to see any files in the root partition, to fix them.
So none of the methods like chroot, grub-install do not work.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ ls /mnt
lost+found
ubuntu@ubuntu:~$
```Following is the output from fdisk and blkid::

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130e8a61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+   7  HPFS/NTFS
/dev/sda2           18237       22856    37110150    5  Extended
/dev/sda3           22857       59329   292969372+  83  Linux
/dev/sda4           59330      121601   500199840   83  Linux
/dev/sda5   *       18237       21883    29294496   83  Linux
/dev/sda6           21884       22856     7815591   82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="509888B998889EDA" TYPE="ntfs" 
/dev/sda3: UUID="fecd05b8-08a0-4963-a0cd-c9a2541ecc68" TYPE="ext4" 
/dev/sda5: UUID="a48f39db-148a-47d3-8421-ed13e651a00d" TYPE="ext4" 
/dev/sda6: UUID="5561ff5b-9d48-4b17-bd5b-e2dc633e1a09" TYPE="swap" 
```Might not be able to respond to the replies for the thread immediatly, as I will be running for work now. Will definetly take look after I get back.

-Thanks

---

### Post by handy on 2011-03-09
If I was in your situation & I had valuable information stored on these partitions, the first thing I would do would be use Clonezilla to duplicate the whichever or all of the partitions onto another drive.

After that, I would then start to work at trying to recover from this problem.

Preferably using the copy (again, the value of the data on board dictates just how much trouble you go to). If you have nothing that is not backed up on the drive then it may be best to just scrap your installation & rebuild (sounds like windows doesn't it?) I should be quiet now. :|

---

### Post by bulbus on 2011-03-09
Thanks that was Handy!
Will go ahead re-install, if someone else doesn't suggest another alternative!

---

