---
title: "windows 7 &quot;bumped&quot; my ubuntu partition. how to recover data?"
date: 2010-07-06
forum: General Help
---

### Post by j-d33zy on 2010-07-06
Hi, I installed windows 7 over an existing xp partition, and windows 7 made a 100 mb partition as some sort of windows swap space thing. this basically made my ubuntu partition unreadable, even with gparted. any help as to how to recover this data?

---

### Post by j-d33zy on 2010-07-07
Bump??

---

### Post by Darkness Des on 2010-07-07
If it helps, I'm about 95% sure that the 100 MB partition is the Bootloader.

---

### Post by philinux on 2010-07-07
> **j-d33zy said:**
> Hi, I installed windows 7 over an existing xp partition, and windows 7 made a 100 mb partition as some sort of windows swap space thing. this basically made my ubuntu partition unreadable, even with gparted. any help as to how to recover this data?

Use this and post back the results.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Windows may have only eaten grub2.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by j-d33zy on 2010-07-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   107,421,695   107,419,648  83 Linux
/dev/sda2         107,423,742   234,209,279   126,785,538   5 Extended
/dev/sda5         107,423,744   111,327,231     3,903,488  82 Linux swap / Solaris
/dev/sda6         111,329,280   234,209,279   122,880,000  83 Linux
/dev/sda4    *    234,211,635   312,576,704    78,365,070  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   122,879,999   122,673,152   7 HPFS/NTFS
/dev/sdb3         122,881,185   625,137,344   502,256,160   5 Extended
/dev/sdb5         615,064,653   625,137,344    10,072,692  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        66317a7c-6aed-437d-a6c5-e26b3602e53c   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda4        4fc9a97e-5bef-407e-8693-41941ecd0afe   ext3                                     
/dev/sda5        ff2f2c29-3381-4b98-84ff-203eb1c1d6bc   swap                                     
/dev/sda6        6d4f0f61-9117-4451-9087-2cc91ce0a4ca   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CE30F74E30F73BD1                       ntfs       System Reserved               
/dev/sdb2        DA26FCBD26FC9BA7                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        b9c505a5-f478-4e53-9f09-52e5ca7f848e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set a7292a5a-e1b1-4d1b-af5b-7911f8deb9c2
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=a7292a5a-e1b1-4d1b-af5b-7911f8deb9c2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set a7292a5a-e1b1-4d1b-af5b-7911f8deb9c2
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=a7292a5a-e1b1-4d1b-af5b-7911f8deb9c2 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff2f2c29-3381-4b98-84ff-203eb1c1d6bc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
  39.3GB: boot/grub/grub.cfg
   2.5GB: boot/initrd.img-2.6.32-21-generic
  39.3GB: boot/initrd.img-2.6.32-22-generic
   2.4GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: boot/vmlinuz-2.6.32-22-generic
  39.3GB: initrd.img
   2.5GB: initrd.img.old
   2.4GB: vmlinuz
   2.4GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6d4f0f61-9117-4451-9087-2cc91ce0a4ca ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6d4f0f61-9117-4451-9087-2cc91ce0a4ca ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6d4f0f61-9117-4451-9087-2cc91ce0a4ca
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=4fc9a97e-5bef-407e-8693-41941ecd0afe ro splash quiet
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=4fc9a97e-5bef-407e-8693-41941ecd0afe ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6d4f0f61-9117-4451-9087-2cc91ce0a4ca /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff2f2c29-3381-4b98-84ff-203eb1c1d6bc none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  66.4GB: boot/grub/core.img
  66.4GB: boot/grub/grub.cfg
  66.4GB: boot/initrd.img-2.6.32-21-generic
  66.4GB: boot/vmlinuz-2.6.32-21-generic
  66.4GB: initrd.img
  66.4GB: vmlinuz

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
search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=4fc9a97e-5bef-407e-8693-41941ecd0afe ro   splash quiet
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=4fc9a97e-5bef-407e-8693-41941ecd0afe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4fc9a97e-5bef-407e-8693-41941ecd0afe
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 66317a7c-6aed-437d-a6c5-e26b3602e53c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=66317a7c-6aed-437d-a6c5-e26b3602e53c ro single
	initrd /boot/initrd.img-2.6.32-21-generic
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=4fc9a97e-5bef-407e-8693-41941ecd0afe /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff2f2c29-3381-4b98-84ff-203eb1c1d6bc none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 156.3GB: boot/grub/core.img
 156.3GB: boot/grub/grub.cfg
 156.3GB: boot/initrd.img-2.6.32-22-generic
 156.3GB: boot/vmlinuz-2.6.32-22-generic
 156.3GB: initrd.img
 156.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  74 b7 87 39 42 e4 f5 59  32 7c b3 e3 6d 18 cf 8f  |t..9B..Y2|..m...|
