---
title: "Adding windows to a partition"
date: 2010-04-24
forum: General Help
---

### Post by wcutrombonekid on 2010-04-24
so, through some stupid acts of my own doing, I accidentally deleted windows from my computer.  A little more extreme than what I meant to do, but the partition was too big, there was a bunch of unused space and I was trying to shrink it....guess i got my wish.


anyway, i have a partition set up to put it back in, does anyone know of a tutorial that shows how to do it?  I can't seem to find one, it would surprise me if there wasn't, theres one for everything else.

Thanks
Chris

---

### Post by yabbadabbadont on 2010-04-24
Try this [guide.](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by wcutrombonekid on 2010-04-25
> **yabbadabbadont said:**
> Try this [guide.]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

this looks like its exactly what I need

only problem is that when i'm using a livecd, in the terminal, I need su privilages, but it wont give them to me because i don't have a profile or anything with a user password.  Is there a way to do this?

---

### Post by wilee-nilee on 2010-04-25
> **wcutrombonekid said:**
> this looks like its exactly what I need

only problem is that when i'm using a livecd, in the terminal, I need su privilages, but it wont give them to me because i don't have a profile or anything with a user password.  Is there a way to do this?

So you might share with us where your actually at. It seems that you now have windows back on and you want to restore the grub boot is this correct? I think on a live cd it is sudo and just hit enter for the password.

---

### Post by wcutrombonekid on 2010-04-25
> **wilee-nilee said:**
> So you might share with us where your actually at. It seems that you now have windows back on and you want to restore the grub boot is this correct? I think on a live cd it is sudo and just hit enter for the password.

so, i don't think windows ever left

it doesn't make sense, when i'm on the live cd, it shows that the content is still there, but when I go and actually boot into ubuntu, it shows that nothings there.  I've tried to just go sudo update-grub and updates, but when i try and boot into windows, it says that windows cannot find it.  This makes me think is the windows boot loader maybe?!?!?

The reason I was messing with it was because when I first put ubuntu on my computer, i just wanted to play with it, so I only had 25 GB alotted for it.  Now i use it constantly and needed more space for media and different programs and games.  So i wanted to shrink my windows partition and put the space on my linux partition.  It shrunk fine, then i moved it over and somehow after it got done, thats when it started acting wierd.  I imagion its because I moved it, which messed up all the pathways.  But i have a limited knowledge of this stuff.

Sometimes i get a little too heroic for my skill level
:P

---

### Post by wilee-nilee on 2010-04-25
Post this boot script in code tags if you can this will help those that can really help you.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Is this a wubi install? it is hard to tell from your description at least for me.

---

### Post by wcutrombonekid on 2010-04-25
no, windows is on a totally different partition, thats why I was taking space away from it and trying to give it to linux

EDIT: just a bad typer

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec919399

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,787,924    16,787,862   7 HPFS/NTFS
/dev/sda2         294,857,010   625,137,344   330,280,335   7 HPFS/NTFS
/dev/sda3          16,787,925    74,670,119    57,882,195   5 Extended
/dev/sda5          16,787,988    20,788,109     4,000,122  82 Linux swap / Solaris
/dev/sda6          20,788,173    74,670,119    53,881,947  83 Linux
/dev/sda4          74,670,120   294,857,009   220,186,890  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        002CA9622CA95386                       ntfs       RECOVERY                      
/dev/sda2        A48E552B8E54F6F0                       ntfs                                     
/dev/sda4        42c8f18e-a421-49e3-bf75-f7b85ca83626   ext4                                     
/dev/sda5        2a8eb8fa-6db8-4763-bcaa-8f462ceba299   swap                                     
/dev/sda6        a4871420-9ba3-45a9-98d6-9d2734732341   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a4871420-9ba3-45a9-98d6-9d2734732341 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4871420-9ba3-45a9-98d6-9d2734732341

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
# howmany=1

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        a4871420-9ba3-45a9-98d6-9d2734732341
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=a4871420-9ba3-45a9-98d6-9d2734732341 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        a4871420-9ba3-45a9-98d6-9d2734732341
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=a4871420-9ba3-45a9-98d6-9d2734732341 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, memtest86+
uuid        a4871420-9ba3-45a9-98d6-9d2734732341
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a4871420-9ba3-45a9-98d6-9d2734732341 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2a8eb8fa-6db8-4763-bcaa-8f462ceba299 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  27.7GB: boot/grub/menu.lst
  12.3GB: boot/grub/stage2
  31.6GB: boot/initrd.img-2.6.31-14-generic
  19.7GB: boot/initrd.img-2.6.31-15-generic
  30.6GB: boot/initrd.img-2.6.31-16-generic
  19.2GB: boot/initrd.img-2.6.31-17-generic
  32.2GB: boot/initrd.img-2.6.31-19-generic
  33.4GB: boot/initrd.img-2.6.31-20-generic
  38.2GB: boot/vmlinuz-2.6.31-14-generic
  18.9GB: boot/vmlinuz-2.6.31-15-generic
  16.3GB: boot/vmlinuz-2.6.31-16-generic
  25.1GB: boot/vmlinuz-2.6.31-17-generic
  31.5GB: boot/vmlinuz-2.6.31-19-generic
  33.4GB: boot/vmlinuz-2.6.31-20-generic
  33.4GB: initrd.img
  32.2GB: initrd.img.old
  33.4GB: vmlinuz
  31.5GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-04-25
Did you shrink W7 with the virtual disk management in W7?

---

### Post by wcutrombonekid on 2010-04-26
> **wilee-nilee said:**
> Did you shrink W7 with the virtual disk management in W7?

no, I shrunk Windows Vista on a live cd of ubuntu 9.10 using gparted

---

### Post by wilee-nilee on 2010-04-26
> **wcutrombonekid said:**
> no, I shrunk Windows Vista on a live cd of ubuntu 9.10 using gparted

Sorry missed the Vista info in the script, I don't have an answer for you but your here at or about the right time as far as people who help with this sort of stuff. Weekdays have more on generally so if you don't get an answer tonight bump it about this time or a few hours earlier tomorrow.

---

### Post by john newbuntu on 2010-04-26
Have you tried any of the Windows utilities to restore/recover vista?  I assume you have the installation CD with you.  If you boot off of it, there is startup repair and system restore.  You might want to backup Ubuntu data before trying these.

---

### Post by wcutrombonekid on 2010-04-26
> **john newbuntu said:**
> Have you tried any of the Windows utilities to restore/recover vista?  I assume you have the installation CD with you.  If you boot off of it, there is startup repair and system restore.  You might want to backup Ubuntu data before trying these.

thats what i'm afraid off, wont that just departition the entire disc?  i'd really rather not do that

---

### Post by wcutrombonekid on 2010-04-26
> **wcutrombonekid said:**
> thats what i'm afraid off, wont that just departition the entire disc?  i'd really rather not do that


sweet that worked.

one problem though

when I boot into windows now, every time it gives me the option of booting into it through two different options, both are labled exactly the same (Windows Vista (TM) Buisness (recovered))  The top one is broken and wont load anything, but the bottom one works and sends me to my windows partition without any issue.  On this screen it is titled "windows boot manager"  I tried to find a way to edit that, but as far as I can tell, theres no way for me to.  How do I get this screen to just go away?  Before I messed with it, I would pick the windows loader and it would go straight into it.

---

### Post by john newbuntu on 2010-04-27
If you are using windows only, there is a command line utility in vista called bcdedit.exe that can be used to modify boot parameters:
[http://technet.microsoft.com/en-us/library/cc721886%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc721886%28WS.10%29.aspx)

---

