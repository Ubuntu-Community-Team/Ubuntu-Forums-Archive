---
title: "Need help with messy Boot options"
date: 2010-06-18
forum: General Help
---

### Post by nemiux on 2010-06-18
Hello,
I guess I should start from the beggining how it all was that my boot got "messy". First I had Windows XP Sp3, after that, I installed ubuntu to my hard drive with option "Install inside Windows". Boot.ini got 2 boot options either XP or Ubuntu. Now the part when it got quite messy. I installed windows Vista on my other HDD (yes hdd, not other partition) and it took over boot, so not the boot.ini would be shown, but the bcdedit.exe file. When I uninstalled Vista (that later was upgraded to Win7) The bcdedit.exe boot stayed. After that I installed Ubuntu into a seperate partition, but it got even more messy, because of the grub boot. So I finnaly ended up uninstalling Ubuntu from that partition and used 
ms-sys to restore boot to what it was earlier, cause I started getting Grub error. So at the end, this is what I want to ask:
1) How to remove bcdedit.exe boot, so when I start computer it would boot from my win xp boot.ini file?
2) How do I install ubuntu into a seperate partition, but Computer would also start with boot.ini, not menu.lst grub loader?

Thank you

---

### Post by wilee-nilee on 2010-06-18
That is a pretty good description but to clarify the setup post the bootscript in my sig with code tags.

---

### Post by nemiux on 2010-06-18
Let's hope this helps```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /GRLDR /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/loop0 already mounted or Wubi//host busy

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3d0c3d0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   157,549,454   157,549,392   7 HPFS/NTFS
/dev/sda2         157,549,455   976,773,167   819,223,713   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         157,549,518   358,265,564   200,716,047   7 HPFS/NTFS
/dev/sda6         358,265,628   776,212,604   417,946,977   7 HPFS/NTFS
/dev/sda7         776,212,668   976,773,167   200,560,500   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4bf2a4fc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   419,585,669   419,585,607   7 HPFS/NTFS
/dev/sdb3         419,585,670   871,976,069   452,390,400   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       1a886bf8-53b1-4343-82fa-03061553643e   ext3                                     
/dev/sda1        A0A4EB88A4EB5EF2                       ntfs       Sisteminis                    
/dev/sda5        443C9D4F3C9D3CBC                       ntfs       Senas mano                    
/dev/sda6        6CE42103E420D0DE                       ntfs       Pagr.                         
/dev/sda7        5E2C892A2C88FE71                       ntfs       Kristinos                     
/dev/sdb1        60F81DAEF81D8406                       ntfs       Much                          
/dev/sdb3        92E0BB2EE0BB1785                       ntfs       Stambus failai                

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=A0A4EB88A4EB5EF2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]
timeout=8
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
c:\wubildr.mbr="Ubuntu" 

=================== sda1: Location of files loaded by Grub: ===================


  15.0GB: ubuntu/disks/boot/grub/menu.lst
  22.5GB: ubuntu/disks/boot/initrd.img-2.6.27-11-generic
  26.7GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  41.5GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  15.1GB: ubuntu/disks/boot/initrd.img-2.6.28-19-generic
   3.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-11-generic
  13.0GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
  17.6GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
  13.3GB: ubuntu/disks/boot/vmlinuz-2.6.28-19-generic
=============================== StdErr Messages: ===============================

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by wilee-nilee on 2010-06-18
Thanks for posting the script, I think you will need somebody more knowledgeable then myself for this.

So you have the wubi install, and you want to eventually have Ubuntu on it's own HD. Do you want to save anything from the wubi install?

And are you spooked by grub and thats why you want to have windows control the dual boot your aiming at?

This is the UF and we are generally grub-centric it is actually much easier to manipulate, if you know how. I have a jaunty setup on a laptop and upgraded grub-legacy to grub2 that when set up correctly is a easy way to have a boot that works every time.

---

### Post by nemiux on 2010-06-18
Well, I don't really have to save anything, it's just drivers and few software programs. All the knowledge is in my head or other hdd's. Maybe grub2 would be good to boot, but to know that, I need to remove bcdedit.exe booting, so it wouldn't be that long. If anyone would know how to remove bcdedit.exe tool from my computer, then it would be very cool. :)

---

### Post by wilee-nilee on 2010-06-18
> **nemiux said:**
> Well, I don't really have to save anything, it's just drivers and few software programs. All the knowledge is in my head or other hdd's. Maybe grub2 would be good to boot, but to know that, I need to remove bcdedit.exe booting, so it wouldn't be that long. If anyone would know how to remove bcdedit.exe tool from my computer, then it would be very cool. :)

If you don't get help here you might consider a MS forum as your problem is a windows problem. You will probably eventually get help but since the boot is so messy I'm not sure many will want to mess with it. I hope I'm wrong here, and I'm not trying to discourage you but make sure you are aware of the possibilities.

Really if you have a backup of the XP and don't need to save anything in the Ubuntu wubi install if it was me I would wipe all of the HD's then install XP in sda, then a grub2 Ubuntu release like karmic or lucid in sdb and put grub in sdb when installing and put it first in the boot from list and relax with a fully working system. But thats just me.

I don't see the bcdedit in the bootscript either, I'm not familiar with that so I may be missing it. I see the standard BCD stuff.

---

### Post by nemiux on 2010-06-18
I believe that ```
 Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
``` Is the BCDedit.exe, by seeing boot sector type win vista/7 that have bcdedit, but systen Win XP, as it is.

---

