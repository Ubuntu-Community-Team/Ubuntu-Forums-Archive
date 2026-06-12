---
title: "Error from grub while attempting boot"
date: 2011-09-30
forum: General Help
---

### Post by Ralph L on 2011-09-30
I put a new 160gb drive in my Compaq Presario 2100 (2195us) to be exact.  It has worked fine until I added a 4th ubuntu operating system partition.  (I am having trouble getting wifi to work and have been trying several alternatives--hence the large numbers of os partitions.)  When I added the 4th partition and tried to boot I got error: out of disk Grub rescue.  Upon investigation I found that the bios had a 137gb limit in it.  So I set up a boot partition (sda3) right after my XP partition.  I set the boot flag on sda3, set sda3 to /boot, and under "Advanced" on next to last step in the install, set to install grub on sda3.  Then I completed the install.  Still got the message error: no such partition Grub rescue.  So having a separate boot partition at a low address didn't help.

I then deleted one of my os partitions and reinstalled lucid on one of the other partitions.  Again I set the boot flag for sda3, set sda3 to /boot, and under "Advanced" set to reload grub to sda3.  Then I completed the installation.  On reboot I got error: could not find partition Grub rescue.  I don't know what to do now.

Here is the output of boot_info_script.sh.  

Any help would be appreciated.

Ralph

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 47320943 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for /grub.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    41,881,454    41,881,392   7 NTFS / exFAT / HPFS
/dev/sda2         170,160,541   312,576,704   142,416,164   5 Extended
/dev/sda5         170,160,543   190,836,134    20,675,592  83 Linux
/dev/sda6         190,836,198   211,495,724    20,659,527  83 Linux
/dev/sda7         211,495,788   231,834,014    20,338,227  83 Linux
/dev/sda3    *     41,881,455    50,861,789     8,980,335  83 Linux
/dev/sda4          50,861,790    55,151,144     4,289,355  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4E2C2F27143FDAEE                       ntfs       
/dev/sda3        24097c43-29d8-49aa-bcaf-61f9f2a44ad0   ext3       Boot_Partition
/dev/sda4        241341ec-4e8e-4956-a39e-1e8475e75cc3   swap       
/dev/sda5        ded2c007-b53c-4e99-a513-6e394c6e49f0   ext3       Lucid_Lynx
/dev/sda6        793ad018-3bd8-4b3b-9cac-37d8d581707a   ext4       Lucid_Lynx_B
/dev/sda7        df61c938-6392-4733-a465-afd44de3a68a   ext4       Lucid_Lynx_A

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Boot_Partition    ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/Lucid_Lynx_B      ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4E2C2F27143FDAEE
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

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
UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=3cdda27e-30d3-4ed3-8628-a05fc4833c32 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  81.655463696 = 87.676886528   boot/grub/core.img                             1
  81.662391186 = 87.684324864   boot/grub/grub.cfg                             1
  81.708858013 = 87.734218240   boot/initrd.img-2.6.32-21-generic              3
  81.716792583 = 87.742737920   boot/initrd.img-2.6.32-33-generic              4
  81.688590527 = 87.712456192   boot/vmlinuz-2.6.32-21-generic                 2
  81.720836163 = 87.747079680   boot/vmlinuz-2.6.32-33-generic                 2
  81.716792583 = 87.742737920   initrd.img                                     4
  81.708858013 = 87.734218240   initrd.img.old                                 3
  81.720836163 = 87.747079680   vmlinuz                                        2
  81.688590527 = 87.712456192   vmlinuz.old                                    2

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
# / was on /dev/sda6 during installation
UUID=793ad018-3bd8-4b3b-9cac-37d8d581707a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=24097c43-29d8-49aa-bcaf-61f9f2a44ad0 /boot           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=241341ec-4e8e-4956-a39e-1e8475e75cc3 none            swap    sw              0       0
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
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
search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4e2c2f27143fdaee
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ec9645aa-f136-4a08-8783-45f75c69d9f1
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=ec9645aa-f136-4a08-8783-45f75c69d9f1 ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ec9645aa-f136-4a08-8783-45f75c69d9f1
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=ec9645aa-f136-4a08-8783-45f75c69d9f1 ro single
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ec9645aa-f136-4a08-8783-45f75c69d9f1
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ec9645aa-f136-4a08-8783-45f75c69d9f1 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ec9645aa-f136-4a08-8783-45f75c69d9f1
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ec9645aa-f136-4a08-8783-45f75c69d9f1 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b6fe7fd1-05a2-47af-9bf6-bb40c2809e3a
	linux /boot/memtest86+.bin 
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
UUID=df61c938-6392-4733-a465-afd44de3a68a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=3cdda27e-30d3-4ed3-8628-a05fc4833c32 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 102.999364853 = 110.594725888  boot/grub/core.img                             1
 103.001653671 = 110.597183488  boot/grub/grub.cfg                             1
 103.219079971 = 110.830643200  boot/initrd.img-2.6.32-21-generic              1
 103.107961655 = 110.711330816  boot/vmlinuz-2.6.32-21-generic                 1
 103.219079971 = 110.830643200  initrd.img                                     1
 103.107961655 = 110.711330816  vmlinuz                                        1

