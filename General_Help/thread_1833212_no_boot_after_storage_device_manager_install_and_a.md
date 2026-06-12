---
title: "no boot after storage device manager install and action"
date: 2011-08-25
forum: General Help
---

### Post by bth73 on 2011-08-25
Installed storage device manager and activated sdb1 1.5tb hard drive to mount at boot up as per:( [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm) ) , Now no boot up. crash report said something about not finding a monitor? Driver for nvidia (173) activated but not in use. Don't know how to enable it either.
 help please?  Thank you.
Directions followed:
 Install Storage Device Manager if it has not been added.
        Go to Applications (or Main Menu) > Ubuntu Software Center.
        Enter pysdm in the Search Box.
        Select Storage Device Manager, click the "Install" button.
    Go to System > Administration > Storage Device Manager.
    Extend the list of sda and select the sda you want to auto mount, click 'OK' to configure.
    Click the "Assistant" button.
    Uncheck "Mount file system in read only mode" and keep "The file system is mounted at boot time" checked.
    Click the "Mount", "Apply" then "Close" button, and restart the system.

In case you wish to remove the auto-mount of a certain drive or partition, you can similarly use Storage Device Manager to do the setting.

   If you need to identify disk partitions by label, paste ls /dev/disk/by-label -g in Terminal, or to view partition sizes and file systems, enter sudo fdisk -l. Disk Utility mentioned in "Name or Label a Partition" also gives you a glance of device numbers, partition types, sizes and labels.


 boot.log:

fsck from util-linux-ng 2.17.2

/dev/sdb1: clean, 226351/60989440 files, 5379534/243928320 blocks (check in 5 mounts)

udevd[358]: can not read '/etc/udev/rules.d/z80_user.rules'




mount: /dev/sdb1 already mounted or /media/sdb1 busy

mount: according to mtab, /dev/sdb1 is mounted on /

mountall: mount /media/sdb1 [448] terminated with status 32

mountall: Filesystem could not be mounted: /media/sdb1

init: udev-fallback-graphics main process (857) terminated with status 1


Skipping /media/sdb1 at user request

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

 * Starting AppArmor profiles       [80G 
[74G[ OK ]

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=fd2d9656-eb2d-4a6f-bda5-eca18d37f7a8  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=ea1b86f4-93bf-4916-81df-3f04afe2fd58  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1     ext3  errors=remount-ro         0  0  
Three day old fresh install of 11.04.3. x64. AMD 3800+, gigabyte ga k8ns ultra 939, fx5200 video, 1tb sata1, 1.5tb sata1, 750gb ide, 4g ddr 3200 mem.

---

