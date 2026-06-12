---
title: "Grub Error 17 after HD partition resize"
date: 2011-04-15
forum: General Help
---

### Post by cybermecano on 2011-04-15
Hi,

I get the frustrating Grub Error 17 while starting, which looks like this :

```
Grub Loading stage1.5.

Grub loading, please wait...

Error 17
```

This happen after a resizing partition I've done like follow :

**Step 1-** Successful decrease of the ubuntu partition (by the left) using Gparted runned from ubuntu live-CD.
As a result of Step 1, I've got an unallocated partition which was between the windows one and the ubuntu one, everything was ok because I succesfully reboot my system and using Grub menu, I loaded my windows XP Media Center Edition without any problem.

**Step 2-** From Windows I extended the windows partition to the unallocated one and there problems began. The system asked me to restart and then the extension was done and finally when the system restart again I get the Grub Error 17 as described on the top.

**Step 3-** I runned the ubuntu live-CD to try to fix the problem and I do the following :

**Step 3-1-** Gparted looks like the atached screenshot **Gparted_now.jpeg**.
**Step 3-2-** I went to the Terminal :
```
$ sudo grub
grub> find /find/grub/stage1

Error 15 : File not found

grub> root (hd0,4) #as described on my /boot/grub/menu.lst

grub> setup (hd0)

Error 17 : Cannot mount selected partition

grub>
```

The other problem is that I can only access my ubuntu partition and not the windows one from the ubuntu live-CD and to my eyes it doesn't make a sens. You can get a glance to **access_windows.jpg** to see the error message I get when I try to open the windows partition from the graphique menu.

Now, I don't know what to do and I don't want to scew it up.

So please help...

Thanks.

---

### Post by cybermecano on 2011-04-15
other steps :

```
$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/hda: Not found or not a block device.
```

:confused:

---

### Post by coffeecat on 2011-04-15
Boot up with the live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file in code tags. I see from your wallpaper that you are using Ubuntu 8.04. If you can, use the 8.04 live CD also. It will be useful to see whether 8.04 designates your main HD as sda or hda. If sda that will explain why grub-install is giving you "/dev/hda: Not found or not a block device.". Some HDs were still designated hda in Hardy, but even some IDE drives were coming out as sda, if I remember correctly. Indeed, your first screenshot shows Gparted showing the HD as sda. Which version of Ubuntu was this from?

The live CD's inability to mount your Windows partition is explained in your second screenshot. It is seeing the filesystem as unclean and it needs to be repaired in Windows itself. If we can sort out the grub error, then you should be able to boot Windows up in safe mode and repair the filesystem.

---

### Post by cybermecano on 2011-04-15
Here is the RESULTS.txt content

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 320.0 Go, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x465d0d5d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392   6 FAT16
/dev/sda2    *        112,455   400,323,671   400,211,217   7 HPFS/NTFS
/dev/sda3         400,323,672   615,401,954   215,078,283   5 Extended
/dev/sda5         400,323,735   598,292,729   197,968,995   1 FAT12
/dev/sda6         598,292,793   615,401,954    17,109,162   1 FAT12
/dev/sda4         615,401,955   625,137,344     9,735,390   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D6-0A1A                              vfat       DellUtility                   
/dev/sda2        AED00CAFD00C7FB7                       ntfs                                     
/dev/sda4        0000-0000                              vfat       DellRestore                   
/dev/sda5        a01475e8-f2f0-4411-a5c6-4b81c45f77dd   ext3                                     
/dev/sda6        8cc36517-6541-462a-920d-9effedb85dc5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a01475e8-f2f0-4411-a5c6-4b81c45f77dd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8cc36517-6541-462a-920d-9effedb85dc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 223.9GB: boot/grub/menu.lst
 221.8GB: boot/grub/stage2
 221.8GB: boot/initrd.img-2.6.24-19-generic
 221.8GB: boot/initrd.img-2.6.24-19-generic.bak
 244.3GB: boot/initrd.img-2.6.24-21-generic
 244.4GB: boot/initrd.img-2.6.24-21-generic.bak
 244.4GB: boot/initrd.img-2.6.24-22-generic
 244.4GB: boot/initrd.img-2.6.24-22-generic.bak
 244.4GB: boot/initrd.img-2.6.24-23-generic
 262.4GB: boot/initrd.img-2.6.24-23-generic.bak
 244.4GB: boot/initrd.img-2.6.24-24-generic
 244.4GB: boot/initrd.img-2.6.24-24-generic.bak
 244.4GB: boot/initrd.img-2.6.24-27-generic
 262.3GB: boot/initrd.img-2.6.24-27-generic.bak
 244.4GB: boot/initrd.img-2.6.24-28-generic
 262.3GB: boot/initrd.img-2.6.24-28-generic.bak
 221.7GB: boot/vmlinuz-2.6.24-19-generic
 244.3GB: boot/vmlinuz-2.6.24-21-generic
 244.3GB: boot/vmlinuz-2.6.24-22-generic
 244.4GB: boot/vmlinuz-2.6.24-23-generic
 235.7GB: boot/vmlinuz-2.6.24-24-generic
 262.3GB: boot/vmlinuz-2.6.24-27-generic
 262.4GB: boot/vmlinuz-2.6.24-28-generic
 244.4GB: initrd.img
 244.4GB: initrd.img.old
 262.4GB: vmlinuz
 262.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3



