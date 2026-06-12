---
title: "Grub finds no kernels, only memtest"
date: 2011-07-31
forum: General Help
---

### Post by tigerlxxv on 2011-07-31
Okay. I ran grub-customiser to set default kernel, and saw the GFX mode setting, thinking "Hey, my monitor is native at 1440x900! I'll use that!" ...Didn't think about how the GFX card isn't initialized at that point, so my res is limited to 640x480... So the first problem was a system hang at the grub menu, with "Input Not Supported" displayed on the monitor. Thanks to a combination of useful threads here and at the Gentoo Forums, I learned some basic chrooting. Good times. I changed the GFX mode back, and ran update-grub, and with a grin on my face, I rebooted. The grin went away fast, when I saw that none of the kernels showed in the grub menu, and I have only the two memtest entries. It appears that, while all the files are still intact, grub is not seeing the kernels. I had an idle partition of about 13 GB on hand, so after trying all sorts of things, I did a clean install on the little 13 GB partition. Still no dice, after doing an apt-get purge grub etc etc etc on my main Ubuntu partition, to make sure that the new grub was running. I still have only memtest, even though I can open the /boot directory and see the kernel files. I tried going into the grub command line and starting manually, but tab-complete does not suggest any of the kernel files, and tells me that the files do not exist, if I type in their full names. I realize this is getting a little long now, so I'll cut straight to the bootinfo script results that I've seen so much of in my searches:

