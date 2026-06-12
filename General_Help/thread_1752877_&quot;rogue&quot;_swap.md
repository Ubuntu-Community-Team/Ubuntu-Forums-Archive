---
title: "&quot;rogue&quot; swap"
date: 2011-05-08
forum: General Help
---

### Post by Cnaeus on 2011-05-08
Hi all,
pretty recently I came in shortage with hard disc space, and therefore I want to use my linux partition as well for storage. Now, I have, in theory, a 512 Mb swap partition, because 3Gb ram seems more than enough and I never use hibernation. That's ok, but practically it says (outside of disc manager) that I have a 2Gb swap memory, and indeed, this is the amount of disc space that is just missing (I have 16Gb linux partition of which 512Mb is supposed to be the swap). Now, I need that space, so I would like to shrink the swap back to the volume it is supposed to be. Since disk manager doesn't recognize tis 2Gb "rogue" swap, I guess there must be some type of swap file in the linux partition...
could anyone help me with this please, I mean to somehow regain this 2Gb disc space?
many thanks

---

### Post by ~Plue on 2011-05-08
Could you post the output of the following from a terminal;
```
cat /proc/swaps && cat /etc/fstab && free -m
```And just to make sure there isn't another partition;
```
sudo fdisk -l
```

---

### Post by Cnaeus on 2011-05-08
Ok, thanks for your attention... this is what I have:

_for "cat /proc/swaps && cat /etc/fstab && free -m" it goes like:_

```
Filename                                Type            Size    Used    Priority
/dev/ramzswap0                          partition       1547040 0       100
/dev/sda5                               partition       530104  0       -1
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
#Entry for /dev/sda6 :
UUID=a1c4fbab-16d3-42d1-88e9-86ff617b759b       /       ext4    errors=remount-ro01
#Entry for /dev/sda2 :
UUID=5AAC2531526DF104   /media/DATA     ntfs-3g defaults,nosuid,nodev,locale=hu_HU.UTF-8  0       0
#Entry for /dev/sda1 :
UUID=5E08C2DA382E2B26   /media/System7  ntfs-3g defaults,locale=hu_HU.UTF-8     00
#Entry for /dev/sda5 :
UUID=cf3ff5cb-723e-479a-9175-403f6cdf0da6       none    swap    sw      0       0


             total       used       free     shared    buffers     cached
Mem:          3021       2311        710          0        585       1202
-/+ buffers/cache:        523       2498
Swap:         2028          0       2028

```

_and it is pretty clear that I dont have a 2gb swap: (sudo fdisk -l)_

```
/dev/sda1   *           1        5242    42106333+   7  HPFS/NTFS
/dev/sda2            5243       36949   254686477+   7  HPFS/NTFS
/dev/sda3   *       36950       38913    15775585+   5  Extended
/dev/sda5           38848       38913      530113+  82  Linux Swap / Solaris    
/dev/sda6           36950       38847    15245312   83  Linux
```

---

### Post by ~Plue on 2011-05-09
> **Cnaeus said:**
> 
```
Filename                                Type            Size    Used    Priority
/dev/ramzswap0                          partition       1547040 0       100
```
That might be because casper is somehow installed on the system, in which case, search synaptic/ package manager you're using  and remove it. If it isn't installed, you can follow the instructions [here]("http://ubuntuforums.org/showpost.php?p=7268741&postcount=4") to remove the compcache.

---

### Post by Cnaeus on 2011-05-09
Thanks for the lead! Problem is, I'm using remastersys, so I'd like to keep casper for that... So I chose the other option - and after that the unwanted swap disappeared, but the disk space just didnt came back! :(( Do I really have to delete casper then?:confused:

---

### Post by ~Plue on 2011-05-10
> **Cnaeus said:**
> Thanks for the lead! Problem is, I'm using  remastersys, so I'd like to keep casper for that... So I chose the other  option - and after that the unwanted swap disappeared, but the disk  space just didnt came back! :sad:( Do I really have to delete casper then?:confused:
Compressed cache is stored on physical memory so you're not supposed to get it back on the HD..Sorry i didn't mention it earlier but i thought you were only after the extra swap space.

Following the OP: Post the full output of *sudo fdisk -l* including the disk information.

---

### Post by Cnaeus on 2011-05-12
Fact is, I just made a clean install with the latest 11.04 Kubuntu edition... My previous system was actually a 10.04 ubuntu upgraded with kde-desktop and it was quite buggy.

thanks for your help anyway, its good to know that casper does tricky things. I will be aware of it next time I use it...

---

