---
title: "grub2 external hdd help"
date: 2011-03-31
forum: General Help
---

### Post by dKasya on 2011-03-31
Dear Ubuntu Community,
I am having trouble with setting up the grub based system on my external hdd. I am trying to have one grub which is going to load operating systems, and livecd if any (usb install). I am stuck at installing Ubuntu 10.10 Minimal version (i don't need gui for linux).

Here is what I have done so far:
1. Created 2 primary partitions - windows 7 recovery and data (ntfs)
2. Created an extended partition for linux stuff.
3. Create a logic partition (10MB) for grub (ext2)
4. Copy boot directory from ubuntu-mini to grub
5. grub-install --root-directory=mounted_dir_for_grub_partition /dev/sdb => Tested it. Opens the grub2 menu with values changed in grub.cfg
6. Create a new primary/logical (tried both) partition (15MB) for Ubuntu Minimal (ext2) for installation
7. Copy the contents from ubuntu-mini.iso to that partition.
8. Add Grub Menu Entry:

menuentry "LiveCD Ubuntu Minimal" {
   set gfxpayload=keep
   set root=hd0,msdos6
   linux /linux --quiet
   initrd /initrd.gz
}

The menu entry is on that list but when i click i keep getting 2 errors:

error: file not found
error: you need to load the kernel first

I know that it can't find the files "linux" and "initrd.gz" but I don't know how to make it, so it found it. What should i do?

Thanks in advance.
Gasim Gasimzada

---

### Post by dKasya on 2011-03-31
bump. anyone?

---

### Post by dKasya on 2011-04-01
I think I have to solve this issue myself.

---

### Post by wilee-nilee on 2011-04-01
You have a Frankenstein like set up using grub2, that probably is not needed, and a strange install method, if you just want a minimal install of just the Ubuntu on a external there are easier ways. You don't need a ext2 boot partition.

If you want some help click on the bootscript in my signature and run it and post the generated text file in code tags.

---

### Post by dKasya on 2011-04-05
Thanks for the reply. I'll check it out tomorrow (have an exam to finish tomorrow)

Gasim

---

### Post by dKasya on 2011-04-05
Here is the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytesn

Partition  Boot         Start           End          Size  Id System

/dev/sda1          31,455,331   671,083,244   639,627,914   f W95 Ext d (LBA)
/dev/sda5          31,455,333   671,083,244   639,627,912   7 HPFS/NTFS
/dev/sda2         671,084,544   702,537,727    31,453,184  83 Linux
/dev/sda3    *    702,537,728   817,881,087   115,343,360   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048       329,727       327,680   7 HPFS/NTFS
/dev/sdb2             329,728    31,787,007    31,457,280   5 Extended
/dev/sdb5    *        331,776       352,255        20,480  83 Linux
/dev/sdb6             354,304       415,743        61,440  83 Linux
/dev/sdb3          31,787,008   966,287,359   934,500,352   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        9644420b-4b1c-4bcc-a272-0ab51e95979e   ext4                                     
/dev/sda3        2CCCE4C6CCE48C00                       ntfs                                     
/dev/sda5        4A040486040476EB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3258BE1D70FF6358                       ntfs       Windows 7 Recovery            
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        4E0CA8CC5AB909E9                       ntfs       Data                          
/dev/sdb5        115c9978-1978-4a08-b061-e99bf2cb1deb   ext2                                     
/dev/sdb6        8f6ce484-75af-4daf-ab26-c056a8a95a1e   ext2                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /media/115c9978-1978-4a08-b061-e99bf2cb1deb ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6        /media/8f6ce484-75af-4daf-ab26-c056a8a95a1e ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Windows 7 Recovery fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
  insmod vgan
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
insmod jpeg
if background_image /boot/grub/bg.jpg ; then
  set color_normal=white/black
  set color_highlight=red/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu 10.10 (Linux 2.6.35-28-generic)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9644420b-4b1c-4bcc-a272-0ab51e95979e ro quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_windows7 ###
menuentry "Windows 7 Ultimate Edition" {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set f0201fca201f96a6
        chainloader +1
}

### END /etc/grub.d/20_windows7 ###

### BEGIN /etc/grub.d/40_separator ###
menuentry " --- Other --- " {
	set root=''
}
### END /etc/grub.d/40_separator ###

### BEGIN /etc/grub.d/45_linux_recovery ###

menuentry 'Ubuntu 10.10 (Linux 2.6.35-28-generic) - Recovery' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9644420b-4b1c-4bcc-a272-0ab51e95979e ro 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/45_linux_recovery ###

### BEGIN /etc/grub.d/50_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9644420b-4b1c-4bcc-a272-0ab51e95979e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/50_memtest86+ ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1

=================== sda2: Location of files loaded by Grub: ===================


 348.0GB: boot/grub/core.img
 348.9GB: boot/grub/grub.cfg
 358.2GB: boot/initrd.img-2.6.35-28-generic
 344.9GB: boot/vmlinuz-2.6.35-28-generic
 358.2GB: initrd.img
 344.9GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "LiveCD" {
	set gfxpayload=keep
	set root=hd0,msdos1
	linux	/linux -- quiet
	initrd	/initrd.gz
}

=================== sdb5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
```

sdb is my external hard drive (sda has to be fixed because I have installed ubuntu over xp and win7 over ubuntu; needs a reformatting hdd being honest). The thing I am trying to do is to have more than one linux operating systems in my extended partition (will start with ubuntu minimal). What should i do? Its ok to clean the disk and start everything over. I just need to get it working.

Will putting windows 7 recovery in my extended partition boot to it if I am using Grub2 menu for it? Because I have heard that windows only boots from primary partition but since its boot from grub2 should it work in a logical partition?

And need an advice (I am new to this kind of stuff but want to understand it better). Should I put my Data partition in extended partition or its better to have it as primary partition?

Thanks,
Gasim

---

### Post by dKasya on 2011-04-11
bump?

---

