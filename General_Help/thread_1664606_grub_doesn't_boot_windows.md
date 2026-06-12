---
title: "grub doesn't boot windows"
date: 2011-01-11
forum: General Help
---

### Post by TuTToWeB on 2011-01-11
Hi to all,
I've installed maverick on an aspire one 751h, over a previous 9.04 installation.
With the latter ubuntu, I didn't get any boot problems.
With maverick, I got this problem and I'm not able to boot neither windows xp, nor recovery partition. I've just figured out this issue and I can't resolve it.
This guy [http://ubuntuforums.org/showthread.php?t=1564023](http://ubuntuforums.org/showthread.php?t=1564023) got the same issue of mine, but there's no solution on that thread. Moreover, I've run boot script and I'm posting the result here.
Thank you in advance

---

### Post by Synthetic Sam on 2011-01-11
The boot script looks like everything is set up correctly, you have grub2 installed to the mbr of the first disk, and the grub.cfg lists both Windows Vista (recovery partition) and Windows XP as recognised boot options.  At what point is the boot failing? After selecting Windows XP in grub, or before that point?

[edit] [COLOR="Silver"]After further inspection of your boot script, it seems that the bootable flag is set on the Win XP partition, while the MBR points at /dev/sda3 (the ubuntu partition) for boot.[/COLOR]  This may not be causing any problems, my boot drive looks like this, with the windows boot partition flagged as bootable, and my /boot on sda5:

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15b083f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       34624   278008558    7  HPFS/NTFS
/dev/sda3           34624       60802   210273281    5  Extended
/dev/sda5           34624       46781    97655808   83  Linux
/dev/sda6           46782       58939    97654784   83  Linux
/dev/sda7           58939       60802    14960640   82  Linux swap / Solaris

```

After further searching around, it would appear that Grub2 pretty much ignores bootable flags, so with that in the MBR like you have, then the bootable flag is not an issue.

---

### Post by TuTToWeB on 2011-01-11
> **Synthetic Sam said:**
> The boot script looks like everything is set up correctly, you have grub2 installed to the mbr of the first disk, and the grub.cfg lists both Windows Vista (recovery partition) and Windows XP as recognised boot options.  At what point is the boot failing? After selecting Windows XP in grub, or before that point?

[edit] [COLOR="Silver"]After further inspection of your boot script, it seems that the bootable flag is set on the Win XP partition, while the MBR points at /dev/sda3 (the ubuntu partition) for boot.[/COLOR]  This may not be causing any problems, my boot drive looks like this, with the windows boot partition flagged as bootable, and my /boot on sda5:

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15b083f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       34624   278008558    7  HPFS/NTFS
/dev/sda3           34624       60802   210273281    5  Extended
/dev/sda5           34624       46781    97655808   83  Linux
/dev/sda6           46782       58939    97654784   83  Linux
/dev/sda7           58939       60802    14960640   82  Linux swap / Solaris

```

After further searching around, it would appear that Grub2 pretty much ignores bootable flags, so with that in the MBR like you have, then the bootable flag is not an issue.
Boot fails when I choose either of windows partitions. No problem when I boot linux normally.
I don't understand why grup is failing so much. I've never got such a problem.

---

### Post by Quackers on 2011-01-11
Please post boot script outputs in CODE tags.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda1               2,048    20,973,567    20,971,520  12 Compaq diagnostics
/dev/sda2    *     20,980,890   134,705,024   113,724,135   7 HPFS/NTFS
/dev/sda3         134,705,025   310,622,993   175,917,969  83 Linux
/dev/sda4         310,624,256   312,580,095     1,955,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        864CA2444CA22F3D                       ntfs       PQSERVICE                     
/dev/sda2        B010288210285220                       ntfs       ACER                          
/dev/sda3        3bbfb671-2d71-4947-8f6c-3d8387bcefef   ext3                                     
/dev/sda4        25693149-6845-4db8-81c1-e1096e26d1d4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768x32
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_915resolution ###
insmod 915resolution
915resolution 58 1366 768 32
### END /etc/grub.d/01_915resolution ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 864ca2444ca22f3d
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set b010288210285220
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=25693149-6845-4db8-81c1-e1096e26d1d4 none            swap    sw              0       0
192.168.1.3:/exports/expansion	/media/2TB	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14
192.168.1.3:/exports/web	/media/WEB	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14
192.168.1.3:/exports/documenti	/media/DOCUMENTI	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14

=================== sda3: Location of files loaded by Grub: ===================


 102.7GB: boot/grub/core.img
 102.7GB: boot/grub/grub.cfg
 102.7GB: boot/initrd.img-2.6.35-22-generic
 102.7GB: boot/initrd.img-2.6.35-24-generic
 102.6GB: boot/vmlinuz-2.6.35-22-generic
 102.7GB: boot/vmlinuz-2.6.35-24-generic
 102.7GB: initrd.img
 102.7GB: initrd.img.old
 102.7GB: vmlinuz
 102.6GB: vmlinuz.old
```

It looks like you have over-written Windows Vista (or 7) with XP at some time. The Windows Loader referring to sda1 will not boot as there are only 2 boot files in that partition - no operating system.
The Windows XP loader looks to be good, so really should be booting.
Did you resize the XP partition before you installed Maverick? If so what program did you use?
Do you have a Windows XP repair/installation disc?

---

### Post by Quackers on 2011-01-11
Double post, due to failed message - which lied :-)

---

### Post by TuTToWeB on 2011-01-11
> **Quackers said:**
> Please post boot script outputs in CODE tags.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda1               2,048    20,973,567    20,971,520  12 Compaq diagnostics
/dev/sda2    *     20,980,890   134,705,024   113,724,135   7 HPFS/NTFS
/dev/sda3         134,705,025   310,622,993   175,917,969  83 Linux
/dev/sda4         310,624,256   312,580,095     1,955,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        864CA2444CA22F3D                       ntfs       PQSERVICE                     
/dev/sda2        B010288210285220                       ntfs       ACER                          
/dev/sda3        3bbfb671-2d71-4947-8f6c-3d8387bcefef   ext3                                     
/dev/sda4        25693149-6845-4db8-81c1-e1096e26d1d4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768x32
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_915resolution ###
insmod 915resolution
915resolution 58 1366 768 32
### END /etc/grub.d/01_915resolution ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3bbfb671-2d71-4947-8f6c-3d8387bcefef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 864ca2444ca22f3d
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set b010288210285220
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=3bbfb671-2d71-4947-8f6c-3d8387bcefef /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=25693149-6845-4db8-81c1-e1096e26d1d4 none            swap    sw              0       0
192.168.1.3:/exports/expansion	/media/2TB	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14
192.168.1.3:/exports/web	/media/WEB	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14
192.168.1.3:/exports/documenti	/media/DOCUMENTI	nfs	soft,intr,rsize=8192,wsize=8192,timeo=14

=================== sda3: Location of files loaded by Grub: ===================


 102.7GB: boot/grub/core.img
 102.7GB: boot/grub/grub.cfg
 102.7GB: boot/initrd.img-2.6.35-22-generic
 102.7GB: boot/initrd.img-2.6.35-24-generic
 102.6GB: boot/vmlinuz-2.6.35-22-generic
 102.7GB: boot/vmlinuz-2.6.35-24-generic
 102.7GB: initrd.img
 102.7GB: initrd.img.old
 102.7GB: vmlinuz
 102.6GB: vmlinuz.old
```

It looks like you have over-written Windows Vista (or 7) with XP at some time. The Windows Loader referring to sda1 will not boot as there are only 2 boot files in that partition - no operating system.
The Windows XP loader looks to be good, so really should be booting.
Did you resize the XP partition before you installed Maverick? If so what program did you use?
Do you have a Windows XP repair/installation disc?
I didn't understand regarding windows vista. 
What is labeled as "Windows Vista" is the repair partition.
I didn't resized nor formatted any partition, except old ext3 where  9.04 was installed.
I'm an expert user and I would't have done something that could have damaged my pc. The only thing I could to is to restore old windows mbr that I think to I stored it somewhere!
To reply ur last question. No! I dont have repair disc, because it is one of the partition I want to boot!

---

### Post by Quackers on 2011-01-11
I see. I didn't mean that you had done it accidentally.
I said what I said because sda1 is labelled as Windows Vista/7 boot sector type, (not XP) and has 2 Vista/7 boot files in it (although they are upper case rather than mostly lower case). This may be explained by the fact that it is a recovery partition.
I would suggest re-installing grub, as this may be the quickest way to fix things - if it works.
Either from your Ubuntu desktop, or from a live cd/usb desktop please run these commands in a terminal.
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If no errors are reported please reboot and see if Ubuntu boots directly. If it does please run from a terminal ```
sudo update-grub
``` and watch as grub.cfg is run to see whether the windows loader is found.

---

### Post by b0b138 on 2011-01-11
I could be wrong, but shouldn't the line for xp in the boot.ini point to partition 1 and not 2? Assuming numbering starts at 0

multi(0)disk(0)rdisk(0)**partition(2)**\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


lol...as quakers said, I'm wrong. Looked at mine and its the same

---

### Post by Quackers on 2011-01-11
> **b0b138 said:**
> I could be wrong, but shouldn't the line for xp in the boot.ini point to partition 1 and not 2? Assuming numbering starts at 0

multi(0)disk(0)rdisk(0)**partition(2)**\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

Hard drive numbers start from 0, partition numbers start from 1

---

### Post by TuTToWeB on 2011-01-11
> **Quackers said:**
> I see. I didn't mean that you had done it accidentally.
I said what I said because sda1 is labelled as Windows Vista/7 boot sector type, (not XP) and has 2 Vista/7 boot files in it (although they are upper case rather than mostly lower case). This may be explained by the fact that it is a recovery partition.
I would suggest re-installing grub, as this may be the quickest way to fix things - if it works.
Either from your Ubuntu desktop, or from a live cd/usb desktop please run these commands in a terminal.
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If no errors are reported please reboot and see if Ubuntu boots directly. If it does please run from a terminal ```
sudo update-grub
``` and watch as grub.cfg is run to see whether the windows loader is found.
no way, my friend
Either recovery partition and winxp dont boot. However, typing alt+f10 I figured out recovery partition is able to boot.
Unfortunately, recovery program doesn't support mbr restoration. It means "recovery" just "formatting"

---

### Post by Quackers on 2011-01-11
That is to be expected when using the key sequence like that. At least that still works :-)
Did you try re-installing grub?

