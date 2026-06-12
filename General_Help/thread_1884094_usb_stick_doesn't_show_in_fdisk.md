---
title: "usb stick doesn't show in fdisk"
date: 2011-11-20
forum: General Help
---

### Post by 7Sasha on 2011-11-20
Hi, my ubuntu machine wouldn't recognize my usb pendrive,
while it works on other PC's with Win. 

Fdisk -l output: 
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bffbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       57861   464657408    7  HPFS/NTFS
/dev/sda3           57861      121602   512000001    5  Extended
/dev/sda5           57861       59841    15905792   82  Linux swap / Solaris
/dev/sda6           59841      121602   496093184   83  Linux

```

**lsusb**
```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:9090 A4 Tech Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
_Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3_

**dmesg | tail** after ejecting and plugging in the stick:
```
[  403.279372] usb 1-2.2: USB disconnect, address 5
[  405.495156] usb 1-2.2: new high speed USB device using ehci_hcd and address 6

```

**cat /etc/fstab**
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=6184edd4-b53a-424f-9bfa-26c0e2bf5207 none            swap    sw              0       0
```

I'm clueless. Any help?
Thank's in advance.

---

### Post by hal8000 on 2011-11-20
If its been used under windows it may have a corrupt filesystem.
My usb stick is recognised as /dev/sdb1

I would make a temp directory:

mkdir /home/user/test/

(replace user with your username)

Then try mounting the usbstick at the terminal:

sudo mount /dev/sdb1 -t auto /home/user/test

This will give some clue as to what is wrong, either cant detect the filesystem or partition. You could try running a scandisk from windows.

---

### Post by 7Sasha on 2011-11-20
As expected
```
mount: special device /dev/sdb1 does not exist
```
I've tried to format the stick to both FAT and FAT32 partitions using Win machine. None of them read.

Thanks for your reply.

---

### Post by hal8000 on 2011-11-20
I had a USB memory stick once which wasn't very good and kept losing data and corruption from both windows and linux. I think it was made by Sandisk.
One more thing to try, try and use a different USB port, and make sure that it plugs direct into your PC not via a USB hub.

Although lsusb shows your device its not reading the partition table on the usb drive. testdisk may be able to help but is more difficult to use.

---

### Post by 7Sasha on 2011-11-21
testdisk doesn't see the stick either,
though it works properly on Win without any data loss or any abnormal activity,
nor direct connection of the stick without the hub helped.

+ i've tested 2 more sticks from different manufactures and they wouldn't work either

---

### Post by 7Sasha on 2011-11-21
+ My lubuntu machine recognizes the drive properly.

---

