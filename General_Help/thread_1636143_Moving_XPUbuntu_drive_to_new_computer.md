---
title: "Moving XP/Ubuntu drive to new computer"
date: 2010-12-02
forum: General Help
---

### Post by crayZsaaron on 2010-12-02
Alright, I've got a stumper for you guys.  Maybe this would be more appropriate on a Microsoft forum, but I'll try you guys first, because you tend to be quite a bit more intelligent, in general.

My parents used to have an old HP computer with Windows 98 installed.  Then, they bought the retail version of Windows XP and installed that in its place.  They gave the computer to me about four years ago, when I was 13.  I used this computer for a surprisingly long time, eventually installing Ubuntu 9.04 alongside Windows (dual boot), and then set it aside in favor of a series of slightly-newer, yet still generally awful computers.  Recently, I built my first computer, an AMD Phenom II machine (the old computer was an Intel Pentium III).  It has Ubuntu 10.10 installed.  

Today, I opened up that old computer (which was actually the dustiest thing I have ever seen... I'm surprised it ever even booted without overheating) and removed the IDE drive with Windows XP and Ubuntu 9.04 installed.  I installed it in my new computer and booted to the old hard drive.  I fondly looked upon the GRUB operating system selection screen (we had some good times together...), first choosing Ubuntu 9.04 to make sure everything worked correctly.  It did.  I rebooted and chose Windows this time.  The screen went blank except for the words "Starting Up..." in the top left hand corner (I think this is from GRUB, not Windows).  Nothing happened in a 5-minute period.  I tried this multiple times.  Now, I know that these are just about most ridiculous circumstances ever and I probably shouldn't even have a glimmer of hope for this little "experiment".  Even so, I... do.  Do you guys have any suggestions?  If nothing else works, I'm entitled to an $11.99 copy of Windows XP from Dell, so I'll just wipe the hard drive, call for that, and everything will be fine.

Thanks!

-Seth

---

### Post by crayZsaaron on 2010-12-06
Binp!

---

### Post by wilee-nilee on 2010-12-06
A legitimate XP disc is almost impossible to get except through a 3rd party now, like ebay. The manufactures still we give you a OEM set but some probably wont after a while. Get the Dell disc, to start with as a backup, and a tool for repairing as well.

You can try this to see if the bootscript shows anything.
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

9.04 just reached its end of life in October so maybe a fresh install over it with grub2 will pick up the XP and boot it. 
[http://fridge.ubuntu.com/node/2132](http://fridge.ubuntu.com/node/2132)

---

### Post by argedion on 2010-12-06
> I rebooted and chose Windows this time. The screen went blank except for the words "Starting Up..." in the top left hand corner (I think this is from GRUB, not Windows). Nothing happened in a 5-minute period.

The problem is Windows needs to load new drivers for the new computer. Also that copy of the WPL is corrupt in the new system. The activation is not reconizing any of the hardware. You could try to reboot and give it a while and see if anything happens or if it just stays in the dark world of loading up. If it does fail getting the disk from dell may help. Also try booting up in Safe Mode and see if it boots like that. Again Drivers may be a big part of the problem.

---

### Post by wilee-nilee on 2010-12-06
> **argedion said:**
> The problem is Windows needs to load new drivers for the new computer. Also that copy of the WPL is corrupt in the new system. The activation is not reconizing any of the hardware. You could try to reboot and give it a while and see if anything happens or if it just stays in the dark world of loading up. If it does fail getting the disk from dell may help. Also try booting up in Safe Mode and see if it boots like that. Again Drivers may be a big part of the problem.

+1 you can also initiate a chkdsk at startup from the safe mode.

XP can be transfered and still be Activated. Vista and W7 can be fully backed up and reinstalled with a recovery and be active as well. At least W7 has worked this way using its backup program, a full image.

If it was me and you wanted that original snapshot  version XP does have full backup tool, it has to be manually installed from  XP disc in the home version though. This would just be done in the original enclosure to a external HD.

---

### Post by crayZsaaron on 2010-12-07
Thanks for your response!  Here is the results.txt from your boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    66,460,904    66,460,842   7 HPFS/NTFS
/dev/sda2          66,460,905    78,156,224    11,695,320   5 Extended
/dev/sda5          66,460,968    77,545,754    11,084,787  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135    99,619,064     1,959,930   5 Extended
/dev/sdb5          97,659,198    99,619,064     1,959,867  82 Linux swap / Solaris
/dev/sdb3          99,619,065   156,248,189    56,629,125  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DA3040CD3040B275                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c60cf3fa-47d6-492c-a669-d697418cabd2   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        372de761-9577-48be-ba19-c6b2890cb229   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        f7ceb49b-7448-4af1-9a6a-824a3d0bde2e   ext4       Second partition              
/dev/sdb5        232dd58f-45c4-44fc-8ac2-c2ab1e7a6aa9   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sdb3        /media/Second partition  ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
default		0

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
# kopt=root=UUID=c60cf3fa-47d6-492c-a669-d697418cabd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c60cf3fa-47d6-492c-a669-d697418cabd2

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
uuid		c60cf3fa-47d6-492c-a669-d697418cabd2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c60cf3fa-47d6-492c-a669-d697418cabd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c60cf3fa-47d6-492c-a669-d697418cabd2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c60cf3fa-47d6-492c-a669-d697418cabd2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c60cf3fa-47d6-492c-a669-d697418cabd2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
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
UUID=c60cf3fa-47d6-492c-a669-d697418cabd2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c7872682-08ed-4d0b-b617-e85f8289a67a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/menu.lst
  38.5GB: boot/grub/stage2
  39.2GB: boot/initrd.img-2.6.28-11-generic
  35.3GB: boot/vmlinuz-2.6.28-11-generic
  39.2GB: initrd.img
  35.3GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=372de761-9577-48be-ba19-c6b2890cb229

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.31-22-generic
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-22-generic (recovery mode)
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.10, kernel 2.6.28-11-generic
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-11-generic (recovery mode)
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=372de761-9577-48be-ba19-c6b2890cb229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.10, memtest86+
uuid		372de761-9577-48be-ba19-c6b2890cb229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=372de761-9577-48be-ba19-c6b2890cb229 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=232dd58f-45c4-44fc-8ac2-c2ab1e7a6aa9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  48.7GB: boot/grub/menu.lst
  48.4GB: boot/grub/stage2
  48.4GB: boot/initrd.img-2.6.28-11-generic
  48.3GB: boot/initrd.img-2.6.31-22-generic
  48.3GB: boot/initrd.img-2.6.32-25-generic
  48.4GB: boot/initrd.img-2.6.35-22-generic
  23.2GB: boot/initrd.img-2.6.35-23-generic
  48.3GB: boot/vmlinuz-2.6.28-11-generic
  48.3GB: boot/vmlinuz-2.6.31-22-generic
  48.3GB: boot/vmlinuz-2.6.32-25-generic
  48.4GB: boot/vmlinuz-2.6.35-22-generic
  23.2GB: boot/vmlinuz-2.6.35-23-generic
  23.2GB: initrd.img
  48.4GB: initrd.img.old
  23.2GB: vmlinuz
  48.4GB: vmlinuz.old
```

---

### Post by 0949er on 2010-12-07
windows doesnt know what to do with all the new hardware, thats why it is hanging.

I assume that the linux distro works because it was build for i386 or whatever, and your current hardware is comparable with that out of the box.

---

### Post by crayZsaaron on 2010-12-07
Rough.  I do have access to all files on my XP partition, for example, system32 files.  But I don't know if that will help me.  Anyone?  Today, I let it hang there for a good 20 minutes; it's definitely not doing anything.  And I can't boot into safe mode (I tried mashing F8 after GRUB).  So I'm thinking there's probably no hope, right?

---

### Post by Mark Phelps on 2010-12-08
Well ... maybe ... if you're willing to start over.

There has been SOME success moving XP to a different machine if, before the move, as many of the hardware-specific driver are removed as possible, especially, the video driver.

This would mean you would have to remove the drivers from Device Manager, then power-down the PC and remove all add-in cards, and then reboot with only generic drivers in place.

There's no guarantee (there never IS with MS Windows), but that might reduce your driver set enough that it will boot on the new PC.

---

### Post by mastablasta on 2010-12-08
> **Mark Phelps said:**
> Well ... maybe ... if you're willing to start over.
 
There has been SOME success moving XP to a different machine if, before the move, as many of the hardware-specific driver are removed as possible, especially, the video driver.
 
This would mean you would have to remove the drivers from Device Manager, then power-down the PC and remove all add-in cards, and then reboot with only generic drivers in place.
 
There's no guarantee (there never IS with MS Windows), but that might reduce your driver set enough that it will boot on the new PC.
 
it worked for me.
 
you need to uninstall all drivers (motherboard/sound, graphics...), then boot into safe mode and then run it off.
 
then when you move to new computer you need boot to safe mode first and then normal boot (i can't remember this part exactly).
 
and then install all drivers. i did it with winXp when a motherboard died prematurely on another computer. so i moved mine there, and then bought a new one for my computer and a new graphics card.
 
roumor is that as long as you don't change too many things at once you will be able to do it. because windows keeps track of your ram and sound card and stuff liek that. but if you change things bit by bit then it's possible.
 
 
my Windows version was XP Home OEM 32bit (but bought in a shop together with motherboard for computer).
 
I am not sure but i think it was this guide that ui used back then:[http://michaelstevenstech.com/moving_xp.html](http://michaelstevenstech.com/moving_xp.html)

---

### Post by dandnsmith on 2010-12-08
It may be possible to get somewhere by invoking the safe start when starting (either Ctrl held down or F8), and then you can bypass some or all of the drivers (and then remove them before trying to go further).

You also have to think about HDD access mode, as the original setup may expect the stuff organised DHS where now you go for LBA.

---

### Post by crayZsaaron on 2010-12-08
Can I remove the drivers manually from system32?  Because I just did, and nothing new happened when I booted up.  See, I can't put the hard drive back in that old computer because the motherboard is shot.  Hm.

---

### Post by mastablasta on 2010-12-09
better you consult microsoft technical help or some microsoft help forums as they will probabyl have more knowledge on how to solve this issue.
 
drivers can be downloaded from internet. or they are usually on the disk.
 
you final option (but try EVRYTHING ELSE BEFORE THIS) would be to simply install windows on new computer, call microsoft support and tell them you just changed the motherboard. They can fix/change something (i think they register a new maschine for your widnows key) and it should then all work (might take a while before windows are registered for new maschine). you can only do this on non OEM versions i believe.

---

### Post by dandnsmith on 2010-12-09
I really hope you didn't remove all of the system32 content - if you did you might as well start a re-install now (unless you can restore them).

What I meant was to go into System|Properties to get to Device Manager, and then remove drivers from hardware which is now different.

PS in my last post DHS should have been CHS (but this isn't always what the BIOS would say - it depends on the BIOS maker).

---

### Post by cascade9 on 2010-12-09
I've had the method that mastablasta posted work at times, fail at other times. I've never quite figured out why it works with some hardware changes but not others. :| 

> **wilee-nilee said:**
> A legitimate XP disc is almost impossible to get except through a 3rd party now, like ebay.[]("http://fridge.ubuntu.com/node/2132")

Really? *blinks* I'll count myself as lucky that the place I go to still has OEM Win XP for sale (not that I have any need for XP anymore).

---

### Post by crayZsaaron on 2010-12-09
[QUOTE=dandnsmith]I really hope you didn't remove all of the system32 content[/QUOTE]
No, I removed some files that looked like propietary drivers.  Technically I didn't delete anything, because I just moved them to my other hard drive.

Well, I think this may not be worth the hassle.  I'm just going to call Dell up, order that $11.99 XP replacement disk, and use that.  Actually, first I should get a disk drive so I can actually install the CD...

---

