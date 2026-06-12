---
title: "Install Grub2 on an internal hd"
date: 2011-03-13
forum: General Help
---

### Post by TimEnid on 2011-03-13
Yesterday i received a new hd, i installed ubuntu 10.10 on it, but when i boot it up, i dont get the splash screen, i just get a black screen with the blinking cursor. could this be because grub is not installed? so i put back my previous hd (which already has 10.10 on it) and i kept in the new hd. So if this is the problem, how can i install grub2 on that particular hd?

should i try to install grub on the new hd thru the boot cd, or will doing it from my already installed os be ok?

---

### Post by wilee-nilee on 2011-03-13
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by TimEnid on 2011-03-13
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sdj

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
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

sdj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *        112,455    71,167,949    71,055,495  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   937,164,799   937,162,752  83 Linux
/dev/sdb2         937,166,846   976,773,119    39,606,274   5 Extended
/dev/sdb5         937,166,848   976,773,119    39,606,272  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,417,183,231 1,417,181,184  83 Linux
/dev/sdd2       1,417,185,278 1,465,147,391    47,962,114   5 Extended
/dev/sdd5       1,417,185,280 1,465,147,391    47,962,112  82 Linux swap / Solaris


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdj1                  63 2,929,002,929 2,929,002,867   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        DC96260D9625E92A                       ntfs       E                             
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8e4ba2bb-1881-4629-bca4-d9881ce75b5c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ae558e1e-36a0-4615-a404-7d9e7255659a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        86CEFEB2CEFE9A1F                       ntfs       WD                            
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        ba601319-390b-458a-b5f1-a4c1d2132100   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        2369430c-0a78-42b3-803a-ba5175d1164b   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sdj1        A8508E6E508E4354                       ntfs       Buffalo 1.5tb                 
/dev/sdj: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
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
menuentry 'Ubuntu, with Linux 2.6.38-020638rc6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux    /boot/vmlinuz-2.6.38-020638rc6-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.38-020638rc6-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638rc6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    echo    'Loading Linux 2.6.38-020638rc6-generic ...'
    linux    /boot/vmlinuz-2.6.38-020638rc6-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-020638rc6-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 8e4ba2bb-1881-4629-bca4-d9881ce75b5c
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8e4ba2bb-1881-4629-bca4-d9881ce75b5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=ae558e1e-36a0-4615-a404-7d9e7255659a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 262.1GB: boot/grub/core.img
 133.4GB: boot/grub/grub.cfg
   4.5GB: boot/initrd.img-2.6.35-23-generic
 136.9GB: boot/initrd.img-2.6.35-24-generic
 138.3GB: boot/initrd.img-2.6.35-25-generic
 279.5GB: boot/initrd.img-2.6.35-27-generic
 137.9GB: boot/initrd.img-2.6.38-020638rc6-generic
 263.2GB: boot/vmlinuz-2.6.35-23-generic
 263.2GB: boot/vmlinuz-2.6.35-24-generic
 263.2GB: boot/vmlinuz-2.6.35-25-generic
 263.3GB: boot/vmlinuz-2.6.35-27-generic
 263.3GB: boot/vmlinuz-2.6.38-020638rc6-generic
 137.9GB: initrd.img
 279.5GB: initrd.img.old
 263.3GB: vmlinuz
 263.3GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
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
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ba601319-390b-458a-b5f1-a4c1d2132100 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ba601319-390b-458a-b5f1-a4c1d2132100 ro single 
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
    search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set ba601319-390b-458a-b5f1-a4c1d2132100
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdi1 during installation
UUID=ba601319-390b-458a-b5f1-a4c1d2132100 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdi5 during installation
UUID=2369430c-0a78-42b3-803a-ba5175d1164b none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


 133.2GB: boot/grub/core.img
 421.0GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
 133.2GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
 133.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdi 
