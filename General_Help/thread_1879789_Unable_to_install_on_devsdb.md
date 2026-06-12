---
title: "Unable to install on dev/sdb*"
date: 2011-11-12
forum: General Help
---

### Post by urosg3 on 2011-11-12
Ubuntu 11.10 installer, not offering option to install on sdb* , and even worse, os-prober is unable to detect natty sitting on sdb*.

Whats wrong here, any idea?

---

### Post by Rubi1200 on 2011-11-12
Please post the results of the boot info script so we can help you diagnose the issue.

Thanks.

---

### Post by urosg3 on 2011-11-12
Here:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

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
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          19,533,822    80,291,839    60,758,018   5 Extended
/dev/sda5          19,533,824    21,680,127     2,146,304  82 Linux swap / Solaris
/dev/sda6          21,682,176    80,291,839    58,609,664  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    51,199,154    51,199,092   7 NTFS / exFAT / HPFS
/dev/sdb2          51,199,998   312,576,704   261,376,707   f W95 Extended (LBA)
/dev/sdb5         128,921,688   312,576,704   183,655,017  83 Linux
/dev/sdb6          51,200,000    53,151,743     1,951,744  82 Linux swap / Solaris
/dev/sdb7          53,153,792    82,448,383    29,294,592  83 Linux
/dev/sdb8          82,450,432   128,921,599    46,471,168  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        31fe697f-af8e-448a-ac70-abfb8588a91b   ext4       
/dev/sda5        f9a5c5c1-6c6e-46e1-8e88-b85b971cf3c7   swap       
/dev/sda6        ae518e6c-0b41-4df5-89f3-6b5b480b32ed   ext4       
/dev/sdb1        6AB49CA5B49C74F3                       ntfs       
/dev/sdb5        5fd23876-52f0-4463-9fd6-069377ab9427   ext4       
/dev/sdb6        8dfe3507-5071-4e71-8362-a1552610401b   swap       
/dev/sdb7        a040760a-537c-4450-b637-c51361b1325f   ext4       
/dev/sdb8        0a88d8a3-d54c-428d-b0ce-d8f732ab5e24   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /home                    ext4       (rw,commit=0)
/dev/sdb7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=31fe697f-af8e-448a-ac70-abfb8588a91b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=31fe697f-af8e-448a-ac70-abfb8588a91b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 31fe697f-af8e-448a-ac70-abfb8588a91b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 6AB49CA5B49C74F3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	linux /boot/vmlinuz-2.6.38-12-generic root=UUID=a040760a-537c-4450-b637-c51361b1325f ro quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	linux /boot/vmlinuz-2.6.38-12-generic root=UUID=a040760a-537c-4450-b637-c51361b1325f ro single
	initrd /boot/initrd.img-2.6.38-12-generic
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

=============================== sda1/etc/fstab: ================================

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
UUID=31fe697f-af8e-448a-ac70-abfb8588a91b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ae518e6c-0b41-4df5-89f3-6b5b480b32ed /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f9a5c5c1-6c6e-46e1-8e88-b85b971cf3c7 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=8dfe3507-5071-4e71-8362-a1552610401b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.568943024 = 9.200832512    boot/grub/core.img                             1
   2.564247131 = 2.753339392    boot/grub/grub.cfg                             1
   2.819934845 = 3.027881984    boot/initrd.img-3.0.0-13-generic               3
   1.825607300 = 1.960230912    boot/vmlinuz-3.0.0-13-generic                  1
   1.825607300 = 1.960230912    vmlinuz                                        1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 109.599678040 = 117.681758208  boot/grub/core.img                             1

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1680x1050-24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=a040760a-537c-4450-b637-c51361b1325f ro   quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=a040760a-537c-4450-b637-c51361b1325f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos7)'
	search --no-floppy --fs-uuid --set=root a040760a-537c-4450-b637-c51361b1325f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-020638rc5-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-020638rc5-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.38-020638rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638rc5-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-020638rc5-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro single
	initrd /boot/initrd.img-2.6.38-020638rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro single
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-7-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-7-generic root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro single
	initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-rc2 (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-rc2 root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.38-rc2
}
menuentry "Ubuntu, with Linux 2.6.38-rc2 (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cd7e5ab7-82de-4ac2-b067-505c8e28c31d
	linux /boot/vmlinuz-2.6.38-rc2 root=UUID=cd7e5ab7-82de-4ac2-b067-505c8e28c31d ro single
	initrd /boot/initrd.img-2.6.38-rc2
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 6AB49CA5B49C74F3
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=a040760a-537c-4450-b637-c51361b1325f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=5fd23876-52f0-4463-9fd6-069377ab9427 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f9a5c5c1-6c6e-46e1-8e88-b85b971cf3c7 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=8dfe3507-5071-4e71-8362-a1552610401b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.502941132 = 29.531058176   boot/grub/core.img                             1
  34.644573212 = 37.199327232   boot/grub/grub.cfg                             1
  26.253120422 = 28.189073408   boot/initrd.img-2.6.38-12-generic              2
  27.873355865 = 29.928787968   boot/vmlinuz-2.6.38-12-generic                 2
  26.253120422 = 28.189073408   initrd.img                                     2
  27.873355865 = 29.928787968   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  a2 7d 73 3d a7 33 e3 c3  d7 de 4e e2 ac 56 f5 ca  |.}s=.3....N..V..|