============================= sda3/grub/grub.cfg: ==============================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 793ad018-3bd8-4b3b-9cac-37d8d581707a
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 24097c43-29d8-49aa-bcaf-61f9f2a44ad0
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 24097c43-29d8-49aa-bcaf-61f9f2a44ad0
	linux	/vmlinuz-2.6.32-21-generic root=UUID=793ad018-3bd8-4b3b-9cac-37d8d581707a ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 24097c43-29d8-49aa-bcaf-61f9f2a44ad0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=793ad018-3bd8-4b3b-9cac-37d8d581707a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 24097c43-29d8-49aa-bcaf-61f9f2a44ad0
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 24097c43-29d8-49aa-bcaf-61f9f2a44ad0
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4e2c2f27143fdaee
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro single
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ded2c007-b53c-4e99-a513-6e394c6e49f0
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ded2c007-b53c-4e99-a513-6e394c6e49f0 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set df61c938-6392-4733-a465-afd44de3a68a
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=df61c938-6392-4733-a465-afd44de3a68a ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.564410686 = 24.228351488   grub/core.img                                  1
  22.517516613 = 24.177999360   grub/grub.cfg                                  1
  20.079623699 = 21.560331776   initrd.img-2.6.32-21-generic                   3
  19.984656811 = 21.458361856   vmlinuz-2.6.32-21-generic                      2


```

---

### Post by Ralph L on 2011-10-04
I got booting to work by setting up the boot partition (after installation from the Live cd, but when still running on the Live cd) by following the directions on setting up a separate boot partition for grub2  after installation given in [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall) .  However, in the future I would like to be able to set up the boot partition **during install**.  As I indicated in the #1 above I tried to do this originally, but failed.  I created the boot partition successfully, but I was unable to set it up correctly.

Does anybody know how correctly set up a separate boot partition (to work around the 137GB limit in my bios) **during install from the LiveCD**.

Thanks
Ralph

---

### Post by oldfred on 2011-10-04
You can just create a partition at the front of the drive or if XP is small enough then just after XP. If multiple installs you cannot share a /boot but would need one for each system.

If only having one install with XP, you can create a small system partition of 20GB and use the rest of the drive for /home and a shared NTFS partition for data to share between systems. Data can be beyond the 137Gb, just the entire boot or system has to be inside.

Many have XP in smaller partitions (20 to 40Gb), Ubuntu's / (root) in a smaller partition (10 to 20GB) and then the rest of the drive whether primary partitions or logical partitions (does not matter) as data /home & shared as NTFS. Then the two bootable partitions are at the front of the drive.

---

### Post by Ralph L on 2011-10-05
OldFred,

Thank you very much for responding.

Are you saying that using a separate boot partition near the beginning of the drive does not allow ubuntu system partitions above 137GB?  I run with multiple ubuntu system partitions so that I can experiment with different alternatives without messing up the system partition I really use. In addition, I use a singe "data partition" that can be mounted in any of my system partitions.  

Anyway I like the freedom to put my system partitions any place on the disk.  I had hoped that creating a boot partition near the front of the disk would allow system partitions to be placed near the tail end of the disk.  Are you saying that this won't work?  And I had hoped that I could do this boot partition setup at install time and not have to type in a bunch of commands to set up that boot partition.  Are you saying that the LiveCD installation option to mark a partition as /boot doesn't really make it a shared boot partition?

Thanks
Ralph

---

### Post by oldfred on 2011-10-05
You have to create a /boot at the beginning of the drive for every install if you want to have a system at the end of the drive. A shared /boot may have version issues on grub, grub2 or even the kernels.

If you just put all the data at the end of the drive then there is no issue. Since I have all my data in shared data partitions, I only use 20 or 25GB for / (root). In the first 137GB I can fit a lot of systems and leave the last 30GB for data.

---

