---
title: "Can't Access Ubuntu"
date: 2011-04-26
forum: General Help
---

### Post by Richiegs on 2011-04-26
I installed Ubuntu 10.04 within Windows XP using Wubi, but now I want to create a separate partition for Ubuntu. After I resized Windows partition and restarted my PC, I could not access Ubuntu anymore to finish creating a separate partition for Ubuntu. I replaced the file "Wubildr" in C:\ in Windows, but it still didn't work. Thank you in advance for anyone who offers help.

---

### Post by Richiegs on 2011-04-26
The error message was about the kernel being missing.

---

### Post by Rubi1200 on 2011-04-26
Hi,

please do the following so we can see what is going on with the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Richiegs on 2011-04-26
Here is the RESULTS.txt - /                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   162,529,604   162,433,215   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       631f5061-ce87-4d27-a709-15f657d22a90   ext3                                     
/dev/sda1        07D5-0709                              vfat       DellUtility                   
/dev/sda2        01CC040FDC1A1860                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda2/Wubi/boot/grub/menu.lst: ========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=2ECCD170CCD13337 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2ECCD170CCD13337

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-22-generic
uuid        2ECCD170CCD13337
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=2ECCD170CCD13337 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        2ECCD170CCD13337
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=2ECCD170CCD13337 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        2ECCD170CCD13337
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2eccd170ccd13337
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2eccd170ccd13337
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2eccd170ccd13337
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2eccd170ccd13337
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2eccd170ccd13337
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


  22.0GB: boot/grub/grub.cfg
  21.9GB: boot/grub/menu.lst
  21.9GB: boot/initrd.img-2.6.32-22-generic
  21.9GB: boot/vmlinuz-2.6.32-22-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by Richiegs on 2011-04-26
Please advise what I should do now after pasting the RESULT.txt. Thanks

---

### Post by bcbc on 2011-04-26
I think the resize changed the uuid on the windows partition. sudo blkid shows it as 01CC040FDC1A1860, whereas grub.cfg has it as 2eccd170ccd13337.

So that might be the main problem, when you see the grub menu, hit 'e' on the first entry, then DELETE the line starting "search --no-floppy....." and hit CTRL+x to boot.

But that's not all.

Replacing the wubildr was probably a bad idea - depending on where you got it. So if you have the original use that.
Also, did you use LVPM to resize the root.disk at some point? because you have grub legacy installed instead of grub2. LVPM doesn't work anymore because it has a dependency on grub legacy, and this will uninstall grub2 (required for wubi on latest releases).

But you probably have enough grub2 in the wubildr (and you still have the grub.cfg file) so you should be able to get the thing booting. Once booted check and reinstall grub2 if required:
```
sudo apt-get install grub-pc
```this should remove grub (legacy) and install grub-pc (grub2). When/if you get prompted where to install Grub to, select only /dev/loop0

Try that.

---

### Post by Mark Phelps on 2011-04-26
As an aside  ...

> After I resized Windows partition and restarted my PC,

WHAT did you use to do the resizing? A Windows utility? Or a Linux utility (e.g., GParted)?

Ordinarily, shrinking an XP partition using GParted should work out fine.

---

### Post by Richiegs on 2011-04-26
> **bcbc said:**
> I think the resize changed the uuid on the windows partition. sudo blkid shows it as 01CC040FDC1A1860, whereas grub.cfg has it as 2eccd170ccd13337.

So that might be the main problem, when you see the grub menu, hit 'e' on the first entry, then DELETE the line starting "search --no-floppy....." and hit CTRL+x to boot.

But that's not all.

Replacing the wubildr was probably a bad idea - depending on where you got it. So if you have the original use that.
Also, did you use LVPM to resize the root.disk at some point? because you have grub legacy installed instead of grub2. LVPM doesn't work anymore because it has a dependency on grub legacy, and this will uninstall grub2 (required for wubi on latest releases).

But you probably have enough grub2 in the wubildr (and you still have the grub.cfg file) so you should be able to get the thing booting. Once booted check and reinstall grub2 if required:
```
sudo apt-get install grub-pc
```this should remove grub (legacy) and install grub-pc (grub2). When/if you get prompted where to install Grub to, select only /dev/loop0

Try that.

Bcbc, I am able to access Ubuntu now. Thanks for your help!

---

### Post by bcbc on 2011-04-26
> **Richiegs said:**
> Bcbc, I am able to access Ubuntu now. Thanks for your help!

Great, you're welcome. 

PS when you re-installed grub2, make sure it regenerated grub.cfg

OH!!! I just remembered - if you reinstall grub2 on a wubi install you'll run into the corrupt loop device issue. Please check out the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") and run the "Permanent Fix" before rebooting to clean up the /boot/grub directory and then regenerate grub.cfg.

---

