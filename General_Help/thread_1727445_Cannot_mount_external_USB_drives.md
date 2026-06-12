---
title: "Cannot mount external USB drives"
date: 2011-04-12
forum: General Help
---

### Post by nd0586 on 2011-04-12
[B]Hi,

Yet another new Ubuntu user stuck and asking for help... sorry!

I have recently installed Ubuntu 10.10 on my machine as dual boot using WUBI but on a seperate partition to Windows. Loving it so far, but i cannot get any external drives to mount - i've tried pen drives, camera memory cards and hard drives but nothing comes up.

I have just tried restarting with a pen drive plugged in, and it finally showed something in the computer folder - "memory stick drive" is shown (and my internal CD drive, which i'm not sure was there before.), but i still can't access it and when I try to unmount it gives me the message [/B]

Error detaching: helper exited with exit code 1: Detaching device /dev/sdc
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

**when i type "mount" with the pen drive still plugged in i get:**

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda5 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,all ow_other,blksize=4096)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nige/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nige)

**and when i type sudo fdisk -1:**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda01da01

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6397 51383871 7 HPFS/NTFS
/dev/sda2 6398 19457 104904450 5 Extended
/dev/sda5 6398 19457 104904418+ 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2112492

Device Boot Start End Blocks Id System
/dev/sdb1 1 60801 488384001 7 HPFS/NTFS

**when i type ls -l /media**

total 208
lrwxrwxrwx 1 root root 7 2011-03-15 20:26 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-03-15 20:26 floppy0
drwxrwxrwx 1 root root 8192 2011-03-15 20:18 sda1
drwxr-xr-x 2 root root 4096 2011-03-22 17:44 sda5
drwxrwxrwx 1 root root 163840 2011-03-17 21:34 sdb1
lrwxrwxrwx 1 root root 4 2011-03-28 19:17 usb -> usb0
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb0
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb1
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb2
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb3
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb4
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb5
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb6
drwxr-xr-x 2 root root 4096 2011-03-28 19:17 usb7


[B]hope that that's enough info for someone to be able to tell what's wrong!

thanks to anyone who can help![/B]

---

### Post by sanguinoso on 2011-04-12
Try: ```
cd /media/usb0
```

And then
```
ls
```

---

### Post by nd0586 on 2011-04-12
Hi,

thanks for your help!

I now seem to have USB 1-7 folders in my media folder, along with a folder called USB with a shortcut symbol, which i don't think were there before. however none of the folders contain anything, even when i have my drives plugged in.

any further ideas?!

---

### Post by jchw on 2011-05-14
I also have a problem with my USB drive in Ubuntu 10.10 when I try to connect a USB memory stick. 

All my sticks work fine in Mint and my mouse works OK so it is not a hardware problem.

In one thread I saw a suggestion to remove usbmount which I did and now I can see my memory sticks but I am unable to access the data properly.

As I use a 32G USB stick as a backup devise this is a serious issue and at the moment I see no way of of rectifying the situation.

Any thoughts on why this happened and how to correct it? At the moment this looks like a reinstallation job which I would be reluctant to do as my backup device is not working.

---

