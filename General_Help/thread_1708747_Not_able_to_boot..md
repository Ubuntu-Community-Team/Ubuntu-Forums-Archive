---
title: "Not able to boot."
date: 2011-03-17
forum: General Help
---

### Post by VitalBodies on 2011-03-17
I have been using Ubuntu for many years. : )
I bought a new hard drive (has not arrived yet) and getting ready to install it when it arrives. 
My computer/workstation has a number of hard drives installed inside that are all SATA drives. 
The boot drive (Ubuntu only, I do not use Windows) is a 500GB USB notebook drive installed in an external case. 

I have an 80GB internal drive with an old Ubuntu install. I decided to remove that drive (pulled the drive) to make room for the new drive. 

But the new drive did not come in the mail, so I put the computer back together without the old 80GB drive (SATA 0). 

To my surprise it would not boot to the 500GB USB drive? 
Black screen with the blinking dash...

Removed every drive but the USB 500GB drive and the CD from the BIOS boot menu. Made the USB THE drive to boot to.  
Black screen with the blinking dash...

Using a 10.10 LiveCD I can access that 500GB drive. 
Thus, it is hooked up and works but does not boot. Gparted says there is a BOOT FLAG in the Linux partition of the 500GB drive. 

My only conclusion was I altered the boot order for GRUB so I put the 80GB drive back in the computer. 
I did not edit GRUB in any way, I simply physically pulled the drive when the computer was off. 
Black screen with the blinking dash...

Hmmm...

Ran a script (bootinfoscript) with this output from the LiveCD: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

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

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   586,067,264   586,067,202  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   937,164,799   937,162,752  83 Linux
/dev/sdd2         937,166,846   976,771,071    39,604,226   5 Extended
/dev/sdd5         937,166,848   976,771,071    39,604,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f3922d37-71a2-430f-92fb-c125b10df55c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b46e7cdc-fe77-411e-8900-b4384d4aaabd   ext4       200 GB                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        152a096c-7641-46fb-8275-0d1c71f9751e   ext4       300GBext4                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        c76094bd-dd3a-47b6-a9cc-03170df9ceaa   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        539c10b5-a4d0-4584-89bc-c33e2e26f688   swap                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/c76094bd-dd3a-47b6-a9cc-03170df9ceaa ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3922d37-71a2-430f-92fb-c125b10df55c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
   7.3GB: boot/grub/grub.cfg
   4.0GB: boot/initrd.img-2.6.31-21-generic
  30.4GB: boot/initrd.img-2.6.32-25-generic
  11.8GB: boot/initrd.img-2.6.35-22-generic
   3.0GB: boot/vmlinuz-2.6.31-21-generic
   1.7GB: boot/vmlinuz-2.6.32-25-generic
  29.8GB: boot/vmlinuz-2.6.35-22-generic
  11.8GB: initrd.img
  30.4GB: initrd.img.old
  29.8GB: vmlinuz
   1.7GB: vmlinuz.old

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
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
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
    initrd /boot/initrd.img-2.6.31-21-generic
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdh1 during installation
UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdh5 during installation
UUID=539c10b5-a4d0-4584-89bc-c33e2e26f688 none            swap    sw              0       0

=================== sdd1: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
 382.6GB: boot/grub/grub.cfg
 179.5GB: boot/initrd.img-2.6.35-22-generic
 105.1GB: boot/initrd.img-2.6.35-23-generic
 262.9GB: boot/initrd.img-2.6.35-24-generic
 467.3GB: boot/initrd.img-2.6.35-25-generic
  36.3GB: boot/initrd.img-2.6.35-27-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
 118.1GB: boot/vmlinuz-2.6.35-23-generic
 118.1GB: boot/vmlinuz-2.6.35-24-generic
 118.1GB: boot/vmlinuz-2.6.35-25-generic
  36.1GB: boot/vmlinuz-2.6.35-27-generic
  36.3GB: initrd.img
 467.3GB: initrd.img.old
  36.1GB: vmlinuz
 118.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

I am not trying to dual boot although I sometime install ubuntu on drives just in case for a backup working drive. 
To make a long story short, I am still stuck.

---

### Post by Krytarik on 2011-03-17
I am somehow wondering how you where at all able to boot into your 500GB disk, if you are sure that the current OS is really located there, since there are no entries for it in the current Grub config.

The current state is that way:
- the Grub boot loader is installed on your 80GB disk
- it also accesses the config files on those disk
- like I said, there are no entries for your 500GB disk

- there is an apparently valid Grub config on your 500GB disk
- but there is no Grub boot loader installed

