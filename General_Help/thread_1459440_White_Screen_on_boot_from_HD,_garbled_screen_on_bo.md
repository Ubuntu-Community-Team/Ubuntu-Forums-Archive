---
title: "White Screen on boot from HD, garbled screen on boot from CD Ubuntu 9.04"
date: 2010-04-21
forum: General Help
---

### Post by LinuxNeubie on 2010-04-21
First, I've never used Linux - at all - and have NO idea what I'm doing. Originally I installed Ubuntu with a partition that was too small for any practical use, so I installed it again, thinking it would simply overwrite the other one as Windows would do. Obviously not. Now I have two Ubunto installations, neither of which work. I get a White Screen after the Ubuntu thing that shows its progress. If I try to boot from the CD, the Ubuntu thing works again, then I get a completely garbled screen which is totally unreadable and unuseable. I should also mention that I originally installed with a 19" square flatscreen from HP, but have upgraded to an Acer H233H. Since I have no clue what to do whatsover Ubuntu is just taking up space. I'd like to be able to use it, and I'd like to be able to get rid of one or other of the installations. All help would be appreciated.

---

### Post by 666f6f on 2010-04-21
Hi, welcome to the forums.

First of, we need to identify your [disk partitions]("http://en.wikipedia.org/wiki/Disk_partitioning").

1. Load Ubuntu from the CD
2. Open a terminal (hit Alt+F2, type gnome-terminal) and type ```
sudo fdisk -l > ~/Desktop/disks.txt
```
3. Post the contents of the disks.txt file (found on your Desktop).

---

### Post by LinuxNeubie on 2010-04-22
Well if I could see anything at all I would. When I boot from the CD, all I get is about 80 or so vertical blinking lines. Alt+f2 doesn't do anything, or if it does I can't see it. Thanks for the reply. Any other thoughts?

---

### Post by LinuxNeubie on 2010-04-22
Or do you mean at the first screen, before it actually tries to do anything else? And whichever the case, I wouldn't be able to see the "desktop" on anything but windows, unless there's a way to write the file directly to the root of C:\ in the NTFS. Thanks!

---

### Post by klemes on 2010-04-22
There is an option in the LiveCD to use safe grahics mode.Have you used it?

---

### Post by LinuxNeubie on 2010-04-22
No, I'll try it though. Thanks!

---

### Post by LinuxNeubie on 2010-04-22
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe93b722a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35391   284278176    7  HPFS/NTFS
/dev/sda2           35392       36481     8755393+   c  W95 FAT32 (LBA)
/dev/sda3           36482       60475   192731805    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32541   261385551    7  HPFS/NTFS
/dev/sdb2           32542       36481    31648050    5  Extended
/dev/sdb5           33887       36367    19928601   83  Linux
/dev/sdb6           36368       36481      915673+  82  Linux swap / Solaris
/dev/sdb7           32542       33823    10297602   83  Linux
/dev/sdb8           33824       33886      506016   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by LinuxNeubie on 2010-04-22
Obviously I was able to get it to boot from the LiveCD after telling it to use safe graphics mode - thanks for the help. What you see above is the info it gave me for the fdisk -l command. Is there a way to install the correct monitor driver now or do I need to re-re-reinstall? Thanks!

---

### Post by klemes on 2010-04-22
It seems you have two different Linux installations as you said you had ,complete with two separate swap partitions as well,unless of course you have split the /home or some other directory into a separate partition which I do not think it's the case.If you do not have any data that needs to be salvaged first I would definately advise to proceed with a fresh installation ,and while at it delete ALL the Linux partitions (/ + swaps) and repartition the resulting free space roughly as follows:

sdb2 ->  swap -> 2GB
sdb3 -> / (root) -> about 20GB
sdb4 -> /home  -> rest of free space

-Note that you amy or may not need a logical extended partition but this you'll know it after making sdb2 partition. Then it will or it will NOT  allow you to make any more primary partitions . In the later case you will have to make an extended partition and tehn carry on with adding more partitions.. 
If your free space is not big enough and you are not planning to install kernel sources etc
you could opt for a smaller root partition(but not smaller than 10 GBs)
Good Luck!!!!:popcorn:

---

### Post by 666f6f on 2010-04-22
Definetely agree with klemes about disk partitioning, although I'm not sure that re-re-reinstall will solve the problem. I say that because neither the Live CD nor the two installations will successfuly boot into a graphical environment.

LinuxNeubie, before re^n-installing, can you please try the following:

1. Boot the LiveCD using safe graphics mode (klemes clever suggestion)
2. Open a terminal and type ```
wget http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh?use_mirror=kent && chmod +x boot_info_script055.sh && sudo ./boot_info_script055.sh && sudo mv RESULTS.txt ~/Desktop && sudo lshw > ~/Desktop/lshw.txt
```
3. Post here the RESULTS.txt and lshw.txt, found on your desktop.

---

### Post by LinuxNeubie on 2010-04-23
OK, I'll do the webpage and post it shortly. Thanks!

---

### Post by LinuxNeubie on 2010-04-23
This is the "Results.txt" paste:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe93b722a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   568,556,414   568,556,352   7 HPFS/NTFS
/dev/sda2         568,556,478   586,067,264    17,510,787   c W95 FAT32 (LBA)
/dev/sda3         586,067,265   971,530,874   385,463,610   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   522,771,164   522,771,102   7 HPFS/NTFS
/dev/sdb2         522,771,165   586,067,264    63,296,100   5 Extended
/dev/sdb5         544,378,653   584,235,854    39,857,202  83 Linux
/dev/sdb6         584,235,918   586,067,264     1,831,347  82 Linux swap / Solaris
/dev/sdb7         522,771,291   543,366,494    20,595,204  83 Linux
/dev/sdb8         543,366,558   544,378,589     1,012,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        566C3BDC6C3BB619                       ntfs       Main 500gb                    
/dev/sda2        0C76-7023                              vfat       DO NOT USE                    
/dev/sda3        8A98B67A98B663FB                       ntfs       3 500gb                       
/dev/sdb1        E418BF9B18BF6AE6                       ntfs       300gb                         
/dev/sdb5        18c29f6f-fbb4-4afe-989d-a57a54c94d04   ext3                                     
/dev/sdb6        21814824-758a-4194-9e71-561739c7b33b   swap                                     
/dev/sdb7        4968e588-4834-4cae-9ea0-e8add2fe2280   ext3                                     
/dev/sdb8        30f560bf-f875-4627-bc2c-8b3b01a77f21   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/3 500gb           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/300gb             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/Main 500gb        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="XP Pro"  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition"  /bootlog 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18c29f6f-fbb4-4afe-989d-a57a54c94d04

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

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        18c29f6f-fbb4-4afe-989d-a57a54c94d04
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        18c29f6f-fbb4-4afe-989d-a57a54c94d04
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        18c29f6f-fbb4-4afe-989d-a57a54c94d04
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        18c29f6f-fbb4-4afe-989d-a57a54c94d04
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        18c29f6f-fbb4-4afe-989d-a57a54c94d04
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=21814824-758a-4194-9e71-561739c7b33b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 285.6GB: boot/grub/menu.lst
 285.6GB: boot/grub/stage2
 285.6GB: boot/initrd.img-2.6.28-11-generic
 285.6GB: boot/initrd.img-2.6.28-18-generic
 285.6GB: boot/vmlinuz-2.6.28-11-generic
 285.6GB: boot/vmlinuz-2.6.28-18-generic
 285.6GB: initrd.img
 285.6GB: initrd.img.old
 285.6GB: vmlinuz
 285.6GB: vmlinuz.old