=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: Aucun fichier ou dossier de ce type
hexdump: /dev/sda3: Aucun fichier ou dossier de ce type
```

and, yes I'm using ubuntu 8.04 (hardy heron) live-cd which is the same cd I used to install ubuntu

---

### Post by coffeecat on 2011-04-15
I must admit that I'm puzzled. Everything looks in order in your boot script output, yet you get error 17 when you try to boot.

From the legacy grub manual:

> 
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.The boot script is not reporting any problem with sda5, but to be sure, boot up the live CD, open Gparted, right-click on sda5 and choose "Check". By the way, I'm assuming that there is a "check" option in the Hardy version of Gparted. If not, then from a terminal:

```
sudo fsck /dev/sda5
```

Next, I agree with you about trying to re-install grub to the mbr and embedding area with:

```
grub> root (hd0,4)
grub> setup (hd0)
```

But you tried that and it didn't work. I don't understand - unless the filesystem needs repair with fsck.

Last. You tried:

```
$ sudo grub-install /dev/hda
```

Which didn't work. Once you've done a filesystem check on sda5, try:

```
$ sudo grub-install /dev/sda
```

sda, not hda.

---

### Post by cybermecano on 2011-04-15
Gparted is now checking sda5.

By the way I wonder if the problem is not here

```
Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 320.0 Go, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x465d0d5d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392   6 FAT16
_**/dev/sda2**    *****_        112,455   400,323,671   400,211,217   7 HPFS/NTFS
/dev/sda3         400,323,672   615,401,954   215,078,283   5 Extended
/dev/sda5         400,323,735   598,292,729   197,968,995   1 FAT12
/dev/sda6         598,292,793   615,401,954    17,109,162   1 FAT12
/dev/sda4         615,401,955   625,137,344     9,735,390   b W95 FAT32

```

I mean that the Boot is set on /dev/sda2 which is the windows partition. Is that ok ?

---

### Post by cybermecano on 2011-04-15
Here is the details of Gparted sda5 check :

```
GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (ext3) on /dev/sda5  03:14    ( SUCCES )
     	
calibrate /dev/sda5  00:00    ( SUCCES )
     	
path: /dev/sda5
start: 400323735
end: 598292729
size: 197968995 (94.40 GiB)
check filesystem on /dev/sda5 for errors and (if possible) fix them  03:14    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda5
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

253365 inodes used (4.09%)
2003 non-contiguous inodes (0.8%)
# of inodes with ind/dind/tind blocks: 11237/121/1
12525039 blocks used (50.61%)
0 bad blocks
2 large files

197028 regular files
31672 directories
69 character device files
26 block device files
2 fifos
520 links
24551 symbolic links (22013 fast symbolic links)
8 sockets
--------
253876 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
resize2fs /dev/sda5
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 24746124 blocks long. Nothing to do!


========================================
```

and here what I get for grub-install /dev/**sda** 

```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

