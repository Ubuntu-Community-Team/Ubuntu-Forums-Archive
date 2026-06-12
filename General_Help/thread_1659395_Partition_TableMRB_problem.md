---
title: "Partition Table/MRB problem?"
date: 2011-01-04
forum: General Help
---

### Post by phredbull on 2011-01-04
I have an external 500gb USB drive that was initially set-up as follows; part1(primary)-NTFS storage, part2(primary)-swap, part3(primary)-Ext4 Mint9 /, part4(extended), part5(logical) Ext4 Mint9 /home, part6(logical) Ext4 storage.

I accidentally installed a Crunchbang live .iso over the drive using this code:
```
sudo dd if=/path/to/iso/crunchbang-10-20101205-openbox-i686.iso of=/dev/sdX bs=4M;sync
```(I selected this device instead of a USB stick. :mad:)
I was able to recover all but the first NTFS partition using Testdisk, but when I try to boot from the USB disk, it still boots the Crunchbang live .iso. I can boot into the Mint9 install from Grub2 on my internal drive. In Disk Utility, after the last partition it shows 18446744 TB(!) of unallocated space. Gparted shows the entire disk as unallocated, with a warning: Can't have a partition outside the disk!

Here is the output of boot_info_script055.sh:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,929,094    29,929,032   c W95 FAT32 (LBA)
/dev/sda2          29,929,095    31,969,349     2,040,255  82 Linux swap / Solaris
/dev/sda3          52,452,225    58,605,119     6,152,895  83 Linux
/dev/sda4          31,969,350    52,452,224    20,482,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    234,375,168   236,328,943     1,953,776  82 Linux swap / Solaris
/dev/sdb2         236,328,960   259,766,271    23,437,312  83 Linux
/dev/sdb3         259,768,278   976,784,129   717,015,852   f W95 Ext d (LBA)
/dev/sdb5         259,768,320   494,141,439   234,373,120  83 Linux
/dev/sdb6         494,143,488   976,773,119   482,629,632  83 Linux

