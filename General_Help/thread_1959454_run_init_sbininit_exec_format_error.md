---
title: "run init: /sbin/init exec format error"
date: 2012-04-15
forum: General Help
---

### Post by szechman on 2012-04-15
I upgraded from 11.10 32bit to 11.10 64bit from a live cd. Now when I boot I get the following error (even in recovery mode) run init: /sbin/init exec format error.

I have run boot info script and here are the results.

Anyone have any ideas?

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       644531240 sectors, but according to the info from 
                       fdisk, it has 675839999 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 16388 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304    17,747,967    17,649,664   7 NTFS / exFAT / HPFS
/dev/sda3          17,747,968   693,587,967   675,840,000   7 NTFS / exFAT / HPFS
/dev/sda4         693,590,014   976,771,071   283,181,058   5 Extended
/dev/sda5         693,590,016   968,466,431   274,876,416  83 Linux
/dev/sda6         968,468,480   976,771,071     8,302,592  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1967 MB, 1967128576 bytes
61 heads, 62 sectors/track, 1015 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,838,729     3,838,668   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       0464615d-ac44-9c4c-a2b2-2f3c38db3513   ext2       casper-rw
/dev/sda1        07DA-0B08                              vfat       DellUtility
/dev/sda2        207E530C7E52D9DC                       ntfs       RECOVERY
/dev/sda3        424856094855FBDB                       ntfs       OS
/dev/sda5        630d4021-b92a-40c8-ae4b-3b61fde9249d   ext4       
/dev/sda6        ce5708f9-13b1-4d48-94ed-dc744b43d378   swap       
/dev/sdb1        F2FB-C9A9                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/Movie             udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=630d4021-b92a-40c8-ae4b-3b61fde9249d

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

title        Ubuntu 11.10, kernel 3.0.0-17-generic-pae
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro quiet splash 
initrd        /boot/initrd.img-3.0.0-17-generic-pae

title        Ubuntu 11.10, kernel 3.0.0-17-generic-pae (recovery mode)
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro  single
initrd        /boot/initrd.img-3.0.0-17-generic-pae

title        Ubuntu 11.10, kernel 3.0.0-17-generic
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-17-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro quiet splash 
initrd        /boot/initrd.img-3.0.0-17-generic

title        Ubuntu 11.10, kernel 3.0.0-17-generic (recovery mode)
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-17-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro  single
initrd        /boot/initrd.img-3.0.0-17-generic

title        Ubuntu 11.10, kernel 3.0.0-16-generic-pae
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro quiet splash 
initrd        /boot/initrd.img-3.0.0-16-generic-pae

title        Ubuntu 11.10, kernel 3.0.0-16-generic-pae (recovery mode)
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro  single
initrd        /boot/initrd.img-3.0.0-16-generic-pae

title        Ubuntu 11.10, kernel 3.0.0-16-generic
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-16-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro quiet splash 
initrd        /boot/initrd.img-3.0.0-16-generic

