---
title: "fstab problem: trying to mount hard drive"
date: 2010-08-18
forum: General Help
---

### Post by kanukatchit on 2010-08-18
installed ubuntu 10.4 on a formatted hard drive IDE. desktop has two other drives , one SATA drive and one SCSI drive. SCSI drive has windows. 

Both windows and ubuntu load fine through GRUB2 etc

I had installed WUBI before on the SATA drive and then i uninstalled it. 

problem is that when i log in to Ubuntu i see on fdisk 

SATA  /dev/sda  (this had WUBI) 
IDE   /dev/sdb  
           sdb1 (this has linux)
           sdb2  extended
           sdb5  SWAP
SCSI  /dev/sdd 

but i cannot access the SATA drive /dev/sda 
i tried mounting the drive but i get an error saying this is mounted as
/dev/sdb5 

how do i mount the SATA drive to get access to the drive ? i messed around with this drive when i was using WUBI. i.e. tried to mount it to recover grub but never got it working. Now somehow it seems that this old mounted drive is messing with my current Ubuntu install.
please suggest how to recover my fstab is shown below
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  nodev,noexec,nosuid  0  0  
/dev/sda1  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
/dev/sdb1  /media/sdb1  ext4  defaults             0  0  
/dev/sdc2  /media/sdc2  vfat  defaults             0  0  
/dev/sdd1  /media/sdd1  ntfs  defaults             0  0  
/dev/sdb5  /media/sdb5  swap  defaults             0  0

--------------------------------------------------------------------------

changed the connect sequence in BIOS and mounted the volume using 
sudo mount /dev/sdb1 /media/sdb1

---

### Post by mikewhatever on 2010-08-18
According to fstab, sda1 is your root partition. That's where your Ubuntu installation is, and it should be mounted when Ubuntu is running. Are there more partitions on sda?

---

