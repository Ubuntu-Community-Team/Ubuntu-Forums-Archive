---
title: "boot problem"
date: 2010-06-16
forum: General Help
---

### Post by bebifeis on 2010-06-16
I have dual boot windows 7 and ubuntu 10.04, but after installing windows 7, i can no longer boot with ubuntu, I have follow the instructions on how to install/fix grub2 with livecd but after reinstalling grub2, when I reboot i get black screen, where the command starts with "grub>", i dont get it because as stated in the tutorials, it should boot already. thanks!:confused:

---

### Post by farcyde21 on 2010-06-16
I've had that problem before and the resolution to my issue was having an external drive connected via USB.  Try disconnecting any USB wires and rebooting to see if that fixes your problem.  If not, I hope someone else can help you.

---

### Post by oldfred on 2010-06-16
bebifeis Welcome to the forum. It sounds like what you have done should be correct.

Just so we can see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by bebifeis on 2010-06-17
here's the results from boot info.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 480067960 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,740,969   477,740,907   7 HPFS/NTFS
/dev/sda2         477,740,970   625,137,344   147,396,375   5 Extended
/dev/sda5         601,794,963   625,137,344    23,342,382  82 Linux swap / Solaris
/dev/sda6         477,741,096   596,638,034   118,896,939  83 Linux
/dev/sda7         596,638,098   601,794,899     5,156,802  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C5CD0D35CD0A8D2                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5bc6632f-2b14-4048-ac81-fd9d94508c51   swap                                     
/dev/sda6        205e3e30-5736-4688-b69b-3bba60d4da65   ext3                                     
/dev/sda7        8a612463-fd54-44d1-a43b-bc15cb8b552d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 

================================ sda1/boot.ini: ================================

&#65279;[boot loader]
timeout=0
default=c:\grldr.mbr
[operating systems]
C:\grldr.mbr="Grub4Dos"
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.24-27-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro  single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=205e3e30-5736-4688-b69b-3bba60d4da65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8a612463-fd54-44d1-a43b-bc15cb8b552d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 245.7GB: boot/grub/core.img
 245.8GB: boot/grub/menu.lst
 245.7GB: boot/grub/stage2
 245.7GB: boot/initrd.img-2.6.24-27-generic
 245.6GB: boot/initrd.img-2.6.24-27-generic.bak
 245.7GB: boot/initrd.img-2.6.32-21-generic
 245.7GB: boot/vmlinuz-2.6.24-27-generic
 245.7GB: boot/vmlinuz-2.6.32-21-generic
 254.0GB: grub/core.img
 245.7GB: initrd.img
 245.7GB: initrd.img.old
 245.7GB: vmlinuz
 245.7GB: vmlinuz.old
```

---

### Post by oldfred on 2010-06-17
You have grub4dos which I know nothing about. You have installed grub legacy to the Ubuntu partition but also have parts of grub2. Often the two versions of grub do not get along and you need to uninstall one or the other. Was installing old grub a recommendation from Neosmart? 


I prefer Grub2 to any other boot loader and grub legacy as a second choice. Some like the other boot loaders but I know nothing about them and cannot really help fix them.

---

### Post by bebifeis on 2010-06-18
oh i forgot to remove grub4dos and the one neosmart made, both of them didnt work...

here's another result from boot info

```
                Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info Summary:  ==============================

 => Windows is installed in the MBR of /dev/sda

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying  to 
                       chain load sector #477741096 on boot drive #1
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6:  _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6  and 
                       looks at sector 480067960 of the same hard drive  for 
                       the stage2 file. A stage2 file is at this  location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,740,969   477,740,907   7 HPFS/NTFS
/dev/sda2         477,740,970   625,137,344   147,396,375   5 Extended
/dev/sda5         601,794,963   625,137,344    23,342,382  82 Linux swap  / Solaris
/dev/sda6         477,741,096   596,638,034   118,896,939  83 Linux
/dev/sda7         596,638,098   601,794,899     5,156,802  82 Linux swap  / Solaris


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE        LABEL                         

/dev/loop0                                               squashfs                                 
/dev/sda1        5C5CD0D35CD0A8D2                        ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5bc6632f-2b14-4048-ac81-fd9d94508c51    swap                                     
/dev/sda6        205e3e30-5736-4688-b69b-3bba60d4da65    ext3                                     
/dev/sda7        8a612463-fd54-44d1-a43b-bc15cb8b552d    swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/menu.lst:  ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from  0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default  entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the  default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive  editing
# control (menu entry editor and command-line)  and entries protected by  the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with  the
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
## update-grub will ignore non-xen kernels when running in domU and vice  versa
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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-21-generic  root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-21-generic  root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.24-27-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic  root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic  root=UUID=205e3e30-5736-4688-b69b-3bba60d4da65 ro  single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the  Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux  OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=205e3e30-5736-4688-b69b-3bba60d4da65 /               ext3     relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8a612463-fd54-44d1-a43b-bc15cb8b552d none            swap     sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8  0       0

=================== sda6: Location of files loaded by Grub:  ===================


 245.7GB: boot/grub/core.img
 245.8GB: boot/grub/menu.lst
 245.7GB: boot/grub/stage2
 245.7GB: boot/initrd.img-2.6.24-27-generic
 245.6GB: boot/initrd.img-2.6.24-27-generic.bak
 245.7GB: boot/initrd.img-2.6.32-21-generic
 245.7GB: boot/vmlinuz-2.6.24-27-generic
 245.7GB: boot/vmlinuz-2.6.32-21-generic
 254.0GB: grub/core.img
 245.7GB: initrd.img
 245.7GB: initrd.img.old
 245.7GB: vmlinuz
 245.7GB: vmlinuz.old

```

---

### Post by oldfred on 2010-06-18
If you want to boot with grub or grub2 you have to install grub to the MBR. Not sure what Neo has done to windows boot sector, it is not a standard windows but may work.

Sometimes old grub interfers with grub2 and you have to totally uninstall both and reinstall one. But just try installing grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

