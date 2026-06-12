---
title: "windows 7 and Ubuntu dual boot"
date: 2012-05-18
forum: General Help
---

### Post by gkyasitha on 2012-05-18
i used ubuntu for a along time as the only thing i do from the computer is watching movies and browsing internet. for my exam purposes i have to use this application call "bpp ipass" which only run in windows, so i installed windows while having ubuntu and recoverd the grub using "boot-repair" by booting a usb stick. so things got all right.

there is this 19gb partition that when i try to access using windows it says  
"access denied" but i can access when i'm in ubuntu. It contain some files name boot or i can't clearly remember but they looks like some temperorary files so i formatted that partition.(while on ubuntu) afterwards i didn't even boot on windows as i primarily use ubunutu. but today morning i found out that "windows 7 loader" entry is not there in grub menu.

i log into ubuntu and check whether there is windows 7 files and its drive. - yes there is.

i downloaded and run grub-repair - nothing happen

i put windows 7 dvd boot and choose repair. - restart and see the grub menu - no change

log in to ubuntu run grub-repair restart and see the grub menu - now there are 2 new entries.

windows 7 loader sda 1 when enterd - say this not a bootable drive put a floppy blah blah..

and the 2nd entry

windows 7 loader sda 8 when enterd - blank screen for few seconds then comes "intel realtek audio...." and press again enter
"it searches for mc address "//" thing that rotate and nothing happens.  
now i don't know what to do next??? :(

please google found some similar threads but they didn't help.

      

```

            Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda6 starts at sector 61448688. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    40,965,749    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda2          40,965,750   160,810,649   119,844,900   f W95 Extended (LBA)
/dev/sda5          40,965,813    61,448,624    20,482,812   7 NTFS / exFAT / HPFS
/dev/sda6          61,448,688    81,931,499    20,482,812   b W95 FAT32
/dev/sda7          81,931,563   122,897,249    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda8    *    122,897,313   160,810,649    37,913,337   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   228,685,274   228,685,212   7 NTFS / exFAT / HPFS
/dev/sdb2         228,685,824   308,684,799    79,998,976  83 Linux
/dev/sdb3         308,686,846   312,580,095     3,893,250   5 Extended
/dev/sdb5         308,686,848   312,580,095     3,893,248  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DE4D-41AE                              vfat       New Volume
/dev/sda5        526072E96072D2E9                       ntfs       
/dev/sda6        90D0-60F9                              vfat       
/dev/sda7        D858C98B58C968B8                       ntfs       
/dev/sda8        04EC04FFEC04ECAC                       ntfs       
/dev/sdb1        57034F23252F8A40                       ntfs       
/dev/sdb2        c55b6fa3-3ea1-4454-8431-f432089d1378   ext3       
/dev/sdb5        aac0c2b5-b736-41ec-8e1f-b78cf14ec869   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /media/04EC04FFEC04ECAC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /                        ext3       (rw,errors=remount-ro)


=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

========================== sda8/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=c55b6fa3-3ea1-4454-8431-f432089d1378 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	echo	'Loading Linux 2.6.32-41-generic ...'
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=c55b6fa3-3ea1-4454-8431-f432089d1378 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=c55b6fa3-3ea1-4454-8431-f432089d1378 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=c55b6fa3-3ea1-4454-8431-f432089d1378 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set c55b6fa3-3ea1-4454-8431-f432089d1378
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de4d-41ae
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda8)" {
	insmod ntfs
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 04EC04FFEC04ECAC
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=c55b6fa3-3ea1-4454-8431-f432089d1378 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=aac0c2b5-b736-41ec-8e1f-b78cf14ec869 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.286869049 = 148.484395008  boot/grub/core.img                             3
 142.999065399 = 153.544077312  boot/grub/grub.cfg                             1
 127.709625244 = 137.127165952  boot/initrd.img-2.6.32-37-generic              3
 138.286865234 = 148.484390912  boot/initrd.img-2.6.32-41-generic              4
 122.499034882 = 131.532337152  boot/vmlinuz-2.6.32-37-generic                22
 138.276412964 = 148.473167872  boot/vmlinuz-2.6.32-41-generic                 4
 138.286865234 = 148.484390912  initrd.img                                     4
 127.709625244 = 137.127165952  initrd.img.old                                 3
 138.276412964 = 148.473167872  vmlinuz                                        4
 122.499034882 = 131.532337152  vmlinuz.old                                   22

....................................................................................

```
sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77317731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       10010    59922450    f  W95 Ext'd (LBA)
/dev/sda5            2551        3825    10241406    7  HPFS/NTFS
/dev/sda6            3826        5100    10241406    b  W95 FAT32
/dev/sda7            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda8   *        7651       10010    18956668+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x151543c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14235   114342606    7  HPFS/NTFS
/dev/sdb2           14236       19215    39999488   83  Linux
/dev/sdb3           19215       19458     1946625    5  Extended
/dev/sdb5           19215       19458     1946624   82  Linux swap / Solaris


