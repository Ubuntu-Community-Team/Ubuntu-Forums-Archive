---
title: "hidden swap space issue"
date: 2009-10-18
forum: General Help
---

### Post by map7 on 2009-10-18
Lately I've been having swap space issues on my Ubuntu 904 32bit machine and the system will freeze up.  I noticed that if I remove all the swap lines from my fstab and reboot, gkrellm still states I have swap space available.

If I then issue the command 'sudo swapoff -a' it reports 0MB of swap space, which is the correct amount.  Then if I do 'sudo swapon -a' it still says 0MB which is correct.  The incorrect value in all this is when I reboot it somehow finds 700MB of swap space, then if I forget to type sudo swapoff -a then the machine tries to use this swap space, fails and then freezes up.

Where else is swap space defined apart from my fstab.

Here is my fstab anyway
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c0fa8838-7afa-4bca-967f-2aedd629902f /               ext4    noatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Swap space
#UUID=e67dcc50-91be-4f19-8ab0-57902ea648a1 none	swap	sw	0	0

# Data drive
#/dev/sdc2       /home/map7/data1        ext4    auto,user,relatime      0 0
/dev/sdb1       /home/map7/data2        ext3    auto,user,relatime      0 0

# OLD Ubuntu 810 system drive.
/dev/sda1       /home/map7/old  ext3    auto,user,relatime      0 0

```

I once had some swap space on my other drives which I used, but I removed those partitions, and I don't think I issued the swapoff command beforehand.   Now that partition is gone it maybe trying to use it still in some old config file.

---

### Post by mike555 on 2009-10-19
if you search these forums you will see a way to make a swap file (instead of partition), that might be the way for you to go...

---

### Post by P4man on 2009-10-19
After booting, type "mount" in a terminal and see what swap its trying to mount (**edit**: it seems mount doesnt show swap. Try

```
swapon -s
```

). Perhaps you have a swap partition on a different drive you forgot about. I believe Ubuntu will mount any swap it sees, even if its not in fstab

> **mike555 said:**
> if you search these forums you will see a way to make a swap file (instead of partition), that might be the way for you to go...

Did you actually read his post?

---

### Post by map7 on 2009-10-23
I managed to reboot the server today :)

This is what I found when typing 'swapon -s'

~ $swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	774136	0	100
/dev/sda2                               partition	4803424	0	-1

Seems like some Memory drive or something, but I don't know where it's setting this.

Typing blkid I get

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="35e69b05-2437-4baf-b88b-25e3ae49d94a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="6e017929-6283-42a4-9d3a-be11859e942f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="c0fa8838-7afa-4bca-967f-2aedd629902f" TYPE="ext4" 
/dev/sda2: UUID="e67dcc50-91be-4f19-8ab0-57902ea648a1" TYPE="swap" 
/dev/ramzswap0: TYPE="swap"


Found this which helped solve it:
[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

---

### Post by dcstar on 2009-10-23
> **map7 said:**
> 
..........
Found this which helped **solve** it:
[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

**Solved** means do what is in my sig.

---

