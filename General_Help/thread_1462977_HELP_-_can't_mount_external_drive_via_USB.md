---
title: "HELP - can't mount external drive via USB"
date: 2010-04-26
forum: General Help
---

### Post by derande on 2010-04-26
running 9.10.
have an external USB seagate hard drive that will not mount on my laptop.

sudo fdisk -l:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ebd8130

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35785   287442981   83  Linux
/dev/sda2           35786       38913    25125660    5  Extended
/dev/sda5           37836       38913     8659003+  82  Linux swap / Solaris
/dev/sda6           35786       37835    16466562   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 888.2 GB, 888183151616 bytes
204 heads, 61 sectors/track, 139403 cylinders
Units = cylinders of 12444 * 512 = 6371328 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1      139403   867363776    7  HPFS/NTFS**

sdb1 is my usb hard drive so fdisk sees it but i cannot get it to mount. 

error:
~$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

anything i'm doing wrong or any idea what's happening?

i can plug this same drive/usb cable onto my 9.10 desktop and it immediately mounts and i can access it but my laptop all of a sudden will not.

:(

---

### Post by klemes on 2010-04-26
sudo mount /dev/sdb1 implies that you have a correct  entry for sdb1 in your /etc/fstab,well do you? 
Better show us your fstab if you are not too sure...

The full command for manual mounting the aformentioned USB drive would be :

```
sudo mkdir /media/sdb1 && **mount -t ntfs /dev/sdb1 /media/sdb1**
```

---

### Post by derande on 2010-04-26
when i:

~$ sudo mkdir /media/sdb1 && mount -t ntfs /dev/sdb1 /media/sdb1[sudo] password for derande: 
mkdir: cannot create directory `/media/sdb1': File exists

current fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                   0  0  
# / was on /dev/sda1 during installation
UUID=2cd2cdb1-7d44-435f-8962-fe152de9ce2e  /              ext4         errors=remount-ro                          0  1  
# swap was on /dev/sda5 during installation
UUID=1adca7c1-1231-44c6-96c7-22d3342ab4f0  none           swap         sw                                         0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                      0  0  
/dev/sdc1                                  /media/sdc1    vfat         users,user                                 0  0  
/dev/sda6                                  /media/sda6    ext4         noauto                                     0  0  
/dev/sdb1                                  /media/sdb1    vfat         uid=root,owner,group,gid=users,users,user  0  0  


sdb1 looks correct, yes?

---

### Post by rnerwein on 2010-04-26
hi
may be i am wrong, but i have never seen a line like yours.
/dev/sdb1                                  /media/sdb1[COLOR=Blue]    vfat[/COLOR][COLOR=Red]          uid=root,owner,group,gid=users,users,user[/COLOR]  0  0  

try:
[COLOR=Lime]/dev/sdb1                                  /media/sdb1 ntfs defaults,auto,umask=000   0 0[/COLOR]
in /etc/fstab.

by the side - your filesystem is ntfs.
ciao

---

### Post by derande on 2010-04-26
mount -t ntfs /dev/sdb1 /media/sdb1 will now mount the drive.

how can i configure to automount when i plug in directly from usb? is that going to be an additional entry into fstab?

---

