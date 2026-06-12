---
title: "My boot menu has lost its OSes...."
date: 2011-03-15
forum: General Help
---

### Post by Envergure on 2011-03-15
I just restarted to switch from Ubuntu to Windows, and I was greeted with the GRUB screen, but the menu oprions have changed from:
Ubuntu on some number kernel
Ubuntu on some number kernel (safe mode)
Windows 7 (loader)
Memory Test

to:
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set [and some hex numbers]
linux /boot/vmlinuz-2.6.35-27-generic root=UUID=[hex number] ro quiet spash
initrd /boot/initrd.img-2.6.35-27-generic


The above is in an editable text box, not a menu.  The computer is getting pretty hot.

What's going on?  Has my BIOS failed?  Has my HDD failed?

For what it's worth, Ubuntu did some updates since I last shut down, but I don't know what they were.

GNU GRUB version 1.98+20100804-5ubuntu3
Ubuntu 10.10 on an Acer Aspire 5920G (64-bit).

---

### Post by Rubi1200 on 2011-03-16
Hi,
please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Envergure on 2011-03-16
Here's the result.

The computer has started working again without any changes.  Well, *something* must have changed, but it wasn't me.  I ran the script from my normal Ubuntu desktop, not the CD.



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   401,876,260   401,669,413   7 HPFS/NTFS
/dev/sda3         401,876,990   625,141,759   223,264,770   5 Extended
/dev/sda5         401,876,992   615,979,007   214,102,016  83 Linux
/dev/sda6         615,981,056   625,141,759     9,160,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1A1A727F1A725829                       ntfs       System Reserved               
/dev/sda2        C89C782A9C7814E2                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        31a24f00-b0ab-4e7d-8502-e2e8a14b2135   ext4                                     
/dev/sda6        9cb96fb5-aebe-43b4-92d5-9f60cb1216ec   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31a24f00-b0ab-4e7d-8502-e2e8a14b2135
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 1a1a727f1a725829
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=31a24f00-b0ab-4e7d-8502-e2e8a14b2135 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9cb96fb5-aebe-43b4-92d5-9f60cb1216ec none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 208.0GB: boot/grub/core.img
 257.5GB: boot/grub/grub.cfg
 226.2GB: boot/initrd.img-2.6.35-22-generic
 230.7GB: boot/initrd.img-2.6.35-23-generic
 231.6GB: boot/initrd.img-2.6.35-24-generic
 234.8GB: boot/initrd.img-2.6.35-25-generic
 235.4GB: boot/initrd.img-2.6.35-27-generic
 206.7GB: boot/vmlinuz-2.6.35-22-generic
 210.1GB: boot/vmlinuz-2.6.35-23-generic
 210.1GB: boot/vmlinuz-2.6.35-24-generic
 210.1GB: boot/vmlinuz-2.6.35-25-generic
 218.7GB: boot/vmlinuz-2.6.35-27-generic
 235.4GB: initrd.img
 234.8GB: initrd.img.old
 218.7GB: vmlinuz
 210.1GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2011-03-16
As far as I can tell, the results look fairly normal. In other words, nothing unusual stands out.

Do you remember if one of the updates was for the grub-* packages? Perhaps just a temporary glitch?

---

### Post by Envergure on 2011-03-23
I didn't notice if it updated Grub.  Anyway, the computer works fine now.  Maybe it was just a badly-timed cosmic ray or something.

---

### Post by WorMzy on 2011-03-23
Could have been a stuck key, or maybe you pressed a key accidentally; that looks like the "edit entry" screen, which lets you modify the way grub boots an OS.

The next time you see the OS list, look at the bottom of the screen. It should say something like "Press E to edit, or C for command line", if you press the edit button, it'll take you back to the screen that had you worried. :)

---