```

:confused:

Do you think that reinstalling ubuntu on sda5 could solve the problem ?

---

### Post by psusi on 2011-04-15
The boot flag has no meaning to anyone but the Windows boot loader.

You appear to still be running 8.04, which is now obsolete.  You should install 10.04 or 10.10, which use grub2, which does not suffer from this kind of breakage.

---

### Post by cybermecano on 2011-04-15
Do you think that installing ubuntu 10.10 on my sda5 will solve the problem, since all my data are actually held under the windows partition, I'm really afraid to loose everything !!!!

---

### Post by LostFarmer on 2011-04-15
The partition information shows that the linux partitions are FAT12 ??  Will let '[coffeecat]("http://ubuntuforums.org/member.php?u=129087")' comment.

---

### Post by oldfred on 2011-04-15
Lostfarmer has noticed:

/dev/sda5         400,323,735   598,292,729   197,968,995   1 [COLOR=Red]FAT12[/COLOR]
/dev/sda6         598,292,793   615,401,954    17,109,162   1 [COLOR=Red]FAT12[/COLOR]

/dev/sda5        a01475e8-f2f0-4411-a5c6-4b81c45f77dd   [COLOR=Red]ext3[/COLOR]                                     
/dev/sda6        8cc36517-6541-462a-920d-9effedb85dc5   [COLOR=Red]swap [/COLOR]  

Fdisk is showing files as FAT12 and blkid is showing as Linux types. Some real inconsistency in partition table for file structure.

If from liveCD what type does Disk Utility show?
Linux should be type 83 and swap type 82

What does this show?

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt
 
Post PT.txt

---

### Post by cybermecano on 2011-04-15
```
$ sudo sfdisk -d /dev/sda > PT.txt
bash: PT.txt: Permission denied
```

so I made this

```
/$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start on cylinder boundary.
cylinders DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   112392, Id= 6
/dev/sda2 : start=   112455, size=400211217, Id= 7, bootable
/dev/sda3 : start=400323672, size=215078283, Id= 5
/dev/sda4 : start=615401955, size=  9735390, Id= b
/dev/sda5 : start=400323735, size=197968995, Id= 1
/dev/sda6 : start=598292793, size= 17109162, Id= 1
```

also I get this

```
$ sudo mount /dev/sda5 /boot
$ sudo grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.
```

Any idea about re-installing ubuntu on sda5 ? Will it resolve the problem ?

Thanks

---

### Post by coffeecat on 2011-04-15
> **oldfred said:**
> Lostfarmer has noticed:

/dev/sda5         400,323,735   598,292,729   197,968,995   1 [COLOR=Red]FAT12[/COLOR]
/dev/sda6         598,292,793   615,401,954    17,109,162   1 [COLOR=Red]FAT12[/COLOR]

/dev/sda5        a01475e8-f2f0-4411-a5c6-4b81c45f77dd   [COLOR=Red]ext3[/COLOR]                                     
/dev/sda6        8cc36517-6541-462a-920d-9effedb85dc5   [COLOR=Red]swap [/COLOR]  

Fdisk is showing files as FAT12 and blkid is showing as Linux types. Some real inconsistency in partition table for file structure.

Yes, I missed that. Agreed - there is an inconsistency between the partition table entry and the filesystem itself.

> **cybermecano said:**
> ```
$ sudo sfdisk -d /dev/sda > PT.txt
bash: PT.txt: Permission denied
```

The first command produces a text file called PT.txt in the directory in which you ran the command. You don't need to run a bash command on it. Simply double-click on the PT.txt file and it will open in a text editor. **EDIT**: sorry, to clarify. I can't see why that permission denied message came up. There is no command to go with it. Did it just appear in the line after the sfdisk command? Did the sfdisk command produce a file called PT.txt? (end_edit)

> **cybermecano said:**
> Any idea about re-installing ubuntu on sda5 ? Will it resolve the problem ?

If you reinstall Ubuntu on sda5 and set the partition to be reformatted, that should resolve the problem. But you'd need to reformat sda6 back to being  a swap partition first.

However, it may not be necessary to reformat because those partitions are probably both formatted correctly. The problem is probably false entries in the partition table which are easily amended with sfdisk. Let's see  the contents of PT.txt - then we can confirm this or not as the case may be.

---

### Post by cybermecano on 2011-04-15
Here is the content of the PT.txt file

```
# table de partitions de /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   112392, Id= 6
/dev/sda2 : start=   112455, size=400211217, Id= 7, bootable
/dev/sda3 : start=400323672, size=215078283, Id= 5
/dev/sda4 : start=615401955, size=  9735390, Id= b
/dev/sda5 : start=400323735, size=197968995, Id= 1
/dev/sda6 : start=598292793, size= 17109162, Id= 1
```

---

### Post by oldfred on 2011-04-15
Does System, Administration, Disk Utility let you see/change partition type? If so you can try that. OR:

You need to save PT.txt and change this make no other changes as it has to read the entire partition table back in:

/dev/sda5 : start=400323735, size=197968995, Id= [COLOR=Red]1[/COLOR]
/dev/sda6 : start=598292793, size= 17109162, Id= [COLOR=Red]1[/COLOR]

/dev/sda5 : start=400323735, size=197968995, Id= [COLOR=Red]83[/COLOR]
/dev/sda6 : start=598292793, size= 17109162, Id= [COLOR=Red]82[/COLOR]

Then read PT.txt back into partition table - note reversed >

sfdisk /dev/sda < PT.txt

see 
man sfdisk for more info.

---

### Post by coffeecat on 2011-04-15
Boot from the live CD and save this as PT_modified.txt:

```
# table de partitions de /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   112392, Id= 6
/dev/sda2 : start=   112455, size=400211217, Id= 7, bootable
/dev/sda3 : start=400323672, size=215078283, Id= 5
/dev/sda4 : start=615401955, size=  9735390, Id= b
/dev/sda5 : start=400323735, size=197968995, Id=83
/dev/sda6 : start=598292793, size= 17109162, Id=82
```Now write it to the partition table with:

```
sudo sfdisk --force /dev/sda < PT_modified.txt
```This should make the partition table entries for sda5 and sda6 consistent with the filesystems in them. Now try a reboot. If you still get a grub error, you could try re-installing grub with the commands you tried before.

---

### Post by cybermecano on 2011-04-16
Thanks a lot everybody. Indeed, it was about an inconsistency between the partition table entry and the filesystem itself.

Now, Grub error 17 is solved and I can go through to my ubuntu hardy. Nevertheless, I must fix my windows partition but this is another issue...

Thanks again.

---

### Post by jeffersonx1 on 2011-05-10
Hey guys,

I have the same problem: increased size of a partition (sda2 - DATA under windows)(there was 50gig unpartitioned space after) and now can't boot.
I also have a separate boot partition - apparently sda5
tried to reinstall grub but getting errors similar like the topic starter
here my results.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xbbc58b91

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,402,047   102,400,000   7 HPFS/NTFS
/dev/sda2         102,402,048   409,769,954   307,367,907   7 HPFS/NTFS
/dev/sda3         409,769,955   450,735,704    40,965,750  83 Linux
/dev/sda4         450,751,770   488,392,064    37,640,295   f W95 Ext d (LBA)
/dev/sda5         450,751,833   451,233,719       481,887  83 Linux
/dev/sda6         451,249,848   480,568,409    29,318,562  83 Linux
/dev/sda7         480,584,475   488,392,064     7,807,590  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        70CE05BDCE057D1A                       ntfs                                     
/dev/sda2        F6CEE2B5CEE26D75                       ntfs       DATA                          
/dev/sda3        09942f16-fa71-48f2-bb66-b6553caa508e   ext3                                     
/dev/sda5        28f9470e-7f28-4d44-803b-181cf36b38b8   ext3                                     
/dev/sda6        86009ceb-252c-4590-b140-2eaa2863a3ff   ext3                                     
/dev/sda7        ce2a3669-6485-40af-8ee1-06a94109b4a0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda3        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda5        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


=================== sda1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/stage2

============================= sda5/grub/menu.lst: =============================

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
default        saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# howmany=all

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root        (hd0,6)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro quiet splash vga=791
initrd        /initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,6)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro single
initrd        /initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd0,6)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro quiet splash vga=791
initrd        /initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,6)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro single
initrd        /initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,6)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sda5: Location of files loaded by Grub: ===================


 230.9GB: grub/menu.lst
 230.9GB: grub/stage2
 230.8GB: initrd.img-2.6.24-23-generic
 230.8GB: initrd.img-2.6.24-23-generic.bak
 230.8GB: initrd.img-2.6.24-26-generic
 230.8GB: initrd.img-2.6.24-26-generic.bak
 230.7GB: vmlinuz-2.6.24-23-generic
 230.8GB: vmlinuz-2.6.24-26-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=86009ceb-252c-4590-b140-2eaa2863a3ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=28f9470e-7f28-4d44-803b-181cf36b38b8 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=09942f16-fa71-48f2-bb66-b6553caa508e /media/mysql    ext3    relatime        0       3
UUID=ce2a3669-6485-40af-8ee1-06a94109b4a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by coffeecat on 2011-05-10
Hi. You don't, in fact, have the same problem as the OP even though you are getting a similar error message. The OP's problem was a mismatch between the partition table entries and the actual filesystems on two partitions. Your problem is that grub in the mbr is looking to partition sda7 from grub stage 2. Partition sda7 is your swap partition whereas your Ubuntu boot partition where grub stage resides in now sda5. The numbers must have changed when you did your repartitioning, because your /etc/fstab shows that /boot was originally sda7 and that there was no swap partition. You must have changed things in the sda4 extended partition for this renumbering to have occurred. Fortunately, the fstab entries for your boot and root partitions are OK, but you have no fstab entry for your swap partition.

You need to reinstall legacy grub to the mbr. Boot up with a 8.04 Ubuntu live CD and open a terminal. Now:

```
sudo grub
```At the grub prompt:

```
root (hd0,4)
setup (hd0)
quit
```Exit the terminal and reboot and you should be OK. Post back if there are any further problems.

**EDIT**: Whoops! Wait one moment. You will also need to edit your /boot/grub/menu.lst on sda5 from the live CD. You need to change this:

```
title        Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root        (hd0,6)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro quiet splash vga=791
initrd        /initrd.img-2.6.24-26-generic
```

..to this...

```
title        Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root        (hd0,4)
kernel        /vmlinuz-2.6.24-26-generic root=UUID=86009ceb-252c-4590-b140-2eaa2863a3ff ro quiet splash vga=791
initrd        /initrd.img-2.6.24-26-generic
```

Plus every Ubuntu stanza that follows similarly. Post back if you need help with that.

---

### Post by psusi on 2011-05-10
8.04 is also no longer supported on the desktop; you need to upgrade.

---

