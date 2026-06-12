---
title: "Boot Issues"
date: 2010-11-26
forum: General Help
---

### Post by guy_ho on 2010-11-26
Hello,

I'm having trouble booting up my machine with 10.04 on it. I've found that it increases the chances of booting properly if I unplug the keyboard, although this morning I still had to turn the power on twice to get past the purple logo screen. Usually, rather than the 5 white dots turning red when booting up, the dots all turn red, and then nothing happens at all. 

Initially, after a few attempts, I noticed that the 'num lock' light on the keyboard wasn't lit, so that's why I tried booting up with the keyboard unplugged. Because the keyboard didn't seem to be working, I couldn't get into bios, to see if I could boot from an installation CD, if that was the problem.

Please feel free to ask me questions to find out more info about my machine, so I can find out and pass it on.

Thanks,


Guy

---

### Post by sikander3786 on 2010-11-26
Seems like a hardware specific problem.

Did you try with some other keyboard?

Is this a laptop or desktop? Please list some hardware specs.

---

### Post by Penguin=) on 2010-11-26
Seems like something you may have installed, that could of corrupted your system.

Have you downloaded anything suspicious in the last week?

---

### Post by guy_ho on 2010-11-26
I don't have another keyboard, but I'll try to get hold of another to test the possibility that this might be the root of the problem.

Here are some specs about the machine -

- desktop!
- Intell Q6600 Quad core (2.9gb)
- nvidia geforce graphics card

Let me know what else I need to find out, and if it involves any digging, it would be really helpful if you could suggest how to find it out. I've had the machine 2 years, and I don't tend to do much on it besides use Firefox, listen to music, & watch videos.

---

### Post by Hippytaff on 2010-11-26
Might it be an Nvidia driver issue - has it booted ok up until now?

---

### Post by guy_ho on 2010-11-26
A previous version I had of ubuntu really didn't seem to get on well with nvidia. I've had very few problems over the last couple of years with boot issues - last year I lost a hard drive, but since I got the machine in 2008, it's all been pretty good really. 

I've got a 10.10 installation CD, so I guess if I really wanted to see if it was a problem with my current installation, I could give that a go to rule it out.

Thanks again for taking the time, y'all.

---

### Post by Hippytaff on 2010-11-26
If you can boot from live cd then it's not graphics driver issues. it's always worth posting the results.txt from this script when haveing boot isses too. Just to rules stuff out and point to any boot problems
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by guy_ho on 2010-11-26
Alright, here we go -

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   958,919,849   958,919,787  83 Linux
/dev/sda2         958,919,850   976,768,064    17,848,215   5 Extended
/dev/sda5         958,919,913   976,768,064    17,848,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        35b44990-36bb-4280-a805-de8ff75a2f7e   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d55f6229-d594-4ef1-8044-dacf500a0dcf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6853-5BA9                              vfat       LaCie                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc         30DE-4484                              vfat       SANSA M350                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/LaCie_            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc         /media/SANSA M350        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=35b44990-36bb-4280-a805-de8ff75a2f7e

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		35b44990-36bb-4280-a805-de8ff75a2f7e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=35b44990-36bb-4280-a805-de8ff75a2f7e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d55f6229-d594-4ef1-8044-dacf500a0dcf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 181.0GB: boot/grub/menu.lst
 126.0GB: boot/grub/stage2
 133.8GB: boot/initrd.img-2.6.32-21-generic
 160.1GB: boot/initrd.img-2.6.32-22-generic
 133.9GB: boot/initrd.img-2.6.32-23-generic
 181.9GB: boot/initrd.img-2.6.32-24-generic
 269.4GB: boot/initrd.img-2.6.32-25-generic
 335.7GB: boot/initrd.img-2.6.32-26-generic
 126.1GB: boot/vmlinuz-2.6.32-21-generic
 170.9GB: boot/vmlinuz-2.6.32-22-generic
 184.6GB: boot/vmlinuz-2.6.32-23-generic
 181.2GB: boot/vmlinuz-2.6.32-24-generic
 214.7GB: boot/vmlinuz-2.6.32-25-generic
 335.6GB: boot/vmlinuz-2.6.32-26-generic
 335.7GB: initrd.img
 269.4GB: initrd.img.old
 335.6GB: vmlinuz
 214.7GB: vmlinuz.old

---