```

                  Boot Info Script 0.60    from 31 July 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 266240 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the / directory.
    Operating System:  
    Boot files:        /extlinux.conf /ldlinux.sys

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   599,979,554   599,979,492   7 NTFS / exFAT / HPFS
/dev/sda2    *    599,979,555   625,137,344    25,157,790  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    20,466,808    20,466,746  12 Compaq diagnostics
/dev/sdb2    *     20,466,810   166,802,894   146,336,085   6 FAT16
/dev/sdb3         166,802,895   267,032,429   100,229,535   7 NTFS / exFAT / HPFS
/dev/sdb4         267,032,430   312,576,704    45,544,275   f W95 Extended (LBA)
/dev/sdb5         267,032,493   312,576,704    45,544,212  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1007 MB, 1007681536 bytes
31 heads, 62 sectors/track, 1024 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32     1,560,575     1,560,544  83 Linux
/dev/sdc2           1,560,576     1,968,127       407,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        14A1E58F52989DB4                       ntfs       
/dev/sda2        5824c48a-88f6-47f9-b874-5d515f73ba13   ext4       
/dev/sdb1        4AA0132B16D9B5D2                       ntfs       PQSERVICE
/dev/sdb2        D20C15E70C15C6FF                       ntfs       ACER
/dev/sdb3        18F4E43FF4E4212C                       ntfs       DATA
/dev/sdb5        240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6   ext4       
/dev/sdc1        48b22415-47bb-4d47-a5a4-46b9aafab248   ext4       
/dev/sdc2        53FAE63A4A2430DD                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/14A1E58F52989DB4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
    linux    /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=5824c48a-88f6-47f9-b874-5d515f73ba13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
    echo    'Loading Linux 2.6.32-33-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=5824c48a-88f6-47f9-b874-5d515f73ba13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5824c48a-88f6-47f9-b874-5d515f73ba13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 4aa0132b16d9b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set d20c15e70c15c6ff
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 95/98/Me (on /dev/sdb3)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 18f4e43ff4e4212c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-22-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-29-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-30-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu 10.04.2 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux /boot/vmlinuz-2.6.32-32-generic-pae root=/dev/sdb5
    initrd /boot/initrd.img-2.6.32-32-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5824c48a-88f6-47f9-b874-5d515f73ba13 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 292.426881313 = 313.990972928  boot/grub/core.img                             1
 288.673268795 = 309.960562176  boot/grub/grub.cfg                             2
 292.474946499 = 314.042582528  boot/initrd.img-2.6.32-33-generic-pae          1
 292.392377377 = 313.953924608  boot/vmlinuz-2.6.32-33-generic-pae             1
 292.474946499 = 314.042582528  initrd.img                                     1
 292.392377377 = 313.953924608  vmlinuz                                        1

============================= sdb5/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
set default="Ubuntu, with Linux 2.6.32-33-generic-pae (on /dev/sda2)"
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

### BEGIN /etc/grub.d/10_linux_proxy ###
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="Ubuntu, with Linux 2.6.32-33-generic-pae (on /dev/sda2)"
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480x8
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
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

### BEGIN /etc/grub.d/10_linux_proxy ###
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=240c4212-5a7f-4bbd-94a6-3a6fb45c0ee6 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.514757633 = 145.507863040  boot/grub/core.img                             1
 136.915007114 = 147.011369472  boot/grub/grub.cfg                             1
 138.191980839 = 148.382509568  boot/initrd.img-2.6.32-22-generic-pae          1
 136.471201420 = 146.534836736  boot/initrd.img-2.6.32-24-generic-pae          1
 137.307146549 = 147.432425984  boot/initrd.img-2.6.32-25-generic-pae          1
 138.279802799 = 148.476807680  boot/initrd.img-2.6.32-26-generic-pae          2
 138.719938755 = 148.949400064  boot/initrd.img-2.6.32-27-generic-pae          1
 138.494116306 = 148.706925056  boot/initrd.img-2.6.32-28-generic-pae          1
 138.510271549 = 148.724271616  boot/initrd.img-2.6.32-29-generic-pae          1
 128.470022678 = 137.943636480  boot/initrd.img-2.6.32-30-generic-pae          2
 139.385271549 = 149.663795712  boot/initrd.img-2.6.32-32-generic-pae          1
 137.848669529 = 148.013881856  boot/vmlinuz-2.6.32-22-generic-pae             1
 136.487265110 = 146.552084992  boot/vmlinuz-2.6.32-24-generic-pae             1
 136.483335972 = 146.547866112  boot/vmlinuz-2.6.32-25-generic-pae             1
 138.272398472 = 148.468857344  boot/vmlinuz-2.6.32-26-generic-pae             1
 136.907873631 = 147.003709952  boot/vmlinuz-2.6.32-27-generic-pae             1
 137.232935429 = 147.352742400  boot/vmlinuz-2.6.32-28-generic-pae             1
 137.244196415 = 147.364833792  boot/vmlinuz-2.6.32-29-generic-pae             1
 127.452337742 = 136.850905600  boot/vmlinuz-2.6.32-30-generic-pae             1
 138.664560795 = 148.889938432  boot/vmlinuz-2.6.32-32-generic-pae             1
 141.457979679 = 151.889349120  grub/grub.cfg                                  1
 139.385271549 = 149.663795712  initrd.img                                     1
 128.470022678 = 137.943636480  initrd.img.old                                 2
 138.664560795 = 148.889938432  vmlinuz                                        1
 127.452337742 = 136.850905600  vmlinuz.old                                    1

============================= sdc1/extlinux.conf: ==============================

--------------------------------------------------------------------------------
default puppy
display boot.msg
prompt 1
timeout 50

F1 boot.msg
F2 help.msg
F3 help2.msg

label puppy
kernel vmlinuz
append initrd=initrd.gz pmedia=usbflash
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.132801056 = 0.142594048    initrd.gz                                      1
   0.131000519 = 0.140660736    vmlinuz                                        1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

   0.131004333 = 0.140664832    extlinux.conf                                  1
   0.126998901 = 0.136364032    ldlinux.sys                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  ae c7 91 46 86 37 15 29  50 50 d1 3d 39 74 7b ef  |...F.7.)PP.=9t{.|
00000010  73 ce fc 41 e1 69 9b e0  ee a5 f1 bf c3 5f 62 3a  |s..A.i......._b:|
00000020  1a ba 4d e1 cd 2a d6 e0  4b 2f 8d 2e c4 a8 93 c5  |..M..*..K/......|
00000030  0f 4e 53 cd df 96 e0 aa  b8 c9 20 9a f3 0d 1e e3  |.NS....... .....|
00000040  c5 9f 10 74 6f 14 b6 9f  aa 69 fa 6e b3 a6 59 b6  |...to....i.n..Y.|
00000050  a5 a7 f8 62 f5 59 5f 5d  28 32 d1 23 01 80 fb 77  |...b.Y_](2.#...w|
00000060  15 dc 46 e6 5d a0 12 c2  bd 53 e3 cf 8e 3c 45 e2  |..F.]....S...<E.|
00000070  5d 6e d3 c2 be 02 f0 fc  5a 77 81 7c 3d 69 16 99  |]n......Zw.|=i..|
00000080  e1 ad 1c 4e c3 ed 13 ec  58 ae 6f 1f 68 21 5e 66  |...N....X.o.h!^f|
00000090  50 44 68 7c b5 0a 08 00  93 5e 6d e1 2f 83 df 15  |PDh|.....^m./...|
000000a0  3c 3d e2 23 27 88 63 87  4b 5d 56 c2 4b 38 23 5b  |<=.#'.c.K]V.K8#[|
000000b0  d4 94 c4 cc bb 93 24 01  b7 77 ca 47 3d 09 f4 a9  |......$..w.G=...|
000000c0  8e 13 0f 82 c2 cf 19 9c  57 4a 6f de 8c 1c 7e 15  |........WJo...~.|
000000d0  a5 a1 7d af 6d ef ad c9  96 07 15 2a b5 2a 43 fe  |..}.m......*.*C.|
000000e0  1d b6 f5 6f 5b 6d b2 f2  39 2f 0f f8 f6 fe f7 45  |...o[m..9/.....E|
000000f0  d0 6e 6d 41 b0 d4 ed 2e  4d ee b4 35 28 c4 72 e8  |.nmA....M..5(.r.|
00000100  2c 9f f2 cc 80 48 27 20  83 b7 3c a8 c1 ae ce 7b  |,....H' ..<....{|
00000110  7b df 88 d6 d7 be 24 b3  f1 04 da 57 8a 6c 70 cf  |{.....$....W.lp.|
00000120  79 f6 d1 19 86 03 c8 31  ee e3 38 19 07 d4 0f 40  |y......1..8....@|
00000130  0f 63 a6 7e cf 13 f8 a3  59 8e 3b bb 98 b4 c9 ed  |.c.~....Y.;.....|
00000140  b4 45 6b fb bb df 32 38  a7 9f 76 dd c7 07 2c a4  |.Ek...28..v...,.|
00000150  02 70 73 da bd 6b 52 f8  17 6f e1 fb 2d 26 da ca  |.ps..kR..o..-&..|
00000160  ea c3 55 8f 48 d4 16 1b  d1 6a 83 76 a8 98 04 92  |..U.H....j.v....|
00000170  7b 64 e0 80 7a 67 9a ee  c8 33 de 14 a1 9d 43 ea  |{d..zg...3....C.|
00000180  ad c6 a3 e6 6b 46 9a bb  77 b3 b3 bd f7 b3 76 b1  |....kF..w.....v.|
00000190  12 a1 8c 54 9d 65 3b 35  6d d5 ee af 6f 2d bb 23  |...T.e;5m...o-.#|
000001a0  ca ac bc 7f e2 1f 00 ff  00 66 4b a8 eb 03 57 b8  |.........fK...W.|
000001b0  bd 56 5b bb fd 5d fc c9  ee 10 26 10 1e 00 00 fe  |.V[..]....&.....|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 14 f3 b6 02 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 


```Thanks for looking. I have a feeling there's something obvious I'm missing....

