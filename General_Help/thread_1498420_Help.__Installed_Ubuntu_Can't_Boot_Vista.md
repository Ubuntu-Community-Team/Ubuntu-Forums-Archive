---
title: "Help.  Installed Ubuntu Can't Boot Vista"
date: 2010-05-31
forum: General Help
---

### Post by bluec10 on 2010-05-31
I installed Ubuntu and Vista doesn't appear on the grub boot menu.  How can I modify it so that I can get Vista?  I'm running Ubuntu from the DVD and I can edit the grub.cfg file, but what do I add to start Vista.

Thanks

---

### Post by harrismh777 on 2010-05-31
It doesn't go in grub.cfg... it goes in /boot/grub/menu.lst

You will need an entry in /boot/grug/menu.lst something like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1


That assumes that windows is on your first disk, first partition (hd0,0).

The thing that is puzzeling to me is that the install did not do this for you 
automatically. ubuntu is famous for doing this correctly...  did you make a change?

If you loaded over the windows partition then vista is gone... which, In my opinion, is a good thing.

---

### Post by oldfred on 2010-05-31
It depends on whether you have a new install or upgrade from a new install of 9.10 with grub2 and grub.cfg or an upgrade from before 9.10 or from 9.10 that was an upgrade with grub legacy 0.97 and menu.lst. (if you can follow the previous sentence you are doing better than me, I am not sure I understand it):)

Post this so we know what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mikewhatever on 2010-05-31
Before you try adding Vista, can you open Applications-Accessories->Terminal and post the output of the following command:

sudo fdisk -l

---

### Post by bluec10 on 2010-05-31
Here is the output of the fdisk command:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38f89c05

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50993   409600000    7  HPFS/NTFS
/dev/sdb2           50993      108360   460800000    7  HPFS/NTFS
/dev/sdb3          108361      121602   106359809    5  Extended
/dev/sdb5          108361      121602   106359808   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x666ed75f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       31055   239215882+   6  FAT16
/dev/sda3           31056       60801   238934745    7  HPFS/NTFS
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders
Units = cylinders of 6944 * 4096 = 28442624 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)
Partition 1 does not start on physical sector boundary.

---

### Post by bluec10 on 2010-05-31
Just ran the boot_info_script055 and here are the results:

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1741077127 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 1741089927 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1741084831 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 1741085831 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,466,810   498,898,574   478,431,765   6 FAT16
/dev/sda3         498,898,575   976,768,064   477,869,490   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   819,202,047   819,200,000   7 HPFS/NTFS
/dev/sdb2         819,202,048 1,740,802,047   921,600,000   7 HPFS/NTFS
/dev/sdb3       1,740,804,094 1,953,523,711   212,719,618   5 Extended
/dev/sdb5       1,740,804,096 1,953,523,711   212,719,616  83 Linux


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders, total 1941441 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     1,941,439     1,941,377   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4258414916D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        44F07983F0797C4C                       ntfs       ACER                          
/dev/sda3        9604926A04924CDD                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1CEC16E4EC16B84A                       ntfs       EXTRA1                        
/dev/sdb2        F8AACB07AACAC0FC                       ntfs       EXTRA2                        
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        66466636-9d3d-42b3-8196-2afec02e0d0b   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6B46-3D81                              vfat       KERRY'S IPO                   
/dev/sdc         A88B-3652                              vfat       iPod                          
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/66466636-9d3d-42b3-8196-2afec02e0d0b ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=8
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=66466636-9d3d-42b3-8196-2afec02e0d0b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=66466636-9d3d-42b3-8196-2afec02e0d0b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 66466636-9d3d-42b3-8196-2afec02e0d0b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4258414916d9b5d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f07983f0797c4c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=66466636-9d3d-42b3-8196-2afec02e0d0b /               ext4    errors=remount-ro 0       1

=================== sdb5: Location of files loaded by Grub: ===================


 942.9GB: boot/grub/core.img
 992.4GB: boot/grub/grub.cfg
 942.9GB: boot/initrd.img-2.6.32-22-generic-pae
 942.9GB: boot/vmlinuz-2.6.32-22-generic-pae
 942.9GB: initrd.img
 942.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 10 01 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  c0 9f 1d 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  02 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 0b d8 20 78 3f 00  00 00 81 9f 1d 00 00 00  |.... x?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 10 01 20 00  |.<.*UOKJIHC... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 9f 1d 00 66 07 00 00  00 00 00 00 02 00 00 00  |....f...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 81 3d 46 6b 49  50 4f 44 20 20 20 20 20  |..).=FkIPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by mikewhatever on 2010-05-31
So, where is Vista installed? sdb1? sdb2? ...

---

### Post by bluec10 on 2010-05-31
> **mikewhatever said:**
> So, where is Vista installed? sdb1? sdb2? ...

on sdb1

---

### Post by mikewhatever on 2010-05-31
What happens when you select Windows XP from sda1 to boot? Don't you get another boot screen offering different Windows to boot? Secondary Windows installations usually put their boot files on the already existing Windows partition, and according to the bootscript, there are no Vista boot files on sdb1. Hence the question.

---

### Post by techunit on 2010-05-31
please try the following code to see if Vista becomes visible in the grub menu...

```
sudo update-grub
```

---

### Post by wilee-nilee on 2010-05-31
n

---

### Post by oldfred on 2010-05-31
ON sda1you have grub installed to the partition. It says pqservice so I do not know if it is vital to fix but I would try the test disk repair.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The Vista Partition sda1 shows no errors but the script says ntfs in one place and FAT16 in the other.
/dev/sda2    *     20,466,810   498,898,574   478,431,765   6 FAT16

I would try using system, administration, disk utility and see if it says 7  or 6. It will look more like 0x07. If it is not 0x07 change to NTFS or 0x07.
If that does not work it may need chkdsk or other windows repairs.
Do you have a windows repair CD to load the recovery enviroment?

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors

---

### Post by bluec10 on 2010-06-03
> **mikewhatever said:**
> What happens when you select Windows XP from sda1 to boot? Don't you get another boot screen offering different Windows to boot? Secondary Windows installations usually put their boot files on the already existing Windows partition, and according to the bootscript, there are no Vista boot files on sdb1. Hence the question.

I get a blank screen with a blinking cursor in the upper left hand corner.  It just hangs.

I selected the Windows recovery option and finally got somewhere.  It ran whatever recovery protocols that it runs and after rebooting I was able to get into Vista...but not from the Vista option on the Grub menu.  I still use the recovery option and it gets me into Vista.

I ran the update Grub command and it didn't make any difference.

---

### Post by wilee-nilee on 2010-06-03
I would follow oldfred's instructions, you have installed grub in windows.

---

### Post by oldfred on 2010-06-03
Grub2 seems to be reporting partitions with the wrong descriptions, boot works but recovery is the main install and the main install is seen as recovery.

See this thread for the same issue.

[http://ubuntuforums.org/showthread.php?t=1500245](http://ubuntuforums.org/showthread.php?t=1500245)

---

