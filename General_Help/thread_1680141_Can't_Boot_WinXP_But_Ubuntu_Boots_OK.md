---
title: "Can't Boot WinXP But Ubuntu Boots OK"
date: 2011-02-02
forum: General Help
---

### Post by ram2008 on 2011-02-02
[SIZE="1"]Last evening after being in Ubuntu (10.04) for several hours I tried to boot to WinXP but could not.  Got a message saying Windows could not boot because Hal.dll was either missing or corrupted.  Today I replaced that file from another XP computer that works OK but Windows still will not boot.  The last thing that happened in WinXP several hours before the problem occurred was I had run Chessmaster 9000.  No new software installed, no new partitions or anything like that.

Using version 1.98 of grub.  When I type fdisk -l, nothing happens.  Terminal just brings up another command prompt line.  I've attached the results of the boot info script below.  Hopefully this will help in diagnosing the problem.  Thanks for your help.[/SIZE]

Here's the first part of the Results.txt file. I had to take it out of the file because it was over limit:

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdg

---

### Post by Rubi1200 on 2011-02-02
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    



sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /wubildr.mbr /wubildr

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 1.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   585,938,943   585,936,896  83 Linux
/dev/sda2    *    585,954,810   647,371,304    61,416,495   7 HPFS/NTFS
/dev/sda3         647,371,305   968,912,279   321,540,975   5 Extended
/dev/sda5         647,371,368   659,661,029    12,289,662   7 HPFS/NTFS
/dev/sda6         659,661,093   753,866,189    94,205,097   7 HPFS/NTFS
/dev/sda7         753,866,253   850,127,669    96,261,417   7 HPFS/NTFS
/dev/sda8         850,127,733   968,912,279   118,784,547   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 2000 MB, 2000682496 bytes
61 heads, 8 sectors/track, 8007 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *              1     3,907,582     3,907,582   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        412d732b-8b7e-484e-9a59-a8bd7cd955c8   ext4                                     
/dev/sda2        5EC539A84E411154                       ntfs       Windows XP                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        58BA1D2A20A9854F                       ntfs                                     
/dev/sda6        1547F729455297EA                       ntfs       Applications1                 
/dev/sda7        0FA4E3234628902B                       ntfs       Applications2                 
/dev/sda8        DC381F17381EF06E                       ntfs       Virtualbox                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A2E42B01E42AD6F7                       ntfs       DISK3_VOL1                    
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        B965-47D7                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdg1        /media/B965-47D7___      vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
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
search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 412d732b-8b7e-484e-9a59-a8bd7cd955c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5ec539a84e411154
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set a2e42b01e42ad6f7
	drivemap -s (hd0) ${root}
	chainloader +1
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
# / was on /dev/sda1 during installation
UUID=412d732b-8b7e-484e-9a59-a8bd7cd955c8 /               ext4    errors=remount-ro 0       1
/dev/sdb1       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   5.0GB: boot/grub/grub.cfg
   5.5GB: boot/initrd.img-2.6.32-22-generic-pae
   6.4GB: boot/initrd.img-2.6.32-23-generic-pae
   6.4GB: boot/initrd.img-2.6.32-24-generic-pae
   6.5GB: boot/initrd.img-2.6.32-25-generic-pae
   7.5GB: boot/initrd.img-2.6.32-26-generic-pae
   6.5GB: boot/initrd.img-2.6.32-27-generic-pae
   7.1GB: boot/initrd.img-2.6.32-28-generic-pae
   5.4GB: boot/vmlinuz-2.6.32-22-generic-pae
   6.4GB: boot/vmlinuz-2.6.32-23-generic-pae
   6.5GB: boot/vmlinuz-2.6.32-24-generic-pae
   6.5GB: boot/vmlinuz-2.6.32-25-generic-pae
   6.5GB: boot/vmlinuz-2.6.32-26-generic-pae
   6.5GB: boot/vmlinuz-2.6.32-27-generic-pae
   6.5GB: boot/vmlinuz-2.6.32-28-generic-pae
   7.1GB: initrd.img
   6.5GB: initrd.img.old
   6.5GB: vmlinuz
   6.5GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  fa 8a b4 13 00 00 00 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by Grepomate on 2011-03-24
This is covered elsewhere but here to help.

