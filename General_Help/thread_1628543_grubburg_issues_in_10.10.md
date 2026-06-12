---
title: "grub/burg issues in 10.10"
date: 2010-11-22
forum: General Help
---

### Post by brent0n on 2010-11-22
the only OS on my hdd is 10.10 and it's installed on /dev/sda2/ but i broke the bootloader when trying to install burg(and didn't realize it until i restarted.) i'm using a livecd atm but i've been trying to reinstall grub/reconfigure it for ages and i'm just not having any luck. can anyone help?

---

### Post by dcstar on 2010-11-23
> **brent0n said:**
> the only OS on my hdd is 10.10 and it's installed on /dev/sda2/ but i broke the bootloader when trying to install burg(and didn't realize it until i restarted.) i'm using a livecd atm but i've been trying to reinstall grub/reconfigure it for ages and i'm just not having any luck. can anyone help?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Then once you have a working system:

```
sudo dpkg-reconfigure burg-pc
```

---

### Post by wilee-nilee on 2010-11-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    61,790,207    61,583,360  83 Linux
/dev/sda3          61,790,208   234,440,598   172,650,391   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1EDA666DDA6640DF                       ntfs       System Reserved               
/dev/sda2        e6064f20-f65c-4997-810b-64882f30871e   ext4                                     
/dev/sda3        429E4FE39E4FCDDB                       ntfs       media                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/stage2

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=e6064f20-f65c-4997-810b-64882f30871e /               ext4    errors=remount-ro 0       1

=================== sda2: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/core.img
  11.3GB: boot/grub/stage2
   1.3GB: boot/initrd.img-2.6.35-22-generic
  11.3GB: boot/vmlinuz-2.6.35-22-generic
   1.3GB: initrd.img
  11.3GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-11-23
You have a bit of a borked setup are you backed up so you could just wipe the HD and reinstall.

The link for grub2 in post 2 will not fix this.

---

