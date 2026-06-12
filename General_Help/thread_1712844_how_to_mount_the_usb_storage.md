---
title: "how to mount the usb storage"
date: 2011-03-23
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-23
#lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

#fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000661aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38544   309601280   83  Linux
/dev/sda2           38544       38914     2967553    5  Extended
/dev/sda5           38544       38914     2967552   82  Linux swap / Solaris

How to mount usb storage device in my ubuntu 10.10. Please help me

Thank you,

---

### Post by Mark Phelps on 2011-03-23
If you connect it after launching Ubuntu, you should get a drive icon appearing on your desktop.

If you have it connected before launching Ubuntu, just go into Places.  It should be listed there.  Click on it to open it (that mounts it by default).

---

