---
title: "Grub WILL NOT recognize Win XP"
date: 2010-02-21
forum: General Help
---

### Post by xXAlphaXx on 2010-02-21
Lemme provide a little info;

Firstly, this system is in a tri-boot. Win XP, Win Vista, and Ubuntu. I just installed Ubuntu so that grub would install as the main boot loader and I wouldn't have these problems. However it only recognizes Vista and Ubuntu.

I manually entered the Windows XP entry in menu.lst but when ever I try too boot it, it just tells me invalid device requested.


Heres my entry for Windows XP and the partitions on my drive:

Partitions:

```

/dev/sda1   NTFS   (Windows Vista)
/dev/sda2   extended
/dev/sda5   linux-swap
/dev/sda6   ext3   (Ubuntu)
/dev/sda7   NTFS   (Windows XP)
/dev/sda3   NTFS   (Windows Vista Recovery)

```

menu.lst entry:

```

# This entry is Windows XP
title           Windows XP
rootnoverify   (hd0,6)
savedefault
makeactive
chainloader     +1

```

Any ideas?

---

### Post by meierfra. on 2010-02-21
Sounds like the XP boot files got deleted at some stage. 
But lets check out your system before jumping to conclusion.  Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt.

---

### Post by xXAlphaXx on 2010-02-21
Ran it, this is what I got.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd03d783

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   360,080,909   360,080,847   7 HPFS/NTFS
/dev/sda2         360,080,910   467,716,409   107,635,500   5 Extended
/dev/sda5         360,080,973   361,060,874       979,902  82 Linux swap / Solaris
/dev/sda6         361,060,938   406,283,849    45,222,912  83 Linux
/dev/sda7         406,283,913   467,716,409    61,432,497   7 HPFS/NTFS
/dev/sda3         467,724,288   488,390,655    20,666,368   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        424C3DD64C3DC607                       ntfs                                     
/dev/sda3        340A890B0A88CB76                       ntfs       HP_RECOVERY                   
/dev/sda5        6e5d738f-4a51-4a96-8f6f-e51297646ba7   swap                                     
/dev/sda6        db90024e-1b23-47f6-876f-94c76968d4a0   ext3                                     
/dev/sda7        6C6C8FCF6C8F930E                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=db90024e-1b23-47f6-876f-94c76968d4a0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=db90024e-1b23-47f6-876f-94c76968d4a0

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		db90024e-1b23-47f6-876f-94c76968d4a0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=db90024e-1b23-47f6-876f-94c76968d4a0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		db90024e-1b23-47f6-876f-94c76968d4a0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=db90024e-1b23-47f6-876f-94c76968d4a0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		db90024e-1b23-47f6-876f-94c76968d4a0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows operating systems:
root

# This entry will be for Windows XP
title		Windows XP (loader)
rootnoverify	(hd0,6)
savedefault 
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista Recovery (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


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
UUID=db90024e-1b23-47f6-876f-94c76968d4a0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6e5d738f-4a51-4a96-8f6f-e51297646ba7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 203.7GB: boot/grub/menu.lst
 203.7GB: boot/grub/stage2
 203.7GB: boot/initrd.img-2.6.28-11-generic
 203.7GB: boot/vmlinuz-2.6.28-11-generic
 203.7GB: initrd.img
 203.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by meierfra. on 2010-02-21
Good news, you have all boot files.

But RESULTS.txt does not match your description. 
You should be able to boot into XP but not into Vista:


> title		Windows XP (loader)
rootnoverify	(hd0,6)
savedefault 
makeactive
chainloader	+1

Due to the makeactive, this should give Grub Error 12.  Also where are no boot files on /dev/sda7.   So this entry is useless.


> title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

This will  load the boot sector of /dev/sda1 (your Vista partition).  According to RESULTS. txt /dev/sda1  holds all the boot files:

> sda1:
    Boot sector type:  Windows XP
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

But the boot sector type is XP. This means choosing "Windows Vista(loader)" entry on Grub menu should actually boot Windows XP. Is that true?  


> title		Windows Vista Recovery (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

This entry should boot your Recovery partition.

Before I make suggestion how to get Vista and XP to boot, I just want  to confirm that currently you are able to boot  XP but not Vista.

---

### Post by meierfra. on 2010-02-21
> I just installed Ubuntu so that grub would install as the main boot loader and I wouldn't have these problems. 
Are you planning to keep Ubuntu? Or  should we arrange things so that you can safely remove Ubuntu.

---

### Post by xXAlphaXx on 2010-02-21
Yes I plan on keeping all three OSes

UPDATE::

I was playing around with it and tried too log in on the Vista entry. The Vista entry boots XP.

The Vista recovery boots Vista recovery, so now we are trying too recover Vista, I renamed the entry in menu.lst so Vista is now XP.

But that doesn't make sense because its at 0,0 when XP is at 0,6 ...


And this is the part when confusion sets in. :)






EDIT:: Ugh thanks for the help but I don't even know why I am keeping Win Vista. I'm leveling this drive and doing a dual boot between XP and Ubuntu. I never have any problems with these two.

Again thank you. :)

---

### Post by meierfra. on 2010-02-21
> And this is the part when confusion sets in.
This is what is happening:

root (hd0,0)
chainloader +1

tells Grub to load the boot sector of /dev/sda1

The boot sector of /dev/sda1 is an XP boot  sector. An XP boot sector looks for /ntldr on the same partition. /ntldr looks at boot.ini  to figure out which OS to boot. boot.ini. boot.ini says:

> multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional"

So ntldr boots XP. 


To be able to boot Vista, you have to replace the XP boot sector on /dev/sda1 by  a Vista boot sector.

Boot from  your  Vista  CD/DVD. If you do not have one, you can download a  Vista Recovery CD from  [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").


At the first screen select your favorite language.
At the second screen choose "Repair your Computer".

If a pop windows appears, offering  to repair a problem with the "Startup options",   decline.

 On the  next screen select "Use recovery tools ..."  and click on "Next".

Choose "Command Prompt" at the next screen.
This will open a terminal. In the terminal type

```
bootrec /fixboot
```

Reboot.  Try   the entry on the Grub menu which you just renamed to "Windows XP".  You should either boot  directly into Vista, or get  boot menu with Vista and XP.

Don't worry if you don't have an entry for XP.  After you  successfully booted into Vista, we will work on XP.

---

### Post by meierfra. on 2010-02-21
> EDIT:: Ugh thanks for the help but I don't even know why I am keeping Win Vista. I'm leveling this drive and doing a dual boot between XP and Ubuntu. I never have any problems with these two.
I just finished  typing my instruction, when I saw your edit. So feel free to ignore my previous post. (edit: if you are planning to erase the whole drive and not only Vista, you can also ignore this post)

Even if you plan on ditching Vista, you need to fix  your  setup. Currently if you format or deleted the Vista partition, you will erase your XP boot  files and won't be able to XP any more.  

My next post will contain instructions how to move the XP boot files to the XP partition.  You should do that regardless, whether you plan to keep Vista or not.

---

### Post by meierfra. on 2010-02-21
> I'm leveling this drive and doing a dual boot between XP and Ubuntu. 

Are you going to erase the whole drive or just Vista?

---

