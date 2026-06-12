---
title: "Problem with Gub (I think)"
date: 2010-10-22
forum: General Help
---

### Post by Ianman on 2010-10-22
Hi everyone,

I just installed 10.10 and its been a while since I used Ubuntu but I have run into a small problem. Here is the situation:

1. I had to do the installation twice
2. During the first installation while setting up partitions, I overlooked a setting, namely that the bootloader was to be installed on an external USB disk. This was selected by default.
3. I ran through the rest of the setup and when I rebooted, I did not see Grub. Logical because it was installed onto the wrong disk which I did not realise at this moment.
4. So I ran the setup again as I am still really new to Linux
5. This second time is when I realised that the bootloader was installed onto an external usb disk. So I corrected that and finished the installation
6. Now I am able to boot into Ubuntu but when I select Ubuntu, the first thing that pops up on the screen is that a specific deb cannot be found in /lib/modules/2.6.35-22-generic. I am guessing this has to do with my mistake the during the first installation

How do I fix this? Is it something I have to configure in grub?

Thanks!!

---

### Post by Rubi1200 on 2010-10-22
Does running ```
sudo dpkg --configure -a
``` return errors?

If you can boot into Ubuntu, please also post the results of the boot-script linked at the bottom of my post. 

Wrap the text with the # tag when replying please.

Thanks.

---

### Post by Ianman on 2010-10-24
Hi Rubi1200,

Sorry for not getting back sooner!

By the way the actual error is:
"modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory."


I have run the script you requested and here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   409,602,047   409,395,200   7 HPFS/NTFS
/dev/sdb3         409,602,048 1,756,703,798 1,347,101,751   7 HPFS/NTFS
/dev/sdb4       1,756,704,766 1,953,523,711   196,818,946   5 Extended
/dev/sdb5       1,756,704,768 1,758,703,615     1,998,848  82 Linux swap / Solaris
/dev/sdb6       1,758,705,664 1,953,523,711   194,818,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4E88E52788E50E71                       ntfs       Downloads                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FEACFC39ACFBE9D3                       ntfs       System Reserved               
/dev/sdb2        ACB6097AB6094674                       ntfs                                     
/dev/sdb3        2E76F01476EFDA9B                       ntfs       STUFF                         
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        e60dba86-5e08-4007-83bb-9439a67a7d79   swap                                     
/dev/sdb6        85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4 ro  vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4 ro single  vga=792 splash
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 85de6eeb-f8eb-4b82-a35d-e1cdcd8520c4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set feacfc39acfbe9d3
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 993.0GB: boot/grub/core.img
 993.0GB: boot/grub/grub.cfg
 901.5GB: boot/initrd.img-2.6.35-22-generic
 993.0GB: boot/vmlinuz-2.6.35-22-generic
 901.5GB: initrd.img
 993.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  46 cb c7 57 af e9 40 59  6e bd 1c 4e 4f 56 57 8f  |F..W..@Yn..NOVW.|
00000010  1c 5b b9 56 23 4c 1a 24  01 f7 4b c7 54 09 77 72  |.[.V#L.$..K.T.wr|
00000020  b9 6e ed 0a 5e 12 82 4d  47 10 11 14 c9 a9 f6 22  |.n..^..MG......"|
00000030  23 28 4e ac be 75 a5 bd  3a be ed 5e 95 f9 37 a7  |#(N..u..:..^..7.|
00000040  e7 41 c4 3f 92 47 c4 5e  6d 2c 0b 1a 86 6b 73 70  |.A.?.G.^m,...ksp|
00000050  25 14 be 9a 79 01 b0 98  dd f6 7b 2c 1a 59 ca 95  |%...y.....{,.Y..|
00000060  aa 07 40 70 9f 52 c4 91  b6 27 fa da ae 88 f9 34  |..@p.R...'.....4|
00000070  b5 65 7b 9b 8c 9d 0b 13  e2 8b 06 f1 b1 ac d5 26  |.e{............&|
00000080  4d 78 0f d7 6d 40 68 44  0a 47 03 78 5d d9 45 af  |Mx..m@hD.G.x].E.|
00000090  f2 1f b8 eb 44 04 3f a4  11 72 81 76 20 c7 2c 8b  |....D.?..r.v .,.|
000000a0  61 c1 11 bc 41 66 4b 5f  53 29 b7 69 12 26 23 6b  |a...AfK_S).i.&#k|
000000b0  2c eb d2 6a 9f b4 ba b3  d1 13 c0 af 92 42 58 c7  |,..j.........BX.|
000000c0  3d 71 26 f3 19 ee b8 b4  ba 32 0e f9 ed d6 fa e6  |=q&......2......|
000000d0  58 c9 59 53 38 01 68 86  fa 2c a2 57 07 7d e8 c6  |X.YS8.h..,.W.}..|
000000e0  fe 15 a1 29 47 10 11 15  87 4b 06 2f 84 02 f3 59  |...)G....K./...Y|
000000f0  37 c9 16 b0 46 89 2e b0  5b 59 f5 30 3e 89 e5 9a  |7...F...[Y.0>...|
00000100  8a af 9c 22 4f 9c 21 93  17 99 5b 26 3e 4d 75 bc  |..."O.!...[&>Mu.|
00000110  f5 85 bf 64 1d 59 c3 f8  1a eb 6d fa d7 dc b9 52  |...d.Y....m....R|
00000120  b8 2e ea 21 57 6f 9e f3  7f ea 45 47 32 51 d8 af  |...!Wo....EG2Q..|
00000130  eb 8c 4b af 0a 78 15 6d  b8 4e 52 4e 21 ff 14 f3  |..K..x.m.NRN!...|
00000140  94 07 a5 e4 7c 30 30 62  20 70 2d e4 b9 60 ec d7  |....|00b p-..`..|
00000150  ff 00 3a 72 98 c4 68 dc  e7 78 70 cd ba 51 ca 86  |..:r..h..xp..Q..|
00000160  0f dc e8 2d ce 9c 8f 82  36 07 e6 2c b3 51 29 10  |...-....6..,.Q).|
00000170  fb bb 0e d4 1b 0a 9b 81  fb d4 23 03 17 e3 de 5c  |..........#....\|
00000180  40 a9 f3 d7 f8 e2 ae d5  60 a5 5c 09 41 fe f0 05  |@.......`.\.A...|
00000190  7e ba 6a dd 09 6d 50 4e  65 68 16 a1 bc 18 3c 70  |~.j..mPNeh....<p|
000001a0  47 10 11 16 8f c6 a0 81  ea 1c 5f 71 83 2b b3 9e  |G........._q.+..|
000001b0  92 61 b0 18 27 fb ac 3f  c9 e4 8d 1e 36 0d 00 fe  |.a..'..?....6...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 1e 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  1e 00 00 b8 9c 0b 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Many thanks for your help!

Kind Regards,
Ian

---