00000010  be f1 ea 0f d2 25 bf 73  87 fe 68 b1 f1 b5 eb 4b  |.....%.s..h....K|
00000020  5a 52 cf 98 db 22 71 83  ed 7d 78 5e 22 55 fa 94  |ZR..."q..}x^"U..|
00000030  3b d2 7d d8 73 09 bc 5a  53 c3 49 a4 c4 fc 10 00  |;.}.s..ZS.I.....|
00000040  7c 19 b3 01 f2 c2 46 f2  7e bd b7 75 88 bc a0 67  ||.....F.~..u...g|
00000050  0d 49 08 04 09 7c 30 a4  13 4a fd cf e9 4e fb 31  |.I...|0..J...N.1|
00000060  bf 6d c3 bd 63 ff 7d d9  b3 31 c3 f9 b0 9c f8 03  |.m..c.}..1......|
00000070  c2 2a 85 df 04 30 bc 9c  b4 1e b3 5f fc ad c3 97  |.*...0....._....|
00000080  77 00 1e ef 8a 4e e8 f9  f3 ae e6 10 89 a3 52 8d  |w....N........R.|
00000090  ff 52 87 7b 78 05 fc 61  5d cd 51 bf b8 0c aa ce  |.R.{x..a].Q.....|
000000a0  e5 f7 c9 58 f3 06 f3 4d  c1 f7 a1 b0 17 61 ee 7e  |...X...M.....a.~|
000000b0  be a0 09 80 62 51 30 62  b7 5e 71 16 c0 18 fe 59  |....bQ0b.^q....Y|
000000c0  7f 0c 66 ff 07 db 4a 0c  4f df e7 57 bc fe 02 83  |..f...J.O..W....|
000000d0  42 73 a5 f1 ec 6b 2c 9f  4f ff b6 5e 0e 56 b8 f2  |Bs...k,.O..^.V..|
000000e0  36 4b f1 04 5b ee 00 d8  7a af 9a 12 b0 0e c0 16  |6K..[...z.......|
000000f0  06 81 77 01 43 b9 b8 94  87 60 08 d1 7b 02 c0 a2  |..w.C....`..{...|
00000100  72 99 77 85 00 60 84 24  04 c9 21 27 2d 28 4b ef  |r.w..`.$..!'-(K.|
00000110  bb 74 64 bf 71 61 2d 6f  df f7 e6 71 cb 17 41 6d  |.td.qa-o...q..Am|
00000120  f6 65 77 c1 c1 57 f6 9c  07 29 fb 63 97 54 1a 8e  |.ew..W...).c.T..|
00000130  51 69 df 30 c4 fd f1 aa  f5 cd fd 92 b3 63 88 ea  |Qi.0.........c..|
00000140  b3 ba 9c 3e c4 18 fd 58  df 6d d8 20 47 b9 20 18  |...>...X.m. G. .|
00000150  01 40 03 d2 19 45 0d 18  b1 0f 63 be 6e e7 7f 6a  |.@...E....c.n..j|
00000160  9e c1 d7 94 06 00 50 06  e0 54 a5 b5 ca 00 bc 06  |......P..T......|
00000170  1b 10 c0 a6 74 fd dd ff  5b f7 76 27 d9 83 40 1f  |....t...[.v'..@.|
00000180  06 80 c0 35 03 1f a1 c9  38 cb 31 31 09 01 38 62  |...5....8.11..8b|
00000190  4a 0d 3f 27 f4 27 19 f1  b8 79 02 a4 a3 a3 75 39  |J.?'.'...y....u9|
000001a0  cc 3d c8 17 a6 59 6f d0  59 5f 7d b2 f1 a6 05 5f  |.=...Yo.Y_}...._|
000001b0  4c b0 07 1c 34 b4 24 33  04 17 9c 47 bc f8 00 fe  |L...4.$3...G....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 20 00 00 fe  |............ ...|
000001d0  ff ff 05 fe ff ff 02 c0  20 00 00 58 7e 03 00 00  |........ ..X~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

