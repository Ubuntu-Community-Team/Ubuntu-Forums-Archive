---
title: "External Hard Drive mounting"
date: 2012-09-08
forum: General Help
---

### Post by huzz18 on 2012-09-08
Ok i am new to Ubuntu 12.04 , just transfered from windows , i have been trying many posts and following wtv they have posted but i am still unable to mount my external hard drive .  Using disk utility , when i try to mount i get the following error -

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /home/hdd

This is what I get for sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d004

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   618995711   309496832   83  Linux
/dev/sda2       618997758   625141759     3072001    5  Extended
/dev/sda5       618997760   625141759     3072000   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae5ac89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001    b  W95 FAT32

And this is what I get for sudo lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0bc2:5071 Seagate RSS LLC 
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 006 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 003: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller

---

### Post by dgharmon on 2012-09-08
> **huzz18 said:**
> Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sdb1 on /home/hdd

Mount the hard drive as root, then change ownership for the current user .. from a command console type:

$sudo -i
$mkdir /mnt/sda1
$mount /dev/sda1 /mnt/sda1
$chown -R users:users /mnt/sda1

---

### Post by huzz18 on 2012-09-08
Thanks a ton this worked :) Really appreciated the quick response.

---

### Post by zandman on 2013-02-10
And fixed my problem with an external hdd that gave me rights errors also
[I]jaap@PhenomX2:~$ /dev/sdd1
bash: /dev/sdd1: Permission denied[/I]
Now i have a working 2nd back-drive as planned

Thanks \\:D/

---

