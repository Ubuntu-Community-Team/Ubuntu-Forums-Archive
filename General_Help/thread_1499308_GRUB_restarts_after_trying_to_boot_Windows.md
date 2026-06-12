---
title: "GRUB restarts after trying to boot Windows"
date: 2010-06-01
forum: General Help
---

### Post by Dorsenstein on 2010-06-01
This happened after installing Ubuntu 10.04 LTS. When I was installing, GRUB said it couldn't install to /dev/sda/4 and /dev/sda/6. I knew my Windows 7 loader was /dev/sda/2 and so I installed GRUB to everything except 4 and 6.  However, when I boot the computer and try to boot Windows 7 on /dev/sda/2 It shows a blank screen with a cursor for a moment and then just Reloads GRUB. Any suggestions?

---

### Post by wilee-nilee on 2010-06-01
Post this script to confirm all this, in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can also have it post in the code tags by highlighting the pasted text into the reply and clicking on the # sign in the gui's top portion.

---

### Post by drs305 on 2010-06-01
This will likely describe your situation and provide the solution:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")
but post your boot info script information if it doesn't.

It is generally recommended to install Grub2 only to the drive and not to specific partitions, and you definitely don't want it on the Windows partition.

---

### Post by Dorsenstein on 2010-06-02
See, I tried reinstalling GRUB to my only drive on /dev/sda, but now I don't even have a boot option and it just boots straight to ubuntu.

EDIT: Here's My boot info

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 819763458 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 819763458 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 819763458 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 819763458 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304    20,254,719    20,156,416   7 HPFS/NTFS
/dev/sda3          20,254,720   819,484,671   799,229,952   7 HPFS/NTFS
/dev/sda4         819,491,715   976,768,064   157,276,350   5 Extended
/dev/sda5         819,491,778   970,277,804   150,786,027  83 Linux
/dev/sda6         970,277,868   976,768,064     6,490,197  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0416                              vfat       DellUtility                   
/dev/sda2        BECA7C70CA7C26B5                       ntfs       RECOVERY                      
/dev/sda3        0A587EA3587E8CE7                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c76f8ed6-d9f7-4731-98d7-1eade17fa32f   ext4                                     
/dev/sda6        9ced54e7-6db9-45da-b102-ca577fe2e94b   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c76f8ed6-d9f7-4731-98d7-1eade17fa32f

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Chainload into GRUB 2
root        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        c76f8ed6-d9f7-4731-98d7-1eade17fa32f
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c76f8ed6-d9f7-4731-98d7-1eade17fa32f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set beca7c70ca7c26b5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c76f8ed6-d9f7-4731-98d7-1eade17fa32f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9ced54e7-6db9-45da-b102-ca577fe2e94b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 419.8GB: boot/grub/core.img
 422.8GB: boot/grub/grub.cfg
 419.7GB: boot/grub/menu.lst
 419.7GB: boot/grub/stage2
 426.8GB: boot/initrd.img-2.6.31-21-generic
 429.0GB: boot/initrd.img-2.6.32-22-generic
 424.6GB: boot/vmlinuz-2.6.31-21-generic
 426.6GB: boot/vmlinuz-2.6.32-22-generic
 429.0GB: initrd.img
 426.8GB: initrd.img.old
 426.6GB: vmlinuz
 424.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by wilee-nilee on 2010-06-02
n

---

### Post by drs305 on 2010-06-02
> **Dorsenstein said:**
> See, I tried reinstalling GRUB to my only drive on /dev/sda, but now I don't even have a boot option and it just boots straight to ubuntu.

The reason is that you are using Grub (with an option to chainload to Grub2) and in /boot/grub/menu.lst you have:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

As written, you can press ESC to show the Grub menu. If you want the menu to appear automatically, place a # symbol in front of *hiddenmenu*:

> # Hides the menu by default (press ESC to see the menu)
**#**hiddenmenu

You can edit this once you have booted by running the following command:
```
gksu gedit /boot/grub/menu.lst
```
You may also want to change the *timeout* value in the same section to more than 3 to give you more time to press the ESC key if the menu doesn't display.


Note that Grub2 has found Windows and you will see that option if you select "Chainload into Grub 2". Unfortunately it wouldn't work even if you selected G2 and then Windows. The reason is that Grub2 is installed in sda1, sda2 and sda3. Windows won't boot with that configuration and you must correct that using the procedure linked to in my previous post:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by Dorsenstein on 2010-06-02
Thanks! I just have one more question.  When I am using testdisk and have gotten to the Fifth Screen, I have a RECOVERY and OS partition that are both used by Windows. Which one should I select?

---

### Post by drs305 on 2010-06-02
> **Dorsenstein said:**
> Thanks! I just have one more question.  When I am using testdisk and have gotten to the Fifth Screen, I have a RECOVERY and OS partition that are both used by Windows. Which one should I select?

I am not a Windows guy. I would expect it to be the Windows partition if the other one is strictly a recovery partition. However, I see the "boot flag" is on the smaller sda2 partition so please wait until someone more familiar with Windows confirms this.

---

### Post by Mark Phelps on 2010-06-03
For future reference, your partitions are as follows:
-- sda2: Win7 boot loader
-- sda3: Win7 OS

So, you should boot from sda2; you will not be able to boot from sda3.

---

### Post by drs305 on 2010-06-03
Mark,

Thanks for the input. Is every normal Win 7 install going to have a separate boot partition and then a main OS partition?

---