---

### Post by tigerlxxv on 2011-08-01
It occurs to me that I should mention that there were no updates or other kernel/hardware/software changes at the time that I did this. Just the one line in the grub config file.

---

### Post by tigerlxxv on 2011-08-01
Also, does it seem weird to anyone else, that sdb5 has TWO grub.cfg files? There's one in /grub, and again in /boot/grub...

---

### Post by westie457 on 2011-08-01
Hi I had similar situation to yours a few weeks ago when I was trying to recreate the problems that someone on the Forums had. Managed to recreate them and happily stuffed up part of my hard drive and like you could only get Memtest to be recognised by a SuperGrub2 disc (which has no options to write anything at all).

So I tried this How-to [here]("http://ubuntuforums.org/showthread.php?t=1581099") and managed to remove all traces of Grub. Unfortunately for me in the middle of all this there was a power failure. Result could not boot anything even though all the partitions were still in place. Out came the Live USB stick that has saved apps installed (a  persistence file) and went for the reinstall over the top of what was there. This failed spectacularly with errors in the sources list. You are laughing at this I can tell. In hindsight I should have tried to reinstall Grub using the How-to already posted. So I did a clean install with format to the EXT4 partition of a different distro. Not a problem for me as this was on the spare box which had very little on it.

That was how I fixed things.

That might not be the best option for you, You could try the How-to from the beginning or reinstall the distro you have without formatting anything. Be aware though that you might be one of the unlucky few that somehow lose everything. 90 - 98% of reinstalls go through with no problems at all

If it does not work then the only option might be to start again from scratch. I agree not the best thing to do so that really is the last resort.

I have left this bit till last to see if yiu read this all the way through.

Back up whatever you can before you do anything else.

Oh and Good Luck.

---

### Post by oldfred on 2011-08-01
Have you tried booting the other drive?

Or you may want to reinstall a grub2 boot loader for the other install.

Your Vista/7 install is saying it is in a FAT16 partition per partition table. That cannot be and it has to be NTFS. I think the number just got changed and if you can boot, try changing it to NTFS 07 with Disk Utility, do not reformat or you will erase everythig.

You may want to back up partition table. Another way to fix it is edit this file and read it back in.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

You would just need to change type before reimporting:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by tigerlxxv on 2011-08-15
Good news! I was able to fix it by booting from the LiveCD and running ```
 os-prober 
``` from the terminal, then running ```
 update-grub2 
``` again. I didn't know about os-prober, but it found all my kernels AND the Vista bootloader, allowing update-grub2 to do its thing. Thanks so much for your help!

---

### Post by tigerlxxv on 2011-09-09
...Although now I have to redo the Vista bootloader, as it hangs on the loading screen with the green bar. Alas. I tried running the built-in boot repair, figuring I can redo grub's instructions if that went awry, but it was unable to repair.... Back to the Search function! ... At least I have my Lucid back :)

---