```fyi, this is the drive that i am trying to boot 10.10 from
> No boot loader is installed in the MBR of /dev/sdd

---

### Post by wilee-nilee on 2011-03-13
Put the sdd drive to be read first in the bios, top oh the list above the other HD's. Boot the live cd and run these two commands.
```
sudo mount /dev/sdd1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdd
```
Reboot you should get the grub menu, boot in and run.
```
sudo update-grub
```

Here is the link to the commands and reloading grub2 from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by YesWeCan on 2011-03-13
There are a couple of things you ought to fix here. DO both using a Ubuntu live CD/USB:

You should restore a Windows MBR to sda.
[B]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/B]
This will allow you to boot sda from the bios.

Then you can add the Grub2 MBR to sdd
as above #4

---

### Post by wilee-nilee on 2011-03-13
> **YesWeCan said:**
> There are a couple of things you ought to fix here. DO both using a Ubuntu live CD/USB:

You should restore a Windows MBR to sda.
[B]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/B]
This will allow you to boot sda from the bios.

Then you can add the Grub2 MBR to sdd
as above #4

Disregard this post it was not asked for and is not needed before or after fixing the sdd boot. If you have a windows set up there are recovery discs on the web for sliding in the MS bootloader on sda if needed.

---

### Post by TimEnid on 2011-03-13
> **wilee-nilee said:**
> Put the sdd drive to be read first in the bios, top oh the list above the other HD's. Boot the live cd and run these two commands.
```
sudo mount /dev/sdd1 /mnt
```then
```
sudo grub-install --root-directory=/mnt /dev/sdd
```Reboot you should get the grub menu, boot in and run.
```
sudo update-grub
```Here is the link to the commands and reloading grub2 from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

thanks, this worked.

but when i open my terminal, i see this line > tim@tim-System-Product-Name
why does it say System Product Name?

---

### Post by YesWeCan on 2011-03-13
> **wilee-nilee said:**
> Disregard this post it was not asked for and is not needed before or after fixing the sdd boot. If you have a windows set up there are recovery discs on the web for sliding in the MS bootloader on sda if needed.
How rude! :p
This will allow Tim to boot directly into Vista even if he messes up Grub for any reason or removes the sdd drive or whatever.

---

### Post by wilee-nilee on 2011-03-13
> **TimEnid said:**
> thanks, this worked.

but when i open my terminal, i see this line 
why does it say System Product Name?

When you installed at the screen where you put in the user name and password there is a line that adds the computer, I always just delete that part and leave my user name.

Also as YesWecan suggested if you have windows on sda2 and want the MS or lilo boot loader in the sda mbr we can do that as well their commands are correct for lilo. This just makes sure that Windows can boot straight from that drive without grub.

I didn't comment on this originally as sda2 is missing some key files that should be there in the script, sometimes they just don't show when they are there though.

---

### Post by wilee-nilee on 2011-03-13
It was rude for you to post when the instructions were correct already. I do this every day and can take care of this, I like help when its asked for; but not personal opinions not needed. This just muddles the process, the most important person here is the OP not our personal opinions.

If you took the time to look at the script you would see that sda2 is missing key boot files, out of the mbr.

As we see now everything is fixed, I suggested looking at your lilo if needed, take a deep breath and chill bro.;)

---

### Post by TimEnid on 2011-03-13
> **wilee-nilee said:**
> When you installed at the screen where you put in the user name and password there is a line that adds the computer, I always just delete that part and leave my user name.

Also as YesWecan suggested if you have windows on sda2 and want the MS or lilo boot loader in the sda mbr we can do that as well their commands are correct for lilo. This just makes sure that Windows can boot straight from that drive without grub.

I didn't comment on this originally as sda2 is missing some key files that should be there in the script, sometimes they just don't show when they are there though.
ok, thanks. no need to install the windows bootloader.

is there anyway to go back and remove that computer name?

---

### Post by YesWeCan on 2011-03-13
> **wilee-nilee said:**
> It was rude for you to post when the instructions were correct already. I do this every day and can take care of this, I like help when its asked for; but not personal opinions not needed. This just muddles the process, the most important person here is the OP not our personal opinions. 

If you took the time to look at the script you would see that sda2 is missing key boot files, out of the mbr.

As we see now everything is fixed, I suggested looking at your lilo if needed, take a deep breath and chill bro.:)

You aren't being any less rude. Quite self-righteous, in fact.  :neutral:

---

### Post by wilee-nilee on 2011-03-13
> **TimEnid said:**
> ok, thanks. no need to install the windows bootloader.

is there anyway to go back and remove that computer name?

I'm not sure about that, copy and paste that line from the terminal so it is clear what's up.

---

### Post by YesWeCan on 2011-03-13
> **TimEnid said:**
> thanks, this worked.

but when i open my terminal, i see this line 
why does it say System Product Name?
So it looks like your hostname got set to this weird default.

Check this by running 'hostname' in a terminal. It should give the same name.

There are loads of online tutorials about how to change the hostname. Here is one I picked out just now: [http://www.ehow.com/how_5214749_change-host-name-ubuntu.html](http://www.ehow.com/how_5214749_change-host-name-ubuntu.html)

---

### Post by TimEnid on 2011-03-13
> **YesWeCan said:**
> So it looks like your hostname got set to this weird default.

Check this by running 'hostname' in a terminal. It should give the same name.

There are loads of online tutorials about how to change the hostname. Here is one I picked out just now: [http://www.ehow.com/how_5214749_change-host-name-ubuntu.html](http://www.ehow.com/how_5214749_change-host-name-ubuntu.html)

thanks for the suggestion and help, i was able to change it with ubuntu tweak.

---

