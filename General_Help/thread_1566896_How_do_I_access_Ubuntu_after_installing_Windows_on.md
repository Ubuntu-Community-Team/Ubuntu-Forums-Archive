---
title: "How do I access Ubuntu after installing Windows on a partition?"
date: 2010-09-03
forum: General Help
---

### Post by braniac5 on 2010-09-03
Hi folks, I've been using Ubuntu for three years but now have a job that requires me to have Windows 7 on my computer at home. I decided I'd do a clean install of Windows and then later re-install Ubuntu on a partition. 

I saved all my Ubuntu files to an external hard drive, put in a shiny copy of Windows 7 to perform a clean install...but it said I need a NTFS partition to proceed (I did not have one). I downloaded the gnome partitioner, created a new NTFS partition (like magic!) and installed Windows 7. 

After Windows was up and running, I put in the Ubuntu live cd and when I got to the partition option...the old partition was still there, with Ubuntu still on it. For whatever reason, I thought it would be deleted when I installed Windows. 

So, one question: how do I access this partition? I would like to have the option to switch back and forth between operating systems on startup. 

If that's impossible, is there some way to delete the old Ubuntu installation? I don't mind getting rid of it, as the only thing still on it is a single episode of "Futurama." 

I feel like this will have a really simple solution, I'm just not literate enough in the ways of partitioning to know what I'm doing...

---

### Post by Rubi1200 on 2010-09-03
Hi,
to get a better overview of your setup please boot the computer with the Ubuntu CD (choosing to try not install) and post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by braniac5 on 2010-09-03
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6cbb13d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   236,404,735   236,404,673  83 Linux
/dev/sda2    *    236,404,736   472,004,607   235,599,872   7 HPFS/NTFS
/dev/sda3         472,005,765   488,392,064    16,386,300   5 Extended
/dev/sda5         472,005,828   488,392,064    16,386,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7   ext3                                     
/dev/sda2        1D6B98D53287E848                       ntfs       NTFS                          
/dev/sda5        19b8d2a2-0857-41dc-8bc2-c8e33b29fac2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /media/NTFS              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
# kopt=root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/memtest86+.bin
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
UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=19b8d2a2-0857-41dc-8bc2-c8e33b29fac2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.4GB: boot/grub/menu.lst
   7.4GB: boot/grub/stage2
   7.3GB: boot/initrd.img-2.6.28-11-generic
   7.4GB: boot/initrd.img-2.6.31-22-generic
   7.4GB: boot/vmlinuz-2.6.28-11-generic
   7.4GB: boot/vmlinuz-2.6.31-22-generic
   7.4GB: initrd.img
   7.3GB: initrd.img.old
   7.4GB: vmlinuz
   7.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by Mark Phelps on 2010-09-03
> **braniac5 said:**
> I downloaded the gnome partitioner, created a new NTFS partition (like magic!) and installed Windows 7. After Windows was up and running, I put in the Ubuntu live cd and when I got to the partition option...the old partition was still there, with Ubuntu still on it. For whatever reason, I thought it would be deleted when I installed Windows. 
You said you created an NTFS partition -- that's where Win7 got installed.  Unless you deleted the Linux partition and created the NTFS partition in its place, I would expect the Linux partition to still be there.
> So, one question: how do I access this partition? 
Certainly NOT from within Win7 -- since it can't read Ext4 partitions at all.  You COULD access it by booting from a LiveCD -- if all you want to do is copy off your files.
> I would like to have the option to switch back and forth between operating systems on startup. 
If your Ubuntu installation is intact, you can use a LiveCD to reinstall GRUB -- see section 11.2 in the link below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

> is there some way to delete the old Ubuntu installation? I don't mind getting rid of it, as the only thing still on it is a single episode of "Futurama." 
Boot from a LiveCD, confirm that the Ubuntu partition is NOT mounted, and delete it.

---

### Post by llawwehttam on 2010-09-03
I wouldn't install GRUB.

I would use [http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)

Manageable from windows.

---

### Post by braniac5 on 2010-09-03
> **Mark Phelps said:**
> Boot from a LiveCD, confirm that the Ubuntu partition is NOT mounted, and delete it.

How do I know if it's mounted or not mounted? 

> **llawwehttam said:**
> I wouldn't install GRUB.

When I was searching for similar threads, a lot came up where installing GRUB was a big recommendation, and usually it ended up with the user wiping everything and doing a clean install of both systems. Is there a reason GRUB is such a risk?

---

### Post by Rubi1200 on 2010-09-03
According to the bootscript you have an Ubuntu partition. The problem is that GRUB is not installed to the MBR.

There is also a Windows partition; so everything looks fine.

There is NO danger in reinstalling GRUB (and it is the recommended method). Once installed from the LiveCD, GRUB will recognize the Windows partition and allow you to choose between both at boot.

I do not see the point in installing another bootloader, as suggested above, when GRUB is a powerful and configurable tool.

The link posted by Mark Phelps will allow you to do this. Personally, I recommend using the instructions in section 11.1 (the first method is the easiest). Please follow the instructions to the letter and don't forget to update GRUB after rebooting (this will allow it to recognize Windows).

If you have any questions, feel free to ask.

---

### Post by oldfred on 2010-09-03
A lot of people do not realize all you have to do is reinstall grub or grub2. Now that we have two versions of grub that do not work together it is a little more confusing.

You have 9.10 installed but grub legacy 0.97 with menu.lst (You must have upgraded). If you do a new install you will get grub2 that uses grub.cfg for the menu.

