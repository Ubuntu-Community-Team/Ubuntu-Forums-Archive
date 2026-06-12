---
title: "Error 13: Invalid or Unsupported Executable Format"
date: 2010-06-25
forum: General Help
---

### Post by vmsean on 2010-06-25
Hello all,

I've searched all over the internet and have found numerous threads on this topic, none of which have helped me fix the problem. I'll post as much info I can about my setup.

I have 3 hard drives... one is for ubuntu (9.10), one is for my data, and one is for Windows7. It looks like this:

1st drive (hda) = ubuntu
2nd drive (hdb) = data
3rd drive (hdc) = windows

I used to be able to dual boot no problem (via grub menu) until I updated to Ubuntu 9.10 awhile ago. Now I get the ever so popular "Error 13" message anytime I try to boot into Windows. I've tried everything with regards to tweaking my menu.lst file.

The odd thing is, if I physically remove drives 1 & 2, my computer will boot into windows with no problem, which sort of tells me that I don't need to run any recovery on the windows drive.

Anyhow, here's an output of relevant info. Any help would truly be appreciated.

sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76a6af7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58336   468583888+  83  Linux
/dev/sda2           58337       60801    19800112+   5  Extended
/dev/sda5           58337       60801    19800081   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23c923c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c37e1aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       60802   488282112    7  HPFS/NTFS

```

cat /boot/grub/menu.lst
```

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

title		Windows7
root		(hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

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
# kopt=root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=16b377f6-d52b-46d8-9c28-9605f79a3ccc

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

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-14-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.10, kernel 2.6.28-13-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Output of Boot Info Script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76a6af7e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   937,167,839   937,167,777  83 Linux
/dev/sda2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sda5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23c923c8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c37e1aa

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        16b377f6-d52b-46d8-9c28-9605f79a3ccc   ext3                                     
/dev/sda5        26379c3f-746c-4124-ac6a-ab267718215c   swap                                     
/dev/sdb1        7853eb65-a45f-41f5-aed3-4d48bcc4c2b3   ext4                                     
/dev/sdc1        3A18F1A618F160F5                       ntfs       System Reserved               
/dev/sdc2        26CCF68ECCF6580F                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


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

title		Windows7
root		(hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

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
# kopt=root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=16b377f6-d52b-46d8-9c28-9605f79a3ccc

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

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-14-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.10, kernel 2.6.28-13-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		16b377f6-d52b-46d8-9c28-9605f79a3ccc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=16b377f6-d52b-46d8-9c28-9605f79a3ccc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=26379c3f-746c-4124-ac6a-ab267718215c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 274.0GB: boot/grub/menu.lst
  22.5GB: boot/grub/stage2
  22.4GB: boot/initrd.img-2.6.28-11-generic
  22.5GB: boot/initrd.img-2.6.28-13-generic
  22.4GB: boot/initrd.img-2.6.28-14-generic
  22.5GB: boot/initrd.img-2.6.28-15-generic
  22.5GB: boot/initrd.img-2.6.28-16-generic
  22.4GB: boot/initrd.img-2.6.31-14-generic
  22.4GB: boot/initrd.img-2.6.31-16-generic
  22.4GB: boot/initrd.img-2.6.31-19-generic
  22.5GB: boot/initrd.img-2.6.31-20-generic
  20.3GB: boot/initrd.img-2.6.31-21-generic
  22.5GB: boot/initrd.img-2.6.31-22-generic
  22.4GB: boot/vmlinuz-2.6.28-11-generic
  22.5GB: boot/vmlinuz-2.6.28-13-generic
  22.4GB: boot/vmlinuz-2.6.28-14-generic
  22.4GB: boot/vmlinuz-2.6.28-15-generic
  22.4GB: boot/vmlinuz-2.6.28-16-generic
  22.4GB: boot/vmlinuz-2.6.31-14-generic
  22.5GB: boot/vmlinuz-2.6.31-16-generic
  22.4GB: boot/vmlinuz-2.6.31-19-generic
  22.5GB: boot/vmlinuz-2.6.31-20-generic
  20.2GB: boot/vmlinuz-2.6.31-21-generic
  22.5GB: boot/vmlinuz-2.6.31-22-generic
  22.5GB: initrd.img
  20.3GB: initrd.img.old
  22.5GB: vmlinuz
  20.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 

```

Thanks,

-Sean

---

### Post by davidmohammed on 2010-06-25
Hi there,
  at a guess change your menu.lst file from
title		Windows7
root		(hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

to

title		Windows7
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

---

### Post by vmsean on 2010-06-25
> **davidmohammed said:**
> Hi there,
  at a guess change your menu.lst file from
title		Windows7
root		(hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

to

title		Windows7
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

Tried that - same outcome.

---

### Post by rob45 on 2010-06-25
hi...im not sure if you can get dual boot using seperate hd's,i think you have to have separate partions on same drive to achieve dual boot.you can press escape during boot,then select which hd you want to boot from,personnaly i would use that method...its simplist choice.

---

### Post by vmsean on 2010-06-25
> **rob45 said:**
> hi...im not sure if you can get dual boot using seperate hd's,i think you have to have separate partions on same drive to achieve dual boot.you can press escape during boot,then select which hd you want to boot from,personnaly i would use that method...its simplist choice.

It was working a month ago... I've never heard that using separate hard drives wasn't an option.

---

### Post by davidmohammed on 2010-06-26
... suggest [upgrade to grub2]("http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/") - for me it makes booting windows from a second drive a snip.

---

### Post by vmsean on 2010-06-28
> **davidmohammed said:**
> ... suggest [upgrade to grub2]("http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/") - for me it makes booting windows from a second drive a snip.

That did the trick. Now I can boot from either drive.

The only thing I have to add to the instructions you posted relates to choosing your bootable drives. For me, It was hard drive #1 and #3 (ubuntu and windows, respectively) which means I chose to mark sda and sdc as bootable.

Thanks!

-Sean

---

