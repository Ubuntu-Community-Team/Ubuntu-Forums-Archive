---
title: "sometimes ext4 /home partition remount read-only"
date: 2010-05-11
forum: General Help
---

### Post by frka on 2010-05-11
Hello!

I'm using Ubuntu 10.04 64bit (Kernel 2.6.32-22-generic) and sometimes my /home partition is remounting in read-only and i have no idea why.

Normally I only use programms like Firefox, Rhythmbox, Evolution and Netbeans 6.8.

What can I do to fix it? Should I switch to the EXT3 filesystem?

***dmesg*** shows me the following information:
```

[ 8758.010352] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 8758.010356] ata7.00: failed command: FLUSH CACHE
[ 8758.010360] ata7.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 8758.010361]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 8758.010363] ata7.00: status: { DRDY }
[ 8758.010366] ata7: hard resetting link
[ 8758.540045] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 8758.550583] ata7.00: configured for UDMA/133
[ 8758.550587] ata7.00: device reported invalid CHS sector 0
[ 8758.550596] ata7: EH complete
[ 8758.565414] end_request: I/O error, dev sdb, sector 94076126
[ 8758.565453] Aborting journal on device sdb6-8.
[ 8758.657798] EXT4-fs error (device sdb6): ext4_journal_start_sb: Detected aborted journal
[ 8758.657803] EXT4-fs (sdb6): Remounting filesystem read-only

```[B][I]lspci | grep SATA
[/I][/B]```

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 

```***hwinfo --disk***
```
27: IDE 700.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD080HJ_S08EJ1LYA85268
  Unique ID: WZeP.Zo5_tlyZCx1
  Parent ID: B35A.Ek2X4++0_p2
  SysFS ID: /class/block/sdb
  SysFS BusID: 7:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:02:00.0/host7/target7:0:0/7:0:0:0
  Hardware Class: disk
  Model: "SAMSUNG HD080HJ"
  Vendor: "SAMSUNG"
  Device: "HD080HJ"
  Revision: "ZH10"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sdb
  Device Files: /dev/sdb, /dev/block/8:16, /dev/disk/by-id/ata-SAMSUNG_HD080HJ_S08EJ1LYA85268, /dev/disk/by-id/scsi-SATA_SAMSUNG_HD080HJS08EJ1LYA85268, /dev/disk/by-path/pci-0000:02:00.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50000f0015a85268
  Device Number: block 8:16-8:31
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (SATA controller)
```***badblocks -v /dev/sdb***
```

badblocks -v /dev/sdb
Checking blocks 0 to 78150743
Checking for bad blocks (read-only test): done
Pass completed, 0  bad blocks found.                         

```

---

### Post by James78 on 2010-05-11
Boot into a livecd and run 'sudo e2fsck /dev/sdb6', use -f argument if it says it's clean.

---

### Post by lmarmisa on 2010-05-11
Look at the /etc/fstab file and check if the /home partition has been defined with the option errors=remount-ro.

---

### Post by StuartN on 2010-05-11
> **frka said:**
> I'm using Ubuntu 10.04 64bit (Kernel 2.6.32-22-generic) and sometimes my /home partition is remounting in read-only and i have no idea why.

A lot of people are having similar problems with Ubuntu 10.04, on both ext3 and ext4. You might want to follow any of these bugs if they look similar to your own:

ext4 journal error, remounted read-only after resume [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379)

Filesystems end up remounted read-only [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937)

Repetitive massive filesystem corruption [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981)

---

### Post by frka on 2010-05-11
> **James78 said:**
> Boot into a livecd and run 'sudo e2fsck /dev/sdb6', use -f argument if it says it's clean.

I tried this befor some times, but the problem is still there.

> **lmarmisa said:**
> Look at the /etc/fstab file and check if the  /home partition has been defined with the option  errors=remount-ro.

In my /etc/fstab is only the root filesystem with the option "errors=remount-ro"

**/etc/fstab**
```

# / was on /dev/sda1 during installation
UUID=8be9eb1d-e94a-4364-9023-5a92424ddfd6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=87f35e3c-4068-4b50-951e-737df038ff1a /home           ext4    defaults        0       2

```> **StuartN said:**
> A lot of people are having similar problems with  Ubuntu 10.04, on both ext3 and ext4. You might want to follow any of  these bugs if they look similar to your own:

ext4 journal error, remounted read-only after resume [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379)

Filesystems end up remounted read-only [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937)

Repetitive massive filesystem corruption [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981)

Thank you. I think it could be one of my problem. 
I will follow these bugs :)

---

### Post by iceman5664 on 2012-11-27
I ran into the same issue when booting from an SD card. I was able to work around it by adding the sync option to /etc/fstab. I theory, this should hurt performance, but I haven't noticed it. I'm only using the SD card to boot XBMC, so local writes shouldn't be a factor. For good measure, I also added the noatime and nodiratime options.

Here's what my fstab looks like:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ea52f83-76a5-484e-99e2-de345866401a /               ext4    errors=remount-ro,sync,noatime,nodiratime 0       1
```

---

### Post by wildmanne39 on 2012-11-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