If your Ubuntu installation boots up properly, then the problem most likely is the boot loader in Windows, so just need to update the boot.ini file.

This worked best for me:
1- Boot from the Windows installation media (CD).
2- After loading initialization files you'll see a menu with 3 options, press "R" for Repair.
3- Will prompt to select the Windows installation to work with, most likely #1, so enter "1", then Enter.
4- It'll then ask for the Administrator password: enter it if you assigned one, otherwise just press Enter.
5- You'll then be presented with a prompt that looks like this: C:\WINDOWS>
6- Type bootcfg /scan, after a few minutes it will show the windows installations identified, you should see at least one, if not most likely your Windows is corrupted and you'll have to reinstall from scratch.
7- In most cases you'll see "[1]: C:\WINDOWS".
8- Just to make sure, type bootcfg /rebuild, it will then ask to confirm that you want to add the installation it found. Press "Y" for Yes.
9- You should be back at the C:\WINDOWS> prompt.
10- Type EXIT then press Enter, the system should reboot to Windows normally.

Hope this helps, otherwise post your results to examine further.
G|

---

### Post by dragonfly41 on 2011-03-24
I've got the same problem .. but substitute "Vista" for "WinXP".   Dell Inspiron 1720.

I can dual boot into Ubuntu but the Windows boot snarls up.   

Windows safe mode only loads drivers then stops.

Repair mode stalls as well.

I can see all my Windows files in Ubuntu File System and I've run the boot info script

So I've tried to repair (not reinstall) Vista from a Vista installation CD.  

The installation starts but after a lot of loading the Vista re-installation stalls although there is a large white cursor seem on the black screen and cursor can be moved around so it has not frozen.

I've left it for a long while but no progress seen on screen.   Certainly no sign of Vista.

So how to reinstall / repair Vista in such circumstances?

I'm sending this from the Ubuntu working wubi.

---

### Post by Rubi1200 on 2011-03-24
Post the results of the boot info script so we can see what is going on.

Thanks.

---

### Post by dragonfly41 on 2011-03-24
Results.txt generated by running boot_info_script055.sh is attached.

Thanks.

---

### Post by Rubi1200 on 2011-03-24
> **dragonfly41 said:**
> Results.txt generated by running boot_info_script055.sh is attached.

Thanks.

I need to take a look at this and then get back to you.

Thanks.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2             403,456    21,374,975    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,374,976   483,151,863   461,776,888   7 HPFS/NTFS
/dev/sda4         483,151,872   488,394,751     5,242,880   f W95 Ext d (LBA)
/dev/sda5         483,153,920   488,394,751     5,240,832  dd Dell Media Direct


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 i386             
/dev/loop1                                              squashfs                                 
/dev/loop2       48596993-88ee-4a4f-a2b7-d5b79073ccde   ext4                                     
/dev/sda1        07D8-0508                              vfat       DellUtility                   
/dev/sda2        5204ADEB04ADD271                       ntfs       RECOVERY                      
/dev/sda3        C8A6B0E3A6B0D364                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        72B4-788D                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024 
=============================== StdErr Messages: ===============================

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by Rubi1200 on 2011-03-24
> **johnplayers said:**
> i m also suffring from this problem.well i dont have enough knowledge about ubuntu.so plz anybody help me?:(
Hi and welcome to the forums :)

If you take a look at my previous posts, you will see there are instructions on running the boot info script.

Follow that and then post the results back here please.

---

### Post by sdowney717 on 2011-03-24
if you have an xp setup disk then you can 
boot the xp installer to a command prompt.

run fixmbr, that will overwrite mbr so it will boot windows.
you loose the grub menu.

then you can reinstall grub to get the grub boot menu back.
And perhaps it will all work like it should.

---

### Post by Rubi1200 on 2011-03-24
@sdowney717; I am not sure that is necessary here if you are referring to the results posted by dragonfly41

@dragonfly41; I think this is the problem:
```
timeout=0 
```You need to edit the boot.ini file and change the timeout to at least 5 and preferably 10 or more (default is 30).
We have seen this with Wubi installs before and changing the timeout usually fixes the problem.

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

The other thing I noticed, even though you say Ubuntu boots, is that there is no mention of the OS on the Wubi install:

> sda3/Wubie.g. > Ubuntu 10.04.1 LTS

