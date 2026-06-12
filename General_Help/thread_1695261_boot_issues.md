---
title: "boot issues"
date: 2011-02-25
forum: General Help
---

### Post by KingLex on 2011-02-25
Hey im having trouble starting my Ubuntu on my external hdd - the version is the latest  Version 10.10
i have been inform by many members on this site due to my cause and im still having trouble.
I have ran this command below 
```
sudo mount /dev/sdf5 /mnt
sudo grub-install**.real** --root-directory=/mnt /dev/sdf

```and the results came back with this - I dont have a live CD - so i installed 
Wubi so i can access the terminal. 

```
Installing GRUB to /dev/sdf as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdf
```After all of that i restarted and try running *"Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdf5)"* and came 
up with the error shown below 

[I]Grub loading stage 1.5 
Grub loading , please wait 
Error 5[/I]

I installed Wubi  so i can gain access to the terminal  cause i don't have a live CD or  flash drive ; 

As i finished i also did a results in advanced as i seen in previous threads many 
was told to do a result so here is mine as well as i hope someone could point me in the right direction 

    ```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdf and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdf1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    31,569,919    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,569,920 1,250,260,991 1,218,691,072   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   515,869,177   515,869,115   7 HPFS/NTFS
/dev/sdf2         515,870,718   976,771,071   460,900,354   5 Extended
/dev/sdf5         515,870,720   964,485,119   448,614,400  83 Linux
/dev/sdf6         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       d7d9e3c3-0f80-43c6-8d17-0cb78e053caa   ext4                                     
/dev/sda1        07D9-0A10                              vfat       DellUtility                   
/dev/sda2        F222DCA622DC70D9                       ntfs       RECOVERY                      
/dev/sda3        E0FADFBDFADF8E62                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdf1        A0123EB8123E9370                       ntfs       Lex Drive_HDD                 
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        105ebc4e-262b-417b-9ac3-849a6060abc8   ext4                                     
/dev/sdf6        d56cb88c-b4d9-4308-a255-60c43e37eb10   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdf5        /media/105ebc4e-262b-417b-9ac3-849a6060abc8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf5        /mnt                     ext4       (rw)


======================== sdf1/Wubi/boot/grub/menu.lst: ========================

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
# kopt=root=UUID=A0123EB8123E9370 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=A0123EB8123E9370

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

title        Ubuntu 10.10, kernel 2.6.35-25-generic-pae
uuid        A0123EB8123E9370
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=A0123EB8123E9370 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic-pae

title        Ubuntu 10.10, kernel 2.6.35-25-generic-pae (recovery mode)
uuid        A0123EB8123E9370
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=A0123EB8123E9370 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.35-25-generic-pae

title        Ubuntu 10.10, memtest86+
uuid        A0123EB8123E9370
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

======================== sdf1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
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
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a0123eb8123e9370
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdf1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a0123eb8123e9370
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdf1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sde3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e0fadfbdfadf8e62
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sdf1/Wubi/etc/fstab: =============================

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

================= sdf1/Wubi: Location of files loaded by Grub: =================


   4.5GB: boot/grub/grub.cfg
  13.0GB: boot/grub/menu.lst
   2.6GB: boot/initrd.img-2.6.35-25-generic-pae
  13.1GB: boot/vmlinuz-2.6.35-25-generic-pae
   2.6GB: initrd.img
  13.1GB: vmlinuz

=========================== sdf5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f4f688b2f68876a0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4ebaae53baae36fd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set bc4ed40d4ed3bdf8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdf5/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 /               ext4    errors=remount-ro 0       1
UUID=d56cb88c-b4d9-4308-a255-60c43e37eb10 none            swap    sw              0       0

=================== sdf5: Location of files loaded by Grub: ===================


 487.6GB: boot/grub/core.img
 380.3GB: boot/grub/grub.cfg
 487.6GB: boot/grub/stage2
 265.3GB: boot/initrd.img-2.6.35-22-generic
 267.1GB: boot/initrd.img-2.6.35-25-generic
 487.6GB: boot/vmlinuz-2.6.35-22-generic
 487.6GB: boot/vmlinuz-2.6.35-25-generic
 267.1GB: initrd.img
 265.3GB: initrd.img.old
 487.6GB: vmlinuz
 487.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf2

00000000  5e 85 98 b4 55 97 d3 58  95 16 64 eb 7b fe ca 7f  |^...U..X..d.{...|
00000010  ff 7c b8 6f 5a 2e 22 d6  ef ad 6b 8f a4 3d 34 8b  |.|.oZ."...k..=4.|
00000020  74 10 d5 95 a5 cb eb bd  0a 9b aa d2 9a 9b db b1  |t...............|
00000030  24 b0 88 71 e8 57 55 bf  cb 6a 97 e6 b9 72 ff 08  |$..q.WU..j...r..|
00000040  94 5d 7c f0 15 dc 56 2b  86 25 00 89 35 f8 7f c3  |.]|...V+.%..5...|
00000050  2f 88 6b ff d7 81 45 08  23 55 50 b2 a9 40 7e 97  |/.k...E.#UP..@~.|
00000060  5d f8 14 4c 3f e2 b1 f7  7c 09 1c 0b e2 fe 65 5b  |]..L?...|.....e[|
00000070  bf 7b c5 f4 af 42 55 ab  2e 65 aa 5c 77 07 f9 15  |.{...BU..e.\w...|
00000080  dc 57 b1 9a fd ff f4 c8  96 2b 48 bd ed de 2b 2e  |.W.......+H...+.|
00000090  65 8f 66 34 40 58 34 08  72 98 bd f3 0b fc 46 12  |e.f4@X4.r.....F.|
000000a0  d1 21 29 2c b8 fa bd 63  2b df 46 30 64 08 60 a2  |.!),...c+.F0d.`.|
000000b0  22 d8 8e 45 6f 77 ac 58  a0 90 23 05 7c 61 6f 8b  |"..Eow.X..#.|ao.|
000000c0  93 45 6f 72 86 39 82 bb  29 58 50 50 81 86 bd c6  |.Eor.9..)XPP....|
000000d0  72 dc a5 c4 d8 7a a5 de  ce 46 52 eb ea 12 2d 56  |r....z...FR...-V|
000000e0  2e 4e 2a 50 be e9 d7 ec  56 39 ec b0 ea bc 91 84  |.N*P....V9......|
000000f0  aa aa aa 43 19 52 65 b9  aa d6 96 09 29 5a 5c bc  |...C.Re.....)Z\.|
00000100  91 93 30 3c ad ba 0c 6a  73 4b 53 75 58 1f 92 11  |..0<...jsKSuX...|
00000110  97 db 8a ee 5c bd df 30  0b a0 12 40 9c e2 be fa  |....\..0...@....|
00000120  be 21 40 37 2d 4f 1c 02  84 07 04 44 77 30 fe f2  |.!@7-O.....Dw0..|
00000130  f7 d7 77 8c aa 53 d4 57  ee 66 de f3 8f f6 b1 0a  |..w..S.W.f......|
00000140  e2 ba 57 de ff b3 5e f8  07 f5 68 e7 cb 89 c5 65  |..W...^...h....e|
00000150  fb d7 17 97 a3 b9 88 8b  08 34 56 05 61 0c 47 34  |.........4V.a.G4|
00000160  bb 4f ac bf d7 24 0e 40  9b 8a ef 7a 0d 2a 58 23  |.O...$.@...z.*X#|
00000170  02 25 65 f1 d8 c8 d1 64  cb f1 f8 d0 b3 20 c3 36  |.%e....d..... .6|
00000180  9e f6 33 a4 84 60 b6 89  a5 6b 1f af d0 e2 b5 4b  |..3..`...k.....K|
00000190  77 49 cb 0e fc 63 11 99  8b ed 9b 2f 13 c2 04 52  |wI...c...../...R|
000001a0  cb b5 26 68 af 2f cb d6  3e ba a9 8c 46 b2 74 24  |..&h./..>...F.t$|
000001b0  be b7 f6 32 a9 b2 12 82  55 0f 91 f8 b8 a6 00 fe  |...2....U.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 bd 1a 00 fe  |...........P....|
000001d0  ff ff 05 fe ff ff 02 50  bd 1a 00 78 bb 00 00 00  |.......P...x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2011-02-25
I am not quite sure how you got grub legacy into the MBR. You have grub2.

I hope the real was a typo in your post aout real:

sudo mount /dev/sdf5 /mnt
sudo grub-install.real --root-directory=/mnt /dev/sdf

Should be this from liveCD or liveUSB.
sudo mount /dev/sdf5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdf
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdf

If you do not have a liveCD you should get one. Is wubi working for now?

If wubi will boot your install in sdf5, then you can reinstall grub2 to the MBR of sdf from that:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdf"  then just run:
sudo grub-install /dev/sdf
#If that returns any errors run:
sudo grub-install --recheck /dev/sdf
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If you still have problems you should uninstall both grub legacy & grub2 and then reinstall just grub2. Note that while both are uninstalled you cannot boot.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Rubi1200 on 2011-02-26
Hi KingLex and thanks for posting the information in a new thread.

Follow oldfred's advice on this one please.

I am curious though as to how legacy-GRUB ended up in the MBR and on the Wubi install?

---

### Post by KingLex on 2011-02-28
> **Rubi1200 said:**
> Hi KingLex and thanks for posting the information in a new thread.

Follow oldfred's advice on this one please.

I am curious though as to how legacy-GRUB ended up in the MBR and on the Wubi install?

):P - no problem - is that a good thing or a bad thing by it doing that ?

---

