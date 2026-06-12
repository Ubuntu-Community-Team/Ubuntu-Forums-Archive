---
title: "Unable to boot into ubuntu.."
date: 2011-03-28
forum: General Help
---

### Post by karthick87 on 2011-03-28
Unable to boot into ubuntu..My results of boot_info_script is below...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,804,095   204,597,248   7 HPFS/NTFS
/dev/sda3         204,804,096   409,602,047   204,797,952   7 HPFS/NTFS
/dev/sda4         409,604,094   625,141,759   215,537,666   5 Extended
/dev/sda5         409,604,096   616,292,351   206,688,256  83 Linux
/dev/sda6         616,294,400   625,141,759     8,847,360  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     7,855,784     7,855,722   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5A4AC1744AC14E07                       ntfs       System Reserved               
/dev/sda2        2EE2D09FE2D06C99                       ntfs                                     
/dev/sda3        60FE3A74FE3A4298                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7a484528-b635-438d-8918-365c61ddd4c0   ext4                                     
/dev/sda6        9c89671c-af14-496c-a7db-fcf04cf67cc4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3962E2727E4D53EC                       ntfs       Datas                         
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Datas             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7a484528-b635-438d-8918-365c61ddd4c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9c89671c-af14-496c-a7db-fcf04cf67cc4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 252.8GB: boot/grub/core.img
 252.8GB: boot/initrd.img-2.6.32-21-generic
 252.8GB: boot/vmlinuz-2.6.32-21-generic
 227.0GB: grub/core.img
 252.8GB: initrd.img
 252.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by Rubi1200 on 2011-03-28
Windows is installed in the MBR. You need to put GRUB there so you can dual-boot.

From the LiveCD:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Back in Ubuntu:

```
sudo update-grub
```

---

### Post by karthick87 on 2011-03-29
Now i am not able to boot both os..Now I get a black screen with grub prompt screen..

---

### Post by oldfred on 2011-03-29
Do you get grub menu or just a grub> command?

The normal two line reinstall sometimes does not work can you have to do the full chroot reinstall.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by karthick87 on 2011-03-29
I just get  grub>

---

### Post by Rubi1200 on 2011-03-29
Try what oldfred suggested and do a full reinstall using the chroot method.

---

### Post by karthick87 on 2011-03-30
I did the full chroot installation.. Still the problem continues..

---

### Post by Rubi1200 on 2011-03-30
Is this a laptop or a desktop PC? How old is it?

Check in BIOS if it can "see" the whole drive or just up to 137GB. If there is an option to enable large disk, do so.

Please run the boot script and post it again so we can see what has changed (if anything).

Thanks.

---

### Post by karthick87 on 2011-03-31
It is a laptop and it is very new..I have again posted the result of the script..

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,804,095   204,597,248   7 HPFS/NTFS
/dev/sda3         204,804,096   409,602,047   204,797,952   7 HPFS/NTFS
/dev/sda4         409,604,094   625,141,759   215,537,666   5 Extended
/dev/sda5         409,604,096   616,292,351   206,688,256  83 Linux
/dev/sda6         616,294,400   625,141,759     8,847,360  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     7,856,126     7,856,064   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5A4AC1744AC14E07                       ntfs       System Reserved               
/dev/sda2        2EE2D09FE2D06C99                       ntfs                                     
/dev/sda3        60FE3A74FE3A4298                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7a484528-b635-438d-8918-365c61ddd4c0   ext4                                     
/dev/sda6        9c89671c-af14-496c-a7db-fcf04cf67cc4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C898-B06D                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/C898-B06D         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda2        /media/2EE2D09FE2D06C99  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/60FE3A74FE3A4298  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/7a484528-b635-438d-8918-365c61ddd4c0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /mnt                     ext4       (rw)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7a484528-b635-438d-8918-365c61ddd4c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9c89671c-af14-496c-a7db-fcf04cf67cc4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 252.8GB: boot/grub/core.img
 252.8GB: boot/initrd.img-2.6.32-21-generic
 252.8GB: boot/vmlinuz-2.6.32-21-generic
 227.0GB: grub/core.img
 252.8GB: initrd.img
 252.8GB: vmlinuz
```

---

### Post by Rubi1200 on 2011-03-31
This is odd. The first script results seemed to indicate all was okay except for GRUB not being in the MBR.

Now, with the new results, it appears GRUB is installed in the MBR but the script is not showing any entries for grub.cfg :confused:

I am going to ask someone else to take a look, so please be patient.

Thanks.

---

### Post by drs305 on 2011-03-31
We don't know where your grub.cfg file went, and we can't be sure other files aren't missing, but you can try to do this from the grub rescue prompt:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod normal
(If that fails try:  insmod (hd0,5)/boot/grub/normal.mod)
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

If it boots, run:
```
sudo update-grub
```

---

### Post by karthick87 on 2011-04-01
I am able to boot now..Thanks a lot :-) But What is hd0?

---

### Post by Rubi1200 on 2011-04-01
hd0 = sda

It is the first drive. So, hd0, 5 = first drive, fifth partition or sda5.

Glad you got things sorted out :-)

---

### Post by karthick87 on 2011-04-02
Thankyou Rubi1200 :)

---

