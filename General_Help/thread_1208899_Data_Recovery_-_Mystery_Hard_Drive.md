---
title: "Data Recovery - Mystery Hard Drive"
date: 2009-07-09
forum: General Help
---

### Post by Rendrago on 2009-07-09
I've Googled and searched and banged my head on the desk to no avail.

I accidentally deleted the partition table on one of my storage drives using GParted.

I am not sure _exactly_ what was on this drive, if it was encrypted or what file system was present. I know this drive had important data on it. If it was encrypted, I have the passphrase. I tried to use testdisk and was overwhelmed.

My two questions are:

[LIST=1]
[*]I would like to learn as much as possible about this drive and then proceed to attempt a recovery. How should I proceed?
[*]I know my file system, mount points, etc. are sloppy and all messed up. How can I clean things up?
[/LIST]

I have 4 drives:
Drive 1 - 250GB - Main Alt-CD Encrypted drive - Ubuntu 9.04 - sda1, 2 & 5
Drive 2 - 500GB - The mystery drive
Drive 3 - 500GB - EXT3 LUKS Encrypted Storage Drive.
Drive 4 - 1000GB - EXT3 Non-Encrypted Storage Drive.

When I boot I am asked for my main drive passphrase and the passphrase for the third drive.

Here's some more info:

**sudo fdisk -l**

```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30370   243946993+  83  Linux
/dev/sda2           30371       30401      249007+   5  Extended
/dev/sda5           30371       30401      248976   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44444444

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8aaad72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00090179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux


```

**/etc/fstab**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/wagps9501-root
UUID=068088f7-a42c-45e8-bb04-e49e2f7debdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=04d73531-f999-4536-9e04-cf1707e05260 /boot           ext3    relatime        0       2
# /dev/mapper/wagps9501-swap_1
UUID=c802baec-47e4-4b85-b588-1f45cdf28dcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# CryptoDevices
/dev/mapper/500GB-1	/media/sdb1	auto	defaults	0	0
```

Running testdisk shows:

```
Disk /dev/sda - 250 GB / 232 GiB - ATA Hitachi HDT72502
Disk /dev/sdb - 500 GB / 465 GiB - ATA ST3500630AS
Disk /dev/sdc - 500 GB / 465 GiB - ATA ST3500320AS
Disk /dev/sdd - 1000 GB / 931 GiB - ATA WDC WD1001FALS-0
Disk /dev/mapper/500GB-1 - 500 GB / 465 GiB
Disk /dev/mapper/sda1_crypt - 249 GB / 232 GiB
Disk /dev/mapper/wagps9501-root - 243 GB / 226 GiB
Disk /dev/mapper/wagps9501-swap_1 - 6316 MB / 6024 MiB
```

The **ATA ST3500320AS** is mounted as **/media/ST3500320AS-500G**.

The **ATA WDC WD1001FALS-0** is mounted as **/media/disk** and shows up as 1000.2 GB Media in Places in Nautilus.

**ATA ST3500630AS** is our mystery drive.

Please help me sort out this giant convoluted mess! Where should I go from here!

:( :( :(

---

