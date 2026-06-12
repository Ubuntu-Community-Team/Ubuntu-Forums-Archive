---
title: "Help restoring Ubuntu Grub/Boot Partition"
date: 2009-10-21
forum: General Help
---

### Post by speed32219 on 2009-10-21
Previsouly I had lost my MBR and Partitions (NTFS/EXT3).  I had a dual boot system iwth XB fist and then added Ubuntu 8.10.  I can see a partition out there during a deep scan using testdisk that I am sure has my Ubuntu and Grub, but when I go and try to add it as a partition it gives me a choice of about 15 different types and I do not see one that is ext2/ext3.  It does say xenix, Beos, Ntfs, etc. but no linux ext2 or ext3.  

How do I go about restoring my master MBR (Grub) and Ubuntu partition?

Step by step would be nice.

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by alphaniner on 2009-10-21
I'm not 100% certain, but I suspect that when you select a partition type in testdisk all you are doing is determining is a setting in the partition table, for example what shows up in the ID field in **fdisk -l**:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007abd8

   Device Boot      Start         End      Blocks   **Id**  System
/dev/sda1   *           1        1958    15727603+  **83**  Linux
/dev/sda2            1959        2318     2891700   **82**  Linux swap / Solaris
/dev/sda3            2319        4276    15727635   **83**  Linux
/dev/sda4            4277       43439   314576797+   **5**  Extended
/dev/sda5            4277       43439   314576766   **83**  Linux

```

In other words, like everything else related to your partition table, your choice shouldn't affect your data.  So, unless there are other differences between the options presented by testdisk (ie. partition boundaries or size) just pick something, then use **cfdisk** to change the partition ID.  Then try to **mount** or **fsck** the partition.

Of course, the fact that testdisk can't properly identify the type of partition may be a bad sign...

---

### Post by speed32219 on 2009-10-21
**When I run fdisk -l **

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2df8f3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19456   156280288+   7  HPFS/NTFS



**I'm running from a live cd**

Here is a deep scan using testdisk

Disk /dev/sdc - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   0 63 19456 254 63  312576643 **depress P - Can't open Filesystem**
D HPFS - NTFS              0   1  1 19455 254 63  312560577 **depress P - List of directories & Files**
D HPFS - NTFS              0   1  2 19456 254 63  312576641 **depress P - Can't open Filesystem But I think this is my Ubuntu Partition possibly should be ext3**

**Here is the MS boot ini file**

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"  **<!-- ntldr, wubilder & wubildr.mbr are in the main directory -->**

**Here is the grub menu.list**
I got this by going into the directory Ubuntu/disks/boot/grub

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
# kopt=root=UUID=C06C66CB6C66BC32 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=C06C66CB6C66BC32 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=C06C66CB6C66BC32 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by speed32219 on 2009-10-21
bump

---

### Post by alphaniner on 2009-10-22
```

Disk /dev/sdc - 160 GB / 149 GiB - CHS 19457 255 63
Partition Start End Size in sectors
D HPFS - NTFS 0 0 63 19456 254 63 312576643
[COLOR="Blue"]D HPFS - NTFS 0 1 1 19455 254 63 312560577[/COLOR]
[COLOR="Red"]D HPFS - NTFS 0 1 2 19456 254 63 312576641[/COLOR]
```

If you get a list of files in testdisk with the blue line, the red line is **definitely** not your ext3 partition.  The partition boundaries used by the blue line effectively prevent there from being any other partitions on the device.  And what about your **fdisk -l** output?

```
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, **19457 cylinders**
Units = cylinders of 16065 * 512 = **8225280 bytes**
Disk identifier: 0xc2df8f3f

Device     Boot  Start    End     Blocks     Id    System
/dev/sdc1          1     **19456**  156280288+   7    HPFS/NTFS
```

Is sdc1 a functioning partition?  Because again, it is effectively taking up the entire drive.  The drive is 19457 cylinders, sdc1 goes to cylinder 19456, meaning there is 8225280 bytes of unpartitioned space.

Also, your boot.ini and menu.list files clearly evidence the use of wubi, which I know nothing about.

---

