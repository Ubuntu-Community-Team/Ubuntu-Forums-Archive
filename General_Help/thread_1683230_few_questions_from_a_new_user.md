---
title: "few questions from a new user"
date: 2011-02-07
forum: General Help
---

### Post by naj690 on 2011-02-07
hi. im a new ubuntu user. i want to ask few questions

1. i installed windows 7 in my drive C. can i install ubuntu 10.04 in drive C also? will it have any side effect?

2. currently i installed my ubuntu in drive D. the problem is i cant find my files that are in drive D in windows 7 whenever i use my ubuntu. is this normal?

---

### Post by TBABill on 2011-02-07
> **naj690 said:**
> hi. im a new ubuntu user. i want to ask few questions
 
1. i installed windows 7 in my drive C. can i install ubuntu 10.04 in drive C also? will it have any side effect?
 
No you won't have any side effect. I generally recommend a user run defrag in Windows first, then back up any important files in case you make an error setting up new partitions. Carefully go through the installation settings to make sure you do NOT install over your Windows partitions. You probably have a few Windows partitions so you'll want to make sure you follow the steps carefully to install to new ones (shrinking one or more of the Windows partitions).
 
 
> 2. currently i installed my ubuntu in drive D. the problem is i cant find my files that are in drive D in windows 7 whenever i use my ubuntu. is this normal?
Ubuntu doesn't use the same file system as Windows so you end up having to go into your drive manager and "mount" the Windows partition you are looking for. It should be one of the NTFS partitions, but may not indicate "D" at all because that's a Windows identifier. Not a big deal, but also make sure you "unmount" when finished. You'll probably see the drive you mounted on your desktop and all you have to do is right click it and select unmount. You see the same thing if you mount a CDROM or some other media.

---

### Post by oldos2er on 2011-02-07
Can you post the output of ```
sudo fdisk -l
``` ?

---

### Post by matt_symes on 2011-02-07
Hi

I am a bit confused (as usually happens). Are you using WUBI or is Ubuntu installed in a partition ? Do you want to use WUBI ?

Your use of windows terminology is a bit confusing. 

Kind regards

---

### Post by naj690 on 2011-02-07
First of all thx for the quick replies

> **oldos2er said:**
> Can you post the output of ```
sudo fdisk -l
``` ?

this is the output i got

> fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track


> Hi

I am a bit confused (as usually happens). Are you using WUBI or is Ubuntu installed in a partition ? Do you want to use WUBI ?


i installed it using WUBI. sorry if i wasnt clear

---

### Post by oldos2er on 2011-02-07
**sudo fdisk -l** ends with the lowercase letter L, not 1 (one). Please retry the command (copy and paste is your friend).

---

### Post by naj690 on 2011-02-07
oh. sorry about that. haha

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x211ccc1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        6481    51852808+   7  HPFS/NTFS
/dev/sda3            6482       58876   420856311+   f  W95 Ext'd (LBA)
/dev/sda4           58876       60802    15471640   12  Compaq diagnostics
/dev/sda5            6482       58876   420856280    7  HPFS/NTFS


---

### Post by oldos2er on 2011-02-08
[https://wiki.ubuntu.com/WubiGuide#How do I access the Windows drives?](https://wiki.ubuntu.com/WubiGuide#How do I access the Windows drives?)

---

### Post by naj690 on 2011-02-09
oh. so that's where it is. thx a lot guys

---

