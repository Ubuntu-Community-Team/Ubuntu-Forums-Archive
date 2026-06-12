---
title: "Yet another mbr problem"
date: 2010-12-01
forum: General Help
---

### Post by sirusgr on 2010-12-01
after an update which got me togrub rescue command and trying some several guides with live ubuntu and didnt manage to work it out , my windows mentality led to a complete deletion of the partiotions and a clean install of ubuntu , but this time i get the grub command prompt every time i open my pc, Any help would be really appreciated.
  ```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       194,559       192,512  83 Linux
/dev/sda2             196,606    39,256,063    39,059,458   5 Extended
/dev/sda5             196,608    39,256,063    39,059,456  83 Linux
/dev/sda3          39,256,064    43,161,599     3,905,536  82 Linux swap / Solaris
/dev/sda4          43,161,600    72,458,239    29,296,640  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a958ab6e-0ce7-407a-999f-15f96fd3d16a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        d0634cb9-4d9b-4c02-a7c4-6024849e7707   swap                                     
/dev/sda4        5470d042-f61d-492e-befe-8eaa490ad97f   ext4                                     
/dev/sda5        035dd59f-de12-4dcd-af61-546e3d8ec513   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a958ab6e-0ce7-407a-999f-15f96fd3d16a /boot           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=5470d042-f61d-492e-befe-8eaa490ad97f /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=d0634cb9-4d9b-4c02-a7c4-6024849e7707 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by dino99 on 2010-12-01
you need to boot on a BOOTABLE partition ( when you have formatted /, you miss to make it bootable)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sirusgr on 2010-12-01
> **dino99 said:**
> you need to boot on a BOOTABLE partition ( when you have formatted /, you miss to make it bootable)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

so i need to reinstall ubuntu? or i can make it bootable from gparted partition editor for example? go to flags menu and mark boot? would that work?

---

