---
title: "Can't mount software RAID 1"
date: 2010-06-17
forum: General Help
---

### Post by Mathieu147 on 2010-06-17
Hi,

I have 4 disks in my machine:
[LIST=1]
[*]1 SDD
[*]2 * 1TB SATA HDD
[*]1 * 500GB SATA HDD
[/LIST]

What I want to do is: using the SSD to have my /, and using the two 1TB disks for a RAID1 for my /home. And the fourth disk would be mounted somewhere in /media.

I installed Ubuntu 10.04 (64 bits) today using alternante CD, and I couldn't make the RAID work during the installation process. So I installed everything on the SSD in one partition.

When the system was installed, I used "Disk Utility" to create a RAID (that was easy, BTW, disk utility is a great tool!).

I searched a little bit to make the RAID automatically start at boot, but I can't mount it... When I use Disk Utility, it works very well, but it doesn't work using the command line:
```
mathieu@mathieu-desktop:~$ sudo mount -t ext4 /dev/md0 /media/raid/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
```
mathieu@mathieu-desktop:~$ dmesg | tail
[   40.606413] EXT4-fs (md0p1): mounted filesystem with ordered data mode
[   40.910007] wlan0: no IPv6 routers present
[ 1150.160572] EXT4-fs (md0p1): mounted filesystem with ordered data mode
[ 1890.871379] EXT4-fs (md0): VFS: Can't find ext4 filesystem
[ 1943.110786]  md0:
[ 2324.310756] EXT4-fs (md0p1): mounted filesystem with ordered data mode
[ 2338.427583] EXT4-fs (md0): VFS: Can't find ext4 filesystem
[ 2495.247881] EXT4-fs (md0p1): mounted filesystem with ordered data mode
[ 2932.487450] EXT4-fs (md0): VFS: Can't find ext4 filesystem
[ 3309.436599] EXT4-fs (md0): VFS: Can't find ext4 filesystem
```

When I try to use the fstab to mount it at boot time, I have a message that says that the partition is not ready yet, or absent.


What could the problem be? And, of course, how can I solve it? :confused:


Thanks very much!

---

### Post by Mathieu147 on 2010-06-18
Ok, Solved! Correct device was /dev/md0p1, not /dev/md0...

---

