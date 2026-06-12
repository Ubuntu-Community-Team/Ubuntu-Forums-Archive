---
title: "GNU GRUB shows Windows 7 but will not boot it"
date: 2011-03-25
forum: General Help
---

### Post by baddoght on 2011-03-25
Please help, I've been pulling what's left of my hair out on this.

At the GNU GRUB boot menu, I am seeing Window's 7 listed, but am unable to boot it.  I've viewed its boot setting which appears correct (/dev/sda1/ hd 0,1).  I tried using the Ubuntu 10.4 LTR install disk to correct grub, but got stuck at the point where it asks for doing the manual partition.

I welcome anyone's input.

Thank-you.

Bad[DOG]/H.T.
Ken

**Here are some supporting details:**
Running GNU GRUB ver 1.98-1ubuntu10
/dev/sda/ - Windows 7
/dev/sdb/ - Linux
/dev/sdc/ - Windows XP

ken@ken-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbc790b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003eda8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6076140b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10011    80413326    7  HPFS/NTFS

---

### Post by baddoght on 2011-03-25
I found another forum and am reading through it.  It might hold the answers, but I figures someone will ask me for the following information.


```

                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _________________________________________________
____

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/sda1        FE94832B9482E58D                       ntfs       System Reserv
ed               
/dev/sda2        0A90856990855C57                       ntfs       Win 7 Local D
isk              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6bed56b5-c119-484c-a46e-92c92347b295   ext4                    
                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8A68AC0168ABE9E1                       ntfs                    
                 
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/8A68AC0168ABE9E1_ fuseblk    (rw,nosuid,nodev,allow_othe
r,blksize=4096,default_permissions)


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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfa
il; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fe94832b9482e58d
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 8a68ac0168abe9e1
    drivemap -s (hd0) ${root}
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
UUID=6bed56b5-c119-484c-a46e-92c92347b295 /               ext4    errors=remount
-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  15.6GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.31-21-generic
   2.0GB: boot/initrd.img-2.6.32-22-generic
   2.0GB: boot/initrd.img-2.6.32-23-generic
   5.9GB: boot/initrd.img-2.6.32-24-generic
   5.8GB: boot/initrd.img-2.6.32-25-generic
   5.7GB: boot/initrd.img-2.6.32-26-generic
   7.4GB: boot/initrd.img-2.6.32-27-generic
   7.7GB: boot/initrd.img-2.6.32-28-generic
   7.3GB: boot/initrd.img-2.6.32-29-generic
   5.6GB: boot/initrd.img-2.6.32-30-generic
   1.5GB: boot/vmlinuz-2.6.31-21-generic
   1.8GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: boot/vmlinuz-2.6.32-23-generic
   1.8GB: boot/vmlinuz-2.6.32-24-generic
  14.7GB: boot/vmlinuz-2.6.32-25-generic
   5.1GB: boot/vmlinuz-2.6.32-26-generic
   5.1GB: boot/vmlinuz-2.6.32-27-generic
  15.9GB: boot/vmlinuz-2.6.32-28-generic
   5.1GB: boot/vmlinuz-2.6.32-29-generic
   5.2GB: boot/vmlinuz-2.6.32-30-generic
   5.6GB: initrd.img
   7.3GB: initrd.img.old
   5.2GB: vmlinuz
   5.1GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" 
/fastdetect /NoExecute=OptIn
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

```

---

### Post by oldfred on 2011-03-25
Windows has to have its boot code in the partition boot sector. You installed grub to sda1 & sdc1 which are windows partitions.

```
sda1: ______________

    File system:       ntfs
    Boot sector type:  Grub 2
   [COLOR=Red] Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr
```
Run this for both sda1 & sdc1
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by drs305 on 2011-03-25
Grub 2 is designed to be installed to the MBR but not to partitions. You have overwritten the Windows boot sector of both sda and sdc by installing Grub to the sda1 and sdc1 partitions. 

