---
title: "Grub confused after partition removal"
date: 2010-09-15
forum: General Help
---

### Post by 2CV67 on 2010-09-15
I recently used GParted to adjust partition sizes on my triple-boot desktop (XP & Ubuntu 10.04 & Ubuntu LTS 8.04).
While I was at it, I eliminated a shared partition I didn't use much.

Now, I can boot to XP & 10.04 OK but not to 8.04.

I assumed the partition references would be handled automatically, but that doesn't seem to have happened.

Grub thinks 8.04 is on sda7 which no longer exists.

I suppose that partition is now sda6.

fstab in 10.04 has:
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 /home ext3 relatime 0 2

and fstab-disk-manager-save has:
#Entry for /dev/sda6 :
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670	/home	ext3	relatime	0	2

fstab in 8.04 has:
# /dev/sda7
UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 /               ext3    relatime,errors=remount-ro 0       1

menu.lst in 10.04 has:
title Ubuntu LTS on sda7
root (hd0,6)
chainloader +1

menu.lst in 8.04 has:
title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

So I am guessing I need to convert my (hd0,6)s to (hd0,5)s & my UUID=5998... to UUID=e3bb...

My question is - which files do I need to update manually & which files will update automatically?

Of course, I have backed up my files & can just try things, but a little expert advice would be comforting!

Thanks!

---

### Post by WorMzy on 2010-09-15
Assuming you're running 10.04 and using Grub2, just run

```
sudo update-grub
```

That should fix things.

---

### Post by -kg- on 2010-09-15
> **WorMzy said:**
> Assuming you're running 10.04 and using Grub2, just run

```
sudo update-grub
```

That should fix things.

Exactly.  That ***should*** fix the problem.

Whenever you create a Logical partition (that is one that is created within an Extended partition, allowing you to have more than 4 partitions per drive), the partition is assigned a drive number, such as sda5, sdb6, etc. sda or sdb indicates the physical hard drive, while the number indicates a partition on that drive.

The number assigned to the Logical partition (Primary partitions are different) is assigned chronologically to their creation, not by order on the disk.  When you delete a Logical partition, the designation of any partition that was created after that partition will change.

For example, you have sda5, sda6, and sda7.  If you delete sda6, then sda7 will become the new sda6 while sda5 stays the same.  If you delete sda5, then both sda6 and sda7 will change.

That's what I'm assuming happened to your Hardy installation, and update-grub should correct that.  I say should because I had a problem with this with an OpenSUSE installation.  I ended up reinstalling OpenSUSE because it used another method of partition identification.  Ubuntu should be OK.

---

### Post by psusi on 2010-09-15
It sounds like you are running grub legacy.  Grub2 does not have a menu.lst.  If you remove grub legacy and install grub2, it should work automagically.

---

### Post by -kg- on 2010-09-15
Actually, doesn't "sudo update-grub" work with legacy as well as GRUB2?

---

### Post by 2CV67 on 2010-09-16
I am still running grub legacy.

I have thought about "upgrading" to grub2 several times, but always backed down after spending some time browsing comments on forums, where there seem to be more potential problems than obvious benefits.

Today I did get as far as SynApt > grub-pc > Mark for installation, to try it, then I saw it wanted to remove grub at the same time, so I stopped.

One problem at a time.

I would like to fix my grub legacy problem today & leave grub2 for some other time...

So which files do I need to change manually?
I assume menu.lst in both partitions.
fstab?
fstab-disk-manager-save??
others???

Thanks!

---

### Post by dcstar on 2010-09-16
> **-kg- said:**
> Actually, doesn't "sudo update-grub" work with legacy as well as GRUB2?

AFAIK yes, pity people don't seem to take this handy advice.

---

### Post by 2CV67 on 2010-09-16
> **-kg- said:**
> Actually, doesn't "sudo update-grub" work with legacy as well as GRUB2?

Sounded good, so I just tried it & it put a new date on the menu.lst file, but did not change anything for the chainloaded:
title Ubuntu LTS on sda7
root (hd0,6)
chainloader +1

---

### Post by 2CV67 on 2010-09-16
Hmm...

I updated all references in my 2 menu.lst files & the fstab file in the LTS partition:
sda7 > sda6
(hd0,6) > (hd0,5)
UUID=5998... > UUID=e3bbb...

But no improvement.

I get the first grub screen, with 10.04 as default & with XP available OK & with the "Ubuntu LTS on sda6" item at the bottom OK.
But when I select that item, instead of opening the second boot screen, as it did before repartitioning, I just get to a "grub>_" invite.
From there Ican enter "reboot" to escape.

Any ideas where I am going wrong?