title        Ubuntu 11.10, kernel 3.0.0-16-generic (recovery mode)
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-16-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro  single
initrd        /boot/initrd.img-3.0.0-16-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro quiet splash 
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Chainload into GRUB 2
root        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        630d4021-b92a-40c8-ae4b-3b61fde9249d
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    echo    'Loading Linux 3.0.0-17-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 630d4021-b92a-40c8-ae4b-3b61fde9249d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 207E530C7E52D9DC
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=630d4021-b92a-40c8-ae4b-3b61fde9249d /               ext4    errors=remount-ro 0       1
# /mnt was on /dev/sda3 during installation
UUID=424856094855FBDB /mnt            ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=ce5708f9-13b1-4d48-94ed-dc744b43d378 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/initrd.img-3.0.0-16-generic-pae           3
               =                boot/initrd.img-3.0.0-17-generic               3
               =                boot/initrd.img-3.0.0-17-generic-pae           3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic-pae              2
               =                boot/vmlinuz-3.0.0-17-generic                  2
               =                boot/vmlinuz-3.0.0-17-generic-pae              2
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  f1 2f 1e 85 a0 e4 ed 8c  fa de 8c 51 17 ac f2 31  |./.........Q...1|
00000010  db b0 4f 41 62 ff 53 b1  f6 10 ed 09 4c 5e 9a 9b  |..OAb.S.....L^..|
00000020  8c 59 4a 5a eb a9 85 d5  74 85 a6 11 e2 fe cd d5  |.YJZ....t.......|
00000030  5f 3c a7 e6 4f 94 12 79  c0 27 d6 95 c6 ee d4 a3  |_<..O..y.'......|
00000040  0a ef 79 83 aa da 26 63  69 18 de d8 4f 03 af a4  |..y...&ci...O...|
00000050  72 bd 6e 43 2b 7f e5 79  d0 1d 35 bc dd 1d 0b 32  |r.nC+..y..5....2|
00000060  a5 3c d9 a4 41 4e 08 b6  b4 0e 6c 7d 54 c5 bf 02  |.<..AN....l}T...|
00000070  6b b3 34 56 55 5e b5 58  5c d8 08 70 56 aa 95 a2  |k.4VU^.X\..pV...|
00000080  ce bd c7 99 e4 c2 d3 f8  a8 11 11 0f b0 3f fc e6  |.............?..|
00000090  d5 36 e4 4c 2b 9b 8b c7  b3 c4 e7 f7 69 16 e3 6b  |.6.L+.......i..k|
000000a0  f6 e2 af 7b 30 27 54 f9  6f 61 47 9e 12 3b 65 63  |...{0'T.oaG..;ec|
000000b0  34 4f 39 7d 50 8e d2 7b  0f ad 37 e9 98 87 de a0  |4O9}P..{..7.....|
000000c0  9d 2b f6 13 31 f9 a6 29  d1 16 3d da 8e 2e 9d b6  |.+..1..)..=.....|
000000d0  88 35 7d 6a a1 b4 fd 76  2f a4 de 80 0e f7 73 da  |.5}j...v/.....s.|
000000e0  7f 20 d5 9e 96 8e f1 4e  f2 7d 3e 42 1d af 66 d6  |. .....N.}>B..f.|
000000f0  de 75 d8 62 b3 c0 aa ec  af 8f c0 c1 33 e2 76 37  |.u.b........3.v7|
00000100  d4 cc 3c aa 17 6b 05 83  a8 24 e9 17 2f b8 8b f1  |..<..k...$../...|
00000110  ff c5 44 db 67 63 c5 25  99 14 13 04 1f d6 0a db  |..D.gc.%........|
00000120  e3 09 2a 45 0a 78 8e ad  cd f9 d4 24 7c ac 29 36  |..*E.x.....$|.)6|
00000130  85 07 fc 9f 97 b0 af a0  43 4b 7f 6a d6 9f 90 df  |........CK.j....|
00000140  6a 00 0e 47 93 49 8d 73  6a 50 6e af 94 7a d0 ff  |j..G.I.sjPn..z..|
00000150  c1 7f b3 1c 2c 98 54 d4  9e c7 43 89 1d f8 29 2d  |....,.T...C...)-|
00000160  1e e5 25 cc c5 50 2e 7f  6a 8b e8 53 82 db 80 0e  |..%..P..j..S....|
00000170  a3 0a 6a 9a 71 1c 6d 57  0e 25 78 4f d7 39 fe 6f  |..j.q.mW.%xO.9.o|
00000180  81 e5 eb 9d 0f 50 8c 98  96 db 8b ca 62 6f c1 3d  |.....P......bo.=|
00000190  25 e3 f6 e6 1e ac 7e 05  29 97 c2 15 c0 df 63 cb  |%.....~.).....c.|
000001a0  90 6c ef 63 cb fe 20 b2  fb 8e 9f d8 cc a7 ff 44  |.l.c.. ........D|
000001b0  ca 5e f6 2d 39 33 16 83  5b ab 20 ae d6 2c 00 fe  |.^.-93..[. ..,..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 62 10 00 fe  |...........Hb...|
000001d0  ff ff 05 fe ff ff 02 48  62 10 00 b8 7e 00 00 00  |.......Hb...~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

---