---

### Post by dragonfly41 on 2011-03-24
Thanks for the advice.

I've looked for Vista boot.ini ... but where is it?

Is it a hidden windows file not seen in Ubuntu?

How do I allow windows hidden files to be seen (in Ubuntu) and copied/edited as advised?

My setup (before Vista crashed on me in safe mode) was using Ubuntu Windows Installer .. BUT .. I didn't go for the full Ubuntu installation and every time I dual boot up into Ubuntu I press ESC to get into Ubuntu menu and I select Demo Mode (see grub.cfg below).   This means that I lose Ubuntu sessions between restarts but I'm wary of wiping out all of my Vista files.

Wubi installed into c:\ubuntu

which I now see in /isodevice/ubuntu

In Ubuntu File System I have a folder "isodevice" and this contains all of my Vista    c:\    programs and data .. which I've backed up to a USB drive.

However I would much prefer to get Vista working again in tandem with Ubuntu.

...

I've looked in isodevice/    (which is more than 50 GB in size)

and at isodevice root I can see some usualWindows files ..

autoexec.bat
bootmgr
config.sys 

and many more

I can also see

wubildr 113. KB
wubilldr.mbr

but I don't see any boot.ini


....


Example:  Inspecting /isodevice/ubuntu/install/boot/grub/grub.cfg

I see this

```

[COLOR=Blue]#This file is modified at runtime by bootmenu.nsh 
 
set default=0 
echo "Completing the Ubuntu installation." 
echo "For more installation boot options, **[COLOR=DarkRed]press `ESC' now..."[/COLOR] **
if sleep --verbose --interruptible 5 ; then 
   set timeout=0 
fi 
echo 
 
# TBD try to boot directly from kernel/initrd within the ISO via the grub2 loop module 
 
search -s -f -n /ubuntu/install/boot/vmlinuz 
 
menuentry "Normal mode" { 
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash  boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --  rootflags=syncio 
    initrd /ubuntu/install/boot/initrd.lz 
} 
 
menuentry "Safe graphic mode" { 
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity xforcevesa boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio 
    initrd /ubuntu/install/boot/initrd.lz 
} 
 
menuentry "ACPI workarounds" { 
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio acpi=off noapic nolapic 
    initrd /ubuntu/install/boot/initrd.lz 
} 
 
menuentry "Verbose mode" { 
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio 
    initrd /ubuntu/install/boot/initrd.lz 
} 
 
[COLOR=DarkRed]**menuentry "Demo mode"**[/COLOR] { 
    linux /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso quiet splash boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --  rootflags=syncio 
    initrd /ubuntu/install/boot/initrd.lz 
} [/COLOR]

```

---

### Post by Rubi1200 on 2011-03-24
My mistake; I was looking at the boot files for sda5 and not concentrating. 

I have asked someone else to offer their perspective, so please be patient.

Thanks.

---

### Post by dragonfly41 on 2011-03-24
Perhaps the attached screenshot explains better .. Vista OS is in sda3   ..

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by ant2ne on 2011-03-24
sounds like you are troubleshooting windows on an ubuntu forum.

Can you boot into Windows safe mode by pressing F8? If so run "sfc /scannnow"

From an XP disk  you can boot to the recovery console (command line) and run check disk. I'm sure you can do that from a vista CD somehow. "chkdsk /r /f c:".

---

### Post by dragonfly41 on 2011-03-24
> sounds like you are troubleshooting windows on an ubuntu forum.

Can you boot into Windows safe mode by pressing F8? If so run "sfc /scannnow"Thanks .. but I'm troubleshooting migrating from Vista only to Ubuntu coexisting with Vista.

If I have Vista questions to be answered I would post in vistaforums.

I'm not able to progress beyond loading drivers in safe mode.  I only have Ubuntu (in demo mode) to work with.   I'm puzzled why I can't even insert a Vista installation disk to repair the installation.

---

### Post by Rubi1200 on 2011-03-25
After consulting with another user, this is what I know:

This is probably not a Wubi issue.

I think you need to use your Vista CD to do a startup repair, but if you are having problems getting that far then I really don't know what to tell you.

It might be worth asking on a Windows forum since they may have more experience with problems getting the Windows CD to run.

If I find more information that can help you, I will post back again.

---