### Post by Hippytaff on 2010-11-26
```

Boot Info Script 0.55 dated February 15th, 2010 
 
============================= Boot Info Summary: ==============================
 
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> No boot loader is installed in the MBR of /dev/sdb
 
sda1: __________________________________________________ _______________________
 
File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/menu.lst /etc/fstab
 
sda2: __________________________________________________ _______________________
 
File system: Extended Partition
Boot sector type: -
Boot sector info: 
 
sda5: __________________________________________________ _______________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
sdb1: __________________________________________________ _______________________
 
File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: According to the info in the boot sector, sdb1 starts 
at sector 0. But according to the info from fdisk, 
sdb1 starts at sector 63.
Operating System: 
Boot files/dirs: 
 
sdc: __________________________________________________ _______________________
 
File system: vfat
Boot sector type: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ __________________________________________________ ___
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start End Size Id System
 
/dev/sda1 * 63 958,919,849 958,919,787 83 Linux
/dev/sda2 958,919,850 976,768,064 17,848,215 5 Extended
/dev/sda5 958,919,913 976,768,064 17,848,152 82 Linux swap / Solaris
 
 
Drive: sdb ___________________ __________________________________________________ ___
 
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start End Size Id System
 
/dev/sdb1 63 625,137,344 625,137,282 b W95 FAT32
 
 
blkid -c /dev/null: __________________________________________________ __________
 
Device UUID TYPE LABEL 
 
/dev/sda1 35b44990-36bb-4280-a805-de8ff75a2f7e ext3 
/dev/sda2: PTTYPE="dos" 
/dev/sda5 d55f6229-d594-4ef1-8044-dacf500a0dcf swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 6853-5BA9 vfat LaCie 
/dev/sdb: PTTYPE="dos" 
/dev/sdc 30DE-4484 vfat SANSA M350 
 
============================ "mount | grep ^/dev output: ===========================
 
Device Mount_Point Type Options
 
/dev/sda1 / ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 /media/LaCie_ vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000, shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc /media/SANSA M350 vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000, shortname=mixed,dmask=0077,utf8=1,flush)
 
 
=========================== sda1/boot/grub/menu.lst: ===========================
 
# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
# grub-install(:cool:, grub-floppy(:cool:,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
 
# Pretty colours
#color cyan/blue white/blue
 
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
 
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=35b44990-36bb-4280-a805-de8ff75a2f7e
 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
 
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
 
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
 
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
 
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
 
## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect
 
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
 
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
 
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
 
## ## End Default Options ##
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-26-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-26-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-26-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-26-generic
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-25-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-25-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-25-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-25-generic
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-24-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-24-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-24-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-24-generic
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-23-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-23-generic
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-22-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-22-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-22-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-22-generic
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro quiet splash 
initrd /boot/initrd.img-2.6.32-21-generic
quiet
 
title Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=35b44990-36bb-4280-a805-de8ff75a2f7e ro single
initrd /boot/initrd.img-2.6.32-21-generic
 
title Ubuntu 10.04.1 LTS, memtest86+
uuid 35b44990-36bb-4280-a805-de8ff75a2f7e
kernel /boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
=============================== sda1/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=35b44990-36bb-4280-a805-de8ff75a2f7e / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=d55f6229-d594-4ef1-8044-dacf500a0dcf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
 
=================== sda1: Location of files loaded by Grub: ===================
 
 
181.0GB: boot/grub/menu.lst
126.0GB: boot/grub/stage2
133.8GB: boot/initrd.img-2.6.32-21-generic
160.1GB: boot/initrd.img-2.6.32-22-generic
133.9GB: boot/initrd.img-2.6.32-23-generic
181.9GB: boot/initrd.img-2.6.32-24-generic
269.4GB: boot/initrd.img-2.6.32-25-generic
335.7GB: boot/initrd.img-2.6.32-26-generic
126.1GB: boot/vmlinuz-2.6.32-21-generic
170.9GB: boot/vmlinuz-2.6.32-22-generic
184.6GB: boot/vmlinuz-2.6.32-23-generic
181.2GB: boot/vmlinuz-2.6.32-24-generic
214.7GB: boot/vmlinuz-2.6.32-25-generic
335.6GB: boot/vmlinuz-2.6.32-26-generic
335.7GB: initrd.img
269.4GB: initrd.img.old
335.6GB: vmlinuz
214.7GB: vmlinuz.old

```
just putting in code tags - easier to read :-)
 
Looks fine to me (you've got loads of old kernels though don't think this will be the problem, just saying :-) )
 
Must be something else...hmmm
 
Sikander got it right from the outset it seems :-)
 
what does
```

dmesg | tail

```
return after boot, and have you looked at the boot logs?
```

cat /var/boot/boot.log

```
I think thats waht the boot log is called (not on my buntu box) if not cd to the log directory and do 
```

ls -a | grep -i boot

```
to find the name.

---

### Post by guy_ho on 2010-11-26
Nice one, thanks. I thought that's what those might be for. I've just updated my kernel on Update Manager, thinking I could re-boot to see what happens.

---

### Post by sikander3786 on 2010-11-26
There seems to be just a minor problem that Grub Legacy is installed instead of Grub2 which comes by default with a clean install of 10.04. I think you just upgraded to 10.04 from some previous version?

> I couldn't get into bios, to see if I could boot from an installation CD, if that was the problem.

I can't get the whole of this statement. Were you unable to get into the Bios just because the keyboard was not plugged in?

Can you clear it up a bit for now. What happens when you power on your PC? You see the Bios screen? You are able to get into the Bios screen? Does keyboard work in Bios? If Ubuntu boots initially and then hangs on the logo screen, can you press Esc and produce those errors in your post?

Thanks.

---

### Post by guy_ho on 2010-11-26
You're right, I did an upgrade, not a fresh install.

What I meant was that I was unable to get into bios because the keyboard wasn't 'seen' by the machine - that is, the 'num lock' light wasn't on, and hitting delete or escape didn't do anything. The machine booted fine when I disconnected the keyboard, but when it was connected, it wouldn't get past the purple screen.

When it was hanging on the purple screen, I couldn't hit anything on the keyboard to change it.

On another note - should I use Synaptic to get rid of the old versions of the kernel? Would it make much difference?

---

### Post by sikander3786 on 2010-11-26
> What I meant was that I was unable to get into bios because the keyboard wasn't 'seen' by the machine - that is, the 'num lock' light wasn't on, and hitting delete or escape didn't do anything. 

In that case, definitely a hardware issue. If it is PS/2 keyboard, try a USB one or vice versa.

> On another note - should I use Synaptic to get rid of the old versions of the kernel? Would it make much difference?

You can do that. But if you don't get upset with a lot of entries in Grub menu or don't care about the disk space they are using, you can leave as they are.

---

### Post by guy_ho on 2010-11-26
Ok, will look into the USB keyboard option.

Thanks!

---

