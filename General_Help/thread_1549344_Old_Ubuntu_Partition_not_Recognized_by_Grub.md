---
title: "Old Ubuntu Partition not Recognized by Grub"
date: 2010-08-09
forum: General Help
---

### Post by GreenOranges on 2010-08-09
So, I've spent the better part of the last four days reading old forum threads and trying everything I can think of to fix this problem.  Finely, I'm posted this thread as my last resort.

Here's what happened:

1. Decided to reinstall Windows XP on my Dell Inspiron 1520.  Put the install disk in, selected the proper partition, formated, and installed.  

2. Remembered something about media center, tried to install the contents of the disk, failed.  Tried to boot from the disk, but the partitions weren't recognized (instead it showed one big 320 GB partition), so I quit out of that.

3. Noticed that grub2 was no more.

3. Downloaded TestDisk from the Internet (neat little program by the way).  Did a quick search of my partitions, corrected the overlapping problems, wrote new partition table to disk.

4. Put in the Live CD, did the whole:

Sudo grub
find /boot/grub/stage1
...

wasn't working.

5. Decided to do what my brother did and install a new partition of Ubuntu for situations like these.

6. Grub is up and working now (legacy version 0.97 which came with the Ubuntu 8.04 Live CD).  and although all my other partitions are recognized, my old Ubuntu 10.04 isn't there.

7. I updated Ubuntu 8.04 to 10.04 and I can now mount all my other partitions inside the new Ubuntu.

8. I've tried editing menu.lst but any combination I try comes up with either error 12 or 15.  Also I downloaded "Storage Device Manager" which modified my fstab file for me.

Below is the results of a neat little script I was lead to on one of these threads.  It tells you just about everything you could possibly want to know about my drives.  Take a look, and if anyone has some good ideas, I'm all ears (note that I've erased the changes I've made to menu.lst).

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392   6 FAT16
/dev/sda2    *        112,455   303,708,824   303,596,370   7 HPFS/NTFS
/dev/sda3         303,708,825   616,944,194   313,235,370   f W95 Ext d (LBA)
/dev/sda5         303,708,951   322,777,979    19,069,029  83 Linux
/dev/sda6         322,778,043   323,725,814       947,772  82 Linux swap / Solaris
/dev/sda7         323,725,941   599,931,359   276,205,419  83 Linux
/dev/sda8         599,931,423   611,707,004    11,775,582  82 Linux swap / Solaris
/dev/sda9         611,707,068   616,944,194     5,237,127   c W95 FAT32 (LBA)
/dev/sda4         616,944,195   625,137,344     8,193,150   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0103                              vfat       DellUtility                   
/dev/sda2        DCF8E72BF8E7031E                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4                                               vfat       DellRestore                   
/dev/sda5        856dd7cb-6712-483f-9c33-b41c7bcb455d   ext3                                     
/dev/sda6        bd6fe23e-9b21-486c-94a4-92b163dfc3ff   swap                                     
/dev/sda7        93b7d032-f74f-4cea-a3e2-f0af4c78a144   ext4                                     
/dev/sda8        4311258d-b888-4364-bffa-3b536236b75c   swap                                     
/dev/sda9        07DA-0103                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/sda1              vfat       (rw)
/dev/sda4        /media/sda4              vfat       (rw)
/dev/sda7        /media/sda7              ext4       (rw)
/dev/sda9        /media/sda9              vfat       (rw)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=856dd7cb-6712-483f-9c33-b41c7bcb455d

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-7-generic
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        856dd7cb-6712-483f-9c33-b41c7bcb455d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda7
title        Microsoft Windows XP Embedded
root        (hd0,6)
savedefault
makeactive
chainloader    +1

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda8
UUID=856dd7cb-6712-483f-9c33-b41c7bcb455d  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda9
UUID=bd6fe23e-9b21-486c-94a4-92b163dfc3ff  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda4                                  /media/sda4    vfat         defaults                    0  0  
/dev/sda7                                  /media/sda7    ext4         defaults                    0  0  
/dev/sda8                                  /media/sda8    swap         defaults                    0  0  
/dev/sda9                                  /media/sda9    vfat         defaults                    0  0  

=================== sda5: Location of files loaded by Grub: ===================


 157.7GB: boot/grub/menu.lst
 157.7GB: boot/grub/stage2
 157.9GB: boot/initrd.img-2.6.27-7-generic
 157.7GB: boot/initrd.img-2.6.31-22-generic
 158.0GB: boot/initrd.img-2.6.32-24-generic
 157.7GB: boot/vmlinuz-2.6.27-7-generic
 157.7GB: boot/vmlinuz-2.6.31-22-generic
 158.0GB: boot/vmlinuz-2.6.32-24-generic
 158.0GB: initrd.img
 157.7GB: initrd.img.old
 158.0GB: vmlinuz
 157.7GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 93b7d032-f74f-4cea-a3e2-f0af4c78a144
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07da-0103
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 12e87667e876494d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod fat
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 07da-0103
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=93b7d032-f74f-4cea-a3e2-f0af4c78a144 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4311258d-b888-4364-bffa-3b536236b75c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 165.8GB: boot/grub/core.img
 170.7GB: boot/grub/grub.cfg
 167.2GB: boot/initrd.img-2.6.31-21-generic-pae
 176.5GB: boot/initrd.img-2.6.32-22-generic-pae
 177.1GB: boot/initrd.img-2.6.32-23-generic-pae
 175.1GB: boot/initrd.img-2.6.32-24-generic-pae
 167.0GB: boot/vmlinuz-2.6.31-21-generic-pae
 167.9GB: boot/vmlinuz-2.6.32-22-generic-pae
 167.9GB: boot/vmlinuz-2.6.32-23-generic-pae
 167.9GB: boot/vmlinuz-2.6.32-24-generic-pae
 175.1GB: initrd.img
 177.1GB: initrd.img.old
 167.9GB: vmlinuz
 167.9GB: vmlinuz.old

================================ sda9/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
```Note that on menu.lst, Microsoft Windows XP Embedded was assigned root (hd0,6).  Now, I thought that was my old Ubuntu partition.  Suspicious, I think so.

---

### Post by earthpigg on 2010-08-09
does grub that was included in 8.04 support ext4?

if i remember correctly:
-ext4 is the default for an ubuntu 10.04 install.
-ext4 was not supported out of the box in 8.04.

EDIT:

i found [this]("http://ubuntuforums.org/showthread.php?t=1276533") thread, which refreshed my memory.

ext4 support in 8.04 was wonky, at best. there where lots of complaints about it that i remember, not just that one thread. could potentially be the cause of your problems.

trying grub2 would be my next step, in your shoes.

---

### Post by GreenOranges on 2010-08-09
> **earthpigg said:**
> does grub that was included in 8.04 support ext4?

if i remember correctly:
-ext4 is the default for an ubuntu 10.04 install.
-ext4 was not supported out of the box in 8.04.

I'm not sure.  I know that when I first loaded 8.04 that I couldn't mount my old Ubuntu because it didn't recognize the file type.  However, I've since updated the grub and I believe that it should recognize ext4.  I know that I can certainly mount the ext4 partition while I've got my new Ubuntu running.

---

### Post by GreenOranges on 2010-08-09
After some tinkering I was able to upgrade Grub2 on my new Ubuntu partition.  This fixed the problem.  Thanks for your help.

---

