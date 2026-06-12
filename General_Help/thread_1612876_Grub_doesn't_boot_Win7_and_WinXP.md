---
title: "Grub doesn't boot Win7 and WinXP"
date: 2010-11-03
forum: General Help
---

### Post by sup3roque on 2010-11-03
Well, I have Win7 installed in my notebook, after I install WinXP, after I install Ubuntu 10.10

Ok, do not judge me please, I need WinXP to my project...

I re-install Grub2 with live CD and the WinXP doesn't show up...

So I re-install WinXP... Re-install Grub2 and WinXP doesn't show up again...

So I custumise Grub2 and I put one line for WinXP (doesn't work)

But Now, Win7 line in Grub2 boot WinXP :confused:

I need HELP please

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total de 976773168 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 HPFS/NTFS
/dev/sda3         274,904,341   976,751,999   701,847,659   f W95 Ext d (LBA)
/dev/sda5         274,904,343   851,005,439   576,101,097   7 HPFS/NTFS
/dev/sda6         851,007,488   909,692,927    58,685,440  83 Linux
/dev/sda7         909,694,976   913,598,463     3,903,488  82 Linux swap / Solaris
/dev/sda8         913,600,548   976,751,999    63,151,452   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        72C6DC68C6DC2DDB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2D3A01CA8F073681                       ntfs       DATA                          
/dev/sda6        f4bb9c97-26a7-4660-b3e3-654b134fc9fe   ext4                                     
/dev/sda7        5df7762b-b4a2-4dcd-83bd-c79d31f8f99b   swap                                     
/dev/sda8        C49CEF169CEF01B2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(6)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(6)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
set locale_dir=($root)/boot/grub/locale
set lang=pt
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=f4bb9c97-26a7-4660-b3e3-654b134fc9fe ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=f4bb9c97-26a7-4660-b3e3-654b134fc9fe ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f4bb9c97-26a7-4660-b3e3-654b134fc9fe
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 72c6dc68c6dc2ddb
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP" {
insmod ntfs
set root=(hd0,8)
search --no-floppy --fs-uuid --set C49CEF169CEF01B2
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=f4bb9c97-26a7-4660-b3e3-654b134fc9fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5df7762b-b4a2-4dcd-83bd-c79d31f8f99b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 451.1GB: boot/grub/core.img
 451.0GB: boot/grub/grub.cfg
 436.9GB: boot/initrd.img-2.6.35-22-generic-pae
 451.1GB: boot/vmlinuz-2.6.35-22-generic-pae
 436.9GB: initrd.img
 451.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by sikander3786 on 2010-11-03
Windows needs to be installed to a primary partition but in your case, XP is installed in sda8 which is a logical partition therefore you are unable to boot it.

sda2 lists operating system Windows 7 but the Boot Sector Type is Windows XP. XP bootloader somehow replaced Vista boot loader but howcome the XP bootloader be able to boot Windows 7? Don't know.

What does sda1 contain?

I think the best workaround will be to install XP to a primary partition, then restore the Vista bootloader from a recovery disc and then to reinstall Grub2.

Wait for some more replies for further enlightenment.

---

### Post by sup3roque on 2010-11-04
Sda1 have de RESTORE partition or REPAIR or something like that...

Ok, I'm going to try to rapair boot of Win7 a than try to put WinXP in a primary and re-install Grub2

Thanks

---

### Post by julio_cortez on 2010-11-04
> **sikander3786 said:**
> I think the best workaround will be to install XP to a primary partition, then restore the Vista bootloader from a recovery disc and then to reinstall Grub2.Wouldn't it result in the Vista bootloader taking care of both Vista and XP, in this way?
I don't know if it's the desired option though..

> **sup3roque said:**
> Ok, do not judge me please, I need WinXP to my  project...Why would we judge you? I still have XP installed on  my PC (I'm still running some legacy home-made software and some old  games) and I am actually writing this post from XP.

---

### Post by halj32 on 2010-11-04
when you have win 7/XP + Ubuntu installed xp doesnt show up on grubr because the win 7/vista boot loader handles xp
boot win 7/vista should then give you the option to boot xp

when you install these OS's you must install XP first then vista/7 then ubuntu
hope this helps
goodluck

---

### Post by WorMzy on 2010-11-04
> **sikander3786 said:**
> Windows needs to be installed to a primary partition

This isn't entirely true. I have Windows XP installed to sdc6 and grub boots it with no problems. However, I installed via OEM disk, so it may install the bootloader differently to a recovery disk.

OP, did you run "sudo update-grub" after reinstalling grub? You'll probably need to boot into Ubuntu, run that, and then grub should create an XP menu entry.

> Ok, do not judge me please, I need WinXP to my project...

Don't worry about it, I need *Vista* for playing games. Even the Windows users don't like that one. :P

---