To get it working with the current disk setup:
- boot with the LiveCD
- mark the root partition of your 500GB disk (/dev/sdd1) as bootable with GParted ("boot" flag)
- mount the root partition of your 500GB disk
```
sudo mount /dev/sdd1 /mnt
```- install the Grub boot loader into the MBR of your 500GB disk
```
sudo grub-install --root-directory=/mnt /dev/sdd
```[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Problem: If you change anything in the setup of your disks, e.g. remove your 80GB disk, or put your 500GB disk inside, the boot config becomes invalid, because the disk order will change, and the boot config is set up for the old order.

Solution: After you changed the disk setup
- boot with a LiveCD
- check at which position your OS drive is now (e.g. with GParted)
- mount the root partition similar like above
- change "[/mnt]/boot/grub/grub.cfg" to reflect the new order

Examples:
- currently the root partition of your 500GB disk is at /dev/sdd1
- there are numerous entries in grub.cfg like this:
```
set root='(hd3,msdos1)'
```- if it were /dev/sda1, the corresponding entries were like this:
```
set root='(hd0,msdos1)'
```Guide to those disk/partition values:
[https://help.ubuntu.com/community/Grub2#Creating%20the%20Custom%20Menu](https://help.ubuntu.com/community/Grub2#Creating%20the%20Custom%20Menu)

Good luck!

---

### Post by VitalBodies on 2011-03-17
Thank you for this well written reply! I have read what you wrote once (and I will re-read it) and am still studying the other pages you linked to. 

I had wondered if I changed the order of the drives and I wondered if some how the boot loader was on the 80GB and I just never knew that I was some how booting from there. I figured that if I put the 80GB drive back where it was (SATA 0 and the same physical location in the computer) that this would be revealed. After replacing the drive I still ended up with the black screen with the blinking dash as I mentioned. As far as I can tell, the GRUB menu (or any sign of GRUB) does not show up while booting - at least no visible sign. Although I am not really sure, I think the black screen and blinking dash is the workstation rather than Ubuntu or GRUB. I am not that familiar with GRUB so my assessments are speculation. 

It is a mystery as to why (as you mentioned) there is no boot loader on the the boot drive. 

The BIOS does not seem to care which USB port the 500GB drive is plugged into, although I am not sure as yet if GRUB does. I have four ports in the back of the workstation for USB and I can not remember which one I had the 500GB drive plugged into. The 500GB drive is intended to remain an External USB drive.  

For myself and others that read this thread seeking help, I want to post my grub.cfg. 
Below is my grub.cfg before attempting the changes mentioned by Krytarik. 

```

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c76094bd-dd3a-47b6-a9cc-03170df9ceaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set c76094bd-dd3a-47b6-a9cc-03170df9ceaa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=5f6cd930-64f6-4dc4-8316-ca3dbda3f6ce ro single
	initrd /boot/initrd.img-2.6.31-21-generic
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

```

---

### Post by VitalBodies on 2011-03-17
> **Krytarik said:**
> I am somehow wondering how you where at all able to boot into your 500GB disk, if you are sure that the current OS is really located there, since there are no entries for it in the current Grub config.

The current state is that way:
- the Grub boot loader is installed on your 80GB disk
- it also accesses the config files on those disk
- like I said, there are no entries for your 500GB disk

- there is an apparently valid Grub config on your 500GB disk
- but there is no Grub boot loader installed

To get it working with the current disk setup:
- boot with the LiveCD
- mark the root partition of your 500GB disk (/dev/sdd1) as bootable with GParted ("boot" flag)
- mount the root partition of your 500GB disk
```
sudo mount /dev/sdd1 /mnt
```- install the Grub boot loader into the MBR of your 500GB disk
```
sudo grub-install --root-directory=/mnt /dev/sdd
```[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Good luck!

Luck happened (great advice)! I followed the advice (the part I quoted) and my system is back up and fully functional. 
Thanks you so much!

The USB 500GB drive has been totally consistent to the eye. It has not moved during ANY or all steps (still external in a case and still USB) although I might have plugged it into a different port in the back of the computer which has never mattered before that I could tell. The drive always showed in the Bios. The odd thing is that (it would seem) the boot loader vanished (as you pointed out). Your help re-installed the boot loader. I was surprised the system would not boot as nothing I knew of (that mattered) had changed. The things that could have mattered like taking out the 80GB had all been put back in place. Why the boot loader would have disappeared is the mystery and is still the mystery. That scenario is also a bit counter intuitive, at least to me. 

I bought my first SSD (Solid State Drive) that I was (am) excited to get going. Still did not arrive yet but research takes time so I ma starting early. I still do not really know how to SWAP/MOVE to a new hard drive. 

I do know how to install a drive, start from scratch and load an OS onto a computer. I have done this countless times. But I do not know how to copy my existing system to a new hard drive and make that work in Ubuntu. Permissions have been one issue in the past that I ran into but that was years ago that I tried. Essentially, it is a bit lazy/practical to not want to do all the updates and system customization (adding programs, firewall, fonts etc etc etc.). I will get there though, just takes a lot of time... 

I am a little nervous about setting up a new drive. I will continue to study the Community Documentation.

---