Thanks!

---

### Post by 2CV67 on 2010-09-16
At the bottom of my first grub screen, is the entry:
"Ubuntu LTS on sda6"

When I select that, I only get a "grub>_" invite.

I just found that if I then enter 
grub>_"configfile (hd0,5)/boot/grub/menu.lst" 
that brings up the second grub screen with my LTS kernels.
They don't boot yet, but this is a good first step.

What I don't understand now, is why selecting "Ubuntu LTS on sda6" from the first screen does not equally bring up the second screen.

The corresponding entry in the first menu.lst is:
> title Ubuntu LTS on sda6
root (hd0,5)
chainloader +1

There doesn't seem much that could go wrong there.
But...

All suggestions welcome!

---

### Post by WorMzy on 2010-09-16
I use grub legacy, but I've never used update-grub for it. I prefer to manually edit menu.lst.

May I ask why you have two menu.lsts? Is this deliberate, or would you prefer to just have one?

Also, could I get you to run this script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Post the content of the file it creates here, and I'll take a look at it.

Use [CODE[COLOR="black"]][[/COLOR]/CODE] tags to keep the information easy to read.

---

### Post by 2CV67 on 2010-09-16
Ah! - that looks impressive!

I have a menu.lst for each of my 2 Ubuntu setups.
They are meant to be separate.
The idea was that I would always be able to use my backup LTS version to fix the current version, which, in the past, often got in a mess after upgrades - typically losing wireless or freezing...
I have always been happy with 2 menus & they always worked OK until this partition removal.
It is ironic that I am now using current Ubuntu to try to fix my backup!

Here are the results of BootInfoScript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 181726901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3         211,302,945   232,396,289    21,093,345  83 Linux
/dev/sda4         114,816,555   211,302,944    96,486,390   5 Extended
/dev/sda5         129,194,730   211,302,944    82,108,215  83 Linux
/dev/sda6         114,816,681   129,194,729    14,378,049  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sdb2          61,432,560   156,296,384    94,863,825  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        2B1B-1302                              vfat       XP                            
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap                                     
/dev/sda3        f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e3bbb061-9a3d-4c6e-960a-03d42b490670   ext3                                     
/dev/sda6        5998da7e-4123-4481-80f0-99a6f3c5e244   ext3       LTS Ubuntu Drive              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        150D-1B41                              vfat       LACIE                         
/dev/sdb2        a19cc0e6-2b6b-4fad-b591-99a1d74ac5bf   ext3       Lacie_linux                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /home                    ext3       (rw,relatime)
/dev/sdb2        /media/Lacie_linux_      ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/LACIE_            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn


=========================== sda3/boot/grub/menu.lst: ===========================

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
default        2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP dition familiale
root        (hd0,0)
savedefault
makeactive
chainloader    +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash

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
# howmany=3

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda6
root (hd0,5)
chainloader +1

#just the end.




=============================== sda3/etc/fstab: ===============================

proc /proc proc defaults 0 0
UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c / ext3 relatime,errors=remount-ro 0 1
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 /home ext3 relatime 0 2
#UUID=48A5-D628 /media/SHARE vfat utf8,umask=007,gid=46 0 2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda3: Location of files loaded by Grub: ===================


 111.6GB: boot/grub/menu.lst
 113.5GB: boot/grub/stage2
 113.7GB: boot/initrd.img-2.6.27-14-generic
 113.7GB: boot/initrd.img-2.6.28-16-generic
 113.6GB: boot/initrd.img-2.6.28-17-generic
 113.7GB: boot/initrd.img-2.6.31-17-generic
 114.1GB: boot/initrd.img-2.6.32-22-generic
 114.1GB: boot/initrd.img-2.6.32-23-generic
 113.7GB: boot/initrd.img-2.6.32-24-generic
 113.6GB: boot/vmlinuz-2.6.27-14-generic
 113.6GB: boot/vmlinuz-2.6.28-16-generic
 113.6GB: boot/vmlinuz-2.6.28-17-generic
 113.6GB: boot/vmlinuz-2.6.31-17-generic
 118.7GB: boot/vmlinuz-2.6.32-22-generic
 114.0GB: boot/vmlinuz-2.6.32-23-generic
 113.7GB: boot/vmlinuz-2.6.32-24-generic
 113.7GB: initrd.img
 114.1GB: initrd.img.old
 113.7GB: vmlinuz
 114.0GB: vmlinuz.old

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
# kopt=root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro

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
# defoptions=splash

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
# howmany=4

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 ro splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 ro single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 ro splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 ro single
initrd        /boot/initrd.img-2.6.24-27-generic