=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4968e588-4834-4cae-9ea0-e8add2fe2280 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4968e588-4834-4cae-9ea0-e8add2fe2280

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4968e588-4834-4cae-9ea0-e8add2fe2280
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4968e588-4834-4cae-9ea0-e8add2fe2280 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4968e588-4834-4cae-9ea0-e8add2fe2280
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4968e588-4834-4cae-9ea0-e8add2fe2280 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4968e588-4834-4cae-9ea0-e8add2fe2280
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18c29f6f-fbb4-4afe-989d-a57a54c94d04 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=4968e588-4834-4cae-9ea0-e8add2fe2280 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=30f560bf-f875-4627-bc2c-8b3b01a77f21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 276.5GB: boot/grub/menu.lst
 276.7GB: boot/grub/stage2
 276.5GB: boot/initrd.img-2.6.28-11-generic
 275.2GB: boot/vmlinuz-2.6.28-11-generic
 276.5GB: initrd.img
 275.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

This is the "lshw.txt" paste:

ubuntu
    description: Desktop Computer
    product: EX511AA-ABA m7463w
    vendor: HP Pavilion 061
    version: 0ny1114RE101EMERY00
    serial: MXF61704LV NA660
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=80ACFB87-8F40-1110-8EEC-8266BA1F3DF9
  *-core
       description: Motherboard
       product: EMERY
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.05
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.19 (12/08/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.2
          serial: 0000-0F62-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: f
             slot: L3 Cache
             capabilities: synchronous internal varies
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: 15.6.2
          serial: 0000-0F62-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 3800MHz
          clock: 200MHz
          capabilities: vmx ht
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 10
             slot: L3 Cache
             capabilities: synchronous internal varies
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
           *-network:0
                description: Wireless interface
                product: AR5413 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: wmaster0
                version: 01
                serial: 00:c0:a8:b1:f2:d2
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.3 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
           *-communication UNCLAIMED
                description: Communication controller
                product: Agere Systems
                vendor: Agere Systems
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-network:1
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:17:31:35:81:e0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom:0
                description: DVD-RAM writer
                product: CD/DVDW TS-H652L
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 0603
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
           *-cdrom:1
                description: DVD reader
                product: DROM6216
                vendor: IDE-DVD
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: HD08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: ST3500410AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: CC37
                serial: 5VM1L69T
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e93b722a
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Main 500gb
                   version: 3.1
                   serial: 92863e26-59ff-6845-9117-232a7c6e99fc
                   size: 271GiB
                   capacity: 271GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-04-27 16:58:07 filesystem=ntfs label=Main 500gb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows FAT volume
                   vendor: RECOVERY
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: FAT32
                   serial: 0c76-7023
                   size: 8534MiB
                   capacity: 8550MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/3 500gb
                   version: 3.1
                   serial: c6e8cfe1-b2be-2141-a521-abd107bb99a4
                   size: 183GiB
                   capacity: 183GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-13 16:23:53 filesystem=ntfs label=3 500gb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD3000JS-60P
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 21.0
                serial: WD-WCAPD1338235
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cab10bee
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/300gb
                   version: 3.1
                   serial: 668c1de6-d946-c34d-8051-d138f7a7af9a
                   size: 249GiB
                   capacity: 249GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-13 17:07:05 filesystem=ntfs label=300gb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 19GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 894MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sdb7
                      capacity: 10056MiB
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sdb8
                      capacity: 494MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@5:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:3c:ca:bd:ae:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by 666f6f on 2010-04-23
OK, thanks for posting the info! Can you please pick one of the two Ubuntu installation and try the following:

1. Boot into recovery mode.
2. Type ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo apt-get install nvidia-glx-185
```
3. Reboot (the same Ubuntu installation) and see if you have a graphical environment?

---

### Post by klemes on 2010-04-23
Your advice is very sound regarding the script and the driver choice suggestion but maybe you missed the fact that he has two identical installations of Ubuntu in his hard disk drive complete with two swaps.
I mean it's a complete waste of hard disk space.That's why I suggested he repartitioned his hard disk drive first and reinstall a single Ubuntu this time and then try to fix his video card drivers issue.:popcorn:
Also I am under the impression he's posting booting off of a Live CD so what's the use to install graphics drivers in that?

---

### Post by 666f6f on 2010-04-23
> **klemes said:**
> Your advice is very sound regarding the script and the driver choice suggestion but maybe you missed the fact that he has two identical installations of Ubuntu in his hard disk drive complete with two swaps.

I mean it's a complete waste of hard disk space.That's why I suggested he repartitioned his hard disk drive first and reinstall a single Ubuntu this time and then try to fix his video card drivers issue.:popcorn:

I can't agree more, it's a complete waste of space and he should re-install and re-partition as you suggested in your earlier post (although I'm not sure if a swap of 2GB is too much or too low since we don't know his physical memory, we should decide based on the amount of his physical memory and the [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") suggestions).

Probably it would be better to first re-install and then fix the problem since it would avoid repeating the steps to fix the problem, but on the other hand, repetition is the father of learning :)

> **klemes said:**
> Also I am under the impression he's posting booting off of a Live CD so what's the use to install graphics drivers in that?

You're right, that's why I asked him to pick an installation and boot in recovery mode.

---

### Post by LinuxNeubie on 2010-04-23
Well, while I'd like to get rid of one or the other or both, my Windows installation is on the same drive as the Linux installs. I have to have my XP, because - unlike you fellows who've been at this a while - I'm lost without it. Just what Bill Gates likes, eh? Is there not a way to fix the one - and I'll try your option to do so - then delete the other and use the space like just another partition? I could certainly do that with Windows and I'd think there'd be a way to do that with Linux. For instance, when I went to "Update" it said I didn't have enough disk space. Can't you tell it where to place the files to do the update? I forget offhand what size I made the partitions, but I believe the first one was 10 gigs or so. Anyway, thanks for the replies! I'll try the upgrade next.

---

### Post by 666f6f on 2010-04-23
> **LinuxNeubie said:**
> Is there not a way to fix the one - and I'll try your option to do so - then delete the other and use the space like just another partition?

Yes there is a way, that's what klemes is suggested in the first place and that's where we're heading at :)

I just wanted to find out where the problem is, prior to re-arrange stuff. The order is not so important, you may first re-arrange and then fix.

---

### Post by LinuxNeubie on 2010-04-23
Well I tried two things. First, I tried sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo apt-get install nvidia-glx-185. Now, I didn't know where to do this, since the recovery mode has several different options and being green as a gourd (assume I know NOTHING please!) I chose the something or other shell without networking. when I input the string it said the file was not found. I'm sure I did something wrong, probably didn't choose the right option. Secondly I tried the "try to auto-fix graphics" option, which gave me the logon sound with a nice black screen instead of the blinking vertical lines. I'm sure you fellows get tired of idiots who know nothing like me, but surely everyone was at this point sometime :) Thanks!

---

### Post by 666f6f on 2010-04-23
> **LinuxNeubie said:**
> I'm sure you fellows get tired of idiots who know nothing like me, but surely everyone was at this point sometime :) Thanks!

You must be saying this because you're a kind person but, in any case, I have to totally disagree with you. We're not tired and the thing is that noone obliges us to be here and help, we do this voluntarily for various reasons, one of which is joy! Others may wish to supplement this list. That said, I consider myself a very small and insignificant contributor, based on facts :)

Regarding the actual problem, working on it...

---

### Post by 666f6f on 2010-04-23
> **LinuxNeubie said:**
> Well I tried two things. First, I tried sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo apt-get install nvidia-glx-185. Now, I didn't know where to do this, since the recovery mode has several different options and being green as a gourd (assume I know NOTHING please!) I chose the something or other shell without networking. when I input the string it said the file was not found. I'm sure I did something wrong, probably didn't choose the right option. Secondly I tried the "try to auto-fix graphics" option, which gave me the logon sound with a nice black screen instead of the blinking vertical lines. I'm sure you fellows get tired of idiots who know nothing like me, but surely everyone was at this point sometime :) Thanks!

In the recovery mode options screen, choose the last option, drop to shell, but **not** the drop to shell without networking option, we need the network to download the drivers. However, if you connect to a Wireless network this might not work either. So..

Are you connecting to a Wireless network? If yes, there are some alternatives.

Regarding the command I gave you to execute, I'm sorry, I'm stupid and I gave you a buggy script which didn't manage to install the nVIDIA drivers. Can you please try again using just this: ```
sudo apt-get install nvidia-glx-185
```

---

### Post by LinuxNeubie on 2010-04-23
Yes it's a wireless network. can I put the drivers on a disk and install them from there? or somewhere on the HD from the LiveCD safeboot?

---

### Post by 666f6f on 2010-04-23
Yes you could try that, but before that, I'm curious to ask and maybe I should have asked earlier, is there a particular reason you're not using Ubuntu Karmic 9.10? The problem may have been fixed there.

---

### Post by LinuxNeubie on 2010-04-23
Well, being a noob, I didn't know which one to get. No problem to download whichever one will work if you have one you think will work better. I saw a thread about a new Linux something-or-other being released in 16 days or so. Frankly, I see many different ones like Kibuntu, Ubuntu, etc., but I have no idea what each one does differently than the others.

---

### Post by 666f6f on 2010-04-23
> **LinuxNeubie said:**
> Well, being a noob, I didn't know which one to get. No problem to download whichever one will work if you have one you think will work better.

I would suggest to 

1. go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click download.
2. Burn the ISO and see if it boots into a graphical environment, hopefully it will!

> **LinuxNeubie said:**
> I saw a thread about a new Linux something-or-other being released in 16 days or so. Frankly, I see many different ones like Kibuntu, Ubuntu, etc., but I have no idea what each one does differently than the others.

The good and bad at the same time thing about Linux and Open source software is choice, but you can safely ignore the alternatives for the time being.

---

### Post by LinuxNeubie on 2010-04-24
Downloading the 9.1 version. You're right 666f6 - I don't see how "Mark as solved" once we do figure it out, so it DOES need to be more accessible.

---

### Post by LinuxNeubie on 2010-04-24
well this one's even worse - it does absolutely nothing except come up to the white ubuntu thing and sit there doing nothing - in every mode it gives an option for, including checking the disk for errors, which it shouldn't have considering I burned it from the ISO to a new disc, never even removed it from the tray and rebooted to it. hmm

---

### Post by 666f6f on 2010-04-24
I've searched through the forums and there other HP Pavilion 061 owners reporting the same problem, like [here]("ubuntuforums.org/showthread.php?t=619645"), and [here]("http://ubuntuforums.org/showthread.php?t=981613"). I know it's very annoying, please be patient and take a pause as I search for a solution.

Why is all this happening? Well, not all hardware manufacturers want their products to be Linux friendly, that's why you should choose your equipment carefully. How to know what hardware to buy? Well, you're always welcome to ask here :)

---

### Post by LinuxNeubie on 2010-04-24
Tried also installing it into windows. Logfile paste is as follows:
04-24 07:53 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-24 07:53 DEBUG  root: Logfile is d:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-24 07:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="K:\\wubi.exe"']
04-24 07:53 DEBUG  CommonBackend: data_dir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data
04-24 07:53 DEBUG  WindowsBackend: 7z=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\bin\7z.exe
04-24 07:53 DEBUG  CommonBackend: Fetching basic info...
04-24 07:53 DEBUG  CommonBackend: original_exe=K:\wubi.exe
04-24 07:53 DEBUG  CommonBackend: platform=win32
04-24 07:53 DEBUG  CommonBackend: osname=nt
04-24 07:53 DEBUG  CommonBackend: language=en_US
04-24 07:53 DEBUG  CommonBackend: encoding=cp1252
04-24 07:53 DEBUG  WindowsBackend: arch=amd64
04-24 07:53 DEBUG  CommonBackend: Parsing isolist=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\isolist.ini
04-24 07:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 07:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 07:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 07:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 07:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 07:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 07:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 07:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 07:53 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-24 07:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-24 07:53 DEBUG  WindowsBackend: Fetching host info...
04-24 07:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 07:53 DEBUG  WindowsBackend: windows version=xp
04-24 07:53 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-24 07:53 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-24 07:53 DEBUG  WindowsBackend: windows_build=2600
04-24 07:53 DEBUG  WindowsBackend: gmt=-5
04-24 07:53 DEBUG  WindowsBackend: country=US
04-24 07:53 DEBUG  WindowsBackend: timezone=America/New_York
04-24 07:53 DEBUG  WindowsBackend: windows_username=Owner
04-24 07:53 DEBUG  WindowsBackend: user_full_name=Owner
04-24 07:53 DEBUG  WindowsBackend: user_directory=D:\Documents and Settings\Owner
04-24 07:53 DEBUG  WindowsBackend: windows_language_code=1033
04-24 07:53 DEBUG  WindowsBackend: windows_language=English
04-24 07:53 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) D CPU 3.00GHz
04-24 07:53 DEBUG  WindowsBackend: bootloader=xp
04-24 07:53 DEBUG  WindowsBackend: system_drive=Drive(D: hd 238106.871094 mb free ntfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(C: hd 113182.730469 mb free ntfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(D: hd 238106.871094 mb free ntfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(I: hd 575.15234375 mb free fat32)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(J: hd 85758.1132813 mb free ntfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free cdfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(M: remote 80180.8125 mb free ntfs)
04-24 07:53 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
04-24 07:53 DEBUG  WindowsBackend: uninstaller_path=None
04-24 07:53 DEBUG  WindowsBackend: previous_target_dir=None
04-24 07:53 DEBUG  WindowsBackend: previous_distro_name=None
04-24 07:53 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 07:53 DEBUG  WindowsBackend: keyboard_layout=us
04-24 07:53 DEBUG  WindowsBackend: keyboard_variant=
04-24 07:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-24 07:53 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 07:53 DEBUG  WindowsBackend: total_memory_mb=2046.4140625
04-24 07:53 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 07:53 DEBUG  CommonBackend: Searching for local CDs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 07:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 07:53 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-24 07:53 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
04-24 07:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
04-24 07:53 INFO   Distro: Found a valid CD for Ubuntu: K:\
04-24 07:53 INFO   root: Running the CD menu...
04-24 07:53 DEBUG  WindowsFrontend: __init__...
04-24 07:53 DEBUG  WindowsFrontend: on_init...
04-24 07:53 INFO   WinuiPage: appname=wubi, localedir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
04-24 07:53 INFO   WinuiPage: appname=wubi, localedir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
04-24 07:54 INFO   root: CD menu finished
04-24 07:54 INFO   root: Running the installer...
04-24 07:54 INFO   WinuiPage: appname=wubi, localedir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
04-24 07:54 INFO   WinuiPage: appname=wubi, localedir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
04-24 07:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=owner
04-24 07:56 INFO   root: Received settings
04-24 07:56 INFO   WinuiPage: appname=wubi, localedir=D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
04-24 07:56 DEBUG  TaskList: # Running tasklist...
04-24 07:56 DEBUG  TaskList: ## Running select_target_dir...
04-24 07:56 INFO   WindowsBackend: Installing into C:\ubuntu
04-24 07:56 DEBUG  TaskList: ## Finished select_target_dir
04-24 07:56 DEBUG  TaskList: ## Running create_dir_structure...
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-24 07:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-24 07:56 DEBUG  TaskList: ## Finished create_dir_structure
04-24 07:56 DEBUG  TaskList: ## Running uncompress_target_dir...
04-24 07:56 DEBUG  TaskList: ## Finished uncompress_target_dir
04-24 07:56 DEBUG  TaskList: ## Running create_uninstaller...
04-24 07:56 DEBUG  WindowsBackend: Copying uninstaller K:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-24 07:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-24 07:56 DEBUG  TaskList: ## Finished create_uninstaller
04-24 07:56 DEBUG  TaskList: ## Running copy_installation_files...
04-24 07:56 DEBUG  WindowsBackend: Copying D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-24 07:56 DEBUG  WindowsBackend: Copying D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\winboot -> C:\ubuntu\winboot
04-24 07:56 DEBUG  WindowsBackend: Copying D:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-24 07:56 DEBUG  TaskList: ## Finished copy_installation_files
04-24 07:56 DEBUG  TaskList: ## Running get_iso...
04-24 07:56 DEBUG  TaskList: New task copy_file
04-24 07:56 DEBUG  TaskList: ### Running copy_file...
04-24 07:59 DEBUG  TaskList: ### Finished copy_file
04-24 07:59 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-24 07:59 DEBUG  TaskList: # Cancelling tasklist
04-24 07:59 DEBUG  TaskList: New task check_iso
04-24 07:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-24 07:59 DEBUG  CommonBackend: Searching for local ISO
04-24 07:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-24 07:59 DEBUG  TaskList: New task get_metalink
04-24 07:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-24 07:59 DEBUG  TaskList: # Cancelling tasklist
04-24 07:59 DEBUG  TaskList: # Finished tasklist

---

### Post by LinuxNeubie on 2010-04-24
IOError - in windows that would be a disk I think, but it installed 690mb worth of stuff into c:\ububtu. Permissions would be as if it weren't running on administrator privelidges, which it should have been since the only user is an administrator. hmmm again

---

### Post by LinuxNeubie on 2010-04-24
I do have another machine, but it's a Dell server box I traded for that the kids use, and if I had more funds I would build my own. Unfortunately I don't and what I have is what I have :)

---

### Post by LinuxNeubie on 2010-04-24
Well I thought I'd be smart and boot from the LiveCD and go down to the partition with the grub boot file and change it so it wouldn't keep booting to a non-working ubuntu, but alas, I'm "not the owner" and can't change the file. So does that mean I can't change it for any reason without being able to boot into it? If so that kinda bites - even in XP I can load a "mini" xp and change whatever I need to if something is screwed up in my regular xp. So, unless we come to some resolution I'm just stuck with 30gb of space out there in nowhere-partition-land?

---

### Post by 666f6f on 2010-04-25
Hi LinuxNeubie,

First off I have a question, in one of your first posts you said:

> **LinuxNeubie said:**
> Well if I could see anything at all I would. When I boot from the CD, all I get is about 80 or so vertical blinking lines. Alt+f2 doesn't do anything, or if it does I can't see it. Thanks for the reply. Any other thoughts?

My question is how did you install in the first place? Maybe that'll help.

Another general question: Can you temporarily connect your machine to the network via an Ethernet cable, or the rest cohabitants (wife/girlfriend/room-mates/co-students/e.t.c.) will be yelling at you? :) That would simplify some steps.

> **LinuxNeubie said:**
> well this one's even worse - it does absolutely nothing except come up to the white ubuntu thing and sit there doing nothing - in every mode it gives an option for, including checking the disk for errors, which it shouldn't have considering I burned it from the ISO to a new disc, never even removed it from the tray and rebooted to it. hmm

It seems we have some serious problem setting up X, don't we? :) Failsafe mode doesn't work so, from here on I can see the following options:

A. *Somehow* (I'm not sure how you installed in the first place) OR by using the failsafe mode re-install Jaunty (Ubuntu 9.04). We'll then install the X drivers (nvidia-glx-180) and pick-up from were we left *some posts ago*.

I'm not very fond of this options because Karmic (Ubuntu 9.10) is the currently maintained release, 9.04 is not anymore in the spotlight.

B. Download the Karmic Alternate CD found [here]("http://ftp.uni-erlangen.de/mirrors/ubuntu-releases/karmic/ubuntu-9.10-alternate-i386.iso") and [perform a text-base installation]("http://ubuntuforums.org/showthread.php?t=211948"). We'll then install the X drivers (nvidia-glx-185).

I'd would probably vote for this solution, but it depends on the answers you'll give in the questions above.

If you feel you have a fast computer available, you may want to test the text-based installation in a virtual machine before to run the real install. Have a look at [this video]("http://www.youtube.com/watch?v=c9ObBRh2M1I") on how to do that. The video's using the Graphical installer, couldn't find one that uses the text-based one.

C. Try another Linux distribution, maybe [Mint]("http://distrowatch.com/table.php?distribution=mint")? I'm not sure what will work best so can't make any real recommendations here. 

D. Give up because Linux has disappointed you, although sad it's still an option.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> Well I thought I'd be smart and boot from the LiveCD and go down to the partition with the grub boot file and change it so it wouldn't keep booting to a non-working ubuntu, but alas, I'm "not the owner" and can't change the file. So does that mean I can't change it for any reason without being able to boot into it? If so that kinda bites - even in XP I can load a "mini" xp and change whatever I need to if something is screwed up in my regular xp. So, unless we come to some resolution I'm just stuck with 30gb of space out there in nowhere-partition-land?

You are the absolute owner of your files and you can do any change you want, that's for sure. Try the following:

1. Open a terminal and type sudo -i, you;ll be dropped to an administrator shell.
2. Edit your files from the command prompt or type nautilus, the file manager will come up with administrator privileges.

Be very very ... very careful with what you do while you are in an administrator context.

---

### Post by Krayona on 2010-04-25
Not sure if it is related, but I frequently get white screen since switching to 10.04. Never had the problem with 9.04. I have to just keep rebooting and eventually it will boot normally. I have posted my problem on general forum.

---

### Post by LinuxNeubie on 2010-04-25
Initial Install - When I first installed it, as I think I posted, I had another monitor, a 19" HP vs19e, although I didn't mention the actual model. Anyway, what I have now is an Acer H233H 23" widescreen monitor. At one point I changed the video card from an Nvida 6300LE with 256mb to an Nvidia 7300GT with 512mb, although I'm fairly sure I didn't make that change after Ubuntu because I've had the card for months. 

LAN - I don't have the option of setting my computer up with the LAN directly because it's an old house, only ONE telephone line (DSL - we don't get cable here) in the entire house and it's completely inaccessible from here other than wirelessly.

Booting: I BELIEVE I know what to do in the boot file - move the Other OS (XP) to the top, which is a fairly simple (seemingly) change to make. I had planned to make a copy of the original boot file, in case I somehow botched it, by simply renaming it before changing anything. Then if I did botch it I could still boot from the livecd and and change it back and keep trying until I got it right.

Control - I would've thought you'd have more control over everything in Linux than windows, I just obviously wasn't aware of what to do or how to do it - thanks! (I now feel like I have a grain of sand on a beach full of it! WHEEEE! Now I just need a nice BACKHOE! lol)

nvidia-glx-185 - is there an option to install this (like f6 in Windows installs) before or while the install is proceeding? or, as I said before, put it on the HD somewhere it could be found to load? Of course that isn't helping when it won't boot even from the 9.1 LiveCD I suppose, but perhaps it could be fixed in 9.04 then upgraded to 9.1? Or will it do that?

---

### Post by LinuxNeubie on 2010-04-25
Downloading the alternate CD now.....

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> Initial Install - When I first installed it, as I think I posted, I had another monitor, a 19" HP vs19e, although I didn't mention the actual model. Anyway, what I have now is an Acer H233H 23" widescreen monitor. At one point I changed the video card from an Nvida 6300LE with 256mb to an Nvidia 7300GT with 512mb, although I'm fairly sure I didn't make that change after Ubuntu because I've had the card for months.

Yes you did mention it! This thread is becoming big and I'm getting lost :)

> **LinuxNeubie said:**
> LAN - I don't have the option of setting my computer up with the LAN directly because it's an old house, only ONE telephone line (DSL - we don't get cable here) in the entire house and it's completely inaccessible from here other than wirelessly.

OK, we'll work something out. Keep the WEP/WPA key in an accessible place near you :)

> **LinuxNeubie said:**
> Booting: I BELIEVE I know what to do in the boot file - move the Other OS (XP) to the top, which is a fairly simple (seemingly) change to make. I had planned to make a copy of the original boot file, in case I somehow botched it, by simply renaming it before changing anything. Then if I did botch it I could still boot from the livecd and and change it back and keep trying until I got it right.

Sounds like a good plan! The only thing to note here is that to change the default entry you need to edit a line which starts with [default]("http://www.gnu.org/software/grub/manual/grub.html#default"). Copy/pasting the whole entry is error prone and I can't guarantee it's going to work.

P.S. I assume you are editing a file named menu.lst and not a file called grub.cfg.

> **LinuxNeubie said:**
> Control - I would've thought you'd have more control over everything in Linux than windows, I just obviously wasn't aware of what to do or how to do it - thanks! (I now feel like I have a grain of sand on a beach full of it! WHEEEE! Now I just need a nice BACKHOE! lol)

Control comes with a price, and must be accompanied with responsibility (read: take backups). The path of enlightenment was never easy ;)

> **LinuxNeubie said:**
> nvidia-glx-185 - is there an option to install this (like f6 in Windows installs) before or while the install is proceeding? or, as I said before, put it on the HD somewhere it could be found to load? Of course that isn't helping when it won't boot even from the 9.1 LiveCD I suppose, but perhaps it could be fixed in 9.04 then upgraded to 9.1? Or will it do that?

We'll have to download and install it off-line since immediately after installation you won't have Internet. We'll have to work out a solution for that..

I believe there is something like "F6 in windows" but! 1. using the text-based installer and 2. that doesn't apply for graphics cards.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> Downloading the alternate CD now.....

As I said earlier, if you feel you have a fast computer available, you may want to test the text-based installation in a virtual machine before to run the real install. Have a look at [this video]("http://www.youtube.com/watch?v=c9ObBRh2M1I") on how to do that. The video's using the Graphical installer, couldn't find one that uses the text-based one.

---

### Post by LinuxNeubie on 2010-04-25
Downloaded Sun's VM but the text-based installer download failed. will try again.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> Downloaded Sun's VM but the text-based installer download failed. will try again.

Maybe that's because I gave you a direct link -for convenience- from Germany, without knowing your actual location. Normally you should choose a server near to you, you can pick one here [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

I've chosen a mirror provided by my ISP and it took only 8 minutes to download the CD.

---

### Post by LinuxNeubie on 2010-04-25
No WPA key - this remotely I didn't think it would be accessed by unauthorized individuals. Would the IP of it or the SSID be sufficient?

---

### Post by LinuxNeubie on 2010-04-25
torrent's much faster, so it's on the way now.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> torrent's much faster, so it's on the way now.

Much better idea!!

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> No WPA key - this remotely I didn't think it would be accessed by unauthorized individuals. Would the IP of it or the SSID be sufficient?

Yes, this information is sufficient. I'm not a security freak but I wouldn't leave my Wifi unsecured, this is just my humble opinion :)

---

### Post by LinuxNeubie on 2010-04-25
installing VM\Ubuntu now....

---

### Post by LinuxNeubie on 2010-04-25
WPA - I live out in the middle of nowhere - in the hills where the First Redneck on the Internet wasn't me, but he was probably within 10 miles! I don't think anyone's going to be snatching up a link on my wireless out here :)

---

### Post by LinuxNeubie on 2010-04-25
Question is - this is a VM which is running inside windows, so does it completely ignore windows\wireless settings\etc. and find its own? if so it found it fine.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> WPA - I live out in the middle of nowhere - in the hills where the First Redneck on the Internet wasn't me, but he was probably within 10 miles! I don't think anyone's going to be snatching up a link on my wireless out here :)

Wow cool, I guess you won't be needing WPA/WEP anytime soon!

---

### Post by LinuxNeubie on 2010-04-25
I suppose you saw I have a 3.0ghz p4 dual-processor with 2gb of RAM - probably not very fast or much memory compared to today's computer. VM is pretty slow tho.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> Question is - this is a VM which is running inside windows, so does it completely ignore windows\wireless settings\etc. and find its own? if so it found it fine.

Exactly, it completely ignores Wireless. All the Virtual Machine sees is a normal Ethernet Adapter, VirtualBox handles requests under the hood and forwards them through the real network.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> I suppose you saw I have a 3.0ghz p4 dual-processor with 2gb of RAM - probably not very fast or much memory compared to today's computer. VM is pretty slow tho.

That means you're still into physically installing Ubuntu, so try to do the following (within the Virtual Machine to start with):

Using the Alternate CD installer..

1. Partition the Virtual Disk the way klemes mentioned in one of the early posts of this thread.
2. Try **not** to install a graphical environment. I will come up with more details in a few minutes, I'm running the installer myself to remind me how to do that..
3. Try to experiment as much as possible, in other words, try to damage as much as you can you Virtual Machine.

**UPDATE:** In order to **not** install a GUI you must change to *expert install mode*. As you might have already guessed, this must be changed during the initial boot screen. You must hit F6 > hit Enter on "Expert mode" > hit ESC > Select Install and hit Enter.

A little note about Expert mode install. In this mode the installation steps are not automatically executed, you have to hit Enter on each one of them and execute them manually. 

A second little note is that it's usually safe to just hit enter (the default value is preselected) on a step with a cryptic question.

Having that said, try to install a base system and nothing else, you'll get a lovely command line after that, raw power :)

---

### Post by LinuxNeubie on 2010-04-25
97% "cleaning up" I suppose we'll see if it works momentarily.....grub boot loader.....by the way, I installed Windows 7 on another part of the system and it re-wrote the MBR taking out the old grub. Can I just use the partition manager in 7, which I think is a bit more advanced than XP's, and repart those two partitions ?

---

### Post by LinuxNeubie on 2010-04-25
This comes from inside the VM - UBUNTU! OILA! In answer to your post, I can always uninstall it and try different things.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> 97% "cleaning up" I suppose we'll see if it works momentarily.....grub boot loader.....by the way, I installed Windows 7 on another part of the system and it re-wrote the MBR taking out the old grub. Can I just use the partition manager in 7, which I think is a bit more advanced than XP's, and repart those two partitions ?

Yes, you can use Partition Manager to re-partition those -I believe 4?- partitions.

A little note about the bootloader. The Windows 7/XP bootloader cannot load Linux, on the other hand Grub, the Linux loader, can load many OSes. We can restore grub and have it load all, Windows 7, Windows XP and Ubuntu.

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> This comes from inside the VM - UBUNTU! OILA! In answer to your post, I can always uninstall it and try different things.

Alright, cool! VirtualBox is very cool software that is available under Linux as well, you can play as much as you want with any distribution. It's the ideal place for toy-breakers :)

I have updated the details on how to avoid Graphical Environment installation [here]("http://ubuntuforums.org/showthread.php?p=9173969").

---

### Post by LinuxNeubie on 2010-04-25
VM screen is terribly small and only running at 600x800. Hardware Drivers says No Proprietary Drivers are in use...not that I expected there to be since I didn't add any

---

### Post by LinuxNeubie on 2010-04-25
One other thing - I am assuming (and we know what assuming does) that because it's working in the VM it will work on the system. 
Deleted the first Ubuntu install..."Expert" installing now.....

---

### Post by 666f6f on 2010-04-25
> **LinuxNeubie said:**
> One other thing - I am assuming (and we know what assuming does) that because it's working in the VM it will work on the system. 
Deleted the first Ubuntu install..."Expert" installing now.....

OK, good luck. Make sure you can login via the command line and right after we'll then try to install the necessary software for the real machine to work (it doesn't hurt that we'll install them in the Virtual Machine, they won't work there, we just want to make sure they can be installed, and if not, what other steps do we need to take to install them).

---

### Post by LinuxNeubie on 2010-04-25
As you mentioned, quite a few "cryptic" options in Expert...and before I do actually install, I'll be putting a Third OS on (Vista). I know, "Why would you do such an idiotic thing?" Well believe it or not I've been in the computer business in one way or the other since 1981 when the IBM PC OS was booted from a 5 1/4 floppy and if you had a 1mb hard drive you were a VERY lucky, and probably very rich, man, because they certainly weren't cheap. However, I've been outside the business since XP but am returning to the fore and need the other OS's so I can figure out all their particulars. As far as I see, they're both even worse HD and memory hogs than XP (many of us long for the days of Windows 98, which, while it had issues, was much superior in SO many ways. Unfortunately it was also extremely susceptible. One reason I'd like to be able to use Linux - hackers don't try to fool with it much because not many people use it and it isn't as easy to hack. The worst performance crippler PERIOD is an Anti-virus program.) Anyway, off the soapbox, it's doing it's thing. DANGIT I just passed the partitioning portion and didn't change anything. Grrrr.

---

### Post by LinuxNeubie on 2010-04-25
Which kernel? Linux-generic, -image-generic, or -image-2.6.31-14-generic? choosing the latter, can change later if necessary.

---

### Post by 666f6f on 2010-04-25
Seems you're doing great (good choice about the kernel). it's a bit late here and I have to go to sleep, I'll catch up with you tomorow! Have a nice week!

---

### Post by LinuxNeubie on 2010-04-26
Seems I'm not doing something right. It still loads like it should, but to the graphic environment instead of the command line like you wanted. I must have missed something in the options somewhere.

---

### Post by 666f6f on 2010-04-26
Hi LinuxNeubie, good day!

We can try to skip Expert Installation (proceed with normal text based installation) and just let it install a Graphical Environment, we'll later boot into failsafe mode to get a command prompt.

What are your partitions now? Have you prepared the disk the way klemes proposed [here]("http://ubuntuforums.org/showthread.php?p=9157986")? If so, use the Alternate CD to physically install ubuntu and make sure you do the right assignments in the Disk Partitioning step.

---

### Post by LinuxNeubie on 2010-04-26
Well I mentioned that I installed Windows 7 and it has a bit more advanced Partitioner than XP, so I went in and deleted the two entirely and combined them so now there's roughly 30gb of nothingness to do something with, so I'll try installing it there. I was going to install Vista, but since I can just use a VM for it there's no need.

---

### Post by 666f6f on 2010-04-26
> **LinuxNeubie said:**
> Well I mentioned that I installed Windows 7 and it has a bit more advanced Partitioner than XP, so I went in and deleted the two entirely and combined them so now there's roughly 30gb of nothingness to do something with, so I'll try installing it there. I was going to install Vista, but since I can just use a VM for it there's no need.

In my humble opinion Vista was more of a transitional step towards Windows 7 -which, it's not bad at all, apart from the fact that it's a proprietary OS- than anything else. It's a good choice to not waste real disk space for Windows Vista and just put them in a VM. You may find your self deleting the Vista Virtual Disk Image file pretty soon.

---

### Post by LinuxNeubie on 2010-04-26
Well I was hoping we'd be able to resolve this, but something is still awry. First, when using the VM, the Wireless Network card is already started, so using it doesn't seem to be a problem. However, no configuration, either auto or manual, would find the wireless network, even though I reconfigured the router specifically for this purpose. Therefore, without the network, many files weren't installed that were with the VM. I don't know if there's a way to install a driver for the card prior to\during installation, much like the video issue. It blinks quickly and a fast look, which I don't know how to stop, seems to be telling me there are errors. I set it to make a log file at the default location but I don't know how to see it. Ideas?

---

### Post by 666f6f on 2010-04-26
> **LinuxNeubie said:**
> Well I was hoping we'd be able to resolve this, but something is still awry. First, when using the VM, the Wireless Network card is already started, so using it doesn't seem to be a problem. However, no configuration, either auto or manual, would find the wireless network, even though I reconfigured the router specifically for this purpose.

I'm not following (again!). Normally, the Wireless network is hidden from the Virtual Machine (NAT networking), unless you changed the networking options (changed to Bridged Networking), which isn't a good idea since it doesn't work well with wireless networks.

If you have no idea what I'm taking about it means you didn't change any relevant configuration option and the Wireless network should be hidden from the Virtual Machine.

> **LinuxNeubie said:**
> Therefore, without the network, many files weren't installed that were with the VM.

I should be sufficient to use only the installation CD to perform a full Ubuntu installation, what files weren't installed?

> **LinuxNeubie said:**
> I don't know if there's a way to install a driver for the card prior to\during installation, much like the video issue. It blinks quickly and a fast look, which I don't know how to stop, seems to be telling me there are errors. I set it to make a log file at the default location but I don't know how to see it. Ideas?

That's why we're using the Alternate CD installer, because it's not possible to change the video graphics card driver prior to or during the installation (anybody feel free to correct me here if I'm wrong), so we must use the text based installer.

---

### Post by LinuxNeubie on 2010-04-26
I didn't make any changes.  I just thought because the wireless card was already operational under windows it wouldn't have had to send a "start" command to it since it would've already been on and working.

When it got to the "Install Programs" tab (wasn't exactly what it was called but it was something of the sort) it hung at 81% - wasn't reading the disk, wasn't doing anything, so I canceled it, went back up to reconfigure network again, still wouldn't work, went back to that tab (should've written it down) and tried it again - still hung.

---

### Post by 666f6f on 2010-04-26
> **LinuxNeubie said:**
> I didn't make any changes.  I just thought because the wireless card was already operational under windows it wouldn't have had to send a "start" command to it since it would've already been on and working.

When it got to the "Install Programs" tab (wasn't exactly what it was called but it was something of the sort) it hung at 81% - wasn't reading the disk, wasn't doing anything, so I canceled it, went back up to reconfigure network again, still wouldn't work, went back to that tab (should've written it down) and tried it again - still hung.

I can see two possibilities.

1. The network doesn't work in the VM for some reason. Can you open a page, say Google for example, from within the VM?

2. The software sources are not properly setup. Can you post the contents of /etc/apt/sources.list? (if you have internet access from within the VM)?

Question: How do you reconfigure the network?

---

### Post by LinuxNeubie on 2010-04-27
> **666f6f said:**
> I can see two possibilities.

1. The network doesn't work in the VM for some reason. Can you open a page, say Google for example, from within the VM? 

The network DOES work in the VM. Perhaps you read it incorrectly. I can open anything, download whatever from it. Well I could. I'll have to re-install it on it again now. Thinking it had served its purpose I deleted it from the Box so that rules out the first question below>

> **666f6f said:**
>  2. The software sources are not properly setup. Can you post the contents of /etc/apt/sources.list? (if you have internet access from within the VM)?

 Question: How do you reconfigure the network?

I reconfigure the network by going to the other machine I have, accessing the router, resetting it and re-assigning IP's then coming back to this one and inputting the settings accordingly.

I KNOW the ultimate solution after days of thinking about it and waking up with a "Now why didn't I think of that before" epiphany - if it's possible, and since Linux is "Open Source" I don't see why it wouldn't be other than not knowing what to do to accomplish it. The BIG question is do you or someone you know understand the OS well enough to do it.

Here goes: The ISO - ANY ISO for that matter - can be changed, manipulated, whatever. Hackers do it all the time, installing virii, malware, etc. as I'm sure you well know. Why can someone not go into the installer package, add whatever command needs to be added to point to a particular driver - for not only my situation but whomever's situation - and also put said driver in the ISO at whatever location it points to. Problem solved. Of course I'm thinking outside the OS, not knowing what intricacies that might entail, but it certainly seems at least possible. Maybe not an ISO for "release" but it could certainly be put on a server and downloaded, or for that matter if I were the one with such a thing I could either make a torrent out of it and host it or set up an FTP server on my machine - obviously I don't have the bandwidth for a bunch of users, but anyone who has cable or DSL is light years beyond where it was 10-15 years ago - as is the entire computer industry. Anyway, just my thought. Yours?

---

### Post by 666f6f on 2010-04-27
> **LinuxNeubie said:**
> The network DOES work in the VM. Perhaps you read it incorrectly. I can open anything, download whatever from it. Well I could. I'll have to re-install it on it again now. Thinking it had served its purpose I deleted it from the Box so that rules out the first question below.

Probably I've misread like you say. I think we need to recapitulate, can you please tell me what is your progress physically installing Ubuntu? Have you tried that like I suggested in one of the latest posts ([post 63]("http://ubuntuforums.org/showthread.php?p=9176120"))?

> **LinuxNeubie said:**
> I KNOW the ultimate solution after days of thinking about it and waking up with a "Now why didn't I think of that before" epiphany - if it's possible, and since Linux is "Open Source" I don't see why it wouldn't be other than not knowing what to do to accomplish it. The BIG question is do you or someone you know understand the OS well enough to do it.

Here goes: The ISO - ANY ISO for that matter - can be changed, manipulated, whatever. Hackers do it all the time, installing virii, malware, etc. as I'm sure you well know. Why can someone not go into the installer package, add whatever command needs to be added to point to a particular driver - for not only my situation but whomever's situation - and also put said driver in the ISO at whatever location it points to. Problem solved. Of course I'm thinking outside the OS, not knowing what intricacies that might entail, but it certainly seems at least possible. Maybe not an ISO for "release" but it could certainly be put on a server and downloaded, or for that matter if I were the one with such a thing I could either make a torrent out of it and host it or set up an FTP server on my machine - obviously I don't have the bandwidth for a bunch of users, but anyone who has cable or DSL is light years beyond where it was 10-15 years ago - as is the entire computer industry. Anyway, just my thought. Yours?

It sounds like a good idea and implementable, I guess what stops us from doing so is time and cost, which essentially is the same thing.

However, I'm neither responsible for such decision nor have the time or the motivation to change things the way you described. You may open a new thread for that here in the forums or start a brainstorm [here]("http://brainstorm.ubuntu.com/").

---

### Post by LinuxNeubie on 2010-04-27
That's what I thought. Just an idea anyway. Last questions then we'll close this thread since it's getting so cumbersome:

If I wipe out that partition again, will it wipe out the bootloader or is that stored in the MBR? It said it wrote to the MBR so I assume it will just point to a file that's no longer there but you know what happens when you assume. Reason being, if I can wipe and start again, I'll try it until I figure it out, but obviously not if it's going to make the entire system unbootable. Thanks!

---

### Post by 666f6f on 2010-04-27
> **LinuxNeubie said:**
> If I wipe out that partition again, will it wipe out the bootloader or is that stored in the MBR? It said it wrote to the MBR so I assume it will just point to a file that's no longer there but you know what happens when you assume. Reason being, if I can wipe and start again, I'll try it until I figure it out, but obviously not if it's going to make the entire system unbootable. Thanks!

If you chose to store it in the MBR, it should be stored in the MBR and stay there until you overwrite the MBR. So, if you wipe out that partition, you won't wiping out the bootloader. The bootloader will remain functional. Good luck!

---

### Post by LinuxNeubie on 2010-04-27
Well if you would, just mark this one as "Solved" and I'll open a new one if necessary - and it probably will be! Thanks a mil!

---

### Post by 666f6f on 2010-04-28
> **LinuxNeubie said:**
> Well if you would, just mark this one as "Solved" and I'll open a new one if necessary - and it probably will be! Thanks a mil!

It's the person who opens the thread that has the permission to mark the thread as solved :) Good luck with your journey in the land of linux!

---