This is from natty.

---

### Post by jonkiribati on 2011-11-12
but your sdb is occupied by a Windows partition and some ext4 partitions if the ext4 partitions don't contain data you can remove them and then you'll get free space and you'll be able to repartitionnate. Or you can tell Ubuntu to use those partitions by indicating if you want to format or not.

---

### Post by urosg3 on 2011-11-12
> **jonkiribati said:**
>  Or you can tell Ubuntu to use those partitions by indicating if you want to format or not.

That was intention, but installer is unable to point sdb* as target, that is problem. How to force instaler to use sdb if no sdb in options

---

### Post by Rubi1200 on 2011-11-12
From the LiveCD/USB open GParted and take a screenshot of the drives to post here please.

Thanks.

---

### Post by urosg3 on 2011-11-12
Tnx to you mate. Screens are:

[[img]http://www.dodaj.rs/t/1K/11Z/3OdfO6So/screenshot-at-2011-11-12.jpg[/img]](http://www.dodaj.rs/?1K/11Z/3OdfO6So/screenshot-at-2011-11-12.png)
Installer, there is no way to select sdb*
[[img]http://www.dodaj.rs/t/3m/Um/2Uz5x3uk/screenshot-at-2011-11-12.jpg[/img]](http://www.dodaj.rs/?3m/Um/2Uz5x3uk/screenshot-at-2011-11-12.png)
Gparted sdb
[[img]http://www.dodaj.rs/t/2b/1T/48vVI1Cl/screenshot-at-2011-11-12.jpg[/img]](http://www.dodaj.rs/?2b/1T/48vVI1Cl/screenshot-at-2011-11-12.png)
Finally gparted sda

---

### Post by urosg3 on 2011-11-13
@Rubi1200
need any additional information? If so, I'm waiting:)

---

### Post by oldfred on 2011-11-13
The os-proper gets confused when it sees both grub & Windows.

Both sda1 & sdb1:
```
Boot files:        /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]
```

Try deleting the extra /boot folder with grub files in Windows top level or root.

I have had gparted & Ubuntu not see my sda with XP when XP still booted ok. I then ran chkdsk on the XP partition and it was fine in gparted. You might try running chkdsk on all NTFS partitions.

---

### Post by urosg3 on 2011-11-13
> **oldfred said:**
> The os-proper gets confused when it sees both grub & Windows.

Both sda1 & sdb1:
```
Boot files:        /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]
```

Try deleting the extra /boot folder with grub files in Windows top level or root.


No idea how, searching in wiki, and there is no similar situation. One more thing, Ubuntu 10.10 run normally, with all options in installer

---

### Post by urosg3 on 2011-11-14
Still no solution here, is there any way?

---

### Post by oldfred on 2011-11-14
Even though my XP booted from sda, I have had gparted not see sda. I then ran chkdsk on the NTFS partition in sda and gparted would see it. (XP booted a bit faster also.)

---

### Post by urosg3 on 2011-11-14
Hmm, I do chkdsk twice and no result. Again, Maverick installer work normally...

---

### Post by oldfred on 2011-11-14
From liveCD does gparted see it, and just the installer does not? Or do both gparted & the installer not see sdb.

---

### Post by urosg3 on 2011-11-14
Just installer, I`m able to mount any partition from Nautilus, Gparted listed them all, only installer, and problem is, I need installer :)

---

### Post by oldfred on 2011-11-14
I know there is a bug in 12.04 where it shows no partitions at all. But there is a work around. I installed 11.10 in my sdd drive and it showed all drives and partitions, but I partition in advance. You could try setting up partitions in advance?

I might try the alternative installer. It is text based, but otherwise the same system gets installed.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

