---
title: "grub error 17"
date: 2010-05-03
forum: General Help
---

### Post by jtmedin on 2010-05-03
Had 3 partitions on a hard disk. Booted vista & deleted the windows 7 partition & then expanded the vista partition into the windows 7 partition. Vista kept working but when i rebooted grub starts to load & gets an error 17. How do i recover? TIA 

Previously grub would come up & give me the choice of ubuntu or vista. If i selected vista i got the choice of vista or windows 7.

---

### Post by oldfred on 2010-05-03
You must have had Vista installed first. Windows combines boot files into the partition with the boot flag (active partition). If you delete the wrong one windows does not boot and needs repair.

You may have renumbered partitions and are not using UUIDs in grub or fstab. to see everything related to booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by jtmedin on 2010-05-04
Here is results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 428018348 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 510695007 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   143,364,059   143,363,997   7 HPFS/NTFS
/dev/sda2         143,364,060   348,152,054   204,787,995   7 HPFS/NTFS
/dev/sda3         425,995,605   625,137,344   199,141,740   5 Extended
/dev/sda5         425,995,668   507,911,039    81,915,372  83 Linux
/dev/sda6         507,911,103   608,253,029   100,341,927  83 Linux
/dev/sda7         608,253,093   616,944,194     8,691,102  82 Linux swap / Solaris
/dev/sda8         616,944,258   625,137,344     8,193,087  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        54ACF470ACF44DCC                       ntfs       local Disk XP                 
/dev/sda2        E4B819BFB8199162                       ntfs       Local Disk VISTA              
/dev/sda5        42159244-b328-43bf-8329-9f399b1e7ad9   ext3                                     
/dev/sda6        997ebc17-32dc-4b27-a3e1-d6fed75c8e87   ext3                                     
/dev/sda7        99f55dc1-d65c-488d-adf2-e9a22d07c394   swap                                     
/dev/sda8        6d94565a-d6a2-4a71-b272-89d8d1426819   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ted)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=0

[operating systems]


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=42159244-b328-43bf-8329-9f399b1e7ad9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=42159244-b328-43bf-8329-9f399b1e7ad9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		42159244-b328-43bf-8329-9f399b1e7ad9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=42159244-b328-43bf-8329-9f399b1e7ad9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		42159244-b328-43bf-8329-9f399b1e7ad9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=42159244-b328-43bf-8329-9f399b1e7ad9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		42159244-b328-43bf-8329-9f399b1e7ad9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=42159244-b328-43bf-8329-9f399b1e7ad9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6d94565a-d6a2-4a71-b272-89d8d1426819 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 219.1GB: boot/grub/menu.lst
 219.1GB: boot/grub/stage2
 219.1GB: boot/initrd.img-2.6.28-11-generic
 219.1GB: boot/vmlinuz-2.6.28-11-generic
 219.1GB: initrd.img
 219.1GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved
#default		10

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=997ebc17-32dc-4b27-a3e1-d6fed75c8e87

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, memtest86+
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=669bdfec-2675-40f7-8bb2-21d32e80d570 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 260.5GB: boot/grub/menu.lst
 261.4GB: boot/grub/stage2
 261.4GB: boot/initrd.img-2.6.31-14-generic
 261.5GB: boot/initrd.img-2.6.31-15-generic
 261.6GB: boot/initrd.img-2.6.31-16-generic
 261.2GB: boot/initrd.img-2.6.31-17-generic
 261.9GB: boot/initrd.img-2.6.31-19-generic
 261.4GB: boot/initrd.img-2.6.31-20-generic
 261.6GB: boot/vmlinuz-2.6.31-14-generic
 261.5GB: boot/vmlinuz-2.6.31-15-generic
 260.8GB: boot/vmlinuz-2.6.31-16-generic
 261.2GB: boot/vmlinuz-2.6.31-17-generic
 261.8GB: boot/vmlinuz-2.6.31-19-generic
 262.5GB: boot/vmlinuz-2.6.31-20-generic
 261.4GB: initrd.img
 261.9GB: initrd.img.old
 262.5GB: vmlinuz
 261.8GB: vmlinuz.old
```

---

### Post by oldfred on 2010-05-04
Grub in the MBR wants to boot from partition 7 which is one of your swap partitions.

You have 9.04 and 9.10 in separate partitions sda5 & sda6.

So you need to reinstall grub to boot from sda6 if you want 9.10 to boot. Old grub is not as good at finding other systems as grub2 but should find your 9.04 and let you boot either and windows.

Be sure to follow the directions for grub legacy not grub2. Mixed installs cause even more problems:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I thought windows had issues with  /boot and /Boot as windows does not know the difference with capital and small letters. Windows normally combines boot of two installs to allow you to choose either.

---

### Post by jtmedin on 2010-05-04
Live booted the ubuntu 9.1 cd & then installed grub. Followed the instructions for 9.04 & boot is now working :). Noticed when i installed grub that grub-pc was removed is that grub2? TIA

---

### Post by oldfred on 2010-05-04
Yes grub-pc is grub2. grub-common seems to be the same for both but has been updated with Lucid.

---

