---
title: "combining partitions"
date: 2010-02-24
forum: General Help
---

### Post by harryliddic on 2010-02-24
I upgrades 9.10 on my 8.04 partition but it didn't work right. Someone suggested a clean install so I made a 9.10 disk and install 9.10 that way.
Ubuntu chose to use the first ppartition it saw and installed 9.10.I now have two versions of 9.10 on my computer and I wish to remove the the first partition and combine that partition with the the newer 9.10 partition. Is there a way to do this without creating two volumes but just one big volume.
If this requires CLI, please be specfic as I am weak on command line projects. If there is no way to combine the volumes please tell me how to clear the unwanted volume safely.

---

### Post by SecretCode on 2010-02-24
Yes, you can combine the volumes - but you'll have to delete one and expand the other. Make sure you have backed up all the data from the one you are going to delete.

Also, resizing volumes can sometimes fail ... so make sure you have backed all the data from **every** volume!

First thing: let's see how your drive is partitioned. Open Applications > Accessories > Terminal and type the following
```
sudo fdisk -l
```
You will be prompted for your user password ... while you enter it nothing appears on the screen.

Copy the output into a post here, surrounded by [**code]code tags[**/code].

---

### Post by harryliddic on 2010-02-24
/dev/sda1   *           1        4061    32619951    7  HPFS/NTFS
/dev/sda2            4062        4864     6450097+   7  HPFS/NTFS
/dev/sda3            4865        9389    36347062+  83  Linux
/dev/sda4            9390        9729     2731050   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+   7  HPFS/NTFS
/dev/sdb2            1825        4679    22932787+   5  Extended
/dev/sdb3            4680        4865     1494045   83  Linux
/dev/sdb5            1825        2057     1871541   83  Linux
/dev/sdb6            4660        4679      160618+  82  Linux swap / Solaris
/dev/sdb7            2590        4659    16627243+   7  HPFS/NTFS
/dev/sdb8            2058        2559     4032283+  83  Linux
/dev/sdb9            2560        2589      240943+  82  Linux swap / Solaris

Partition table entries are not in disk order
harry@harry-desktop:~$

---

### Post by SecretCode on 2010-02-24
Code tags! :D Like this:
> **harryliddic said:**
> ```
/dev/sda1   *           1        4061    32619951    7  HPFS/NTFS
/dev/sda2            4062        4864     6450097+   7  HPFS/NTFS
/dev/sda3            4865        9389    36347062+  83  Linux
/dev/sda4            9390        9729     2731050   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+   7  HPFS/NTFS
/dev/sdb2            1825        4679    22932787+   5  Extended
/dev/sdb3            4680        4865     1494045   83  Linux
/dev/sdb5            1825        2057     1871541   83  Linux
/dev/sdb6            4660        4679      160618+  82  Linux swap / Solaris
/dev/sdb7            2590        4659    16627243+   7  HPFS/NTFS
/dev/sdb8            2058        2559     4032283+  83  Linux
/dev/sdb9            2560        2589      240943+  82  Linux swap / Solaris

Partition table entries are not in disk order
harry@harry-desktop:~$
```

And you missed out the beginning of the output so I'm not sure what size the first hard drive is.

Anyway, you have two separate hard drives. The first has two NTFS partitions and one linux partition (plus a swap, normal). The second has two NTFS partitions and **three** linux partitions plus two swap partitions, which isn't usually needed.

Are both the hard drives internal?

How many installations of windows do you think you have? How many linux installations do you think you have, and how many do you want? Have you set up any windows or linux data partitions (generally a good thing to have)?

---

