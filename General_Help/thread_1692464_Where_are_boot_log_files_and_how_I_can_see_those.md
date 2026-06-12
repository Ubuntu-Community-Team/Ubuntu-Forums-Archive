---
title: "Where are boot log files and how I can see those?"
date: 2011-02-21
forum: General Help
---

### Post by Danial on 2011-02-21
Hi,

Thanks for looking into this problem.

Here is my situation:
 
I was used to have a functional and problem free Karmic but it died about two weeks ago - just refused to boot and I even can not boot with Karmick Live CD. 

It all started when my system crashed using Win7 (more than couple of times in a short period of time).  Later when I decide to go into Ubuntu, I got bellow mentioned scenario. Same Live CD (Karmic) works fine on laptop and same CD was used to install Karmic on this desktop back in October.  Later sometime in December, I started using xfce desktop until everything just came to a halt.

This is what happens when booting from HD, I get to choose the operating system and I hear the login sound and then it stops - monitor goes to no input signal.  When booting with Karmic live CD (pressing <escape> key to get boot options) I get to the Live CD options and choosing live session brings just garbled video on top of the screen. I have tried nomodeset to no avail/same results. There was no hardware/software changes in recent past except the regular updates which was at least two days ago before this problem arose (Karmic was working fine after the system update). 

However, Lucid CD let me get into live session (that is what I am using now). Is there a way to check the boot log to see where the fault is and/or any other way to trouble shoot. Just in case you need, I am attaching bootscript, fstab and fdisk outputs. 


Output for bootscript:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

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
Disk identifier: 0xbd3c5204

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,120,949    10,120,887  82 Linux swap / Solaris
/dev/sda2    *     10,120,950   102,671,414    92,550,465  83 Linux
/dev/sda3         102,671,415   180,249,299    77,577,885  83 Linux
/dev/sda4         180,249,361   976,768,064   796,518,704   5 Extended
/dev/sda5         180,249,363   285,716,024   105,466,662  83 Linux
/dev/sda6         285,716,088   444,293,639   158,577,552  83 Linux
/dev/sda7         444,293,703   602,871,254   158,577,552  83 Linux
/dev/sda8         602,871,318   655,435,934    52,564,617  83 Linux
/dev/sda9         655,435,998   708,000,614    52,564,617  83 Linux
/dev/sda10        813,467,403   895,109,669    81,642,267  83 Linux
/dev/sda11        895,109,733   915,335,504    20,225,772  83 Linux
/dev/sda12        708,000,678   813,467,339   105,466,662   7 HPFS/NTFS
/dev/sda13        915,335,568   976,768,064    61,432,497  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c879c87

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    10,233,404    10,233,342  82 Linux swap / Solaris
/dev/sdc2    *     10,233,405    78,156,224    67,922,820   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a357f

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,024,002,047 1,024,000,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       ce1aca59-ceda-4aef-8230-eb2996535daf   ext4       Temp                          
/dev/sda11       3f608fc3-eef3-4dfe-a755-5e83486bb0e5   ext4       Kachra                        
/dev/sda12       73E1719801BBE72A                       ntfs       Win-apps                      
/dev/sda1        3a7ce152-9022-42d2-8069-088a8ce8d58d   swap       swap                          
/dev/sda13       edbae11b-d8b2-4015-a4ac-db1b42a09578   ext3                                     
/dev/sda2        84781de9-0f61-474c-a56e-d6f455826462   ext4                                     
/dev/sda3        61e2bc23-bf09-45de-aff1-fb53119daa7a   ext4                                     
/dev/sda5        6e000c7f-2221-490e-818d-62a8d5d61578   ext4       Download                      
/dev/sda6        2c97211d-9eb8-4520-9ea7-c091e58b3a3b   ext4       Ganey                         
/dev/sda7        846a0dc9-58ba-468d-9e19-1fc5b59715c4   ext4       Tasaveer                      
/dev/sda8        b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3   ext4       Kaghzat                       
/dev/sda9        1d3711f4-d1cf-472d-b09b-f90667a033fa   ext4       Linux-doc                     
/dev/sdc1        d898c458-3a28-4abf-9a28-c34d356c0046   swap       swap                          
/dev/sdc2        66B8B439B8B40A17                       ntfs                                     
/dev/sdd1        1A080F20080EFB11                       ntfs       AaLee                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdd1        /media/AaLee             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 66b8b439b8b40a17
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=84781de9-0f61-474c-a56e-d6f455826462 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
# UUID=d898c458-3a28-4abf-9a28-c34d356c0046 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       2