please help?
i have 2 hard disks

one is 80gb where windows is installed
another one 160gb sata ubuntu is installed.
the partition that i formatted is 20 gb partion out of 80gb

---

### Post by satish_j on 2012-05-18
if you have bootable XP cd,you can boot into it,go to repair mode and run fixboot command.This should restore MBR.
Then,you will have to boot from Ubuntu Live CD and install grub again.

---

### Post by gkyasitha on 2012-05-18
> **satish_j said:**
> if you have bootable XP cd,you can boot into it,go to repair mode and run fixboot command.This should restore MBR.
Then,you will have to boot from Ubuntu Live CD and install grub again.

i'm using windows 7 not xp(this says xp may be because i used xp before installing ubuntu long long time ago and then format while on ubuntu)

i tried repair using windows 7 dvd

bootrec.exe/fixmbr
bootrec.exe/fixboot
bootrex.exe/RebuildBcd - this says no windows installation is found

now there is no grub menu. sound came from system unit and msg appear disk is not readable.
now i'm in more and more trouble

---

### Post by satish_j on 2012-05-18
> **gkyasitha said:**
> 
bootrec.exe/fixmbr
bootrec.exe/fixboot
bootrex.exe/RebuildBcd - this says no windows installation is found

now there is no grub menu. sound came from system unit and msg appear disk is not readable.
now i'm in more and more trouble

From what i can understand,you have removed the windows7 bootloader files by formatting that 19gb partition,so that effectively means that windows 7 will not appear even if you get grub menu back.If you will have to restore Windows 7 bootloader back,you can ask for how to on Windows 7 forums.
However,if you can get to Grub and into Ubuntu and if you can access Win7 data,you can back it up and re-install the Win7 again.
You will have to boot from Ubuntu Live CD to install grub again.

---

### Post by gkyasitha on 2012-05-18
> **satish_j said:**
> From what i can understand,you have removed the windows7 bootloader files by formatting that 19gb partition,so that effectively means that windows 7 will not appear even if you get grub menu back.If you will have to restore Windows 7 bootloader back,you can ask for how to on Windows 7 forums.
However,if you can get to Grub and into Ubuntu and if you can access Win7 data,you can back it up and re-install the Win7 again.
You will have to boot from Ubuntu Live CD to install grub again.

yes i reinstalled windows 7 and now trying to put grub back again.
the real problem is how can windows loader "entry" got removed from grub menu by formating that 19gb partition. it can't be practical know?

thanks for your time your the only one answered):P.

---

### Post by satish_j on 2012-05-18
> **gkyasitha said:**
> 
the real problem is how can windows loader "entry" got removed from grub menu by formating that 19gb partition. it can't be practical know?

> **gkyasitha said:**
> 
there is this 19gb partition that when i try to access using windows it says  
"access denied" but i can access when i'm in ubuntu. It contain some files name boot or i can't clearly remember but they looks like some temperorary files ...


The files named boot are nothing but Win7 bootloader files..
BTW,Glad you got the problem solved..

---

### Post by Rebelli0us on 2012-05-18
Why don't you run Windows 7 in a VM? That's what I do, with dual-boot you risk trashing your system. VM is harmless, you can add/remove as needed and you can run both OSes simultaneously.

---

### Post by oldfred on 2012-05-18
It would be best to have grub2's boot loader in sdb and set BIOS to boot sdb if your system allows that. Some old systems do not.

And have the Windows boot loader in sda, so you can directly boot Windows if need be. Grub will only chainload a working Windows.

You installed Windows to a logical partition and it can only boot from a primary partition. You do seem to have sda1 as a boot partition, but in one place it say FAT and the other NTFS. I would copy/backkup bootmgr & the BCD folder from sda1, and reformat to NTFS and set boot flag on the sda1 partition. Then restore bootmgr & bcd. Then your Windows repairs should work.

You also have core.img & grldr files or folders in various NTFS partitions on sda that look like they may create issues. I would delete them.

---

