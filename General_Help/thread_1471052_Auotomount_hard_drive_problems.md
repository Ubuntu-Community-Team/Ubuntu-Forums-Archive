---
title: "Auotomount hard drive problems"
date: 2010-05-03
forum: General Help
---

### Post by JdeP on 2010-05-03
Hi,
Dropbox will not start properly because my Lucid installation is on a SS HD (/dev/sdc) but my data, including my Dropbox folder is on an internal NTFS-formatted HD (/dev/sda), and I also have another internal HD for backups (/dev/sdb).

I'm a relative newbie. For some reason I can get the backups HD to auto-mount on startup, but not the data HD. My fstab file looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdc1 during installation
UUID=dccafe9a-c150-4f1b-b73f-97eaf3239266  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sdc5 during installation
UUID=8bbe754f-48fd-425b-821a-27e613236632  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sda1     ntfs  defaults                  0  0 

If anyone can give a clear, simple, guide to how to fix this, I'd be very grateful!
Thanks in advance.

---

### Post by dino99 on 2010-05-03
check with usbmount and mountmanager installed, set prefs into MountManager for devices and partitions

---

### Post by klemes on 2010-05-03
What exactly partition in /dev/sda you want to mount?
Better give us the complete 'sudo fdisk -l' command output.:popcorn:

EDIT: or even better [http://ubuntuforums.org/showpost.php?p=9226452&postcount=2](http://ubuntuforums.org/showpost.php?p=9226452&postcount=2) :)

---

### Post by JdeP on 2010-05-03
There is only one partition on /dev/sda
Here is the output of sudo fdisk -l :

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a04c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3727    29931520   83  Linux
/dev/sdc2            3727        3893     1332225    5  Extended
/dev/sdc5            3727        3893     1332224   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS


Thanks for your help!

---

