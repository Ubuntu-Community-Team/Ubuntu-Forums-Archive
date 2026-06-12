---
title: "md: invalid superblock checksum"
date: 2011-07-11
forum: General Help
---

### Post by themdg on 2011-07-11
Hi There.  I'd like some help with an md error I'm seeing.  

I'm running 2.6.32-28-generic. I have a raid1 (two 1tb drives with two partitions... one for / and one for /home.)   After a power outage, I'm seeing grub complaining about /dev/md0 not existing (ALERT! /dev/md0 does not exist. Dropping to a shell!)

I booted to the latest live CD to have a look around.  My dmesg output includes these ominous lines:

```
[  324.689812] md: md0 stopped.
[  324.697048] md: invalid superblock checksum on sdc1
[  324.697053] md: sdc1 does not have a valid v0.90 superblock, not importing!
[  324.697056] md: md_import_device returned -22
```

Here is the whole dmesg output:  [http://pastebin.com/1TLH8jzb]("http://pastebin.com/1TLH8jzb")

Can some kind soul point me in the right direction?  I'm reading about working more about mdadm etc...but I'm pretty new with raids altogether.  I don't want to hose anything up further.

---

### Post by themdg on 2011-07-13
I have the system booting now.  

When I boot to the live cd, md1(my /home) is created and mounted just fine.  

Looking at /proc/mdstat, md0 simply didn't exist.  

I removed the live cd and let normal booting fail, dropping into the limited shell.

I executed:  ```
mdadm -C /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb1 /dev/sdc1
``` which created /dev/md0

Upon rebooting, I was warned that I needed to boot degraded, which I did.  

/proc/mdstat now looks like:

```
:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[0]
      14651136 blocks [2/1] [U_]

md2 : active raid1 sdb3[0] sdc3[1]
      971840 blocks [2/2] [UU]

md_d0 : inactive sdc1[1](S)
      14651136 blocks

md1 : active raid1 sdc2[1] sdb2[0]
      961136704 blocks [2/2] [UU]

unused devices: <none>
```

So, md2 looks like a good raid of sdb3 and sdc3.  md0 is running on only one partition (sdb1) and sdc1 is inactive.  

Can anyone help me understand this?  Since sdc3 is on the same drive as sdc1, it makes me think the sdc drive has not necessarily gone bad...  But the partition has?  I don't get it.

---

### Post by Drenriza on 2011-07-13
The superblock is a block of data that points to where you OS reside. If you have a invalid superblock, try and tell the system to look at the next superblock location, to point at your OS.
[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)

---