/dev/sdb3 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B02F-4E53                              vfat                                     
/dev/sda2        d75896fe-ecdc-4055-9b27-f15a74f13cf7   swap                                     
/dev/sda3        3a9cff8b-a65f-4955-845b-f680a9af4e90   ext4       ULG/home                      
/dev/sda4        d6cd6be6-68bf-47a4-b71c-5d8cb08a457e   ext4       ULG/                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ddb924c2-137f-4ee1-a44f-ccc87aed7615   swap                                     
/dev/sdb2        07ee50f9-0a44-4662-92bb-b2cc67c27830   ext4       MIF/                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        adc7a697-dd34-431f-b781-3e18fbcdf7ff   ext4       MIF/home                      
/dev/sdb6        24c4749d-b652-476b-8460-44e26074cb28   ext4       ext4_storage                  
/dev/sdb                                                iso9660    CrunchBang Live               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /home                    ext4       (rw)
/dev/sdb6        /media/ext4_storage      ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/MIF_              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/MIF_home          ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
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
menuentry 'Ubuntu, with Linux 2.6.36-020636-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux    /boot/vmlinuz-2.6.36-020636-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro   radeon.modeset=1
    initrd    /boot/initrd.img-2.6.36-020636-generic
}
menuentry 'Ubuntu, with Linux 2.6.36-020636-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    echo    'Loading Linux 2.6.36-020636-generic ...'
    linux    /boot/vmlinuz-2.6.36-020636-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.36-020636-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-020635-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux    /boot/vmlinuz-2.6.35-020635-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro   radeon.modeset=1
    initrd    /boot/initrd.img-2.6.35-020635-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-020635-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    echo    'Loading Linux 2.6.35-020635-generic ...'
    linux    /boot/vmlinuz-2.6.35-020635-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-020635-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b02f-4e53
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux Mint 9, 2.6.36-020636-generic (/dev/sdb3) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux /boot/vmlinuz-2.6.36-020636-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro splash quiet splash
    initrd /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Linux Mint 9, 2.6.36-020636-generic (/dev/sdb3) -- recovery mode (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux /boot/vmlinuz-2.6.36-020636-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro single splash
    initrd /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sdb3) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro splash quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sdb3) -- recovery mode (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro single splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=3a9cff8b-a65f-4955-845b-f680a9af4e90 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=d75896fe-ecdc-4055-9b27-f15a74f13cf7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


  16.6GB: boot/grub/core.img
  19.2GB: boot/grub/grub.cfg
  23.2GB: boot/initrd.img-2.6.35-020635-generic
  22.0GB: boot/initrd.img-2.6.36-020636-generic
  20.4GB: boot/vmlinuz-2.6.35-020635-generic
  20.7GB: boot/vmlinuz-2.6.36-020636-generic
  22.0GB: initrd.img.old
  20.7GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.36-020636-generic (/dev/sdb2)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux    /boot/vmlinuz-2.6.36-020636-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Linux Mint 9, 2.6.36-020636-generic (/dev/sdb2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    echo    'Loading Linux 2.6.36-020636-generic ...'
    linux    /boot/vmlinuz-2.6.36-020636-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sdb2)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-22-generic (/dev/sdb2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 07ee50f9-0a44-4662-92bb-b2cc67c27830
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b02f-4e53
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.36-020636-generic (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux /boot/vmlinuz-2.6.36-020636-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro radeon.modeset=1
    initrd /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Ubuntu, with Linux 2.6.36-020636-generic (recovery mode) (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux /boot/vmlinuz-2.6.36-020636-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro single
    initrd /boot/initrd.img-2.6.36-020636-generic
}
menuentry "Ubuntu, with Linux 2.6.35-020635-generic (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux /boot/vmlinuz-2.6.35-020635-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro radeon.modeset=1
    initrd /boot/initrd.img-2.6.35-020635-generic
}
menuentry "Ubuntu, with Linux 2.6.35-020635-generic (recovery mode) (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set d6cd6be6-68bf-47a4-b71c-5d8cb08a457e
    linux /boot/vmlinuz-2.6.35-020635-generic root=UUID=d6cd6be6-68bf-47a4-b71c-5d8cb08a457e ro single
    initrd /boot/initrd.img-2.6.35-020635-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=07ee50f9-0a44-4662-92bb-b2cc67c27830 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=adc7a697-dd34-431f-b781-3e18fbcdf7ff /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=d7831197-a9d9-4497-b8c7-3f44d4f9f91d none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=ddb924c2-137f-4ee1-a44f-ccc87aed7615 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 129.7GB: boot/grub/core.img
 127.8GB: boot/grub/grub.cfg
 130.6GB: boot/initrd.img-2.6.32-22-generic
 128.1GB: boot/initrd.img-2.6.36-020636-generic
 129.7GB: boot/vmlinuz-2.6.32-22-generic
 131.1GB: boot/vmlinuz-2.6.36-020636-generic
 128.1GB: initrd.img
 121.5GB: initrd.lz
 131.1GB: vmlinuz
```How can I remove the Crunchbang bootloader and .iso, fix my partition table, and make the disk bootable again?

---

### Post by damphoud on 2011-01-04
I'm not sure if this will help any, but it may be of use to rebuild your MBR via the hd manufacturer's diagnostic software.

---

### Post by Rubi1200 on 2011-01-04
Hi,
please post the output of this command:
```
sudo fdisk -lu
```Wrap with the code tag # when posting back please.

Also, how is BIOS normally setup; to boot sdb as first device?

---

### Post by phredbull on 2011-01-04
```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03190319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29929094    14964516    c  W95 FAT32 (LBA)
/dev/sda2        29929095    31969349     1020127+  82  Linux swap / Solaris
/dev/sda3        52452225    58605119     3076447+  83  Linux
/dev/sda4        31969350    52452224    10241437+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66eef7b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   234375168   236328943      976888   82  Linux swap / Solaris
/dev/sdb2       236328960   259766271    11718656   83  Linux
/dev/sdb3       259768278   976784129   358507926    f  W95 Ext'd (LBA)
/dev/sdb5       259768320   494141439   117186560   83  Linux
/dev/sdb6       494143488   976773119   241314816   83  Linux

```
I'm set up to boot from USB devices first.

---

### Post by phredbull on 2011-01-04
> **damphoud said:**
> I'm not sure if this will help any, but it may be of use to rebuild your MBR via the hd manufacturer's diagnostic software.
Unfortunately, the Seagate Manager software doesn't work in Linux or Wine, and I never could get it to work in Win due to some missing .dll. Plus, I was only able to restore the Ext4 partitions, so I even though Win tells me when I plug the drive in, it doesn't see any partitions.

---

### Post by Rubi1200 on 2011-01-04
Have you tried reinstalling GRUB?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by phredbull on 2011-01-04
> **Rubi1200 said:**
> Have you tried reinstalling GRUB?
Well, currently, the first chunk of my disk that used to be NTFS format is now unallocated, and I can't make it into a valid partition, I think because of the (supposed) massive unallocated space at the end of the disk. I'm thinking this needs to be addressed first, would that be correct?

Also, I did try repairing the MBR attempting both methods listed in post#10 in this thread:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
it seemed to wipe over the Crunchbang live bootloader, but will still not boot Grub2.

---

### Post by coffeecat on 2011-01-04
One of your problems is this:

> **phredbull said:**
> ```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03190319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29929094    14964516    c  W95 FAT32 (LBA)
/dev/sda2        29929095    31969349     1020127+  82  Linux swap / Solaris
/dev/sda3        52452225    58605119     3076447+  83  Linux
/dev/sda4        31969350    52452224    10241437+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total[COLOR=Red] 976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66eef7b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   234375168   236328943      976888   82  Linux swap / Solaris
/dev/sdb2       236328960   259766271    11718656   83  Linux
/dev/sdb3       259768278  [COLOR=Red] 976784129 [/COLOR]  358507926    f  W95 Ext'd (LBA)
/dev/sdb5       259768320   494141439   117186560   83  Linux
/dev/sdb6       494143488   976773119   241314816   83  Linux

```I'm set up to boot from USB devices first.

The end of the extended partition is showing as going beyond the end of the physical disk. This often seems to happen after the use of testdisk to restore lost partitions. And this is the reason why Gparted is showing the drive as unallocated. It might also explain the nonsensical output from Disk Utility. Here is more on the subject from forum member srs5694, together with a fix:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

It's probably a good idea to attend to this issue first and then see what remains.

---

### Post by phredbull on 2011-01-06
Coffeecat, your advice helped; I installed gdisk and it fixed the massive unallocated space problem, showing the disk properly in Disk Utility and Gparted.

Then I managed to break it even more.#-o
In Gparted, I saw unallocated spaces between partitions, so I tried to resize 2 of them to fill the empty spaces. It started with the 227gb partition, and it decided to resize the allocation block size, (I think it was 512kb, changed to 256kb.) I wasn't expecting this, but decided to not interrupt the process. It seemed to process the entire partition twice, taking over 12 hours. When it finished, Gparted reported an error, (corrupt sector I think), and where I used to have over 80gb of data, it now shows only 27gb. I ran testdisk again, but it failed to see the partition correctly. There are over 10,000 files and folders in the lost+found folder, but I have no idea what to do with them. I did back up the MBR before using gdisk to convert it to GPT, but I'm not sure if I should try to restore the backup. Is my data still recoverable, or was moving/resizing the partition a destructive process?

---

### Post by oldfred on 2011-01-06
How big were the gaps? New defaults have larger gaps between partitions to fit new 4k sector drives and SSDs. We used to have small gaps that you did not  see due to rounding, now they are larger.

The copy of the MBR/partition table is just starts & ends of the partitions. If you have moved data with gparted then the data will not match and will be lost. Not sure if some of the data will be recoverable or not.

I will PM srs5694 and see if he is available. He is often in this forum.

---

### Post by srs5694 on 2011-01-06
Ouch. The new problems aren't partitioning problems, and I know of no way to fix them. Basically, you'll have to sift through those 10,000 files in lost+found by hand to identify them. (The "file" command can help with that -- it can identify most common file types, so you'll at least know what tool to use to further identify the file.) As for the missing 53GB of data, your best bet is to use [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which can often recover lost files in situations like this. You're unlikely to get filenames, though, so you'll be back to sorting through the files. If this happened to be an OS boot partition, you'll have to re-install the OS -- but don't try this until you've recovered as many files as you can (or as you can stomach).

Sorry to be the bearer of bad news. If somebody else has an idea for easier recovery, you could try it, but AFAIK, once you get to where you are, there's no easy fix.

Oh, one other thing: Before you do anything radical, copy the entire partition (using dd, as in "sudo dd if=/dev/sdb5 of=/dev/sdc1" to copy /dev/sdb5 to /dev/sdc1). This will protect it in case some recovery attempt makes things worse; if it does, you'll at least have the backup. If necessary, buy a new hard drive to make this possible.

I'll close with this: Let this be a lesson to all that resizing partitions *is* risky! I'm sorry you had to learn this the hard way, phredbull, but with any luck somebody else will read this thread and know to back up first, or to not attempt resizing for a trivial reason.

---

### Post by phredbull on 2011-01-07
> **oldfred said:**
> How big were the gaps?
Only 1mb, if I remember correctly. Not like I needed the drive space, just the neat-freak in me not wanting to see a bunch of useless little spaces.

@srs5694:
Ouch indeed. I guess my initial success w/testdisk had me over confident. I assumed resizing the partitions meant simply writing a new partition table w/an extra mb at the beginning and end, not shifting all 80gb of data over by 1mb. I do know the importance of backing up, but my poor *** chose the convenient-but-risky method over the safe-but-costly one. D'oh! Lesson learned. I guess I'll spend all my spare time in the foreseeable future sifting through that lost+found folder...

BTW, will photorec find anything that isn't already in the lost+found folder?

Thanks to all respondents, some very helpful advice!

---

### Post by oldfred on 2011-01-07
Somehow I managed to lose two folders one one of my drives. I used photorec and it found everything on the drive, but it can take a long time. One of the text files that I had saved many times was recovered many times with each version. The issue was I am not sure I ever found the final version. I used my backup and copied bits from several of the found copies and recovered most of the file.

Photorec does not recover file names, as it is just looking thru drive to find data that looks like a file. Photos & music have internal data that you can use to rename file.

---

### Post by srs5694 on 2011-01-07
> **phredbull said:**
> Only 1mb, if I remember correctly. Not like I needed the drive space, just the neat-freak in me not wanting to see a bunch of useless little spaces.

It is *never* worth the risk to resize partitions in order to recover just 1 MB of disk space. Note there's no "IMHO" in that statement. Just live with it until you need to do something bigger with disk repartitioning.

Also, partitioning software has been changing how it aligns partitions recently. In the past, most software aligned partitions on cylinder boundaries, but cylinders as a measure of disk space have been fictions for over a decade now, at least as viewed by the OS. Recently other factors have become important, so new software now aligns partitions on 1 MiB boundary points. When you use both old and new software, there will be small gaps that might be difficult to eliminate, or even impossible from some programs. Some versions of GParted even hide such tiny gaps from users, my guess is to prevent them from trying to do something risky to eliminate them.

> I assumed resizing the partitions meant simply writing a new partition table w/an extra mb at the beginning and end, not shifting all 80gb of data over by 1mb.

Resizing partitions actually involves doing two things:


[list]
[*]Rewriting the partition table data. This is quick and easy to do.
[*]Adjusting the start and/or end points of the filesystems within the partitions. This can be time-consuming and risky. Both the time-consumingness of it and the risk of it increase greatly if the start of the partition is changed, because all the data structures in the filesystem are laid out relative to the start of the partition, so you've got to move all those data structures (and maybe even all the data in every file) to compensate for the change.
[/list]


Unfortunately, GParted tends to hide some of its details from you, so it's not always clear whether it's planning on moving the start of a partition when you tell it to resize a partition. This is unfortunate, and it's one reason I'm reluctant to advise people to resize partitions unless it's very important that they do so. It's also one of the reasons I like [LVM;](http://tldp.org/HOWTO/LVM-HOWTO/) using LVM, there's less need to partition resizing/moving, and when you do need to adjust your filesystems, you can do it without changing the start point, so it's much safer.

---

### Post by srs5694 on 2011-01-07
The forum software is flaking out and duplicating posts again.

---

### Post by srs5694 on 2011-01-07
The forum software is flaking out and duplicating posts again.

---

