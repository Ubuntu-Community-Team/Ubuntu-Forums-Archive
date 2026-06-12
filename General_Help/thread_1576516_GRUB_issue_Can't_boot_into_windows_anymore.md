---
title: "GRUB issue? Can't boot into windows anymore"
date: 2010-09-17
forum: General Help
---

### Post by airtacable on 2010-09-17
Hi All,

I dual boot with ubuntu 10.04 and windows XP. Although I use ubuntu 95% of the time, I use windows for sorting my portable apps and playing games, etc. 

Today I booted into windows and did some general security updates and virus scans (remember those?!), which included an update of avast AV. This resulted in the inevitable restart of the computer, but when I tried to boot into windows (from the ordinary grub menu) I got an error saying the ntoskrnl.exe file is missing or corrupt. I replaced the file using the xp disk and recovery console, but I still got the same error message.

I now think that the issue is with my boot.ini or grub file, but I wanted to seek advice before I go messing with these. I think that one of the security or AV updates altered the boot loader in some way, maybe assuming that it was just windows on the hard drive.

Any ideas guys?

airtacable

---

### Post by printfw on 2010-09-17
Did you try to restore a native windows boot loader to MBR? Will it be the same?

---

### Post by Rubi1200 on 2010-09-17
Windows problems are usually caused by Windows issues and I don't see how an update for Avast could mess up GRUB.

But, just to be sure:

1. boot the computer with the Ubuntu CD in live mode and post the results of the bootscript linked to at the bottom of my post.

