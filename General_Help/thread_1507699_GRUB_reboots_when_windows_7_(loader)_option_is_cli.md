---
title: "GRUB reboots when windows 7 (loader) option is clicked after 10.04 upgrade"
date: 2010-06-11
forum: General Help
---

### Post by auv5 on 2010-06-11
hey ubuntu community!
I'm having a bit of trouble with the GRUB boot loader. I have a disk for ubuntu 9.10, so i decided to install that and upgrade to ubuntu 10.04, before the 10.04 upgrade, the GRUB worked fine. Now when I click the "windows 7 (loader)" option (By the way, for some weird reason, that is what it calls my XP install.) It restarts my computer. I ran the boot info script and got this: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9229039 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 9185759 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A04C723C4C720CF2                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        03917f87-cd57-46b0-a372-8c47077cc863   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        62380fe3-73a9-4c7a-8d67-ebd7147a1d27   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=jack)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03917f87-cd57-46b0-a372-8c47077cc863

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
uuid        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        03917f87-cd57-46b0-a372-8c47077cc863
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=03917f87-cd57-46b0-a372-8c47077cc863 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 03917f87-cd57-46b0-a372-8c47077cc863
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a04c723c4c720cf2
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=03917f87-cd57-46b0-a372-8c47077cc863 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=62380fe3-73a9-4c7a-8d67-ebd7147a1d27 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
    .1GB: boot/grub/menu.lst
    .9GB: boot/initrd.img-2.6.31-14-generic
   1.3GB: boot/initrd.img-2.6.32-22-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.3GB: boot/vmlinuz-2.6.32-22-generic
   1.3GB: initrd.img
    .9GB: initrd.img.old
   1.3GB: vmlinuz
    .6GB: vmlinuz.old
```

hope you can help, if you require other files, just ask.

---

### Post by wilee-nilee on 2010-06-11
Your in good shape the fix will be provided soon there is at least one members on-line that can help you, there are others as well I'm sure.

If you look at the script you have put grub in sda1, the windows partition, for future reference it only goes to the mbr of the disc installed to..

---

### Post by dcstar on 2010-06-11
> **auv5 said:**
> hey ubuntu community!
I'm having a bit of trouble with the GRUB boot loader. I have a disk for ubuntu 9.10, so i decided to install that and upgrade to ubuntu 10.04, before the 10.04 upgrade, the GRUB worked fine. Now when I click the "windows 7 (loader)" option (By the way, for some weird reason, that is what it calls my XP install.) It restarts my computer.
..........

hope you can help, if you require other files, just ask.

```
sudo update-grub
```

---

### Post by wilee-nilee on 2010-06-11
> **dcstar said:**
> ```
sudo update-grub
```

With grub in sda1 this is a testdik job.;)

---

### Post by auv5 on 2010-06-11
The sudo update-grub did not work. What is this tesdtik you speak of?
Thanks for this and future replies :)
auv5

---

### Post by wilee-nilee on 2010-06-11
> **auv5 said:**
> The sudo update-grub did not work. What is this tesdtik you speak of?
Thanks for this and future replies :)
auv5

Here is a link, the instructions are on the page, but I suggest not doing this yet as there may be problems I don't see, and messing with it more, can result in much more damage. I'm not sure if additional work needs to be done.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you decide to just risk it you better be sure you are backed up and have a install dvd just in case. Always be prepared if you know what I mean.;)

Also so hold on I see the person on line who can give you a more definitive answer I'm sure they will be by shortly.

---

### Post by john newbuntu on 2010-06-11
Not to intrude here, but try wilee-nilee's post and see if that works.  If for whatever reason it does not work, only then try what follows:

You have installed a part of grub2 on to /dev/sda1.  Plus you have a combination of the win boot loaders on the same partition.  I would clean that up first by following this link(presuming you have the win7 installation CD).  Follow the section titled "How to restore the Windows Vista or 7 bootloader":
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Note: They give a link to the recovery CD that can be burnt but I have not tried it.

Once that is done, restore the grub2 bootloader by rebooting from a liveCD as given on the same link but under the title "How to restore the Ubuntu grub bootloader (9.10 and beyond)".

---

### Post by auv5 on 2010-06-11
Thank you guys so much for your attention, I will attempt this in about a hour :) also, I am not running windows 7, grub seems to percive my windows XP partition as something called "windows 7 (loader)"
thanks
auv5

---

### Post by wilee-nilee on 2010-06-12
> **john newbuntu said:**
> Not to intrude here, but try wilee-nilee's post and see if that works.  If for whatever reason it does not work, only then try what follows:

You have installed a part of grub2 on to /dev/sda1.  Plus you have a combination of the win boot loaders on the same partition.  I would clean that up first by following this link(presuming you have the win7 installation CD).  Follow the section titled "How to restore the Windows Vista or 7 bootloader":
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Note: They give a link to the recovery CD that can be burnt but I have not tried it.

Once that is done, restore the grub2 bootloader by rebooting from a liveCD as given on the same link but under the title "How to restore the Ubuntu grub bootloader (9.10 and beyond)".

Hey john you know this stuff to no intrusion here.

Also Op in case you don't have a XP disc for fixing things here is a slipstreamed ISO that can be used to reload stuff like the bootloader but not for actual installation. 
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by john newbuntu on 2010-06-12
Thanks Wilee.

@Auv5: Ignore my paragraph to restore win7 bootloader.  Instead, use Wilee's directions in post #9.  But follow the section "How to restore the Windows XP bootloader" in the post that I gave you. Also, just to save you some headaches, only run "fixboot" and NOT fixmbr in your first pass.  Then reboot and see if everything is ok.  Otherwise go through with running both commands.

---

### Post by wilee-nilee on 2010-06-12
The OP has just let me know that the testdisk fixed the situation, it's all good. ;)

---

