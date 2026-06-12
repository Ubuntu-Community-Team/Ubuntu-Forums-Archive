---
title: "missing modules. Droping to shell!"
date: 2011-12-18
forum: General Help
---

### Post by daroox on 2011-12-18
hi,
[http://ubuntuforums.org/showthread.php?t=1511903](http://ubuntuforums.org/showthread.php?t=1511903)
i have the same problem as described here [http://ubuntuforums.org/showthread.php?t=1511903&page=2](http://ubuntuforums.org/showthread.php?t=1511903&page=2)
so i downloaded the boot info script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and here is the result
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   183,860,574   183,653,727   7 NTFS / exFAT / HPFS
/dev/sda3         213,026,814   312,580,095    99,553,282   5 Extended
/dev/sda5         304,408,576   312,580,095     8,171,520  82 Linux swap / Solaris
/dev/sda6         213,026,816   262,058,403    49,031,588  83 Linux
/dev/sda7         262,060,032   302,542,847    40,482,816  83 Linux
/dev/sda8         302,544,896   304,396,287     1,851,392  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4212 MB, 4212129792 bytes
2 heads, 63 sectors/track, 65292 cylinders, total 8226816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     8,226,815     8,226,752   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5AA6FFA3A6FF7E37                       ntfs       System Reserved
/dev/sda2        DC2802AC2802862C                       ntfs       
/dev/sda5        10aa7c72-8893-47c9-9bf8-e9eddc0f6792   swap       
/dev/sda6        44338b7d-2e08-40ac-8cf3-e244664a1651   ext4       
/dev/sda7        eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca   ext4       
/dev/sda8        e62f7fbc-b1bf-4b72-b9b6-458d88692cb3   swap       
/dev/sdb1        B2CE-F556                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/DC2802AC2802862C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    echo    'Loading Linux 3.0.0-13-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
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
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 5AA6FFA3A6FF7E37
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 103.639106750 = 111.281643520  boot/grub/core.img                             1
 103.031265259 = 110.628978688  boot/grub/grub.cfg                             1
 104.333015442 = 112.026722304  boot/initrd.img-2.6.38-10-generic              2
 105.085269928 = 112.834449408  boot/initrd.img-3.0.0-12-generic               2
 105.107421875 = 112.858234880  boot/initrd.img-3.0.0-12-generic-pae           1
 102.503536224 = 110.062333952  boot/initrd.img-3.0.0-13-generic               6
 102.517108917 = 110.076907520  boot/initrd.img-3.0.0-13-generic-pae           1
 101.825504303 = 109.334302720  boot/vmlinuz-2.6.38-10-generic                 1
 104.165447235 = 111.846797312  boot/vmlinuz-3.0.0-12-generic                  1
 104.231979370 = 111.918235648  boot/vmlinuz-3.0.0-12-generic-pae              1
 102.327743530 = 109.873577984  boot/vmlinuz-3.0.0-13-generic                  2
 102.335762024 = 109.882187776  boot/vmlinuz-3.0.0-13-generic-pae              4

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5AA6FFA3A6FF7E37
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 44338b7d-2e08-40ac-8cf3-e244664a1651
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=44338b7d-2e08-40ac-8cf3-e244664a1651 ro recovery nomodeset
    initrd /boot/initrd.img-2.6.38-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=eb6bfdf2-5a39-40d4-90e1-f4fb92caf6ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e62f7fbc-b1bf-4b72-b9b6-458d88692cb3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 127.092575073 = 136.464613376  boot/grub/core.img                             1
 127.155281067 = 136.531943424  boot/grub/grub.cfg                             1
 127.100028992 = 136.472616960  boot/initrd.img-2.6.32-33-generic              1
 127.091175079 = 136.463110144  boot/vmlinuz-2.6.32-33-generic                 1
 127.100028992 = 136.472616960  initrd.img                                     1
 127.091175079 = 136.463110144  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  6b a8 9f e9 11 ba 02 af  b8 ac 84 91 05 44 a8 a1  |k............D..|
00000010  2e e5 1b b5 cb 56 a7 18  d4 3e 17 26 a2 c8 80 90  |.....V...>.&....|
00000020  c6 88 2c 40 ad 6d cf b8  71 49 4d ef f0 73 00 b1  |..,@.m..qIM..s..|
00000030  9b 4a 70 60 ae ae ec e3  41 6a e2 cb 4f 8c ea d1  |.Jp`....Aj..O...|
00000040  46 69 1b 43 67 a5 43 49  a1 1b d6 d6 c8 73 7f cb  |Fi.Cg.CI.....s..|
00000050  8c 9b 4a a8 82 31 ce aa  5b 0e f2 7e a1 77 ab 09  |..J..1..[..~.w..|
00000060  8c a5 01 2d 65 c7 06 8c  ca 6d a5 6d 91 e0 ba 44  |...-e....m.m...D|
00000070  0b 62 d0 39 49 6f 74 8b  7c 88 35 f4 05 38 83 ad  |.b.9Iot.|.5..8..|
00000080  68 ad 5d 96 41 b6 ab 5b  8c cb 25 2b 9a 34 5e a0  |h.].A..[..%+.4^.|
00000090  ed 12 69 cf 44 8d d4 25  1b 99 82 91 36 1c 52 18  |..i.D..%....6.R.|
000000a0  98 74 1d dc b3 85 1e bb  f6 f0 94 69 18 4e ac c1  |.t.........i.N..|
000000b0  7e 67 56 77 ae 10 e3 0a  16 88 07 83 51 6c bb 1b  |~gVw........Ql..|
000000c0  ad f4 7b 68 4b d6 ba d7  ac 6f b4 1e 5e 2d 71 87  |..{hK....o..^-q.|
000000d0  46 67 78 b8 15 1c b4 11  5b 8f 94 d3 2b 6a f8 2f  |Fgx.....[...+j./|
000000e0  51 45 08 ba 3c 11 59 5d  b2 83 17 5c c4 e8 06 ea  |QE..<.Y]...\....|
000000f0  f3 78 f3 af 34 27 3f 6f  aa dc dc 91 cb 68 b6 41  |.x..4'?o.....h.A|
00000100  e6 a5 dc d2 37 e1 88 66  4c 3d aa 6a 81 a4 de b6  |....7..fL=.j....|
00000110  28 38 a3 27 e6 17 9b b9  06 ad ca 44 89 05 8c 17  |(8.'.......D....|
00000120  96 bd 14 87 30 5f 06 ca  a1 23 b6 e8 e9 a8 b6 c3  |....0_...#......|
00000130  52 36 7d df 42 5b 44 21  1b 23 44 6e 16 21 cf 42  |R6}.B[D!.#Dn.!.B|
00000140  18 4c b8 52 59 bf ae db  67 e4 93 36 d8 fb 14 b9  |.L.RY...g..6....|
00000150  a4 74 b9 c4 35 17 b9 5a  16 b7 a5 6b 0d 84 93 23  |.t..5..Z...k...#|
00000160  30 51 2d 8a 2a 58 bf e1  8f 22 f5 c3 4a 72 5e b0  |0Q-.*X..."..Jr^.|
00000170  e1 2c 65 81 4c 9f 48 d2  f8 9b 0d a8 9c 0e d2 34  |.,e.L.H........4|
00000180  9b 34 71 47 6a 97 46 d1  b0 3e 62 e3 5e 4a af 9d  |.4qGj.F..>b.^J..|
00000190  a6 db 45 91 51 7e bd 4f  b9 fc 04 52 29 25 dc 92  |..E.Q~.O...R)%..|
000001a0  12 e5 ba 0c 0c 2a 4a 4a  b6 0f a3 86 6a fc 69 2a  |.....*JJ....j.i*|
000001b0  11 25 9d 6d 08 ea 8a 7a  51 e6 6b ce cf 86 00 ef  |.%.m...zQ.k.....|
000001c0  ff ff 82 ef ff ff 02 60  72 05 00 b0 7c 00 00 ef  |.......`r...|...|
000001d0  ff ff 05 ef ff ff 01 00  00 00 a5 29 ec 02 00 00  |...........)....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Ubuntu is not starting while windows 7 is starting fine

thx for any help

---

