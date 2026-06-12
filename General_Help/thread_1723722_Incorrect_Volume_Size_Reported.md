---
title: "Incorrect Volume Size Reported"
date: 2011-04-07
forum: General Help
---

### Post by Cthulhu_Dreams on 2011-04-07
My MP3 Player (Zen:Vision:M) has roughly  60 GB of space and yet Ubuntu insists only 3.6 GB is available.  I know  this is not true because in Windows the correct amount of room is  displayed and can be filled up. Because my music collection is stored in  my Linux partition I need to solve this issue if I'm going to actually use my MP3 Player.  What is also interesting is the fact that the device doesn't show up in Gparted, System Monitor or fdisk.

When I attempt to look at the Zen's contents through Nautilus I get this message:

Error initializing camera: -1: Unspecified error

And when I update through Banshee every song gives an error of:

Argument cannot be null. Parameter name: obj

---

### Post by Cthulhu_Dreams on 2011-04-08
Bump

---

### Post by srs5694 on 2011-04-08
I'm not familiar with your specific model of MP3 player; however, I do have some observations and suggestions.

First, you must be more precise about what you mean. For instance, and most importantly, you say "Ubuntu insists only 3.6 GB is available" -- but there are several (maybe dozens) of ways you could be determining how much space is available on the device from Ubuntu. Without knowing how you made this determination, it's hard to offer advice.

As a start, I recommend you unplug the device, reconnect the device (including telling it to make its files available to the computer, if that's required), wait a few seconds, and run the following commands in a terminal. Post the output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility:

```

sudo fdisk -lu
df -h
cat /etc/mtab
ls -l /dev/sd*
dmesg | tail
lsusb

```

None of these commands will fix anything; they're all diagnostic commands intended to provide us with information on the device and the partitions and filesystems it contains.

---

### Post by Cthulhu_Dreams on 2011-04-09
I actually was able to get into it when I first plugged it in, it said 3.6 GB in the lower left corner of the Nautilus.

**fdisk -lu**

Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137345 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1            2046   331565055   165782736    5  Extended
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda6            2048   146487295    73240335   83  Linux
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda5       146487296   331565055    92534400   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda2   *   331565535   454655564    61536982    7  HPFS/NTFS
/dev/sda3       454655565   623210252    84276990   83  Linux
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda4       623210496   625141759      963900   82  Linux swap
Warning: Partition 4 does not end on cylinder boundary.
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label

**df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              69G   17G   49G  26% /
none                  2.0G  724K  2.0G   1% /dev
none                  2.0G  636K  2.0G   1% /dev/shm
none                  2.0G  228K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda3              80G   49G   27G  65% /media/sda3
/home/adrian/.Private
                       69G   17G   49G  26% /home/adrian
/dev/sr0              7.5G  7.5G     0 100% /media/STAR_TREK_XI_DOM

**cat /etc/mtab**

/dev/sda6 / ext4 rw,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sda3 /media/sda3 ext2 rw,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/adrian/.Private /home/adrian ecryptfs ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=9ad2a19a45803149,ecryptfs_fnek_sig=4f6a494529b6f98b 0 0
gvfs-fuse-daemon /home/adrian/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=adrian 0 0
/dev/sr0 /media/STAR_TREK_XI_DOM udf ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500 0 0

**ls -l /dev/sd***

brw-rw---- 1 root disk 8,  0 2011-04-09 16:47 /dev/sda
brw-rw---- 1 root disk 8,  1 2011-04-09 16:32 /dev/sda1
brw-rw---- 1 root disk 8,  2 2011-04-09 16:32 /dev/sda2
brw-rw---- 1 root disk 8,  3 2011-04-09 16:32 /dev/sda3
brw-rw---- 1 root disk 8,  4 2011-04-09 16:32 /dev/sda4
brw-rw---- 1 root disk 8,  5 2011-04-09 16:32 /dev/sda5
brw-rw---- 1 root disk 8,  6 2011-04-09 16:32 /dev/sda6
brw-rw---- 1 root disk 8, 16 2011-04-09 16:32 /dev/sdb

**dmesg | tail**

[  393.517040] atkbd serio0: Use 'setkeycodes e014 <keycode>' to make it known.
[  701.700085] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  727.683187] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  727.694984] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  752.054066] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  752.068887] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  754.377880] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  754.387972] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  756.553521] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use
[  756.562570] usb 1-3: usbfs: process 2703 (banshee) did not claim interface 0 before use

**lsusb**

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b179 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 041e:4151 Creative Technology, Ltd Zen Vision:M (mtp)
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by srs5694 on 2011-04-10
Linux is recognizing the device at some level, but there are problems with it, as revealed by the dmesg output and the fact that fdisk didn't find it.

Try this:

```

sudo blkid /dev/sdb

```

If it says there's a filesystem, you might be able to mount it with a command like this:

```

sudo mount /dev/sdb /mnt/somedir

```

Change "/mnt/somedir" to a convenient empty directory. This is a long shot, though; I suspect there are driver issues that will make it difficult to get this device working. Have you tried a Web search on "Linux Creative Zen" or similar keywords?

---

### Post by Cthulhu_Dreams on 2011-04-18
Sorry for the slow response.   The command:

sudo blkid /dev/sdb

Doesn't bring back a response, while my attempt to mount the Zen result in an "unknown device" message.  As for the drivers, the Zen uses the basic MTP Driver.  I can't imagine there is something so wrong with it but even after removing and reinstalling it, I am still having the same problems.

---

