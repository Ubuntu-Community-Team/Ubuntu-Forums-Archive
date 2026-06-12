---
title: "Troubleshooting Ubuntu 9.10!"
date: 2011-03-10
forum: General Help
---

### Post by Advice Pro on 2011-03-10
I can't access my usb devices from [i[Computer[/i], yet I can detect them, but they work fine.  I made sure that volumes_visible is checked at gconf-editor > apps > nautilus > desktop.  The output of the commands:

**lsusb**
```
Bus 002 Device 005: ID 05a4:9866 Ortek Technology, Inc. 
Bus 002 Device 004: ID 04d9:1203 Holtek Semiconductor, Inc. MC Industries Keyboard
Bus 002 Device 003: ID 047d:1029 Kensington Mouse*in*a*Box Optical Elite
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**dmesg** is attached and ```
*dmesg | tail*
[code]
[   16.008952] CPU0 attaching NULL sched-domain.
[   16.008957] CPU1 attaching NULL sched-domain.
[   16.020555] CPU0 attaching sched-domain:
[   16.020558]  domain 0: span 0-1 level MC
[   16.020561]   groups: 0 1
[   16.020565] CPU1 attaching sched-domain:
[   16.020566]  domain 0: span 0-1 level MC
[   16.020568]   groups: 1 0
[   22.396513] eth0: no IPv6 routers present
[   73.500036] Clocksource tsc unstable (delta = -117708037 ns)

```
**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=01fc29b5-aca0-4830-80f9-7cf826c46274 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=40d709cd-7845-4e06-ab81-68cdc186bc6a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
**cat /proc/self/mountstats**
```
device rootfs mounted on / with fstype rootfs
device none mounted on /sys with fstype sysfs
device none mounted on /proc with fstype proc
device udev mounted on /dev with fstype tmpfs
device /dev/disk/by-uuid/01fc29b5-aca0-4830-80f9-7cf826c46274 mounted on / with fstype ext4
device none mounted on /sys/kernel/security with fstype securityfs
device none mounted on /sys/fs/fuse/connections with fstype fusectl
device none mounted on /sys/kernel/debug with fstype debugfs
device none mounted on /dev/pts with fstype devpts
device none mounted on /dev/shm with fstype tmpfs
device none mounted on /var/run with fstype tmpfs
device none mounted on /var/lock with fstype tmpfs
device none mounted on /lib/init/rw with fstype tmpfs
device binfmt_misc mounted on /proc/sys/fs/binfmt_misc with fstype binfmt_misc
device gvfs-fuse-daemon mounted on /home/lapiii/.gvfs with fstype fuse.gvfs-fuse-daemon
device /dev/sdd1 mounted on /media/&#804; with fstype vfat

```
**cat /etc/mtab**
```

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/lapiii/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=lapiii 0 0
/dev/sdd1 /media/&#804; vfat ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

```

---

### Post by bapoumba on 2011-03-12
```
8.120378] sd 6:0:0:2: [sdd] Write Protect is on
```
May be ?

---

### Post by Advice Pro on 2011-03-12
How do I do that?  I've searched the internet and haven't found a solution.

---

### Post by bapoumba on 2011-03-12
Oh :)
These lines are from the file you provided. Is your drive write-protected ?

---

### Post by Advice Pro on 2011-03-12
I don't think the HDD iswrite protected as I've written many files to it.How can I check?  Here are 2 commands and teir outputs that might help:
```

sudo fdisk -l
```
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x950ea52a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37831   303877476   83  Linux
/dev/sda2           37832       38913     8691165    5  Extended
/dev/sda5           37832       38913     8691133+  82  Linux swap / Solaris

Disk /dev/sdd: 16.4 GB, 16372989952 bytes
255 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1991    15985152    c  W95 FAT32 (LBA)

```
```

df -h
```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             286G  5.1G  266G   2% /
udev                  1.5G  308K  1.5G   1% /dev
none                  1.5G  188K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdd1              16G  1.9G   14G  13% /media/&#804;

```

---

### Post by bapoumba on 2011-03-13
It is quite strange as your drive is mounted in /media. It should appear in Places > Computer.
Which Ubuntu release are you using ?

---

### Post by Advice Pro on 2011-03-13
9.10

---

### Post by mörgæs on 2011-03-13
Are you sure that it pays to troubleshoot 9.10, having only one month of support left? 

A fresh install of 10.04 or 10.10 might be worth considering.

---

### Post by Advice Pro on 2011-03-13
I might just burn a disc of 10.10, I couldn't succesfully upgrade via Ubuntu Update.  Anyways, I'd still like to change directories to *Places > Computer.*

---

### Post by coweatyou on 2011-03-13
Places->computer isn't a real directory, the file is mounted in /media and then symlinked to places->computer.  If you open a device in computer then view it's property to get it's id, you'll see it's the same id as a device in /media.

---

### Post by Advice Pro on 2011-03-14
The 1st 2 are screen shots are of my *Computer* and */media* File Browser windows.  */media* doesn't show any of the USB devices.  What are shown in the 2nd screen shot are my SD card, DVD drive, and I think a shortcut of the DVD drive.

> **bapoumba said:**
> It is quite strange as your drive is mounted in /media.Should I relocate to another directory and then symlink to *Computer*?

> **coweatyou said:**
> get it's id
I'm not clear on what the I.D. is, so I attached a 3rd screen shot of a window with the *Basic* tab open. The *Permissions* tab reads "The permissions of ... could not be determined".  All the USB device Properties read the same.

---

### Post by Advice Pro on 2011-03-21
I've upgraded and created a new thread: [Ubuntu 10.04!](http://ubuntuforums.org/showthread.php?t=1709568Troubleshooting)

---

