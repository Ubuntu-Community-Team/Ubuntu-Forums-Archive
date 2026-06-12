---
title: "unable to boot grub..pretty serious lol"
date: 2011-10-16
forum: General Help
---

### Post by owners4life5 on 2011-10-16
okay, so i can't boot into grub, it's allll messed up. i just need to re-install it, etc. i'm not exactly sure what to do. it seems like i have this problem after i install windows 7, lol.

i had this somewhat similar same problem about a year or so ago..see this --->  [http://ubuntuforums.org/showthread.php?t=1632439](http://ubuntuforums.org/showthread.php?t=1632439)

so i figured the best thing to do would be to run the script again, and see what someone can tell me.

i'm doing all of this off of a livecd right now.

thanks in advance

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 141364224 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sdc1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    75,441,239    75,441,177   7 NTFS / exFAT / HPFS
/dev/sda2         120,101,940   124,262,774     4,160,835   5 Extended
/dev/sda5         120,118,005   124,262,774     4,144,770  82 Linux swap / Solaris
/dev/sda3         124,262,775   156,296,384    32,033,610  83 Linux
/dev/sda4          75,441,240   120,101,939    44,660,700   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1              16,065   312,576,704   312,560,640   f W95 Extended (LBA)
/dev/sdb5              16,128   312,576,704   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 14 MB, 14909440 bytes
2 heads, 32 sectors/track, 455 cylinders, total 29120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  57        29,119        29,063   1 FAT12


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA00B94C00B9109D                       ntfs       
/dev/sda3        470c60af-1e44-40d1-abbf-a601e6a29e52   ext4       
/dev/sda4        7F36634454C6AEA9                       ntfs       
/dev/sda5        0a2bb0cf-2fdc-468e-af90-67e40d6625b0   swap       
/dev/sdb5        46E8ABD4E8ABC113                       ntfs       Music
/dev/sdc1        47C6-321B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/470c60af-1e44-40d1-abbf-a601e6a29e52 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Home Edition"  
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=470c60af-1e44-40d1-abbf-a601e6a29e52

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

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro quiet splash 
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic
uuid        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-11-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro  single
initrd        /boot/initrd.img-2.6.38-11-generic

title        Chainload into GRUB 2
root        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        470c60af-1e44-40d1-abbf-a601e6a29e52
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 470c60af-1e44-40d1-abbf-a601e6a29e52
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root FA00B94C00B9109D
    drivemap -s (hd0) ${root}
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=470c60af-1e44-40d1-abbf-a601e6a29e52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f082e852-566c-49f5-b2c4-7167dd1623c6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.763312817 = 64.170368512   boot/grub/core.img                             1
  61.082808971 = 65.587166720   boot/grub/grub.cfg                             1
  60.071109295 = 64.500862464   boot/grub/menu.lst                             1
  60.609252453 = 65.078689280   boot/initrd.img-2.6.38-11-generic              2
  60.617370129 = 65.087405568   boot/initrd.img-3.0.0-12-generic               2
  60.905761242 = 65.397063168   boot/vmlinuz-2.6.38-11-generic                 1
  72.651954174 = 78.009441792   boot/vmlinuz-3.0.0-12-generic                  1
  60.609252453 = 65.078689280   initrd.img.old                                 2
  72.651954174 = 78.009441792   vmlinuz                                        1
  60.905761242 = 65.397063168   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  04 01 01 02 12 22 33 c6  08 04 01 01 02 12 22 33  |....."3......."3|
00000010  c7 08 04 01 01 02 12 22  33 c8 08 04 01 01 02 12  |......."3.......|
00000020  22 33 c9 08 04 01 01 02  12 22 33 ca 08 04 01 01  |"3......."3.....|
00000030  02 12 22 33 cb 08 04 01  01 02 12 22 33 cc 08 04  |.."3......."3...|
00000040  01 01 02 12 22 33 cd 08  04 01 01 02 12 22 33 ce  |...."3......."3.|
00000050  08 04 01 01 02 12 22 33  cf 08 04 01 01 02 12 22  |......"3......."|
00000060  33 d0 08 04 01 01 02 12  22 33 d1 08 04 01 01 02  |3......."3......|
00000070  12 22 33 d2 08 04 01 01  02 12 22 33 d3 08 04 01  |."3......."3....|
00000080  01 02 12 22 33 d4 08 04  01 01 02 12 22 33 d5 08  |..."3......."3..|
00000090  04 01 01 02 12 22 33 d6  08 04 01 01 02 12 22 33  |....."3......."3|
000000a0  d7 08 04 01 01 02 12 22  33 d8 08 04 01 01 02 12  |......."3.......|
000000b0  22 33 d9 08 04 01 01 02  12 22 33 da 08 04 01 01  |"3......."3.....|
000000c0  02 12 22 33 db 08 04 01  01 02 12 22 33 dc 08 04  |.."3......."3...|
000000d0  01 01 02 12 22 33 dd 08  04 01 01 02 12 22 33 de  |...."3......."3.|
000000e0  08 04 01 01 02 12 22 33  df 08 04 01 01 02 12 22  |......"3......."|
000000f0  33 e0 08 04 01 01 02 12  22 33 e1 08 04 01 01 02  |3......."3......|
00000100  12 22 33 e2 08 04 01 01  02 12 22 33 e3 08 04 01  |."3......."3....|
00000110  01 02 12 22 33 e4 08 04  01 01 02 12 22 33 e5 08  |..."3......."3..|
00000120  04 01 01 02 12 22 33 e6  08 04 01 01 02 12 22 33  |....."3......."3|
00000130  e7 08 04 01 01 02 12 22  33 e8 08 04 01 01 02 12  |......."3.......|
00000140  22 33 e9 08 04 01 01 02  12 22 33 ea 08 04 01 01  |"3......."3.....|
00000150  02 12 22 33 eb 08 04 01  01 02 12 22 33 ec 08 04  |.."3......."3...|
00000160  01 01 02 12 22 33 ed 08  04 01 01 02 12 22 33 ee  |...."3......."3.|
00000170  08 04 01 01 02 12 22 33  ef 08 04 01 01 02 12 22  |......"3......."|
00000180  33 f0 08 04 01 01 02 12  22 33 f1 08 04 01 01 02  |3......."3......|
00000190  12 22 33 f2 08 04 01 01  02 12 22 33 f3 08 04 01  |."3......."3....|
000001a0  01 02 12 22 33 f4 08 04  01 01 02 12 22 4c a2 08  |..."3......."L..|
000001b0  04 01 01 02 12 22 4c a3  08 04 01 01 02 12 00 fe  |....."L.........|
000001c0  ff ff 82 fe ff ff c1 3e  00 00 82 3e 3f 00 00 00  |.......>...>?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2011-10-16
Grub isn't installed in the sda MBR. You can easily do this, but note you will lose your Windows bootloader and replace it with Grub.

To do this from the LiveCD you will first mount your Ubuntu partition, and then install Grub. That will allow the MBR to point to your Ubuntu installation on sda3.

After you reboot Ubuntu without the CD, you may need to run "sudo update-grub" to add Windows to your Grub menu.
```

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Don't include the partition number in the second command.

---

### Post by owners4life5 on 2011-10-16
okay, i did this, and now when i boot, i have the option of pressing the esc key, and when i do, i'm provided all of my 11.10 options and the memtest. no windows xp or 7 though... :/

now what?

i wish i could just totally remove all of my grub configs, options, etc., and then just install grub2...but that's probably not exactly "possible"

---

### Post by drs305 on 2011-10-16
> **owners4life5 said:**
> okay, i did this, and now when i boot, i have the option of pressing the esc key, and when i do, i'm provided all of my 11.10 options and the memtest. no windows xp or 7 though... :/

now what?

i wish i could just totally remove all of my grub configs, options, etc., and then just install grub2...but that's probably not exactly "possible"

First, after you press ESC look at the top of the menu. Does it show Grub 1.99 or Grub 0.97. Hopefully it shows Grub 1.99 and boots to Ubuntu. If it does, run the following command to update the Grub 2 menu:
```
sudo update-grub
```

It may be showing Grub 0.97. If it boots, that is fine as well. We can purge Grub and reinstall Grub 2. Just let me know which Grub you are using, if you have Internet capability, and that it boots to Ubuntu without the LiveCD.

---

### Post by owners4life5 on 2011-10-16
> **drs305 said:**
> First, after you press ESC look at the top of the menu. Does it show Grub 1.99 or Grub 0.97. Hopefully it shows Grub 1.99 and boots to Ubuntu. If it does, run the following command to update the Grub 2 menu:
```
sudo update-grub
```

It may be showing Grub 0.97. If it boots, that is fine as well. We can purge Grub and reinstall Grub 2. Just let me know which Grub you are using, if you have Internet capability, and that it boots to Ubuntu without the LiveCD.

okay, so when i'm provided the option to hit escape, all it says at the top is something about "loading grub 1.5" or something like that. after i hit escape, it doesn't say anything at the top.

however, ubuntu boots fine. that's what i'm typing this off of..so that works.

now what?

---

### Post by drs305 on 2011-10-16
Let's just purge all Grubs and reinstall them. It's very simple as long as you have a stable Internet connection.
```

sudo apt-get update 
sudo apt-get purge grub grub-pc grub-common
```
You will receive a message that you are uninstalling your bootloader and that the system may be unbootable. It's ok. TAB to OK if necessary.

```

sudo apt-get install grub-common grub-pc
```
This will install Grub 2. You will be asked if you want to add any kernel options. You currently don't have any, so just TAB to OK and press ENTER.

Next you will be asked where you want to install Grub. You want the asterisk only on the "sda" line. If it isn't there, use the spacebar to place an asterisk next to sda. If there is an asterisk next to any partition (such as sda3), remove it with the spacebar.

Tab to OK, press ENTER and Grub 2 should install.

While it is installing and running update-grub, check to see if it finds Windows. If you don't see it, or if it's not in the menu the next time you boot, run "sudo update-grub".

---

### Post by Leaf on 2011-10-16
^^

EDIT Use the automatic grub detection above!  my way was very manual.

now you'll need to edit the grub configuration file to include a selection for your windows partition.  open in your favorite text editor with root permissions the file /boot/grub/grub.cfg
You'll see the different partition boot menu options inside.
You then need to add a link to your windows partition and name it, using the same format as the other entries.  The only thing that should be different is the title of the selection, and the partition number. (0,0) or (0,1) or whatever it is. 

More info on grub here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by owners4life5 on 2011-10-16
okay, so here is my terminal readout:

```
brian@brian-OptiPlex-GX270:~$ sudo apt-get purge grub grub-pc grub-common
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgladeui-1-11
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 15 not upgraded.
After this operation, 5,927 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161981 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
brian@brian-OptiPlex-GX270:~$ sudo apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgladeui-1-11
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 15 not upgraded.
Need to get 983 kB/2,916 kB of archives.
After this operation, 7,844 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main grub2-common i386 1.99-12ubuntu5 [94.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main grub-pc-bin i386 1.99-12ubuntu5 [792 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main grub-pc i386 1.99-12ubuntu5 [93.1 kB]                   
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main grub-gfxpayload-lists i386 0.5 [3,328 B]                
Fetched 983 kB in 11s (83.3 kB/s)                                                                               
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 161865 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99-12ubuntu5_i386.deb) ...
Selecting previously deselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_1.99-12ubuntu5_i386.deb) ...
Selecting previously deselected package grub-pc-bin.
Unpacking grub-pc-bin (from .../grub-pc-bin_1.99-12ubuntu5_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.99-12ubuntu5_i386.deb) ...
Selecting previously deselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Setting up grub-common (1.99-12ubuntu5) ...
Setting up grub2-common (1.99-12ubuntu5) ...
Setting up grub-pc-bin (1.99-12ubuntu5) ...
Setting up grub-pc (1.99-12ubuntu5) ...

Creating config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up grub-gfxpayload-lists (0.5) ...
brian@brian-OptiPlex-GX270:~$ 

```

so it obviously found Windows 7, not listing XP though..

i'm about to reboot, then see what my options are. if it shows all of them (including xp), i'll let you know, if not showing XP, will run ```
update-grub
``` and then reboot, then let you know from there.

---

### Post by owners4life5 on 2011-10-16
okay, so it turns out that when i rebooted, i noticed on grub2 that there was the windows 7 option, and it actually had a chainload to windows xp under the windows 7 bootloader..

so...
able to access windows 7    ...check.
able to access windows xp   ...check.
able to access ubuntu 11.10 ...check.

in fact, i'm typing this on xp right now. (: see!
[IMG]http://sobloggingeh.blogspot.com/2011/10/blog-post.html[/IMG]

thanks, guys.
marking as solved!

---

### Post by owners4life5 on 2011-10-16
and my image didn't even work :( oh well lol

---

