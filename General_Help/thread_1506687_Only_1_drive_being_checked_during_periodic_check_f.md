---
title: "Only 1 drive being checked during periodic check for errors."
date: 2010-06-10
forum: General Help
---

### Post by Silvernail on 2010-06-10
I am running:
> [    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)


During the periodic boot time check for disk errors, I notice that the application is checking disk #1 or 1.

I have an external USB 1 Terabite Iomega hard drive I would like to have checked also.  Where and what do I enter to have this happen.
> 
dave@dave:~$ di
Filesystem         Mount              Mebis     Used    Avail %Used fs Type
/dev/sda1          /               147365.3  11704.6 128174.9  13%  ext4   
/dev/sdb1          /media/Teragb   940903.9  84203.3 809281.9  14%  ext3   
dave@dave:~$]> dave@dave:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1e2de82a-07ef-4d23-bcab-95158031a690 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb590f73-95f1-4fb8-875d-0fc8bec6d0cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dave@dave:~$

> dave@dave:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:326c Samsung Electronics Co., Ltd ML-2010P Mono Laser Printer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
Bus 001 Device 004: ID 2304:021a Pinnacle Systems, Inc. [hex] Dazzle DVC100 Audio Device
**Bus 001 Device 003: ID 059b:0370 Iomega Corp. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave:~$ 

I have read most of the posts on 'fstab' and 'tune2fs', but they do not seem to deal with adding another drive to the list.

Thanks
Dave

---

### Post by BoneKracker on 2010-06-10
Create an fstab entry for it and assign the number 2 to "pass" (like the entry for root has a 1).

---

### Post by Silvernail on 2010-06-11
That look simple enough.

One thing I do not know is, since I have renamed the drive, where to find the UUID?

Will the name do instead of the number?

Thanks for the feedback.
Dave

---

### Post by plucky on 2010-06-11
> One thing I do not know is, since I have renamed the drive, where to find the UUID?

With the drive attached ```
sudo blkid -c /dev/null
``` will give you the UUID for the partition.

Good Luck

---

### Post by BoneKracker on 2010-06-11
> **Silvernail said:**
> That look simple enough.

One thing I do not know is, since I have renamed the drive, where to find the UUID?

Will the name do instead of the number?

Thanks for the feedback.
Dave

From your own post, Dave: :p
> 
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).

Use of device names in fstab (e.g. /dev/sda6") has, over the past couple of years, become deprecated in favor of entries of style "UUID=<uuid>" or style "LABEL=<label>" (refer to MOUNT(8)).  Theoretically, this obviates some of the need for some persistent device-naming rules (i.e., in udev) and is thought to be more appropriate, in a desktop system where external devices are hotplugged willy-nilly onto various controllers and buses, than relying on devices names (because device naming heuristics tend to be based on bus and controller).  In other words, you don't want your external drive to be /dev/sdb on day and /dev/sdd the next.

UUIDs are assigned automatically when you create a filesystem, but if you're going to the trouble of assigning a LABEL to your filesystems, you might want to use that in fstab instead.  If you'd prefer to create a LABEL but you forgot to make one when you set it up, you can add one to an existing filesystem using gparted or with filesystem-specific command-line tools (e.g. for the ext[2,3,4] filesystems, you can do it with 'tune2fs -L <new label> <device name>'.

---