00000010  44 40 34 9f 1f e9 3b 77  8b 45 d0 1f f2 8f 4a a4  |D@4...;w.E....J.|
00000020  76 f2 3e 8f 8c 6b 65 2f  f6 fd 7b ad 09 e8 f5 19  |v.>..ke/..{.....|
00000030  9e db 6a bf 8b 80 a7 a5  9a 32 6d 93 70 f6 17 7b  |..j......2m.p..{|
00000040  5b 8a 17 c3 e5 c3 bb b3  b1 67 fa 24 95 8a f8 42  |[........g.$...B|
00000050  71 3b 0b e5 91 a6 63 30  f7 70 d5 95 34 ba 9e 1f  |q;....c0.p..4...|
00000060  64 43 71 1f a9 96 43 11  fe 7f b7 26 b7 42 22 3b  |dCq...C....&.B";|
00000070  3e 8c 23 a6 67 73 70 a7  52 64 30 5f 91 78 f1 9d  |>.#.gsp.Rd0_.x..|
00000080  36 9b 4e 77 5b 7e 12 f4  d0 cf b6 4b de f2 4c 6b  |6.Nw[~.....K..Lk|
00000090  94 87 ca 39 9b da 65 b6  fd 5a 73 72 4d 98 1b 93  |...9..e..ZsrM...|
000000a0  2f 78 e1 9d 1f 8a 60 8b  f7 df 4b 37 7b dd bb 81  |/x....`...K7{...|
000000b0  1c d4 b0 ed bf dc 93 d6  2e 7e 90 0c ec f4 2e 2e  |.........~......|
000000c0  f2 9f aa bd 9d 50 c4 ee  71 88 88 f7 d3 d3 76 db  |.....P..q.....v.|
000000d0  6e 49 32 35 71 96 5f b6  47 87 e7 04 7b c9 bf 2e  |nI25q._.G...{...|
000000e0  9a d3 84 e4 6c 4f a3 f3  37 61 b7 ff d9 8d 29 d6  |....lO..7a....).|
000000f0  c0 de 02 a8 bd c9 82 3c  bb ba c7 ea 69 82 df de  |.......<....i...|
00000100  4b c9 14 36 dd cb 57 cf  59 11 be dd b9 bb cd c9  |K..6..W.Y.......|
00000110  65 a8 36 06 7b 22 d1 52  02 ed 2c 70 8c 11 e2 e4  |e.6.{".R..,p....|
00000120  b3 ed 8f 73 7b b3 d1 04  53 eb 5d fb 26 0e bd d9  |...s{...S.].&...|
00000130  77 7f 7e d3 30 14 ae 1f  aa 93 36 dc ab 46 d0 bf  |w.~.0.....6..F..|
00000140  f7 3f fc 54 af 17 30 6c  10 c0 ea 28 0f e2 b4 31  |.?.T..0l...(...1|
00000150  ad 96 c1 e5 8c 70 78 8f  55 1d 9e 51 ee 2a c5 52  |.....px.U..Q.*.R|
00000160  b7 e5 4d 51 9d 5a fb 14  eb 7f d7 ab b2 73 92 2d  |..MQ.Z.......s.-|
00000170  71 09 38 d5 30 b5 53 67  f9 0b 54 fa 0c 24 dd 85  |q.8.0.Sg..T..$..|
00000180  1d 9c 37 6b 7c 60 da bc  cb 39 d2 24 c3 ea dd d6  |..7k|`...9.$....|
00000190  f0 ef c7 78 f5 7c b4 f5  fe cb 24 9a 59 2e 1b 19  |...x.|....$.Y...|
000001a0  85 a9 c9 19 97 7b 77 ef  50 5d ef 5b 21 37 e2 24  |.....{w.P].[!7.$|
000001b0  f1 b8 5b 8f b3 1b bb 72  f3 87 1e 98 5d fa 00 fe  |..[....r....]...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 08 53 07 00 00  |........;...S...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```


Thanks for the help, its much appreciated. the drive in question is sdb, sda is a separate drive im using. cool script too!

---

### Post by oldfred on 2010-07-08
I have not needed it but many recommend testdisk to recover or repair partition issues.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

It looks like you have space in you extended, was that the linux partition. If so I think testdisk will find it and let you store it.

---

