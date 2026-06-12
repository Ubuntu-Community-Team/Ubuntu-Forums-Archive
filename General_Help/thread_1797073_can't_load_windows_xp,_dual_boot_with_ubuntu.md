---
title: "can't load windows xp, dual boot with ubuntu"
date: 2011-07-04
forum: General Help
---

### Post by pelikanu on 2011-07-04
when i choose windows xp from grub menu it appears just cursor, and in few seconds the grub menu appears again and after another choosing, it loads ubuntu.

the same thing like in this thread happens to me, but following the solution over there with update-grub it hasn't solved the problem for me.

i run also the script from there, and my results are:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 294650488 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 7 for (,msdos7)/boot/grub. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v) is installed in the boot sector of 
                       sda2 and looks at sector 291584512 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    63,488,879    63,488,817   7 NTFS / exFAT / HPFS
/dev/sda2    *     63,488,941   312,559,615   249,070,675   f W95 Extended (LBA)
/dev/sda5          63,488,943   282,631,544   219,142,602   7 NTFS / exFAT / HPFS
/dev/sda6         282,632,192   286,840,831     4,208,640  82 Linux swap / Solaris
/dev/sda7         286,842,880   298,471,423    11,628,544  83 Linux
/dev/sda8         298,473,472   312,559,615    14,086,144  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4234609C346094A7                       ntfs       
/dev/sda5        0ADCE142DCE12921                       ntfs       
/dev/sda6        e1cc1602-b6d4-417f-aae6-19665fa4b39d   swap       
/dev/sda7        113d1f11-ae25-4acc-be2c-c4118c7eac1e   ext3       
/dev/sda8        6b94b43c-1ea6-4ac3-a7c5-420c4fbe699f   ext3       
/dev/sdb1        0C687AE7687ACF48                       ntfs       hdd

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/4234609C346094A7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda8        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/hdd               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4234609C346094A7
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
UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=6b94b43c-1ea6-4ac3-a7c5-420c4fbe699f /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e1cc1602-b6d4-417f-aae6-19665fa4b39d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.582054138 = 149.875089408  boot/grub/core.img                             1
 139.580787659 = 149.873729536  boot/grub/grub.cfg                             1
 139.568580627 = 149.860622336  boot/initrd.img-2.6.35-22-generic              7
 139.560913086 = 149.852389376  boot/initrd.img-2.6.35-30-generic              5
 139.539279938 = 149.829160960  boot/vmlinuz-2.6.35-22-generic                 3
 139.545921326 = 149.836292096  boot/vmlinuz-2.6.35-30-generic                 4
 139.560913086 = 149.852389376  initrd.img                                     5
 139.568580627 = 149.860622336  initrd.img.old                                 7
 139.545921326 = 149.836292096  vmlinuz                                        4
 139.539279938 = 149.829160960  vmlinuz.old                                    3


```

i would appreciate if you could help me. i don't want to reinstall windows again. thank you very much

---

### Post by wildmanne39 on 2011-07-04
> **pelikanu said:**
> when i choose windows xp from grub menu it appears just cursor, and in few seconds the grub menu appears again and after another choosing, it loads ubuntu.

the same thing like in this thread happens to me, but following the solution over there with update-grub it hasn't solved the problem for me.

i run also the script from there, and my results are:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 294650488 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 7 for (,msdos7)/boot/grub. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v) is installed in the boot sector of 
                       sda2 and looks at sector 291584512 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    63,488,879    63,488,817   7 NTFS / exFAT / HPFS
/dev/sda2    *     63,488,941   312,559,615   249,070,675   f W95 Extended (LBA)
/dev/sda5          63,488,943   282,631,544   219,142,602   7 NTFS / exFAT / HPFS
/dev/sda6         282,632,192   286,840,831     4,208,640  82 Linux swap / Solaris
/dev/sda7         286,842,880   298,471,423    11,628,544  83 Linux
/dev/sda8         298,473,472   312,559,615    14,086,144  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4234609C346094A7                       ntfs       
/dev/sda5        0ADCE142DCE12921                       ntfs       
/dev/sda6        e1cc1602-b6d4-417f-aae6-19665fa4b39d   swap       
/dev/sda7        113d1f11-ae25-4acc-be2c-c4118c7eac1e   ext3       
/dev/sda8        6b94b43c-1ea6-4ac3-a7c5-420c4fbe699f   ext3       
/dev/sdb1        0C687AE7687ACF48                       ntfs       hdd

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/4234609C346094A7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda8        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/hdd               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 113d1f11-ae25-4acc-be2c-c4118c7eac1e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4234609C346094A7
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
UUID=113d1f11-ae25-4acc-be2c-c4118c7eac1e /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=6b94b43c-1ea6-4ac3-a7c5-420c4fbe699f /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e1cc1602-b6d4-417f-aae6-19665fa4b39d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.582054138 = 149.875089408  boot/grub/core.img                             1
 139.580787659 = 149.873729536  boot/grub/grub.cfg                             1
 139.568580627 = 149.860622336  boot/initrd.img-2.6.35-22-generic              7
 139.560913086 = 149.852389376  boot/initrd.img-2.6.35-30-generic              5
 139.539279938 = 149.829160960  boot/vmlinuz-2.6.35-22-generic                 3
 139.545921326 = 149.836292096  boot/vmlinuz-2.6.35-30-generic                 4
 139.560913086 = 149.852389376  initrd.img                                     5
 139.568580627 = 149.860622336  initrd.img.old                                 7
 139.545921326 = 149.836292096  vmlinuz                                        4
 139.539279938 = 149.829160960  vmlinuz.old                                    3


```

i would appreciate if you could help me. i don't want to reinstall windows again. thank you very much
Hi, I am not an expert but I can see you have two different versions of grub installed, and the second one has some missing files which may be a good thing, because I am surprised you can boot at all, you have windows boot partition on your internal hard drive and your external hard drive that may be causing you a problem, how many operating systems do you have installed and which ones? You might want to unplug your usb drive and then try to boot windows, then post back here the results.

---