### Post by harryliddic on 2010-02-24
I have the new linux 9.10 on the first partition of an my first drive, I have the bad 9.10 on the second partition of the first drive(I want to get rid of that and have one 80 g linux volume. On the second drive the first partition is Winxp( I want to keep that) I have small volumes of both NFTS and linux  that I want to be rid of. I Have a NTFS drive H that I want to expand to take up any remaining space. I forgot my swap space that I want in the right space.  Sorry for this can of worms but I do video editing in both linux and winxp and I obviously don't have enough room. I am resending the fdaik -l I hope this helps I am a bit overwelmed. Thank you for your help.

harry@harry-desktop:~$ sudo fdaisk -l
[sudo] password for harry: 
sudo: fdaisk: command not found
harry@harry-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4061    32619951    7  HPFS/NTFS
/dev/sda2            4062        4864     6450097+   7  HPFS/NTFS
/dev/sda3            4865        9389    36347062+  83  Linux
/dev/sda4            9390        9729     2731050   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+   7  HPFS/NTFS
/dev/sdb2            1825        4679    22932787+   5  Extended
/dev/sdb3            4680        4865     1494045   83  Linux
/dev/sdb5            1825        2057     1871541   83  Linux
/dev/sdb6            4660        4679      160618+  82  Linux swap / Solaris
/dev/sdb7            2590        4659    16627243+   7  HPFS/NTFS
/dev/sdb8            2058        2559     4032283+  83  Linux
/dev/sdb9            2560        2589      240943+  82  Linux swap / Solaris

Partition table entries are not in disk order
harry@harry-desktop:~$

---

### Post by SecretCode on 2010-02-24
Hmm. It's quite a bit more complicated than you suggest. 

> **harryliddic said:**
> I have the new linux 9.10 on the first partition of an my first drive, I have the bad 9.10 on the second partition of the first drive(I want to get rid of that and have one 80 g linux volume.
The first partition is ntfs (on both drives) and there at most one linux installation on the first drive (the 80GB one).

> **harryliddic said:**
> On the second drive the first partition is Winxp( I want to keep that) I have small volumes of both NFTS and linux  that I want to be rid of. I Have a NTFS drive H that I want to expand to take up any remaining space. I forgot my swap space that I want in the right space.  Sorry for this can of worms but I do video editing in both linux and winxp and I obviously don't have enough room.

I'm concerned that there is stuff here you need to keep but aren't aware of.

Need more info ... please get hold of and run the boot info script as described in this thread: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) and post or attach the results.

Please, when posting command output, put [**code] before it and [**/code] afterwards, or use the # button above the message edit box.

---

### Post by drdanielfc on 2010-02-24
I would just suggest using gparted and deleting everything you dont need, but you might not be able to tell the difference between your ubuntu partitions and you shouldnt delete the wrong swap partition...

---

### Post by harryliddic on 2010-02-24
Here is the output of that script


```
sudo bash ~/Desktop/boot_info_script*.sh                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60466447

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    65,239,964    65,239,902   7 HPFS/NTFS
/dev/sda2          65,239,965    78,140,159    12,900,195   7 HPFS/NTFS
/dev/sda3          78,140,160   150,834,284    72,694,125  83 Linux
/dev/sda4         150,834,285   156,296,384     5,462,100  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004d859

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    29,302,559    29,302,497   7 HPFS/NTFS
/dev/sdb2          29,302,560    75,168,134    45,865,575   5 Extended
/dev/sdb5          29,302,623    33,045,704     3,743,082  83 Linux
/dev/sdb6          74,846,898    75,168,134       321,237  82 Linux swap / Solaris
/dev/sdb7          41,592,348    74,846,834    33,254,487   7 HPFS/NTFS
/dev/sdb8          33,045,768    41,110,334     8,064,567  83 Linux
/dev/sdb9          41,110,398    41,592,284       481,887  82 Linux swap / Solaris
/dev/sdb3          75,168,135    78,156,224     2,988,090  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4274088174087A45                       ntfs                                     
/dev/sda2        621311E813F2B768                       ntfs                                     
/dev/sda3        7b981f41-66ef-40e8-aaab-be6c63f2c36e   ext3                                     
/dev/sda4        d80cf13e-6ee8-4ee0-b3fe-2f9b8088b351   swap                                     
/dev/sdb1        19647D1D1338C03F                       ntfs                                     
/dev/sdb3        9935cde3-9f5c-4444-b0f3-ad41df8d887b   ext3                                     
/dev/sdb5        2a9151f9-2457-4020-8204-07f1c653fee5   ext3                                     
/dev/sdb6        f9f89d9a-0f07-4306-9caf-89fadbeb34f8   swap                                     
/dev/sdb7        58A63B0D6737A897                       ntfs                                     
/dev/sdb8        35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba   ext4                                     
/dev/sdb9        a6c44e6d-feb4-4e95-8c3f-c01b8850adf0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb8        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/disk-1            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda2        /media/disk-3            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/disk-4            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb3        /media/disk-5            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7        /media/disk-6            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=signature(4d859)disk(1)rdisk(0)partition(1)\WINDOWS

[operating systems]

signature(4d859)disk(1)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\BACKUUP="Microsoft Windows 2000 Professional" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.10, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.10, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=2a9151f9-2457-4020-8204-07f1c653fee5 /media/temp     ext3    relatime        0       2
# /dev/sda4
UUID=d80cf13e-6ee8-4ee0-b3fe-2f9b8088b351 none            swap    sw              0       0
# /dev/sdb6
UUID=f9f89d9a-0f07-4306-9caf-89fadbeb34f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/hda8 /win/pen vfat rw,uid,umask=0002,iocharset=iso8859-1,utf8 0 0

=================== sda3: Location of files loaded by Grub: ===================


  67.9GB: boot/grub/menu.lst
  67.8GB: boot/grub/stage2
  67.8GB: boot/initrd.img-2.6.24-16-generic
  67.8GB: boot/initrd.img-2.6.24-16-generic.bak
  67.8GB: boot/initrd.img-2.6.24-21-generic
  67.8GB: boot/initrd.img-2.6.24-21-generic.bak
  67.8GB: boot/initrd.img-2.6.27-14-generic
  67.8GB: boot/initrd.img-2.6.28-17-generic
  67.8GB: boot/initrd.img-2.6.31-17-generic
  67.8GB: boot/vmlinuz-2.6.24-16-generic
  67.7GB: boot/vmlinuz-2.6.24-21-generic
  67.9GB: boot/vmlinuz-2.6.27-14-generic
  67.9GB: boot/vmlinuz-2.6.28-17-generic
  67.8GB: boot/vmlinuz-2.6.31-17-generic
  67.8GB: initrd.img
  67.8GB: initrd.img.old
  67.8GB: vmlinuz
  67.9GB: vmlinuz.old

=========================== sdb8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,8)
search --no-floppy --fs-uuid --set 35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4274088174087a45
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-17-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.27-14-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.24-21-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.24-21-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro single
	initrd /boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.24-16-generic (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=7b981f41-66ef-40e8-aaab-be6c63f2c36e ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7b981f41-66ef-40e8-aaab-be6c63f2c36e
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=35da1751-ba4c-4f31-bda0-8d4e9cc6c2ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=a6c44e6d-feb4-4e95-8c3f-c01b8850adf0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


  20.3GB: boot/grub/core.img
  20.3GB: boot/grub/grub.cfg
  17.7GB: boot/initrd.img-2.6.31-14-generic
  20.4GB: boot/initrd.img-2.6.31-17-generic
  19.3GB: boot/vmlinuz-2.6.31-14-generic
  19.0GB: boot/vmlinuz-2.6.31-17-generic
  20.4GB: initrd.img
  17.7GB: initrd.img.old
  19.0GB: vmlinuz
  19.3GB: vmlinuz.old

```

Sorry if I misstated the problem but it wasn't intentional. My fault entirely.

harry

---

### Post by SecretCode on 2010-02-25
> **harryliddic said:**
> Sorry if I misstated the problem but it wasn't intentional. My fault entirely.


Not your fault - it's not easy for a beginner to understand partitions and multiple OSes after several installs. My point is just that you need to be quite careful before deleting anything. Hence, I have some more questions...

What I see is:

The boot loader is GRUB2 on the first hard drive. Its config files are in sdb8, on the second hard drive, and this is where your running copy of Ubuntu is. It supports booting Ubuntu on sdb8, your older Ubuntu on sda3, or windows. This Ubuntu installation doesn't have fstab entries for the other partitions. It's only 4GB.

sda3 is where your earlier Ubuntu installation was. This Ubuntu installation recognises two cdroms - _do you have two cdroms?_ - and mounts sdb5 as "/media/temp". 

_What went wrong with your attempt to upgrade 8.04 to 9.10? Do you have data in the old installation that you want to keep?_

The previous windows boot loader knows about XP on disk(1)rdisk(0)partition(1) which we would call sdb1, first partition of the second drive, and a Windows 2000 installation on sda1. _Did you have Win2000 on this computer? Do you want to keep it?_

sdb7 is an ntfs partition of about 16GB. _Is that how big your H: drive is?_

That leaves a small 1.4GB linux partition at sdb3, which is probably nothing worth keeping, and a 6GB ntfs partition at sda2, which could be anything.

---

### Post by harryliddic on 2010-02-25
I am bowing with many pardons.I do have Windows 2000 on my C:(sda1 ?) I used 'gparted' by sugession and found that the C; drive had not been over-written by 9.10 but the sda2 had been over-written by the fresh install. It also showed the swap partition at sda3 if I remember right.On sdb1 is WinXP then two small partitions one NFTS and one ext3. finally as you suspected drive H: is a NFTS partition. My confusion about the two partitions of  9.10 was the long list of 9.10 boots when grub ran. I needed to run a fresh install because the update of 9.10 from the update manager kept crashing.
What I would like to do is delete the Windows 2000 and combine what is space is left to the the the 9.10 on sda2 and have the boot section in the right place.
Furthermore I have a cdrom and dvd drive but Had to change the name of the dvd so the a very quirky program 'qdvdauthor' would work. I hope I answered all your questions. Thanks for the time you are devoting to my problem. I need to edit and author a hour and half instruction video in linux and I need the extra space.

---

### Post by SecretCode on 2010-02-25
Do you want to keep the Windows 2000 installation as well as the XP installation? That's taking nearly half of the first drive. 

What I think will be best is to delete all the partitions you don't want any more, make new bigger partitions, and reinstall Ubuntu. Do you have any data from the old Ubuntu installation that you need to back up?

It would be a good idea to post a screenshot of gparted - one for drive /dev/sda and one for drive /dev/sdb.

---

### Post by harryliddic on 2010-03-02
I re-installed 9.10 on sba covering the whole drive, I have winxp on sdb. Now comes the problem. The boot sector or grub will not recognise the sdb and the beginning of the winxp on sdb. I would not sweat the lack of winxp except I need it for two programs that assist me in playwriting not that I am an Athol Fugard or any thing. The linux on sda I was mainly to edit video
productions and they produce some very large files. 

I was told to put a nfts partition On the sda and gparted would allow me, I read to switch the drives in BIOS but I did not try because I would have the mirror image of the same problem. Sorry for the delay but I had to edit and author an instruction video due today. Could you look over the problem again. I have included a current 'fdisk' printout. Thank you.


```
harry@harry-desktop:~$ sudo fdisk -l
[sudo] password for harry: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8232    66123508+  83  Linux
/dev/sda2            8233        9729    12024652+   5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
/dev/sda6            9002        9305     2441817   83  Linux
/dev/sda7            9306        9327      176683+  82  Linux swap / Solaris
/dev/sda8            8233        8961     5855629+  83  Linux
/dev/sda9            8962        9001      321268+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+   7  HPFS/NTFS
/dev/sdb2            1825        4679    22932787+   5  Extended
/dev/sdb5            1825        4679    22932756    7  HPFS/NTFS
harry@harry-desktop:~$ 

```

---

### Post by sudhanshu1990 on 2010-03-02
Hello there, 
Yesterday I installed ubuntu 9.10 in my laptop removing windows 7 and since then I am facing a lot of problems some of them are listed below

1. During Installation I formatted my C:(20 gb) to ext4 but still it kept on asking for extra swap space,Accidently I gave my whole 40 gb partition as swap space.
2. Later it installed sucessfully and  I tried to reduce the swap space from the disk utility provided, I was able to devide the swap partition into two parts one 4gb for swap and another 36gb.
3. The serious problem i am facing is that I am not able to use that 36 gb space, disk utility shows it as unallocated space but when I tried to format it, Disk utility shows some error(Ms dosmagic found something..) I tried with fdsk -l and then n but says no read sector available.
I am new to ubuntu so can someone help me here...

---

### Post by harryliddic on 2010-03-02
Read some of the previous posts in this thread. It might give you some insight. you can maybe resize the swap space with 'gparted andd expand the your other partition.
be warned this is advice from someone that is having a similar but not exact problem.

---

### Post by SecretCode on 2010-03-02
@sudhanshu1990, you should start a new thread for your issue, you will get more attention that way.

---

### Post by SecretCode on 2010-03-02
> **harryliddic said:**
> I re-installed 9.10 on sba covering the whole drive
Not quite the whole drive! There are quite a few small partitions on sda, and multiple swap files, that you probably don't need. But let's leave them for the time being and sort out the boot problem. 

> **harryliddic said:**
> I have winxp on sdb. Now comes the problem. The boot sector or grub will not recognise the sdb and the beginning of the winxp on sdb.

Can you set your BIOS to boot from the second hard drive (sdb, but the BIOS probably won't call it that)? This is just to test that the XP installation is completely there.

Also, please run that bootinfo script again!

---

### Post by harryliddic on 2010-03-02
Here is the printout

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60466447

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   132,247,079   132,247,017  83 Linux
/dev/sda2         132,247,080   156,296,384    24,049,305   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris
/dev/sda6         144,601,191   149,484,824     4,883,634  83 Linux
/dev/sda7         149,484,888   149,838,254       353,367  82 Linux swap / Solaris
/dev/sda8         132,247,206   143,958,464    11,711,259  83 Linux
/dev/sda9         143,958,528   144,601,064       642,537  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004d859

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    29,302,559    29,302,497   7 HPFS/NTFS
/dev/sdb2          29,302,560    75,168,134    45,865,575   5 Extended
/dev/sdb5          29,302,623    75,168,134    45,865,512   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c7723185-d4d4-4732-b6d5-55e9e73e50b9   ext4                                     
/dev/sda5        cf28b9b0-f3eb-4b3f-89dc-3777560b9a20   swap                                     
/dev/sda6        4a78e5be-a821-4edc-a6a1-0c8360066a9b   ext4                                     
/dev/sda7        6ecae8d1-b087-479a-a45b-631cc1bc0596   swap                                     
/dev/sda8        c6742cc0-cd61-4029-91c9-d3dda5c65b4a   ext4                                     
/dev/sda9        fc3b0186-fbb6-4743-b978-a5e6291e56c8   swap                                     
/dev/sdb1        19647D1D1338C03F                       ntfs                                     
/dev/sdb5        58A63B0D6737A897                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cf28b9b0-f3eb-4b3f-89dc-3777560b9a20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4a78e5be-a821-4edc-a6a1-0c8360066a9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 4a78e5be-a821-4edc-a6a1-0c8360066a9b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4a78e5be-a821-4edc-a6a1-0c8360066a9b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 4a78e5be-a821-4edc-a6a1-0c8360066a9b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4a78e5be-a821-4edc-a6a1-0c8360066a9b ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4a78e5be-a821-4edc-a6a1-0c8360066a9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6ecae8d1-b087-479a-a45b-631cc1bc0596 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  76.2GB: boot/grub/grub.cfg
  74.8GB: boot/initrd.img-2.6.31-14-generic
  76.5GB: boot/vmlinuz-2.6.31-14-generic
  74.8GB: initrd.img
  76.5GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set c6742cc0-cd61-4029-91c9-d3dda5c65b4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set c6742cc0-cd61-4029-91c9-d3dda5c65b4a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c6742cc0-cd61-4029-91c9-d3dda5c65b4a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set c6742cc0-cd61-4029-91c9-d3dda5c65b4a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c6742cc0-cd61-4029-91c9-d3dda5c65b4a ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c7723185-d4d4-4732-b6d5-55e9e73e50b9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7723185-d4d4-4732-b6d5-55e9e73e50b9 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 4a78e5be-a821-4edc-a6a1-0c8360066a9b
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4a78e5be-a821-4edc-a6a1-0c8360066a9b ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 4a78e5be-a821-4edc-a6a1-0c8360066a9b
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4a78e5be-a821-4edc-a6a1-0c8360066a9b ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=c6742cc0-cd61-4029-91c9-d3dda5c65b4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=fc3b0186-fbb6-4743-b978-a5e6291e56c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  70.4GB: boot/grub/core.img
  70.4GB: boot/grub/grub.cfg
  71.0GB: boot/initrd.img-2.6.31-14-generic
  70.1GB: boot/vmlinuz-2.6.31-14-generic
  71.0GB: initrd.img
  70.1GB: vmlinuz
```

---

### Post by SecretCode on 2010-03-02
The first drive, sda, is messed up: you've installed Ubuntu **three times** on it! As a result you'll have very little free space in the default (third) installation. 

If you haven't done much work on it I suggest you wipe that drive and reinstall Ubuntu ... just once!

- 

The problem of not seeing XP is not obvious to me ... but I suspect it may be to do with having Windows 2000 on the machine originally; Windows installations tend to reuse old installations on different partitions and store some of their boot files there.

**See if you can set your BIOS to boot from the second hard drive, and if it works.** If it does, then my theory above is wrong!

If it can't boot, you may need to run a 'repair installation' using the Windows XP drive. I'm not 100% familiar with this, but you **must** install to the second drive (in fact it would be better if you can **disconnect** the first drive while doing this) - otherwise you'll just end up in the same position.

---

### Post by harryliddic on 2010-03-03
thank you for the great idea of going into the BIOS. That didn't work *per se*but it did work when I went inside the box and switched hard drives. Windows like a woman always wants to be on top. I had to re-install 9.10 and am slowly re-installing the repos but both 9.10 and winXP are now in the grub and are working swimmingly thanks for all your help and time. Now I have to figure how to mark this solved.

---

