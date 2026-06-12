---
title: "Ubuntu not booting after partition resize"
date: 2009-11-01
forum: General Help
---

### Post by rykkers on 2009-11-01
Hi guys, i've looked elsewhere but got thoroughly confused.

I stupidly resized my linux partition using a random tool rather than the live cd, and now it won't boot.

Grub is fine, and boots windows fine but when i choose to launch ubuntu the loading screen comes up abut the bar only goes up a little and then stops and freezes. Recovery mode also won't boot, saying missing files.

Basically is there any way of booting linux? if not do you guys know how i can get some files out so i can reinstall

Thanks

Ryk

---

### Post by rykkers on 2009-11-02
bump... anyone have any suggestions? i'm guessing maybe the uuid in grub needs changing but have no clue what to set it to?

cheers

ryk

---

### Post by alphaniner on 2009-11-02
See if you can access the partition from a LiveCD.  If you have problems mounting it, **fsck** it.  You can also get the UUID using **blkid**.

---

### Post by slakkie on 2009-11-02
Most probably due to change of UUID.

You need to change this in grub and in /etc/fstab.

---

### Post by rykkers on 2009-11-02
hmm, its mounted fine in the live cd, however the only folders i see within it are 'lost+found' which i can't access and 'var' which i can, but doesn't seem to have anything useful for me.

I just checked the UUID and this hasn't changed, i.e. GRUB has the correct ID.

Any ideas? i just really want to save some photos and uni work that i have on there

Cheers for the help

Ryk

---

### Post by rykkers on 2009-11-02
bump.. should i be able to see more in that drive?

---

### Post by rykkers on 2009-11-03
double bump

---

### Post by louieb on 2009-11-03
What random tool?
Which version of Ubuntu? (karmic uses grub2 - other versions use grub legacy). 
Are you sure it GRUB your seeing and not the Win boot loader? (wubi install)?
If GRUB works then there is a /boot/grub folder somewhere. yet you say you just see /var. 

Need info - [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") Please add the results.txt file to your next post.

---

### Post by rykkers on 2009-11-04
Thanks for trying to help, ubuntu version is: 9.04

Please see the info from the shell script below, as you say there should be more folders in there if grub is working, i wonder if i'm doing something wrong, should all my files just be instantly visible through the places menu from the live cd?:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99afdee2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    53,255,474    53,255,412  83 Linux
/dev/sda2    *     53,255,475    75,216,329    21,960,855   7 HPFS/NTFS
/dev/sda3          75,216,330    78,140,159     2,923,830   5 Extended
/dev/sda5          75,216,393    78,140,159     2,923,767  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f3747d46-795c-4cb9-b847-1006998af26d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="2C109A121099E35E" TYPE="ntfs" 
/dev/sda5: UUID="c79e8ce1-c6ea-4f5e-b761-2875741e2531" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
timeout        3

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
# kopt=root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3747d46-795c-4cb9-b847-1006998af26d

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
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f3747d46-795c-4cb9-b847-1006998af26d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f3747d46-795c-4cb9-b847-1006998af26d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


   7.2GB: boot/grub/menu.lst
   7.3GB: boot/grub/stage2
   7.3GB: boot/initrd.img-2.6.28-11-generic
   7.2GB: boot/initrd.img-2.6.28-15-generic
   7.2GB: boot/initrd.img-2.6.28-16-generic
   7.3GB: boot/vmlinuz-2.6.28-11-generic
   7.3GB: boot/vmlinuz-2.6.28-15-generic
   7.2GB: boot/vmlinuz-2.6.28-16-generic

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
```

Thanks very much again

Ryk

---

### Post by m4tic on 2009-11-04
from the live cd, type: sudo e2fsck -f -y -v /dev/sda1
it will take a while, hours if its that bad, if you cant wait reinstall

---

### Post by louieb on 2009-11-04
Something is very wrong. For example the script should have listed file /etc/fstab and it did not. As you said it seems you are missing parts of Ubuntu's file-system.  Its really very weird that GRUB still works.

```
do you guys know how i can get some files out so i can reinstall

```On the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")and other rescue CDs  two programs **testdisk** and **photorec**

Testdisk fixes partiton table problems. and photorec can recover files - even sometimes when a partition has been deleted or formatted. 
Don't know what it will recover for you but it can't hurt. Check the wiki for how to use [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk"). 

Also there is this Ubuntu forum  [How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922&highlight=testdisk+photorec")
> The following steps may not replicate your needs. There are some examples of how to use TestDisk [here]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples")

---

### Post by rykkers on 2009-11-05
Yep, things are definitely missing operating system wise.

luckily, after running "sudo e2fsck -f -y -v /dev/sda1" i can now see all of my documents from the live cd, so i'll just copy them over to my other partition and just re-install ubuntu.

I've definitely learnt a lesson, although some parts do remain a mystery.

Cheers for the help

Ryk

---

### Post by m4tic on 2009-11-05
yep, i guess it will remain a mystery

---