If you just want to reinstall grub to the MBR you will be able to boot both Ubuntu & windows. Grub legacy was not very good at finding windows 7 so we often had to manually add a boot stanza for windows. Grub2 is very good at finding almost all other systems without any manual editing.

When you boot with a liveCD it does not mount anything except possibly swap unless you have clicked on a partition to see what is in it. It will show  a little key symbol to show it is mounted. Often swap is inside an extended partition so the entire extended is mounted but all you have to do is click on the swap partition (right click? I forgot) and swap off to unmount it.

If you are dual booting you may want a separate NTFS partition for any data that you would like in both. I use that for firefox & thunderbird profiles so I have all the same bookmarks & emails in whichever system I have booted.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by BrandyBear on 2010-09-03
i thought 2 GRUBS would work?

---

### Post by oldfred on 2010-09-03
There is a upgrade using old grub to boot grub2. 

But we have seen a lot of cases where both are installed and it creates some issue or another. Total removal of both and reinstall of one or the other then seems to work.

I consider grub2 better but a few have issues and revert to grub legacy. Other just resist change.

[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by braniac5 on 2010-09-03
> **Rubi1200 said:**
>  The link posted by Mark Phelps will allow you to do this. Personally, I recommend using the instructions in section 11.1 (the first method is the easiest). Please follow the instructions to the letter and don't forget to update GRUB after rebooting (this will allow it to recognize Windows).

If you have any questions, feel free to ask.

Hey - I tried the first and second methods, but when I try to update grub all I get is: 

grub-probe: error: cannot find a device for /.

And starting the computer up normally gets this: 

sh :grub>

---

### Post by Rubi1200 on 2010-09-03
Did you do this from the LiveCD?
Did you mount sda1 and install GRUB to sda?

If yes, then perhaps try Method 3; this has worked for others before though it requires more commands.

EDIT: see the posts by oldfred on the previous page. I am not sure if you can install GRUB2 over legacy-GRUB using just the methods linked to.

What version CD are you using; 9.10?

---

### Post by oldfred on 2010-09-03
If you get to sh:grub can you manually boot:

Manual boot:

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot

---

### Post by braniac5 on 2010-09-03
> **Rubi1200 said:**
>  EDIT: see the posts by oldfred on the previous page. I am not sure if you can install GRUB2 over legacy-GRUB using just the methods linked to.

What version CD are you using; 9.10?

I'm using 9.10 - Karmic works best on this computer. I'll try out oldfred's recommendations right now.

---

### Post by braniac5 on 2010-09-03
So I've tried every method on here, but keep getting this when I reboot: 

GNU Grub Version 1.97 ~beta4
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ESC at any time exits. ]
sh :grub>

This is the output of that script I tried previously (I now have Grub 2?):

> This is the output of the boot script downloaded earlier: 

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6cbb13d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   236,404,735   236,404,673  83 Linux
/dev/sda2    *    236,404,736   472,004,607   235,599,872   7 HPFS/NTFS
/dev/sda3         472,005,765   488,392,064    16,386,300   5 Extended
/dev/sda5         472,005,828   488,392,064    16,386,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7   ext3                                     
/dev/sda2        1D6B98D53287E848                       ntfs       NTFS                          
/dev/sda5        19b8d2a2-0857-41dc-8bc2-c8e33b29fac2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
# kopt=root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7
kernel        /boot/memtest86+.bin
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
UUID=52887d2d-f88e-4e9d-b4d0-eeadb3c3e0b7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=19b8d2a2-0857-41dc-8bc2-c8e33b29fac2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.4GB: boot/grub/core.img
   7.4GB: boot/grub/menu.lst
   7.4GB: boot/grub/stage2
   7.3GB: boot/initrd.img-2.6.28-11-generic
   7.4GB: boot/initrd.img-2.6.31-22-generic
   7.4GB: boot/vmlinuz-2.6.28-11-generic
   7.4GB: boot/vmlinuz-2.6.31-22-generic
   7.4GB: initrd.img
   7.3GB: initrd.img.old
   7.4GB: vmlinuz
   7.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdbIf there's no solution to this, is it possible to remove grub so I can load Windows normally?

---

### Post by oldfred on 2010-09-03
You have grub2 in the MBR but menu.lst from grub legacy in sda1 and no grub.cfg which you have to have.

You can chroot into it.

sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then uninstall grub and grub2 (grub-pc) and reinstall grub2.

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda


If you just want windows back. You can use a windows cd and 
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector

Or if you do not have a windows cd you can install lilo (just to the MBR) which works just like windows.
Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by braniac5 on 2010-09-03
> **oldfred said:**
> You can chroot into it.

sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then uninstall grub and grub2 (grub-pc) and reinstall grub2.

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

Good news: I can load my old Ubuntu now. Bad news: Ubuntu loads automatically and Grub does not give me a choice as to which OS to boot into at startup, so now I can't access Windows. Is there a way to get that option to come up now that my Grub issues are (kind of) sorted out? 

(Thanks for all the help, by the way).

---

### Post by oldfred on 2010-09-04
sudo update-grub

That should get the osprober to see the windows install and add it to the grub.cfg or menu. Then if you have a choice on the menu it will present the menu on boot. Otherwise you have to hold shift down from BIOS boot until menu appears.

---

### Post by braniac5 on 2010-09-04
Awesome! Works perfectly. I forgot about the grub update (it was mentioned in the tutorials but slipped my mind just now). A thousand thank yous.

---

