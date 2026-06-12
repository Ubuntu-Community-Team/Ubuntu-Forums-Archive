---
title: "Ubuntu 12.04 + Raid0  + Windows 7 not loading"
date: 2012-05-06
forum: General Help
---

### Post by TheDoug on 2012-05-06
Hi, please someone help me....

(Sorry for my english)

Hi, I have a Pc with 2 Hd (1Tb each) on Raid0. I had a Windows 7 64bits working for several months. 
When I installed the Windows I let a 100Gb partition empty to install Ubuntu someday. 
I was using Linux on a Virtualbox, but this week I tried to install Ubuntu 12.04 in this 100Gb partition.

I used the Ubuntu alternate cd, because the 'normal' cd was giving me trouble with the Raid0. The grub installation always reported a error. After a lot of work I found that I nedded to install grub on partition /dev/mapper/isw_chjbfeec_DougRaid1 (see Bootinfo below).

The Windows installation created a 100Mb boot partition, so I needed to install grub in this partition.

Now I have the Ubuntu working 100% ok. 

The problem is, the Windows is not booting! The windows option is present on the grub menu, but when I choose the windows option there is a black screen and after that the grub is reloaded.

My Bootinfo is:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_chjbfeec_DougRaid 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

isw_chjbfeec_DougRaid1: ________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       isw_chjbfeec_DougRaid1 and looks at sector 3841862992 
                       of the same hard drive for core.img. core.img is at 
                       this location and looks for (,msdos5)/boot/grub on 
                       this drive. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

isw_chjbfeec_DougRaid2: ________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

isw_chjbfeec_DougRaid3: ________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

isw_chjbfeec_DougRaid5: ________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_chjbfeec_DougRaid6: ________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 3,686,402,047 3,686,195,200   7 NTFS / exFAT / HPFS
/dev/sda3       3,686,402,558 3,907,039,743   220,637,186   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda

Drive: isw_chjbfeec_DougRaid _____________________________________________________________________

Disk /dev/mapper/isw_chjbfeec_DougRaid: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_chjbfeec_DougRaid1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_chjbfeec_DougRaid2            206,848 3,686,402,047 3,686,195,200   7 NTFS / exFAT / HPFS
/dev/mapper/isw_chjbfeec_DougRaid3      3,686,402,558 3,907,039,743   220,637,186   5 Extended
/dev/mapper/isw_chjbfeec_DougRaid5      3,686,402,560 3,881,876,479   195,473,920  83 Linux
/dev/mapper/isw_chjbfeec_DougRaid6      3,881,876,992 3,907,039,743    25,162,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_chjbfeec_DougRaid1 C89C73D19C73B910                       ntfs       Reservado pelo Sistema
/dev/mapper/isw_chjbfeec_DougRaid2 6830883A3088116C                       ntfs       
/dev/mapper/isw_chjbfeec_DougRaid5 bbab868a-ea53-4be3-ba7d-2737fe6cb24c   ext4       
/dev/mapper/isw_chjbfeec_DougRaid6 7a830a3c-88fb-4cba-80dc-f32e08abfd5b   swap       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sr0                                                iso9660    Windows7x86x64SK

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_chjbfeec_DougRaid
isw_chjbfeec_DougRaid1
isw_chjbfeec_DougRaid2
isw_chjbfeec_DougRaid3
isw_chjbfeec_DougRaid5
isw_chjbfeec_DougRaid6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/isw_chjbfeec_DougRaid5 /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Windows7x86x64SK  iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


================= isw_chjbfeec_DougRaid1/grldr embedded menu: ==================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

================== isw_chjbfeec_DougRaid5/boot/grub/grub.cfg: ==================

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
set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
  search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=bbab868a-ea53-4be3-ba7d-2737fe6cb24c ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=bbab868a-ea53-4be3-ba7d-2737fe6cb24c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=bbab868a-ea53-4be3-ba7d-2737fe6cb24c ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=bbab868a-ea53-4be3-ba7d-2737fe6cb24c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/mapper/isw_chjbfeec_DougRaid3,msdos1)'
	search --no-floppy --fs-uuid --set=root bbab868a-ea53-4be3-ba7d-2737fe6cb24c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_chjbfeec_DougRaid1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(sda,msdos1)'
	search --no-floppy --fs-uuid --set=root C89C73D19C73B910
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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

====================== isw_chjbfeec_DougRaid5/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_chjbfeec_DougRaid5 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_chjbfeec_DougRaid6 none            swap    sw              0       0
--------------------------------------------------------------------------------

========== isw_chjbfeec_DougRaid5: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
xz: (stdin): Compressed data is corrupt
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


```

How we can see the Windows part at grub is:


```
--class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(sda,msdos1)'
	search --no-floppy --fs-uuid --set=root C89C73D19C73B910
	chainloader +1
}
```

I tried a lot of combinations at the line:

set root='(sda,msdos1)'

, but no success

I tried to change uuid to the /dev/mapper/isw_chjbfeec_DougRaid2 uuid, but the grub reports a error.

I dont know what to do now. 

I really need to boot my windows partition.

Someone knows what to do?

Thanks........

---