title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP dition familiale
root        (hd0,0)
savedefault
makeactive
chainloader    +1



# This entry copied from U23 for Intrepid on /dev/sda3.
title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro single 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.2, kernel 2.6.24-22-generic (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd        /boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro single 
initrd        /boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.2, memtest86+ (on /dev/sda3)
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  60.6GB: boot/grub/menu.lst
  60.6GB: boot/grub/stage2
  60.4GB: boot/initrd.img-2.6.24-23-generic
  60.4GB: boot/initrd.img-2.6.24-23-generic.bak
  60.4GB: boot/initrd.img-2.6.24-24-generic
  60.4GB: boot/initrd.img-2.6.24-24-generic.bak
  60.4GB: boot/initrd.img-2.6.24-25-generic
  60.4GB: boot/initrd.img-2.6.24-25-generic.bak
  60.4GB: boot/initrd.img-2.6.24-26-generic
  60.4GB: boot/initrd.img-2.6.24-26-generic.bak
  60.5GB: boot/initrd.img-2.6.24-27-generic
  60.5GB: boot/initrd.img-2.6.24-27-generic.bak
  60.5GB: boot/initrd.img-2.6.24-28-generic
  60.5GB: boot/initrd.img-2.6.24-28-generic.bak
  60.5GB: boot/vmlinuz-2.6.24-23-generic
  60.5GB: boot/vmlinuz-2.6.24-24-generic
  60.4GB: boot/vmlinuz-2.6.24-25-generic
  60.4GB: boot/vmlinuz-2.6.24-26-generic
  60.4GB: boot/vmlinuz-2.6.24-27-generic
  60.4GB: boot/vmlinuz-2.6.24-28-generic
  60.5GB: initrd.img
  60.5GB: initrd.img.old
  60.4GB: vmlinuz
  60.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

Thanks for what looks like a useful tool!

---

### Post by quadproc on 2010-09-16
> **2CV67 said:**
> Ah! - that looks impressive!

I have a menu.lst for each of my 2 Ubuntu setups.
They are meant to be separate.
The idea was that I would always be able to use my backup LTS version to fix the current version, which, in the past, often got in a mess after upgrades - typically losing wireless or freezing...
I have always been happy with 2 menus & they always worked OK until this partition removal.
It is ironic that I am now using current Ubuntu to try to fix my backup!

Here are the results of BootInfoScript:

I had an almost identical problem a few days ago.  With some help from other forum readers and from the web, I managed to find a solution.

The brief history of my problem: I was intending to delete one of my two swap partitions since one is all that can be used so I used GParted to shuffle things around.  Without my having a chance to accept the change, GParted merged my two swap partitions after the shuffle! This altered the partition numbers; I had started with 5, 6, 7, and 8 but I ended up with 5, 6, and 7.  Since my grub and my OS was located on partition 8, all that I could get at boot time was grub error 17.

I found lots of things on the web that related to this kind of problem but none of those postings helped until I found one that actually worked.  I used it to be able to boot this system and then I used grub-install to replace the now defunct grub that I used to use.  It turns out that grub-install installed grub-pc, not legacy grub.  But this turned out to be OK; it works fine and in some respects it is simpler and easier.

Edit: One additional note: grub-pc changes the way that partitions are numbered as compared to grub legacy; the partition numbers are now 1-relative so you don't need to make them one smaller as you did with grub legacy.

Please see my post relating to the fix that worked for me - it is #13, at the end of the thread:
[http://ubuntuforums.org/showthread.php?t=1570208](http://ubuntuforums.org/showthread.php?t=1570208)

quadproc

---

### Post by WorMzy on 2010-09-16
> sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 181726901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. _Stage2 looks on partition #7 for _
                       _/boot/grub/menu.lst._
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab


This is where the main problem lies, I think. The only way around it (as far as I can think of) is to rerun grub-install on that partition.

[This]("http://wiki.linuxquestions.org/wiki/GRUB#Solution_1") may help you with that.

The options in the second list are not booting because the UUID is incorrect. You're saying that the kernel is on e3bbb061-9a3d-4c6e-960a-03d42b490670, which is sda5; Ubuntu 8.04 is installed on sda6, 5998da7e-4123-4481-80f0-99a6f3c5e244. UUIDs are constant (more or less) so you didn't need to change them after the partition deletion.

---

### Post by 2CV67 on 2010-09-16
Mission Accomplished Guys!

Using configfile instead of chainloder got me to the second screen OK (don't ask me why or how...).

Undoing my screwed-up UUIDs got LTS to boot!

:D :D :D

Very grateful & respectful thanks for all that help!

Great community!

---

