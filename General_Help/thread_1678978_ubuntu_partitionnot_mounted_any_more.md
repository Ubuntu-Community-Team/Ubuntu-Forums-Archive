---
title: "ubuntu partitionnot mounted any more"
date: 2011-01-31
forum: General Help
---

### Post by andreasku on 2011-01-31
Hi,

I have a grub doubleboot with windows and ubuntu.
The system crashed a couple of times last weak because of a hardware defect. Since that time I can't boot ubuntu any more, what I get is:

```
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3.1ubuntu5) built-in shell (ash)
```I tried to follow some instructions for recovering GRUB, but they didn't work for me since I can't mount the partition. Partitions are:

```
Device           | Start | End   | Blocks    | Id | System
/dev/sda1 (boot) | 1     | 10128 | 81347656+ | 7  | HPFS/NFTS
/dev/sda2        | 10128 | 19458 | 74941441  | 5  | Extended
/dev/sda5        | 10128 | 19084 | 71938048  | 83 | Linux
/dev/sda6        | 19084 | 19458 | 3002368   | 82 | Linux Swap / Solaris
```Thanks in advance
Andreas

---

### Post by TheHackOps on 2011-01-31
Is /dev on sda1?

---

### Post by andreasku on 2011-01-31
Hm, not sure if I understand your question. sda1 is the windows partition.
Greetings Andreas

---

### Post by TheHackOps on 2011-01-31
Ok is /dev on the same hard disk at /root and /

---

### Post by andreasku on 2011-01-31
Yes. My notebook has just one harddisk.

---

### Post by TheHackOps on 2011-01-31
Sorry its 1:50 AM, i meant partition

---

### Post by andreasku on 2011-01-31
well, I guess they are all on the linux partition

---

### Post by TheHackOps on 2011-01-31
RLY? no way i would never have guessed. ext1 ext2 ext3 ext4 and so on are your partitions. ext is the file system your using

---

### Post by andreasku on 2011-01-31
the partitions are sda1, sda2...
you need sleep man. Can anyone help me with this?

---

### Post by vanadium on 2011-01-31
I suggest you boot a live session of Ubuntu and perform a file system check of /dev/sda5. Your problem sounds as if the file system on that partition has been damaged to the extent that it cannot be mounted anymore. With a file system check, it might be repaired.

---

### Post by perspectoff on 2011-01-31
> **vanadium said:**
> I suggest you boot a live session of Ubuntu and perform a file system check of /dev/sda5. Your problem sounds as if the file system on that partition has been damaged to the extent that it cannot be mounted anymore. With a file system check, it might be repaired.

+1

Try the solution of reinstalling Grub "to the MBR" (which will reset the Grub2 settings in the partition as well) using the LiveCD. A possibility is that be the MBR or the Grub settings themselves became corrupted somewhere along the line (or, more exactly, one of the partition identifiers, such as the UUID, has changed and the old Grub settings don't properly identify and point to the system files any longer). For this type of problem (and the instance of only two OS on your computer), Grub2 is great. It will analyze your disk, retrieve the correct partition (and OS) identifiers, and configure bootup properly again with a minimum of fuss. 

If the problem is more severe than that and really does represent a filesystem corruption, you may be able to rescue files (for backup) from the corrupted partition using the LiveCD prior to reinstalling (K)Ubuntu altogether. 

My hunch is that the problem isn't with the partition, however, but will be solved by re-installing Grub.

---

### Post by andreasku on 2011-02-09
hi guys,

sorry for not replying earlier!
I could finally fixing it with your help cheers!

First I did a file system check using fsck and then I reinstalled grub2
Important: fsck doesn't work with the ubuntu 10.10 live cd. I found out this is a known issue.
You have to use an older Ubuntu live cd or any other linux live cd.

Cheers!

---

