---
title: "Another windows 7 boot failure"
date: 2010-12-02
forum: General Help
---

### Post by holmes on 2010-12-02
I have a hp g72-b620us laptop. 
There were three partitions a "HP Tools" a "restore" and "windows" 
I resized the windows partition in windows 7 with EASEUS Partition Master. I installed Ubuntu 10.10 on the new partition. 
Ubuntu boots fine but no windows. When I select Windows 7 it crashes after the animated logo. Please help. Thanks


```
#sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x1d505cb8 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           1         992+  42  SFS 
Partition 1 does not end on cylinder boundary. 
/dev/sda2   *           1          26      203776   42  SFS 
Partition 2 does not end on cylinder boundary. 
/dev/sda3              26       29295   235107287+  42  SFS 
/dev/sda4           29296       60802   253073409    5  Extended 
/dev/sda5           29296       29539     1952768   82  Linux swap / Solaris 
/dev/sda6           29539       30754     9764864   83  Linux 
/dev/sda7           30755       60802   241353728   83  Linux 
lap1@lap1-HP-G72-Notebook-PC:~$ 
```




Here's my boot_info_script 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   470,624,174   470,214,575  42 SFS
/dev/sda4         470,624,254   976,771,071   506,146,818   5 Extended
/dev/sda5         470,624,256   474,529,791     3,905,536  82 Linux swap / Solaris
/dev/sda6         474,531,840   494,061,567    19,529,728  83 Linux
/dev/sda7         494,063,616   976,771,071   482,707,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        A6F4B074F4B047F7                       ntfs       SYSTEM                        
/dev/sda3        EE2E10DB2E109F21                       ntfs       windows                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b6eb8afd-9f6b-4177-93c5-4e4e545414db   swap                                     
/dev/sda6        0f828d22-8e1f-4581-be01-f45fe3e59f06   ext4                                     
/dev/sda7        7a41b0c9-b452-458d-b030-7fbe8b5c3796   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=0f828d22-8e1f-4581-be01-f45fe3e59f06 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=0f828d22-8e1f-4581-be01-f45fe3e59f06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0f828d22-8e1f-4581-be01-f45fe3e59f06 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0f828d22-8e1f-4581-be01-f45fe3e59f06 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0f828d22-8e1f-4581-be01-f45fe3e59f06
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set a6f4b074f4b047f7
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ee2e10db2e109f21
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
UUID=0f828d22-8e1f-4581-be01-f45fe3e59f06 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7a41b0c9-b452-458d-b030-7fbe8b5c3796 /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 249.8GB: boot/grub/core.img
 245.3GB: boot/grub/grub.cfg
 243.9GB: boot/initrd.img-2.6.35-22-generic
 244.4GB: boot/initrd.img-2.6.35-23-generic
 249.8GB: boot/vmlinuz-2.6.35-22-generic
 250.0GB: boot/vmlinuz-2.6.35-23-generic
 244.4GB: initrd.img
 243.9GB: initrd.img.old
 250.0GB: vmlinuz
 249.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 74 00 79 00 50 00 72  00 69 00 76 00 69 00 6c  |.t.y.P.r.i.v.i.l|
00000010  00 65 00 67 00 65 00 0d  00 0a 00 09 00 09 00 09  |.e.g.e..........|
00000020  00 53 00 65 00 54 00 61  00 6b 00 65 00 4f 00 77  |.S.e.T.a.k.e.O.w|
00000030  00 6e 00 65 00 72 00 73  00 68 00 69 00 70 00 50  |.n.e.r.s.h.i.p.P|
00000040  00 72 00 69 00 76 00 69  00 6c 00 65 00 67 00 65  |.r.i.v.i.l.e.g.e|
00000050  00 0d 00 0a 00 09 00 09  00 09 00 53 00 65 00 4c  |...........S.e.L|
00000060  00 6f 00 61 00 64 00 44  00 72 00 69 00 76 00 65  |.o.a.d.D.r.i.v.e|
00000070  00 72 00 50 00 72 00 69  00 76 00 69 00 6c 00 65  |.r.P.r.i.v.i.l.e|
00000080  00 67 00 65 00 0d 00 0a  00 09 00 09 00 09 00 53  |.g.e...........S|
00000090  00 65 00 42 00 61 00 63  00 6b 00 75 00 70 00 50  |.e.B.a.c.k.u.p.P|
000000a0  00 72 00 69 00 76 00 69  00 6c 00 65 00 67 00 65  |.r.i.v.i.l.e.g.e|
000000b0  00 0d 00 0a 00 09 00 09  00 09 00 53 00 65 00 52  |...........S.e.R|
000000c0  00 65 00 73 00 74 00 6f  00 72 00 65 00 50 00 72  |.e.s.t.o.r.e.P.r|
000000d0  00 69 00 76 00 69 00 6c  00 65 00 67 00 65 00 0d  |.i.v.i.l.e.g.e..|
000000e0  00 0a 00 09 00 09 00 09  00 53 00 65 00 44 00 65  |.........S.e.D.e|
000000f0  00 62 00 75 00 67 00 50  00 72 00 69 00 76 00 69  |.b.u.g.P.r.i.v.i|
00000100  00 6c 00 65 00 67 00 65  00 0d 00 0a 00 09 00 09  |.l.e.g.e........|
00000110  00 09 00 53 00 65 00 41  00 75 00 64 00 69 00 74  |...S.e.A.u.d.i.t|
00000120  00 50 00 72 00 69 00 76  00 69 00 6c 00 65 00 67  |.P.r.i.v.i.l.e.g|
00000130  00 65 00 0d 00 0a 00 09  00 09 00 09 00 53 00 65  |.e...........S.e|
00000140  00 53 00 79 00 73 00 74  00 65 00 6d 00 45 00 6e  |.S.y.s.t.e.m.E.n|
00000150  00 76 00 69 00 72 00 6f  00 6e 00 6d 00 65 00 6e  |.v.i.r.o.n.m.e.n|
00000160  00 74 00 50 00 72 00 69  00 76 00 69 00 6c 00 65  |.t.P.r.i.v.i.l.e|
00000170  00 67 00 65 00 0d 00 0a  00 09 00 09 00 09 00 53  |.g.e...........S|
00000180  00 65 00 49 00 6d 00 70  00 65 00 72 00 73 00 6f  |.e.I.m.p.e.r.s.o|
00000190  00 6e 00 61 00 74 00 65  00 50 00 72 00 69 00 76  |.n.a.t.e.P.r.i.v|
000001a0  00 69 00 6c 00 65 00 67  00 65 00 00 00 00 00 08  |.i.l.e.g.e......|
000001b0  00 08 06 73 a0 03 00 00  2a 2a 00 00 a8 02 00 fe  |...s....**......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 98  3b 00 00 08 2a 01 00 00  |........;...*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by HiImTye on 2010-12-02
windows doesnt like to be resized. best case scenario is you defrag right before you resize and it likes it but worst case is that it (at least partially) destroys your windows partition

---

### Post by holmes on 2010-12-02
I guess I should have studied up a little on that one first.
Looks like I'll have to reinstall.
Thanks.

---

### Post by oldfred on 2010-12-02
Somewhere in Windows you tried to create more that the 4 primary partitions and windows automatically converted to SFS partitions which are its LVM which is not compatible with anything. Windows also will not convert back without erasing the entire drive.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

### Post by holmes on 2010-12-02
I'm not completely sure about HP's partitioning scheme anyway.I'm Just going to delete and repartition the entire disk. cheers

---