2. go to the Avast forums and see if anyone has had similar problems (I am sure they won't bite if you tell them you use Ubuntu).

---

### Post by sikander3786 on 2010-09-17
> **printfw said:**
> Did you try to restore a native windows boot loader to MBR? Will it be the same?
Restoring Windows MBR will require you later to install GRUB2 in order to boot Ubuntu. It is worth a try though. Can't think of any other workaround. Have you got an XP CD? If so boot to the recovery console and type **fixmbr**. See if Windows works now. If it does, all you need is to re-install GRUB from a live cd.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by airtacable on 2010-09-17
Here's the results of the boot script. Nice one Rubi1200!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,871,476,109 1,871,476,047   7 HPFS/NTFS
/dev/sda2       1,871,476,110 1,953,520,064    82,043,955   5 Extended
/dev/sda5       1,871,476,173 1,875,379,904     3,903,732  82 Linux swap / Solaris
/dev/sda6       1,875,379,968 1,914,449,984    39,070,017  83 Linux
/dev/sda7       1,914,450,048 1,953,520,064    39,070,017  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F08849B588497ADC                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3a6d33da-ffe6-4bf0-8547-f8c91f147880   swap                                     
/dev/sda6        76817393-63d2-4f84-9a13-a7c23b098cad   ext3                                     
/dev/sda7        63ca3bac-9b28-4b9c-a33d-7755b8c63a27   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /home                    ext3       (rw,relatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=76817393-63d2-4f84-9a13-a7c23b098cad

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
# defoptions=quiet splash vga=795

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=76817393-63d2-4f84-9a13-a7c23b098cad ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        76817393-63d2-4f84-9a13-a7c23b098cad
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
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
proc                                       /proc           proc         defaults                            0  0  
# / was on /dev/sda6 during installation
UUID=76817393-63d2-4f84-9a13-a7c23b098cad  /               ext3         relatime,errors=remount-ro          0  1  
# /home was on /dev/sda7 during installation
UUID=63ca3bac-9b28-4b9c-a33d-7755b8c63a27  /home           ext3         relatime                            0  2  
# swap was on /dev/sda5 during installation
UUID=3a6d33da-ffe6-4bf0-8547-f8c91f147880  none            swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,users,umask=000,user  0  0  

=================== sda6: Location of files loaded by Grub: ===================


 974.7GB: boot/grub/menu.lst
 974.8GB: boot/grub/stage2
 974.8GB: boot/initrd.img-2.6.32-22-generic
 974.7GB: boot/initrd.img-2.6.32-23-generic
 974.8GB: boot/initrd.img-2.6.32-24-generic
 974.7GB: boot/vmlinuz-2.6.32-22-generic
 974.7GB: boot/vmlinuz-2.6.32-23-generic
 974.8GB: boot/vmlinuz-2.6.32-24-generic
 974.8GB: initrd.img
 974.7GB: initrd.img.old
 974.8GB: vmlinuz
 974.7GB: vmlinuz.old

---

### Post by Mark Phelps on 2010-09-17
Looks like you're mounting your MS Windows OS partition in fstab.  That can have all kinds of nasty results -- as you have discovered.

When you get MS Windows working again, go into Ubuntu and remove the automount for your MS Windows OS partition from fstab.

---

### Post by Rubi1200 on 2010-09-17
The other problem I see is that it says you have legacy-GRUB installed > Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst. but version 10.04 uses GRUB2.

You need to reinstall GRUB from a LiveCD to correct this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

The first method usually works, but if needs be use the Chroot method (method 3).

---

### Post by airtacable on 2010-09-17
Thanks guys.

The reason for the legacy grub and 10.04 is that I've been lazy and just went for the upgrade instead of a fresh install since 9.04. I'll know better next time.

I'll give those things a try tomorrow.

Chat to ye later,

airtacable

---

### Post by airtacable on 2010-09-18
Hey guys,

I'm in the middle of installing Grub2 (according to these instructions [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) method 1) and I'm not sure which partition to mount:

sda1  Windows  Boot

sda2  Extended
  sda5  SWAP
  sda6  /
  sda7 /home

My current version of grub is in sda6 (/boot/grub) but sda1 has the boot flag. Please advise.

airtacable

---

### Post by airtacable on 2010-09-18
Still have a problem with the above, but I have a few more too:

I used the fixmbr command in the recovery console and it worked . . . . sort of. The command doesn't set the windows partition as the active partition. So now when I turn on my PC, I have no grub menu and it goes directly into windows, but it's looking in the wrong place and I'm getting the kernal not found error as above.

Apparently, the super grub disk will fix this, but as I'm already using a ubuntu live cd, how do I burn a another one. I might try it with UNetBootIn instead.

Any other ideas?

airtacable

---

### Post by WorMzy on 2010-09-18
> **Rubi1200 said:**
> The other problem I see is that it says you have legacy-GRUB installed  but version 10.04 uses GRUB2.

You need to reinstall GRUB from a LiveCD to correct this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

The first method usually works, but if needs be use the Chroot method (method 3).

10.04 installs grub2 by default, but there's nothing preventing users from using grub legacy if they do so choose. Certainly, the presence of grub legacy instead of grub2 won't cause any problems with Windows.

Airtacable, if you still want to use grub legacy, don't worry about installing grub 2; but if you want to try out grub 2, you should install it to your Ubuntu partition, not the Windows partition. The MBR in sda1 will be overwritten after the installation, when you set grub up.

---

### Post by airtacable on 2010-09-18
Ok, so I've followed the instructions to install grub2 using a liveCD, 9.10 in my case, and I restarted my computer and arrived at grub 1.97 beta. This is a command line version so it isn't much use to me.

I'm currently downloading 10.05 and will try again.

---

### Post by Rubi1200 on 2010-09-18
> **airtacable said:**
> Ok, so I've followed the instructions to install grub2 using a liveCD, 9.10 in my case, and I restarted my computer and arrived at grub 1.97 beta. This is a command line version so it isn't much use to me.

I'm currently downloading 10.05 and will try again.
It makes no difference if you use the 9.10 or 10.04 CD because both use GRUB2.

Did you follow the instructions to the letter including making sure you installed to sda etc.?

If the first method did not work, try Method 3: CHROOT

---

### Post by airtacable on 2010-09-18
Yes method 3 worked for me. Thanks Rubi1200.

I'm not sure how I did it, but I managed to the legacy grub back instead of grub2. There's an option for chainloading Grub2 (or something like that)  in the OS list, but I get an error if I go into it. It'll do for the moment. but I'll do a fresh install 10.10 when it comes out to get Grub2.

I still can't get into Windows though, so I'm back where I started.

---