---

### Post by TuTToWeB on 2011-01-11
> **Quackers said:**
> That is to be expected when using the key sequence like that. At least that still works :-)
Did you try re-installing grub?
That gave me the proof booloaders weren't corrupted.
I solved by myself (I dont know where I got this idea).
I dont still believe that cause was the grub resolution. When I disabled 1366x756 resolution, windows started and I dont understand how the resolution affects the booting

---

### Post by Quackers on 2011-01-11
If the resolution used in /etc/default/grub is not supported by the screen it will not boot.
Did I miss something here? At what point in this thread was grub resolution mentioned? Other than in the last post.

---

### Post by TuTToWeB on 2011-01-11
> **Quackers said:**
> If the resolution used in /etc/default/grub is not supported by the screen it will not boot.
Did I miss something here? At what point in this thread was grub resolution mentioned? Other than in the last post.
Why isn't the resolution supported? I mean, I could see grub and items. I could choose linux and the others. I dont understand why it wasn't able to 'find' the operating system.
Anyway, you didn't miss anything. I achieved this conclusion by myself because it was the only different between grub installation of ubuntu 9.04

---

### Post by Quackers on 2011-01-11
That was my point. If you had also said that you had edited /etc/default/grub grub resolution, the road to this point may have been shorter :-)
What matters is whether your screen supports that resolution exactly. If it doesn't, it won't boot past that point.

---

### Post by TuTToWeB on 2011-01-12
> **Quackers said:**
> That was my point. If you had also said that you had edited /etc/default/grub grub resolution, the road to this point may have been shorter :-)
What matters is whether your screen supports that resolution exactly. If it doesn't, it won't boot past that point.
It's pretty weird. Grub resolution was set by poulsbo driver and I didn't touch anything. If driver developer does that, I guess resolution is supported.

---

