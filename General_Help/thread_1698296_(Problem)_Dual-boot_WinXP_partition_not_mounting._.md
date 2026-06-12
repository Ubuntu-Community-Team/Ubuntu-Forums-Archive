---
title: "(Problem) Dual-boot WinXP partition not mounting. Exit code 21 from mount ? 10.04"
date: 2011-03-02
forum: General Help
---

### Post by Thespian on 2011-03-02
I'm running Ubuntu 10.04 on an hp/compaq 8710p laptop, dual booting windows XP and Ubuntu.  Everything has worked fine for years.

Now, on boot-up into ubuntu, it claims it can't mount /dev/sda1 (the windows XP partition) and asks if I want to hit 'S' to skip it, or 'M' to mount it.  Skipping it continues with normal boot-up, just without mounting the XP partion into /media/drv0 like it used to.

Booting in to windows works fine, and I've all ready run chkdsk /f /r (no errors) and rebooted twice.  XP continues to work, but still won't mount during Linux boot.

Looking for advice on what to try next.  Below, find some basic debugging I've all ready done, and the output of diagnostic commands others have requested in other similar threads.

========================================================
root@laptop:~# mount -a
root@laptop:~# echo $?
21

I'm not sure what return code 21 implies.  Trying to mount the partition from "Disk Utility" just gets me the message that it failed to do so, without useful error information.

root@laptop:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20138   161758453+   7  HPFS/NTFS
/dev/sda2           29102       30401    10442250    7  HPFS/NTFS
/dev/sda3           20139       28719    68926882+  83  Linux
/dev/sda4           28720       29101     3068415   82  Linux swap / Solaris

Partition table entries are not in disk order
root@laptop:~# blkid
/dev/sda1: UUID="2BEF0F6D4DE0F164" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="FAFC5F30FC5EE703" TYPE="ntfs" 
/dev/sda3: UUID="e4a0a254-b49c-4b0a-bfb1-a78c4d637c45" TYPE="ext3" 
/dev/sda4: UUID="2aacf1a5-cc47-4dbf-8927-5e3d045d4002" TYPE="swap" 
root@laptop:~# cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=e4a0a254-b49c-4b0a-bfb1-a78c4d637c45     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=2BEF0F6D4DE0F164       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda4
UUID=2aacf1a5-cc47-4dbf-8927-5e3d045d4002      none            swap        sw          0   0

root@laptop:~# mount -t ntfs-3g -o force /dev/sda1 /media/drv0
root@laptop:~# echo $?
21
root@laptop:~# ls /media/drv0
==========================================

Nothing returned from the 'ls' command, and nothing mounted.  I've got the newest version of ntfs-3g from the repository.  This only started recently, and I've had no unclean windows shutdowns.

Disk Utility shows nothing odd for a system this old.  10 "bad" sectors make it to the 'warning' box, but it's still in the green.

I'm out of ideas as to why it won't mount, and how to fix it.  Any suggestions welcomed.

---

### Post by Thespian on 2011-03-02
Looks like an other user reported substantially the same thing in this thread:

[http://ubuntuforums.org/showthread.php?t=1698599](http://ubuntuforums.org/showthread.php?t=1698599)

Cross linking here in case this issue gets traction in that thread.

---

### Post by stdrogo on 2011-03-02
This is certainly the same problem, and I've been unable to find any relevant information about exit code 21. I can only think that there are some shared complications from an update that affects both 10.04 and 10.10.

---

### Post by Thespian on 2011-03-02
If I had to guess, I'd think maybe some change to ntfs-3g  

Any way to tell when it updated, and from what version to what version?

I know I had done a largish set of updates shortly before noticing the problem.  No idea if ntfs-3g was one of the updates though.

---

### Post by stdrogo on 2011-03-02
I haven't been able to find any information about update history from update-manager. Synaptic > File > History doesn't list them.

---

### Post by stdrogo on 2011-03-02
I found a newly listed bug report on launchpad that seems similar [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/727668](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/727668) There is no solution posted yet, but what do you think?
Edit: Downgrading libfuse2 and fuse-utils works for me!

---

### Post by Thespian on 2011-03-02
Thank you stdrogo!  work-around worked for me to.  I'll change my thread to "fixed" if they don't have a setting for "work-around".

---

### Post by immukesh on 2011-03-03
Do you guys mind sharing how you downgraded those packages? Where did you get the old packages from? I tried and it refused to install the package citing conflicts.

---

### Post by sutupud on 2011-03-03
you can just pin down the version in your /etc/apt/preferences:

Package: libfuse2
Pin: version 2.8.1-1.1ubuntu2 # 2.8.4-1ubuntu1 for maverick
Pin-Priority: 1001

Package: fuse-utils
Pin: version 2.8.1-1.1ubuntu2 # 2.8.4-1ubuntu1 for maverick
Pin-Priority: 1001

and then do a 'apt-get --reinstall install libfuse2 fuse-utils'

the same problem esists with maverick when upgrading from 2.8.4-1.1ubuntu1 to 2.8.4-1ubuntu1.3

---

### Post by stdrogo on 2011-03-03
> **immukesh said:**
> Do you guys mind sharing how you downgraded those packages? Where did you get the old packages from? I tried and it refused to install the package citing conflicts.
Easiest way is to go into synaptic and highlight the package you want to downgrade then go Package > Force Version and select the earlier version.

---

### Post by sarang on 2011-03-03
Same error on lucid 10.04 for me as original post; fixed by downgrading libfuse2 and fuse-utils, as suggested by sutupd. Thanks!

Sarang

---