You will have to try to repair the partitions using a Windows repair disk or the procedures outlined in this link:
[Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

Once you have done that, you may be able to boot either W7 (sda) or XP (sdc) by changing the boot order of the disks in BIOS.

I'm not a Windows person so I can't give you guarantees or further guidance on this.

Here are some other good links from *oldfred* which may help you.
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

Once you have Windows repaired, boot the LiveCD and install Grub2 to the sdb MBR and change the BIOS to boot sdb first:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Do not use the partition number in the second command.

If you can boot Ubuntu normally, rather than use the CD, boot and then run this to make sure G2 is still installed to the sdb MBR:
```
sudo grub-install /dev/sdb
sudo update-grub
```

---

### Post by baddoght on 2011-03-25
Thank you OldFred and DRS -

I am running out of time today, but I will pick this up sometime tomorrow.

I did get as far as going through OldFred's steps with the MBR, but this did not fix the problem.  I don't have my Window's disk on hand, but should tomorrow.

Thank you both again!

Bad[DOG]/H.T.
Ken

---

### Post by baddoght on 2011-03-31
Hi all - I did not get back on this until now....

I tried many ways to fix the MBR on the windows drive and was unable to after a couple of days of working on it.  I opted to re-install windows (no big losses).  Now I am trying to use the Ubuntu boot disk to re-install grub and am having problems with that.  I am at the point where I need to select the manual partition.  I guess I am uncertain just what I need to do here....  I am being asked at the Prepare Partitions menu to select where I need to put the boot loader.

Here is what I see:
[FONT=Courier New]
Device        Type   Mount Point   Format?   Size      Used
/dev/sda1     ntfs                           
  /dev/sda1   ntfs                           [/FONT][FONT=Courier New]104 MB    35 MB[/FONT]
[FONT=Courier New]  /dev/sda2   ntfs                           [/FONT][FONT=Courier New]500000 MB 34896 MB
/dev/sdb
  /dev/sdb1   ext4                           500105 MB 36052 MB

[/FONT]note - I do have a /dev/sdc1, but it is a old version of Windows XP I do not need anything to do with.

When I attempt to select /dev/sdb, I get a message stating that there is "no root file system is defined, please correct from the partitioning menu".  Obviously I've done something wrong.

Please advise.

Thank-you.

Bad[DOG]/H.T.
Ken
[FONT=Courier New][/FONT]

---

### Post by drs305 on 2011-03-31
Are you trying to reinstall Ubuntu or just the Grub bootloader?

If you just want to put Grub2 back in control, boot the LiveCD, mount sdb1 and install Grub2 to the MBR:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Don't include the partition number in the second command.

Reboot, and in BIOS change the boot order so sdb boots first.

If you are trying to reinstall the entire Ubuntu OS, it sounds like you have not selected the mount point. On the partitioning page you have to click on the mount point drop down box and select / for sdb1.

Since I cannot be sure of what you are attempting to do, if you have any questions please ask before you continue. If you are partitioning and get it wrong you could be installing over Windows or wiping other data.

---

### Post by baddoght on 2011-03-31
To be clear, I do not wish to overwrite Ubuntu simply take charge of what is already installed.  I'd love to get grub back in a position to manage Windows 7 and Ubuntu.  I think the command lines you gave me will get me to where I want to be, but I am going to wait for your response.

Thanks again for you help.

Ken

---

### Post by drs305 on 2011-03-31
> **baddoght said:**
> To be clear, I do not wish to overwrite Ubuntu simply take charge of what is already installed.  I'd love to get grub back in a position to manage Windows 7 and Ubuntu.  I think the command lines you gave me will get me to where I want to be, but I am going to wait for your response.

Yes, the first set should do it. Just make sure your system boots sdb first so that Grub takes control of the boot. And after you get a normal boot, run "sudo update-grub" to make sure G2 finds your Windows install (if it wasn't in the menu already).

An extra advantage is that if Windows is currently booting when you start it now, if you ever have a boot problem you can change the BIOS boot back to sda to regain Windows.

---

### Post by baddoght on 2011-03-31
Hi DRS -
 
Well this almost worked.  After changing the boot order, it came up with the grub halted at the grub command prompt.  I tried mannually booting, but it said 
 
"Error 8 - A Kernel must be loaded before booting."
 
Will running "sudo update-grub" recreate what I need or do I need to take a different direction?
 
Ken

---

### Post by drs305 on 2011-03-31
> **baddoght said:**
> "Error 8 - A Kernel must be loaded before booting."
 
Will running "sudo update-grub" recreate what I need or do I need to take a different direction?

I have to assume Windows doesn't provide that kind of message.

What kind of CD did you use? Error numbers are only associated with Grub legacy and not Grub2, so it would appear that G2 is still not on the MBR. As the system boots you may be able to see the version number at the top of the screen before it attempts to boot. (You can hold down the SHIFT key during boot to display the menu).

The update-grub command can't be simply run from the LiveCD, since it would try to change the CD's files. You would have to 'chroot' to install Grub2, which may be the next thing you have to do. 

Please run the boot info script and post the contents of RESULTS.txt so we can see what is going on (unless you know you used an old Jaunty CD, etc).

---

### Post by baddoght on 2011-03-31
The message was provided by GRUB (2 I think).  I will have to confirm the exact version on the next reboot.
 
As I am in windows at the moment, I will boot the Ubuntu CD that I am using (but did not build from) - Ubuntu 10.4.2 LTR.
 
Stand by for RESULTS.txt
 
Ken

---

### Post by baddoght on 2011-03-31
I've been having problems getting the script to run (ugg, one thing or another).  I'm am basically out of time, but hope to pick this up tomorrow.  I will look back in the forums later tonight.

As always, thank you for your help.

Ken

---

### Post by baddoght on 2011-04-01
Here we go, took me a day to figure out what I was doing wrong.....  Here are the results:

```

ubuntu@ubuntu:/mnt/home/ken/Downloads$ more RESULTS2.txt
                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdg1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdg ___________________ _________________________________________________
____

Disk /dev/sdg: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/loop0                                              squashfs                
                 
/dev/sda1        FE94832B9482E58D                       ntfs       System Reserv
ed               
/dev/sda2        0A90856990855C57                       ntfs       Win 7 Local D
isk              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6bed56b5-c119-484c-a46e-92c92347b295   ext4                    
                 
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        8A68AC0168ABE9E1                       ntfs                    
                 
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     ext4       (rw)


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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfa
il; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single ubuntu@ubuntu:/mnt/home/ken/Downloads$ more RESULTS2.txt
                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdg1 and 
                       looks at sector 279335 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdg ___________________ _________________________________________________
____

Disk /dev/sdg: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/loop0                                              squashfs                
                 
/dev/sda1        FE94832B9482E58D                       ntfs       System Reserv
ed               
/dev/sda2        0A90856990855C57                       ntfs       Win 7 Local D
isk              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6bed56b5-c119-484c-a46e-92c92347b295   ext4                    
                 
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        8A68AC0168ABE9E1                       ntfs                    
                 
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     ext4       (rw)


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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfa
il; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fe94832b9482e58d
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 8a68ac0168abe9e1
    drivemap -s (hd0) ${root}
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
UUID=6bed56b5-c119-484c-a46e-92c92347b295 /               ext4    errors=remount
-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  15.6GB: boot/grub/grub.cfg
    .2GB: boot/grub/stage2
   2.0GB: boot/initrd.img-2.6.31-21-generic
   2.0GB: boot/initrd.img-2.6.32-22-generic
   2.0GB: boot/initrd.img-2.6.32-23-generic
   5.9GB: boot/initrd.img-2.6.32-24-generic
   5.8GB: boot/initrd.img-2.6.32-25-generic
   5.7GB: boot/initrd.img-2.6.32-26-generic
   7.4GB: boot/initrd.img-2.6.32-27-generic
   7.7GB: boot/initrd.img-2.6.32-28-generic
   7.3GB: boot/initrd.img-2.6.32-29-generic
   5.6GB: boot/initrd.img-2.6.32-30-generic
   1.5GB: boot/vmlinuz-2.6.31-21-generic
   1.8GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: boot/vmlinuz-2.6.32-23-generic
   1.8GB: boot/vmlinuz-2.6.32-24-generic
  14.7GB: boot/vmlinuz-2.6.32-25-generic
   5.1GB: boot/vmlinuz-2.6.32-26-generic
   5.1GB: boot/vmlinuz-2.6.32-27-generic
  15.9GB: boot/vmlinuz-2.6.32-28-generic
   5.1GB: boot/vmlinuz-2.6.32-29-generic
   5.2GB: boot/vmlinuz-2.6.32-30-generic
   5.6GB: initrd.img
   7.3GB: initrd.img.old
   5.2GB: vmlinuz
   5.1GB: vmlinuz.old

================================ sdg1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" 
/fastdetect /NoExecute=OptIn
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
ubuntu@ubuntu:/mnt/home/ken/Downloads$ 

    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=6bed56b5-c119-484c-a46
e-92c92347b295 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6bed56b5-c119-484c-a46e-92c92347b295
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fe94832b9482e58d
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 8a68ac0168abe9e1
    drivemap -s (hd0) ${root}
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
UUID=6bed56b5-c119-484c-a46e-92c92347b295 /               ext4    errors=remount
-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  15.6GB: boot/grub/grub.cfg
    .2GB: boot/grub/stage2
   2.0GB: boot/initrd.img-2.6.31-21-generic
   2.0GB: boot/initrd.img-2.6.32-22-generic
   2.0GB: boot/initrd.img-2.6.32-23-generic
   5.9GB: boot/initrd.img-2.6.32-24-generic
   5.8GB: boot/initrd.img-2.6.32-25-generic
   5.7GB: boot/initrd.img-2.6.32-26-generic
   7.4GB: boot/initrd.img-2.6.32-27-generic
   7.7GB: boot/initrd.img-2.6.32-28-generic
   7.3GB: boot/initrd.img-2.6.32-29-generic
   5.6GB: boot/initrd.img-2.6.32-30-generic
   1.5GB: boot/vmlinuz-2.6.31-21-generic
   1.8GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: boot/vmlinuz-2.6.32-23-generic
   1.8GB: boot/vmlinuz-2.6.32-24-generic
  14.7GB: boot/vmlinuz-2.6.32-25-generic
   5.1GB: boot/vmlinuz-2.6.32-26-generic
   5.1GB: boot/vmlinuz-2.6.32-27-generic
  15.9GB: boot/vmlinuz-2.6.32-28-generic
   5.1GB: boot/vmlinuz-2.6.32-29-generic
   5.2GB: boot/vmlinuz-2.6.32-30-generic
   5.6GB: initrd.img
   7.3GB: initrd.img.old
   5.2GB: vmlinuz
   5.1GB: vmlinuz.old

================================ sdg1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" 
/fastdetect /NoExecute=OptIn
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
ubuntu@ubuntu:/mnt/home/ken/Downloads$

```

---

### Post by drs305 on 2011-04-01
Grub legacy is installed on sdb, and that is most likely what tried to boot and why you got the numbered error message.

Boot the 10.04 LiveCD. Since you got the Grub legacy menu, your system should already be booting from sdb unless you changed it to get Windows back. If sdb isn't the boot drive, change it in the BIOS on boot so the priority is CDROM, sdb and sda.

Once booted into the 10.04 LiveCD, run the commands. You have Grub2 installed to several of the partitions, which is not recommended. This is mistakenly done by selecting more than the main drive(s) (sda, sdb, etc) when you have to designate the location with an asterisk. There should be no asterisks by any of the partitions. In terminal, the mistake is to use a partition number (sdb1) instead of the drive only (sdb) in the 'grub-install' line. 

```
mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Note there is no partition number in the second command.

Save the file, remove the CD and reboot.

---

### Post by baddoght on 2011-04-01
Thank-you!  That got me where I needed to be....

I really appreciate your help.

Bad[DOG]/H.T.
Ken

---