=================== sda2: Location of files loaded by Grub: ===================


  35.3GB: boot/grub/core.img
  46.3GB: boot/grub/grub.cfg
  37.4GB: boot/initrd.img-2.6.32-24-generic
  37.9GB: boot/initrd.img-2.6.32-25-generic
  38.5GB: boot/initrd.img-2.6.32-26-generic
  46.9GB: boot/initrd.img-2.6.32-27-generic
  47.2GB: boot/initrd.img-2.6.32-28-generic
  37.4GB: boot/vmlinuz-2.6.32-24-generic
  37.2GB: boot/vmlinuz-2.6.32-25-generic
  37.5GB: boot/vmlinuz-2.6.32-26-generic
  37.5GB: boot/vmlinuz-2.6.32-27-generic
  39.0GB: boot/vmlinuz-2.6.32-28-generic
  47.2GB: initrd.img
  46.9GB: initrd.img.old
  39.0GB: vmlinuz
  37.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  b6 b6 ff 29 a2 b0 3b f9  ec 05 fa ca 1d 29 7f 7f  |...)..;......)..|
00000010  a7 4f d9 43 ff d6 56 d7  f8 09 6c f9 bb 75 bd c4  |.O.C..V...l..u..|
00000020  17 16 03 a7 f1 72 3c 21  6f b7 fe 91 94 1c 07 f9  |.....r<!o.......|
00000030  5b 1e e9 6b 7d 70 2c c5  e7 b7 9a 5a fc f2 9c f6  |[..k}p,....Z....|
00000040  b7 d6 32 db e7 4f f6 ef  d7 1d 70 21 3c 78 23 d5  |..2..O....p!<x#.|
00000050  ac 1b 56 ed eb 58 26 6b  1b cd 7e 7f 90 5a fd 5b  |..V..X&k..~..Z.[|
00000060  ff 47 8e b1 b8 e8 74 ba  13 c5 f9 67 cb 9e d4 ad  |.G....t....g....|
00000070  e5 0e 22 3f c1 2b 88 99  ed 94 fe f0 49 fb f0 8d  |.."?.+......I...|
00000080  b9 63 c5 58 fe 10 f0 8d  63 26 b8 7c 22 b7 c7 95  |.c.X....c&.|"...|
00000090  b6 df 4d 63 f1 60 32 ff  f2 a1 28 e3 06 b1 82 70  |..Mc.`2...(....p|
000000a0  17 e2 ef c9 6c d6 32 c6  b1 90 ff c2 39 45 22 dd  |....l.2.....9E".|
000000b0  c6 38 9d 2c 56 e8 a7 cd  8c 12 7e 96 d6 ab 81 6d  |.8.,V.....~....m|
000000c0  6b 29 7c b4 9e 24 7e f8  91 42 78 ab 1e 83 94 ac  |k)|..$~..Bx.....|
000000d0  6b 1a df c4 68 34 0a 5f  db 96 c5 36 ec 06 fd 05  |k...h4._...6....|
000000e0  fa 68 a4 21 23 f3 34 9a  af aa 20 03 42 12 84 02  |.h.!#.4... .B...|
000000f0  29 20 09 09 60 12 eb 3b  78 e8 1c c9 17 70 ac 92  |) ..`..;x....p..|
00000100  20 9c 79 e3 d6 0b ac 9f  01 31 00 0f 80 9d 00 03  | .y......1......|
00000110  c0 57 c0 00 5d 3f f8 09  1c 00 3c f5 ff 3d 66 55  |.W..]?....<..=fU|
00000120  65 d3 e5 f0 12 58 00 78  09 4c 00 7c 04 a0 00 5e  |e....X.x.L.|...^|
00000130  02 7c 00 1f 01 25 00 0e  55 cb 88 be 12 bc a5 f5  |.|...%..U.......|
00000140  3e 02 55 00 1f 34 e2 5b  cd 0e 96 71 0a 18 36 d1  |>.U..4.[...q..6.|
00000150  e1 07 4b 7f 27 60 d9 95  59 5a 74 fd 95 b1 c4 6a  |..K.'`..YZt....j|
00000160  c1 37 ae 0f 35 f8 8c e9  f2 fe 23 8c 1b 32 97 ff  |.7..5.....#..2..|
00000170  8b bf 5f af de 03 0b 33  a8 b7 b8 86 a3 c0 42 c0  |.._....3......B.|
00000180  08 8c a1 66 28 78 41 ff  13 fc 05 6e fc bc d7 e5  |...f(xA....n....|
00000190  5c 38 36 f8 45 6a b8 1f  67 b2 28 7e 30 6d 5b b7  |\86.Ej..g.(~0m[.|
000001a0  2c 6b 1a b1 dd 2e 8f cf  c2 09 5a a5 fd bb 04 b6  |,k........Z.....|
000001b0  f7 eb 78 0f c0 44 80 0a  38 d3 58 cb 55 8e 00 fe  |..x..D..8.X.U...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 26 4b 49 06 00 fe  |..........&KI...|
000001d0  ff ff 05 fe ff ff 28 4b  49 06 cf b3 73 09 00 00  |......(KI...s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


Output for fdisk:

```

ubuntu@ubuntu:~$ sudo fdisk -l && df -h

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd3c5204

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         630     5060443+  82  Linux swap / Solaris
/dev/sda2   *         631        6391    46275232+  83  Linux
/dev/sda3            6392       11220    38788942+  83  Linux
/dev/sda4           11221       60801   398259352    5  Extended
/dev/sda5           11221       17785    52733331   83  Linux
/dev/sda6           17786       27656    79288776   83  Linux
/dev/sda7           27657       37527    79288776   83  Linux
/dev/sda8           37528       40799    26282308+  83  Linux
/dev/sda9           40800       44071    26282308+  83  Linux
/dev/sda10          50637       55718    40821133+  83  Linux
/dev/sda11          55719       56977    10112886   83  Linux
/dev/sda12          44072       50636    52733331    7  HPFS/NTFS
/dev/sda13          56978       60801    30716248+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         637     5116671   82  Linux swap / Solaris
/dev/sdc2   *         638        4865    33961410    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a357f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       63742   512000000    7  HPFS/NTFS
Filesystem            Size  Used Avail Use% Mounted on
aufs                  881M   47M  834M   6% /
udev                  881M  304K  881M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  881M  1.5M  879M   1% /dev/shm
tmpfs                 881M  120K  881M   1% /tmp
none                  881M   88K  881M   1% /var/run
none                  881M     0  881M   0% /var/lock
none                  881M     0  881M   0% /lib/init/rw
/dev/sdd1             489G  125G  364G  26% /media/AaLee
ubuntu@ubuntu:~$ 
```


Copy of /etc/fstab:

/etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda2 during installation
UUID=84781de9-0f61-474c-a56e-d6f455826462 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none swap sw 0 0
# swap was on /dev/sdb1 during installation
UUID=d898c458-3a28-4abf-9a28-c34d356c0046 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```

I do not know what other information I need to provide here. Is it hardware, software or is it just time to build another putter because evidently, I can not clean install Karmic any more (update route may be open though) on this 3 year old antique machine.  By the way, I was using 3rd. party proprietary nvidia driver version 185 for g6150 on board graphics.  This driver was offered right after the initial installation of Karmic. 

Please assist and let me know if anything else is needed.

**Thanks for your time and help.**

Danial

---

### Post by Danial on 2011-02-21
Well ](*,)

I guess, I have to settle for a re-install of Lucid and see where I go from there.  

Danial

---

### Post by x1a4 on 2011-02-21
Hi,

Have a look in /var/log/dmesg for clues.  Is the battery on the main board still good?  Reset BIOS to default settings (make a note of current ones first).  Are all the cables and wires (inside and out) properly plugged-in?  Do a memory test.  Do a hard drive test.  Get the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") which contains all sorts of diagnostic tools.  

I'm sorry I couldn't be of more help.  Hopefully this will get you on your way to diagnosing and fixing the problem.  Good luck.

---

### Post by Danial on 2011-02-21
> **x1a4 said:**
> Hi,

Have a look in /var/log/dmesg for clues.  Is the battery on the main board still good?  Reset BIOS to default settings (make a note of current ones first).  Are all the cables and wires (inside and out) properly plugged-in?  Do a memory test.  Do a hard drive test.  Get the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") which contains all sorts of diagnostic tools.  

I'm sorry I couldn't be of more help.  Hopefully this will get you on your way to diagnosing and fixing the problem.  Good luck.

You are a **Good Help** by all means, Thanks. I have checked all the cables (reseating those), checked memory and reseated - ran disk check on all partitions.  **The only thing I had not done is bios reset and battery check.**  Come to think about it, that battery is almost 3 years old now - and I don't know their life cycle.  I will get the boot CD you mentioned and will check the log message for any possible clues.  I will report my findings later.

Your help and guidance is very appreciated.

Danial

---

