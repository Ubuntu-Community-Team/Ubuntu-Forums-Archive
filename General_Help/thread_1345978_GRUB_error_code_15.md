---
title: "GRUB error code 15"
date: 2009-12-04
forum: General Help
---

### Post by Searching_for_answers on 2009-12-04
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003556d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1958    15727603+  83  Linux
/dev/sda2           19044       19457     3325455    5  Extended
/dev/sda3           17579       19043    11767612+  83  Linux
/dev/sda4   *        1959       17578   125467650   83  Linux
/dev/sda5           19045       19457     3317422+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$
```I have both xubuntu 9.04(dev/sda1) and opensuse 11.2(dev/sda4) installed. I also have one partition where they share some files(dev/sda3) a Swap(dev/sda5) and its Extension (dev/sda2). Until recently both everything worked but then I upgraded to 11.2 so that xubutnu got error 15 so I followed a guide but that made opensuse 11.2 get error 15. I'm not an expert but I think GRUB looks for old SUSE which has changed name because on the boot menu I can choose 11.2 RC which doesn't exists anymore. I need help to fix this.

menu.lst
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7144784b-f130-498d-a7b2-774ed7c13c47

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Desktop -- openSUSE 11.2 RC 1 - 2.6.31.3-1 (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31.3-1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 resume=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part5 splash=silent quiet showopts vga=0x346 
initrd        /boot/initrd-2.6.31.3-1-desktop
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Failsafe -- openSUSE 11.2 RC 1 - 2.6.31.3-1 (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31.3-1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x346 
initrd        /boot/initrd-2.6.31.3-1-desktop
savedefault
boot
```[http://www.linuxquestions.org/questions/linux-distributions-5/booting-issues.-grub-error-code-15.-772086/](http://www.linuxquestions.org/questions/linux-distributions-5/booting-issues.-grub-error-code-15.-772086/)

---

### Post by hwttdz on 2009-12-04
"grub-install --version"?

And welcome.

---

### Post by oldfred on 2009-12-04
The question has to be which bootloader is in the MBR?

This script will document the entire boot process:

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Leppie on 2009-12-04
Your GRUB seems to be using two different kind of id's, UUID and id.
Try updating GRUB in Ubuntu:
```
$sudo update-grub
```

This should turn everything into UUID (which is the preferred reference in GRUB). If not, you can always manually change the entries to use UUID.
You can find the UUID's like this:
```
$ls -l /dev/disk/by-uuid
```

Hope this helps

---

### Post by Searching_for_answers on 2009-12-05
mattias@mattias-desktop:~$ grub-install --version
grub-install (GNU GRUB 0.97)
mattias@mattias-desktop:~$ sudo update-grub
[sudo] password for mattias: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

mattias@mattias-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-12-05 08:47 3dfcf698-2d7c-48eb-b1de-7ba82fcdb3ed -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-12-05 08:47 7144784b-f130-498d-a7b2-774ed7c13c47 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-12-05 08:47 a99ca376-a688-49f4-8b2b-46315d96d5a5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-12-05 08:47 be4e5883-92d9-4da0-9532-0de98fd8a36c -> ../../sda3
mattias@mattias-desktop:~$ 


I will now reboot and try the shell script.

---

### Post by Searching_for_answers on 2009-12-05
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 95991846 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003556d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    31,455,269    31,455,207  83 Linux
/dev/sda2         305,925,795   312,576,704     6,650,910   5 Extended
/dev/sda5         305,941,860   312,576,704     6,634,845  82 Linux swap / Solaris
/dev/sda3         282,390,570   305,925,794    23,535,225  83 Linux
/dev/sda4    *     31,455,270   282,390,569   250,935,300  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7144784b-f130-498d-a7b2-774ed7c13c47" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="be4e5883-92d9-4da0-9532-0de98fd8a36c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="dist2" UUID="a99ca376-a688-49f4-8b2b-46315d96d5a5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3dfcf698-2d7c-48eb-b1de-7ba82fcdb3ed" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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
# kopt=root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7144784b-f130-498d-a7b2-774ed7c13c47

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

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7144784b-f130-498d-a7b2-774ed7c13c47 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7144784b-f130-498d-a7b2-774ed7c13c47
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Desktop -- openSUSE 11.2 RC 1 - 2.6.31.3-1 (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31.3-1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 resume=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part5 splash=silent quiet showopts vga=0x346 
initrd        /boot/initrd-2.6.31.3-1-desktop
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Failsafe -- openSUSE 11.2 RC 1 - 2.6.31.3-1 (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31.3-1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x346 
initrd        /boot/initrd-2.6.31.3-1-desktop
savedefault
boot


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
UUID=7144784b-f130-498d-a7b2-774ed7c13c47 /               ext3    relatime,errors=remount-ro 0       1
# /sfiles was on /dev/sda3 during installation
UUID=be4e5883-92d9-4da0-9532-0de98fd8a36c /sfiles         ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=3dfcf698-2d7c-48eb-b1de-7ba82fcdb3ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.1GB: boot/grub/menu.lst
   2.1GB: boot/grub/stage2
   2.2GB: boot/initrd.img-2.6.28-11-generic
   2.2GB: boot/initrd.img-2.6.28-16-generic
   2.1GB: boot/initrd.img-2.6.28-17-generic
   2.1GB: boot/vmlinuz-2.6.28-11-generic
   2.1GB: boot/vmlinuz-2.6.28-16-generic
   2.2GB: boot/vmlinuz-2.6.28-17-generic
   2.1GB: initrd.img
   2.2GB: initrd.img.old
   2.2GB: vmlinuz
   2.1GB: vmlinuz.old

=========================== sda4/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Nov 13 20:12:02 CET 2009
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,3)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 resume=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part5 splash=silent quiet  showopts vga=0x346
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x346
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)###
title Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

=============================== sda4/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part4 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST3160815AS_5RX9MWJQ-part3 /sfiles              ext3       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda4: Location of files loaded by Grub: ===================


  49.1GB: boot/grub/menu.lst
  49.1GB: boot/grub/stage2
  49.1GB: boot/initrd
  49.1GB: boot/initrd-2.6.31.5-0.1-desktop
  49.1GB: boot/vmlinuz
  49.1GB: boot/vmlinuz-2.6.31.5-0.1-desktop

```

When I updated before I rebooted I got kernel generic 2.6.xx.17. Is it really necessary to have x11, x16 and x17 in the boot options?

---

### Post by oldfred on 2009-12-05
You want to show 2 kernels just in case a new one does not work. In menu.lst is this stanza.

## controls how many kernels should be put into the menu.lst
## only counts the first occurrence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]all[/COLOR]

Change the all to 2 and next time the menu.lst is updated it will only show 2 kernels.

You are booting with grub legacy (.97) and also have grub legacy in the PBR - partition boot record for openSuse. That may make it easier to boot if you want chainbooting which just links the Ubuntu grub menu to the openSuse menu.

Add this entry at the end of menu.lst for ubuntu.

title        openSUSE 11.2 (loader) on sda4
root         (hd0,3)
chainloader    +1

Someone else may know what changes to make to the openSuse stanza to allow direct booting. The advantage of chainbooting is any kernel updates to openSuse will be automatically updated in its menu and you will not have to manually edit Ubuntu's menu.lst with every change to openSuse.

---

### Post by Searching_for_answers on 2009-12-06
It worked. Thanks oldfred
 
THREAD SOLVED.

---

### Post by oldfred on 2009-12-06
Glad it worked Searching_for_answers.  

I use(d) chainbooting for my system which has windows, my current install- 9.04 , my new install 9.10 (currently replaced my chainboot because it found everything, but I plan on going back to chainboot), windows, and the next install or an experimental version. I have upgraded in place every 6 months for 3 years and my current install has too much cruft and I now want to houseclean, but also have many custom settings to transfer. I am moving home to a separate home and most data to a separate ext3 data partition and another with windows shared data in a NTFS shared partition. 

Up until last June I just solved problems by looking in google and did not really even notice that many times it took me here to the forums. By offering some help on issues I know a little about (sometimes others point out how little I know, but usually everyone is polite)  and reading many posts I have learned more about Ubuntu in the last 6 months than in the previous 3 years.

I have my 3 year old Ubuntu book that I write in the margins to add info and copy and paste into text files other useful info. I have many bookmarks and for booting issues have several sites that have offered useful info.

---

