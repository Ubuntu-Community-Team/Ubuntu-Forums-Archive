---
title: "&quot;GRUB repair&quot; mode"
date: 2010-08-21
forum: General Help
---

### Post by Tosho on 2010-08-21
Hi there, 
I had Windows 7 installation and after that I install Ubuntu 10.04 on an extended partition, Everything was running quite good with the GRUB and both OS's but last night I Shrink one partition so I can have another one (smaller) and I did this in Windows 7. After restart there was an error from Grub.
I'm going to upload e RESULTS.txt from Boot Info Script. Please give me any idea how to fix that and which partition I have to set as Active and Bootable.
thanx

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /GRLDR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 959. But according to the info from fdisk, 
                       sda8 starts at sector 913442816.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   135,040,392   134,833,545   7 HPFS/NTFS
/dev/sda3         135,058,516   976,766,975   841,708,460   f W95 Ext d (LBA)
/dev/sda5         135,058,518   153,501,074    18,442,557  82 Linux swap / Solaris
/dev/sda6    *    153,501,138   280,478,834   126,977,697  83 Linux
/dev/sda7         280,478,898   913,441,856   632,962,959   7 HPFS/NTFS
/dev/sda8         913,442,816   976,766,975    63,324,160   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5A705C57705C3BC7                       ntfs       System Reserved               
/dev/sda2        FA62650E6264D0C5                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5                                               swap                                     
/dev/sda6        9e010885-8709-473e-b0c7-047a57f6d47b   ext4       Ubuntu                        
/dev/sda7        F622FFED22FFB12B                       ntfs       Storage                       
/dev/sda8        CEA42473A4246067                       ntfs       Work                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

# GRUB2 configuration file '/boot/grub/grub.cfg'.
# generated by 'grub2config'.  Sat 21 Aug 2010 08:52:59 AM UTC
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.3625'.  You can restore it like this.
# dd if=mbr.sda.3625 of=/dev/sda bs=512 count=1
#
# Start GRUB2 global section
#set timeout=30
set menu_color_normal=light-gray/blue
set menu_color_highlight=black/light-gray
# End GRUB2 global section
# Other bootable partition config begins
  menuentry "Windows on (/dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
  }
# Other bootable partition config ends
# Other bootable partition config begins
  menuentry "Windows on (/dev/sda2)" {
    set root=(hd0,2)
    chainloader +1
  }
# Other bootable partition config ends
# Linux bootable partition config begins
  menuentry "Linux on (/dev/sda6)" {
    set root=(hd0,6)
    linux /boot/vmlinuz root=/dev/sda6 ro vga=normal 
  }
# Linux bootable partition config ends

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9e010885-8709-473e-b0c7-047a57f6d47b /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 141.0GB: boot/grub/core.img
 141.0GB: boot/grub/grub.cfg
 141.0GB: boot/initrd.img-2.6.32-21-generic
 141.1GB: boot/initrd.img-2.6.32-24-generic
 141.0GB: boot/vmlinuz-2.6.32-21-generic
 141.0GB: boot/vmlinuz-2.6.32-24-generic
 141.1GB: initrd.img
 141.0GB: initrd.img.old
 141.0GB: vmlinuz
 141.0GB: vmlinuz.old

```

---

