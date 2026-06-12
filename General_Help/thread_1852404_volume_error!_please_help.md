---
title: "volume error! please help"
date: 2011-09-30
forum: General Help
---

### Post by zero.crash.overwrite on 2011-09-30
hello i am new to ubuntu but has been using this os for about two months now.... i have a problem... whenever i try to mount a partition it says:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so, i followed the instruction and it said:

[  558.815207] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  559.046973] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  559.311423] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  562.544906] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  573.572212] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  735.709361] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  949.802159] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  950.898169] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  951.154207] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.
[  951.418176] EXT3-fs (sda3: error: can't find ext3 filesystem on dev sda3.

  The problem is that the filesystem is not ext3 but ntfs. i checked the disk utility it said the filesystem is NTFS but the Storage Device Manager says ext3.... please help... Also in windows the partition works fine.

---

### Post by yetiman64 on 2011-09-30
> **zero.crash.overwrite said:**
> ...The problem is that the filesystem is not ext3 but ntfs. i checked the disk utility it said the filesystem is NTFS but the Storage Device Manager says ext3.... please help... Also in windows the partition works fine.

If you running Ubuntu installed via Wubi then that can occur. 

To clarify for those helping here. **Are you running a Wubi install of Ubuntu ?**

Just for your info a Wubi install of Ubuntu places the Ubuntu ext3 filesystem into a file located on the Windows NTFS filesystem.

---

### Post by Rubi1200 on 2011-09-30
Hi and welcome to the forums zero.crash.overwrite :)

Please help us troubleshoot the problem by posting the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by zero.crash.overwrite on 2011-10-12
I am using ubuntu 10.10

---

### Post by zero.crash.overwrite on 2011-10-12
> **Rubi1200 said:**
> Hi and welcome to the forums zero.crash.overwrite :)

Please help us troubleshoot the problem by posting the results of the boot info script.

There is a link at the bottom of my post with instructions.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/burg/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda2         102,398,310   625,121,279   522,722,970   f W95 Extended (LBA)
/dev/sda5         102,398,373   286,712,054   184,313,682   7 NTFS / exFAT / HPFS
/dev/sda6         286,712,118   471,025,799   184,313,682   7 NTFS / exFAT / HPFS
/dev/sda7         471,025,863   547,061,444    76,035,582   7 NTFS / exFAT / HPFS
/dev/sda3         547,061,508   623,081,024    76,019,517   7 NTFS / exFAT / HPFS
/dev/sda9         623,081,088   625,121,279     2,040,192   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       77d154de-ed46-4e6a-b825-582e1fc6246f   ext4       
/dev/sda1        8E1C68CE1C68B2BF                       ntfs       
/dev/sda5        8C10E10410E0F5DC                       ntfs       c
/dev/sda6        98ACEB34ACEB0C16                       ntfs       b
/dev/sda7        F464F3ED64F3B08A                       ntfs       a
/dev/sda3        4C6C06D76C06BBA8                       ntfs       d
/dev/sda9        0A08A10408A0EFBD                       ntfs       e

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/sda6              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/sda7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda9        /media/sda9              fuseblk    (rw,nosuid,nodev,allow_other,blksize=1024,default_permissions)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

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
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8E1C68CE1C68B2BF
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8E1C68CE1C68B2BF
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8E1C68CE1C68B2BF
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=8E1C68CE1C68B2BF loop=/ubuntu/disks/root.disk ro   quiet splash nolapic_timer
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8E1C68CE1C68B2BF
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=8E1C68CE1C68B2BF loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8E1C68CE1C68B2BF
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Sabayon Linux x86 (genkernel-x86-2.6.31-sabayon) (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7c079f27-de2a-42a3-a414-80cde3d1d097
	linux /boot/kernel-genkernel-x86-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=7c079f27-de2a-42a3-a414-80cde3d1d097 dolvm quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1
	initrd /boot/initramfs-genkernel-x86-2.6.31-sabayon
}
menuentry "Sabayon Linux x86 (genkernel-x86-2.6.31-sabayon) (safe mode) (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 7c079f27-de2a-42a3-a414-80cde3d1d097
	linux /boot/kernel-genkernel-x86-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=7c079f27-de2a-42a3-a414-80cde3d1d097 dolvm init=/linuxrc CONSOLE=/dev/tty1 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86-2.6.31-sabayon
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

======================== sda1/Wubi/boot/burg/burg.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(/dev/loop0)'
search --no-floppy --fs-uuid --set 77d154de-ed46-4e6a-b825-582e1fc6246f
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(/dev/loop0)'
	search --no-floppy --fs-uuid --set 77d154de-ed46-4e6a-b825-582e1fc6246f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=77d154de-ed46-4e6a-b825-582e1fc6246f ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(/dev/loop0)'
	search --no-floppy --fs-uuid --set 77d154de-ed46-4e6a-b825-582e1fc6246f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=77d154de-ed46-4e6a-b825-582e1fc6246f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8e1c68ce1c68b2bf
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Sabayon Linux x86 (genkernel-x86-2.6.31-sabayon) (on /dev/sda3)" --class gentoo --class os --group group_/dev/sda3 {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 7c079f27-de2a-42a3-a414-80cde3d1d097
	linux /boot/kernel-genkernel-x86-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=7c079f27-de2a-42a3-a414-80cde3d1d097 dolvm quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1
	initrd /boot/initramfs-genkernel-x86-2.6.31-sabayon
}
menuentry "Sabayon Linux x86 (genkernel-x86-2.6.31-sabayon) (safe mode) (on /dev/sda3)" --class gentoo --class os --group group_/dev/sda3 {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 7c079f27-de2a-42a3-a414-80cde3d1d097
	linux /boot/kernel-genkernel-x86-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=7c079f27-de2a-42a3-a414-80cde3d1d097 dolvm init=/linuxrc CONSOLE=/dev/tty1 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86-2.6.31-sabayon
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  nodev,noexec,nosuid                   0  0  
/host/ubuntu/disks/root.disk  /            ext4  loop,errors=remount-ro                0  1  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                               0  0  
/dev/sda5                     /media/sda5  ntfs  nls=iso8859-1,umask=000               0  0  
/dev/sda6                     /media/sda6  ntfs  nls=iso8859-1,umask=000               0  0  
/dev/sda7                     /media/sda7  ntfs  nls=iso8859-1,umask=000               0  0  
/dev/sda3                     /media/d  ext3  errors=remount-ro,users,noauto,nodev  0  0  
/dev/sda9                     /media/sda9  ntfs  nls=iso8859-1,umask=000               0  0  
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  13.186195374 = 14.158569472   boot/burg/burg.cfg                             1
   6.688385010 = 7.181598720    boot/burg/core.img                             1
  13.193969727 = 14.166917120   boot/grub/grub.cfg                             1
  12.400661469 = 13.315108864   boot/initrd.img-2.6.35-22-generic              2
   6.472747803 = 6.950060032    boot/vmlinuz-2.6.35-22-generic                 1
  12.400661469 = 13.315108864   initrd.img                                     2
   6.472747803 = 6.950060032    vmlinuz                                        1

---

