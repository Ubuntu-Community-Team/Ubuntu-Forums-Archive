---
title: "How to automount a drive permanently?"
date: 2011-04-23
forum: General Help
---

### Post by karthick87 on 2011-04-23
I would like to mount a (ext4) drive permanently.I don like to use any additional packages to automount. Can anyone say me the manual way of entering the partition information into the fstab entry?

[COLOR=Red]Output: fdisk -l[/COLOR]

```
karthick@karthick:~$ sudo fdisk -l
[sudo] password for karthick: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28219744

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              61       30395   243650561    5  Extended
/dev/sda5              61         124      498688   82  Linux swap / Solaris
/dev/sda6             124         186      498688   82  Linux swap / Solaris
/dev/sda7             186       15484   122880000   83  Linux
/dev/sda8           15484       30395   119770112   83  Linux
```

[COLOR=Red]Output: fstab[/COLOR]

```
karthick@karthick:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4bbfe615-f899-4048-97fc-d376e126bb8a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a4d87872-3791-48d6-aec5-1971e02c65fa /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=19e0a91f-91bd-4026-8f72-1fd2de5952a4 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=12dc4732-2c08-4389-a933-2401ceedbc56 none            swap    sw              0       0
```

---

### Post by satman-ga on 2011-04-23
Add the following to /etc/fstab
/dev/*sda8* */media/disk2* ext4 *user*,auto 0 0

All parts in italics are based on your need and preference. The second part, represented by '/media/disk2' here, is a directory that must already exist at mount time.

Additionally, if you want to mount the partition immediately after editing fstab you can run

sudo mount -a

---

### Post by oldfred on 2011-04-23
satman-ga has it correct.

Some links to understand fstab and mounting.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I consider it essential to run the mount -a as if you have editing errors you may not be able to reboot. If the mount -a returns with no errors it has run and remounted with your changes.

---

### Post by karthick87 on 2011-04-24
Thank you satman-ga and oldfred :)

---

