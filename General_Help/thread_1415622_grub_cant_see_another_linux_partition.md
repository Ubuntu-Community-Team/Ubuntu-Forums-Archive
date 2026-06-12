---
title: "grub cant see another linux partition"
date: 2010-02-25
forum: General Help
---

### Post by alphageek89 on 2010-02-25
i had ubuntu installed on sda7.Now i installed it on one more partition sda10.It gave an ubiquity error when installing grub.I used the live cd to install grub. It still does not show the other ubuntu i installed.

This is how i installed grub from the live cd
sudo grub
find /boot/grub/stage1----it gave me hd0,7
root (hd0,7)
setup (hd0)


when i tried to do root (hd0,10) it said not a valid partition.


this is my fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x97be5b6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6774    51211408+   7  HPFS/NTFS
/dev/sda2            6775       20673   105076409    5  Extended
/dev/sda5            6775       13548    51211408+   7  HPFS/NTFS
/dev/sda6           13549       13562      105808+  83  Linux
/dev/sda7           13563       13701     1050808+  82  Linux swap / Solaris
/dev/sda8           13702       15733    15360000   83  Linux
/dev/sda9           17765       20673    21992008+   7  HPFS/NTFS
/dev/sda10          15734       17764    15350076   83  Linux

---

### Post by oldfred on 2010-02-25
Lets run this script to confirm what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by drs305 on 2010-02-25
Grub legacy and Grub 2 use different ways of naming partitions. If you are using Grub legacy, sda10 would be (hd0,9). The results from the boot info script will reveal all.

---

### Post by alphageek89 on 2010-02-26
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /menu.lst

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97be5b6a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,422,879   102,422,817   7 HPFS/NTFS
/dev/sda2         102,422,942   312,575,759   210,152,818   5 Extended
/dev/sda5         102,422,943   204,845,759   102,422,817   7 HPFS/NTFS
/dev/sda6         204,845,823   205,057,439       211,617  83 Linux
/dev/sda7         205,057,503   207,159,119     2,101,617  82 Linux swap / Solaris
/dev/sda8         207,159,183   237,879,182    30,720,000  83 Linux
/dev/sda9         268,591,743   312,575,759    43,984,017   7 HPFS/NTFS
/dev/sda10        237,890,583   268,590,734    30,700,152  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda10       83f5cf6d-2138-414c-b285-2dd0aaccc505   ext3                                     
/dev/sda1        252270B4333C46A3                       ntfs                                     
/dev/sda5        28CC02FCCC02C3D2                       ntfs                                     
/dev/sda6        bde6e778-f2d0-4314-ae46-9560c97041ce   ext3                                     
/dev/sda7        cc2daceb-0ade-4c16-b2a3-47745b766ce4   swap                                     
/dev/sda8        5de6540d-4843-49df-8e3e-ee95d4a104ea   ext3                                     
/dev/sda9        BEEC8386EC833823                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/c                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/d                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9        /media/e                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5de6540d-4843-49df-8e3e-ee95d4a104ea

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, memtest86+
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cc2daceb-0ade-4c16-b2a3-47745b766ce4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/c ntfs-3g defaults 0 0
/dev/sda5 /media/d ntfs-3g defaults 0 0
/dev/sda9 /media/e ntfs-3g defaults 0 0

=================== sda8: Location of files loaded by Grub: ===================


 115.7GB: boot/grub/menu.lst
 114.8GB: boot/grub/stage2
 114.8GB: boot/initrd.img-2.6.31-19-generic
 114.8GB: boot/vmlinuz-2.6.31-19-generic
 114.8GB: initrd.img
 114.8GB: vmlinuz

================================ sda9/menu.lst: ================================

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
# kopt=root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5de6540d-4843-49df-8e3e-ee95d4a104ea

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, memtest86+
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda9: Location of files loaded by Grub: ===================


    ??GB: menu.lst

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=83f5cf6d-2138-414c-b285-2dd0aaccc505 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cc2daceb-0ade-4c16-b2a3-47745b766ce4 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 122.3GB: boot/vmlinuz-2.6.28-11-generic
 122.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

```

---

### Post by drs305 on 2010-02-26
Let's first just try to add the sda10 linux install to your existing entry to see if it boots. Note this will still be using the Grub installed on sda8, but we can at least see if sda10 is working properly.

Open grub for editing:
```
gksu gedit /boot/grub/menu.lst
```
Add this entry *to the end*, save the file, and reboot. Select the new entry:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5de6540d-4843-49df-8e3e-ee95d4a104ea
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5de6540d-4843-49df-8e3e-ee95d4a104ea ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11 generic
quiet

---

### Post by oldfred on 2010-02-26
The sda10 does not look complete. No initrd files. There is also a menu.lst in sda9, but not in sda10? But the fstab looks ok. So I do not think it will boot. 
Can you check your /boot and /boot/grub in sda10 to see if the files are there and just not listed?

---

### Post by drs305 on 2010-02-26
Heh! I'd made the same comment about the missing initrd file but it disappeared. Recently I have to post twice due to a continuing "missing security" file or some such. 

What got dropped was that the initrd file appeared to be missing but I didn't know if that was a function of the boot info script or if the file was actually missing (in which it won't boot). 

I suggested trying to boot from the new menu item and report the results. (Well, I suggested it to myself apparently).  And is anyone else experiencing the VBulletin security issue?

---

### Post by alphageek89 on 2010-02-26
> **oldfred said:**
> The sda10 does not look complete. No initrd files. There is also a menu.lst in sda9, but not in sda10? But the fstab looks ok. So I do not think it will boot. 
Can you check your /boot and /boot/grub in sda10 to see if the files are there and just not listed?

this is my files under the /boot directory. I guess the grub folder is not there because when i was installing it it gave me an ubiquity error when installing grub

```

total 14544
-rw-r--r-- 1 root root  629446 2010-01-28 10:09 abi-2.6.31-19-generic
-rw-r--r-- 1 root root  111371 2010-01-28 10:09 config-2.6.31-19-generic
drwxr-xr-x 2 root root    4096 2010-02-26 21:02 grub
-rw-r--r-- 1 root root 8409237 2010-02-07 16:30 initrd.img-2.6.31-19-generic
-rw-r--r-- 1 root root  128796 2009-10-23 21:41 memtest86+.bin
-rw-r--r-- 1 root root 1665617 2010-01-28 10:09 System.map-2.6.31-19-generic
-rw-r--r-- 1 root root    1196 2010-01-28 10:11 vmcoreinfo-2.6.31-19-generic
-rw-r--r-- 1 root root 3891264 2010-01-28 10:09 vmlinuz-2.6.31-19-generic


```

and adding the lines to the menu.lst did not help.It says File Not Found.

---

### Post by oldfred on 2010-02-26
Did you post sda8 not sda10, as sda8 had ver 19 where sda10 was
122.3GB: boot/vmlinuz-2.6.28-11-generic

---

### Post by alphageek89 on 2010-02-28
sorry that was from /dev/sda8.This is the one from sda10

```

-rw-r--r-- 1 root root  529118 2009-04-17 09:11 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   96795 2009-04-17 09:11 config-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-03-27 22:45 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-17 09:11 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-17 09:13 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501776 2009-04-17 14:41 vmlinuz-2.6.28-11-generic


```

---

### Post by oldfred on 2010-02-28
If you think your install in sda10 is just missing some files you can chroot into it and update it. I show updating grub but I do not know if other updates are required.

sudo mount /dev/sda10 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get remove grub
apt-get install grub
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

