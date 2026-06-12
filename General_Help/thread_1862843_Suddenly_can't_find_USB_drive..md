---
title: "Suddenly can't find USB drive."
date: 2011-10-17
forum: General Help
---

### Post by Tallguitarguy on 2011-10-17
I have a USB drive with my music on it and it was working fine. Now, when I plug it in it only lights up, but does not show up on the computer whatsoever. Could someone help please?

Details:
Laptop: Dell Inspiron 1501
OS: Ubuntu 11.04
USB Drive: 16gb Danelec

---

### Post by Kai Summers on 2011-10-17
Goto System -> Administration -> Disk Utility 

See if it shows up in there if so try and to mount it here, it should also give you a mount point address if its already mounted and just not showing up on the desktop or in the nautilus windows.

---

### Post by blueridgedog on 2011-10-17
With the disk in, the output of the following commands (run in a terminal) would help diagnose your issue:

```
lsusb
```

and

```
mount
```

and 

```
sudo fdisk -l
```

(lower case L, not a number 1)

---

### Post by Tallguitarguy on 2011-10-20
This is what it said with my iPod, which also suddenly stopped working
> fender@Guitarded:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fender@Guitarded:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fender/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fender)
fender@Guitarded:~$ sudo fdisk -l
[sudo] password for fender: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000512b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14480   116304896   83  Linux
/dev/sda2           14480       14594      913409    5  Extended
/dev/sda5           14480       14594      913408   82  Linux swap / Solaris
fender@Guitarded:~$


---

### Post by Tallguitarguy on 2011-10-20
In Disk Utility it shows the flash drive, but says its not partitioned or something. The ipod doesn't even show up there.

---

### Post by blueridgedog on 2011-10-20
Try a different port or cable.  You are right, the system doesn't see it.

---

### Post by Tallguitarguy on 2011-10-20
Oddly enough my ipod suddenly started working again. I had tried different ports before and got nothing. I think I'll need to get a file recovery software of some sort for my flash drive though, cause then I can just reformat it.

---

### Post by tartalo on 2011-10-20
> **Tallguitarguy said:**
> I think I'll need to get a file recovery software of some sort for my flash drive though, cause then I can just reformat it.

testdisk: fixes corrupted partition tables
fsck: fixes corrupted file systems
photorec: recovers and undeletes files

---

### Post by Tallguitarguy on 2011-10-25
thank you tartalo, I was able to find about 600 of the files I want, which is a start. My computer kinda froze half way, but I have all my music from A-P. I'll try again tomorrow to see if it'll work better then.

---

### Post by Tallguitarguy on 2011-10-31
Everything is sorted out, I was able to get the rest of what I needed from my iPod. Thanks a million for the photorec solution, it was very helpful. It probably would have worked better with a faster computer, which mine is definitely not.

---

