---
title: "Dual boot - Seperate Drves - Change Grub? With Maverick 64"
date: 2011-01-29
forum: General Help
---

### Post by BorisPlankton on 2011-01-29
Hi,
I have dual boot thing going successfully with two separate hard drives. I have decided to remove the windows Drive and just go Linux. However when I disconnect the windows drive then I cannot boot at all.
Do I need to edit grub and if so how?
A while back (prob Karmic) I was sure if I simply took either drive off line then booting worked to both drives.
Anyway grateful for advice.

---

### Post by sikander3786 on 2011-01-29
In that case, it would be better to install Grub to the MBR of your Ubuntu hard disk instead of the Windows one.

But before we do that, we need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would let us see you setup and give you exact commands just to copy/paste in your Terminal and you'll be ready to go.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by BorisPlankton on 2011-01-29
OK I will post the info tom. Apologies but I should have made it clear I intend to format my 'XP' drive. I am only worried about when I do this. Presumably after the above grub action. What has topped me doing already is that when I remove the windows hard drive currently nothing boots. So if I format it and remove windows I might run into trouble.
Grateful for advice.

---

### Post by sikander3786 on 2011-01-29
Thats why I think you need to install Grub to your Ubuntu HDD so that you can boot Ubuntu independent of the other HDD. But, make sure your Bios is capable of booting your 2nd HDD.

Lets see the boot script output.

---

### Post by BorisPlankton on 2011-01-30
> **sikander3786 said:**
> Thats why I think you need to install Grub to your Ubuntu HDD so that you can boot Ubuntu independent of the other HDD. But, make sure your Bios is capable of booting your 2nd HDD.

Lets see the boot script output.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   964,847,834   964,847,772   7 HPFS/NTFS
/dev/sda2         964,847,896   976,768,064    11,920,169   5 Extended
/dev/sda5         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    19,531,775    19,529,728  83 Linux
/dev/sdb2          19,533,822   976,771,071   957,237,250   5 Extended
/dev/sdb5          19,533,824    23,828,479     4,294,656  82 Linux swap / Solaris
/dev/sdb6          23,830,528   976,771,071   952,940,544  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F80C23880C23414C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9d998921-e8b1-4b95-a5e3-aaf9af81f74a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6486b6f1-d427-429e-b28a-f58a18476763   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        08b81364-3e4d-4983-bb59-c65cf6031b1b   swap                                     
/dev/sdb6        a1aefad4-e5fa-4444-aca3-c705c91bb0d3   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6486b6f1-d427-429e-b28a-f58a18476763 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6486b6f1-d427-429e-b28a-f58a18476763
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set f80c23880c23414c
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6486b6f1-d427-429e-b28a-f58a18476763 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=a1aefad4-e5fa-4444-aca3-c705c91bb0d3 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9d998921-e8b1-4b95-a5e3-aaf9af81f74a none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=08b81364-3e4d-4983-bb59-c65cf6031b1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
   5.8GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.35-22-generic
   1.9GB: boot/initrd.img-2.6.35-24-generic
   6.1GB: boot/initrd.img-2.6.35-25-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: boot/vmlinuz-2.6.35-24-generic
   2.0GB: boot/vmlinuz-2.6.35-25-generic
   6.1GB: initrd.img
   1.9GB: initrd.img.old
   2.0GB: vmlinuz
    .6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  66 74 20 57 6f 72 6b 73  20 44 6f 63 75 6d 65 6e  |ft Works Documen|
00000010  74 3c 2f 76 61 6c 75 65  3e 0a 09 09 3c 2f 70 72  |t</value>...</pr|
00000020  6f 70 3e 0a 09 09 3c 70  72 6f 70 20 6f 6f 72 3a  |op>...<prop oor:|
00000030  6e 61 6d 65 3d 22 46 69  6c 65 46 6f 72 6d 61 74  |name="FileFormat|
00000040  56 65 72 73 69 6f 6e 22  3e 3c 76 61 6c 75 65 3e  |Version"><value>|
00000050  30 3c 2f 76 61 6c 75 65  3e 3c 2f 70 72 6f 70 3e  |0</value></prop>|
00000060  0a 09 09 3c 70 72 6f 70  20 6f 6f 72 3a 6e 61 6d  |...<prop oor:nam|
00000070  65 3d 22 54 79 70 65 22  3e 3c 76 61 6c 75 65 3e  |e="Type"><value>|
00000080  77 72 69 74 65 72 5f 4d  53 5f 57 6f 72 6b 73 5f  |writer_MS_Works_|
00000090  44 6f 63 75 6d 65 6e 74  3c 2f 76 61 6c 75 65 3e  |Document</value>|
000000a0  3c 2f 70 72 6f 70 3e 0a  09 09 3c 70 72 6f 70 20  |</prop>...<prop |
000000b0  6f 6f 72 3a 6e 61 6d 65  3d 22 54 65 6d 70 6c 61  |oor:name="Templa|
000000c0  74 65 4e 61 6d 65 22 2f  3e 0a 09 09 3c 70 72 6f  |teName"/>...<pro|
000000d0  70 20 6f 6f 72 3a 6e 61  6d 65 3d 22 44 6f 63 75  |p oor:name="Docu|
000000e0  6d 65 6e 74 53 65 72 76  69 63 65 22 3e 3c 76 61  |mentService"><va|
000000f0  6c 75 65 3e 63 6f 6d 2e  73 75 6e 2e 73 74 61 72  |lue>com.sun.star|
00000100  2e 74 65 78 74 2e 54 65  78 74 44 6f 63 75 6d 65  |.text.TextDocume|
00000110  6e 74 3c 2f 76 61 6c 75  65 3e 3c 2f 70 72 6f 70  |nt</value></prop|
00000120  3e 0a 09 3c 2f 6e 6f 64  65 3e 0a 0a 09 3c 6e 6f  |>..</node>...<no|
00000130  64 65 20 6f 6f 72 3a 6e  61 6d 65 3d 22 54 36 30  |de oor:name="T60|
00000140  32 44 6f 63 75 6d 65 6e  74 22 20 6f 6f 72 3a 6f  |2Document" oor:o|
00000150  70 3d 22 72 65 70 6c 61  63 65 22 3e 0a 09 09 3c  |p="replace">...<|
00000160  70 72 6f 70 20 6f 6f 72  3a 6e 61 6d 65 3d 22 46  |prop oor:name="F|
00000170  6c 61 67 73 22 3e 3c 76  61 6c 75 65 3e 49 4d 50  |lags"><value>IMP|
00000180  4f 52 54 20 41 4c 49 45  4e 20 55 53 45 53 4f 50  |ORT ALIEN USESOP|
00000190  54 49 4f 4e 53 20 33 52  44 50 41 52 54 59 46 49  |TIONS 3RDPARTYFI|
000001a0  4c 54 45 52 20 50 52 45  46 45 52 52 45 44 3c 2f  |LTER PREFERRED</|
000001b0  76 61 6c 75 65 3e 3c 2f  70 72 6f 70 3e 0a 00 fe  |value></prop>...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 27 e3 b5 00 00 00  |..........'.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  a7 f3 4d 61 f7 06 01 5e  bd 75 c2 f4 bb 97 3f 88  |..Ma...^.u....?.|
00000010  dc 2c b3 3e 2a fd 39 ae  f4 25 cf 47 42 30 46 53  |.,.>*.9..%.GB0FS|
00000020  17 14 16 80 da 59 5f 1c  ae ef 88 e3 f5 cb 69 ff  |.....Y_.......i.|
00000030  03 13 ac 5f 6b 4b 63 36  9c 38 93 2c 26 2c 0a 3a  |..._kKc6.8.,&,.:|
00000040  be dd 86 9c 25 4b f0 8a  2c 4b bf a3 49 01 a5 09  |....%K..,K..I...|
00000050  19 ad 7f 03 5c ba 34 69  41 8a 28 6c 1a 28 a5 bb  |....\.4iA.(l.(..|
00000060  ed 61 a9 30 96 a4 39 31  9d 20 a6 c2 14 31 bf 9f  |.a.0..91. ...1..|
00000070  1a 0e 61 75 06 54 7c e4  8d 22 22 2a d7 d7 f1 cc  |..au.T|..""*....|
00000080  70 68 5f f9 81 77 ab 28  a1 d7 5d d1 70 dc 99 c0  |ph_..w.(..].p...|
00000090  0c 47 c3 cf fe e0 3d 38  08 56 1d b3 44 ee a6 54  |.G....=8.V..D..T|
000000a0  66 38 1c fe 36 83 81 ef  da 81 bb ce 11 d1 c0 1f  |f8..6...........|
000000b0  3c cf 6d 62 c2 40 08 3f  d3 06 a6 ab 44 f2 70 8c  |<.mb.@.?....D.p.|
000000c0  5a ac c4 9d fc 8e bb b3  85 c5 3e bb a9 85 50 8a  |Z.........>...P.|
000000d0  71 4a 7e a3 55 50 a7 d5  16 20 51 51 b4 d3 2d 0b  |qJ~.UP... QQ..-.|
000000e0  22 56 ee 1d 08 5f 9e 3c  a3 ca 5d 12 59 3d 12 66  |"V..._.<..].Y=.f|
000000f0  60 e3 84 14 20 ca f6 c8  32 99 ce b6 0b 96 65 76  |`... ...2.....ev|
00000100  23 d2 9c 1f a4 94 74 66  1b 7b df a9 e9 70 de 83  |#.....tf.{...p..|
00000110  19 06 44 3a 31 c3 90 9e  1f 00 55 47 ad 12 7a be  |..D:1.....UG..z.|
00000120  b8 27 10 f2 e5 b3 71 08  b3 13 d1 7b 68 18 f2 94  |.'....q....{h...|
00000130  96 11 f2 b4 1a b4 0d dd  d0 36 f4 71 d8 e8 e0 4a  |.........6.q...J|
00000140  6d c3 7e be 43 e8 55 b0  90 3c 8c 63 86 95 e2 37  |m.~.C.U..<.c...7|
00000150  f0 3e 3b 5e 9b e7 61 eb  97 24 e5 06 50 db 50 d7  |.>;^..a..$..P.P.|
00000160  36 48 68 3c c4 16 de 8f  0d a0 b6 41 8d a7 6d 25  |6Hh<.......A..m%|
00000170  b1 31 f5 9c b5 ed 40 31  df 91 6a db 39 f2 4f fe  |.1....@1..j.9.O.|
00000180  6d fa bd 3c ff 61 f2 5e  3e 7b 7a 3a 68 4e f6 84  |m..<.a.^>{z:hN..|
00000190  3f 8d 2c 61 d8 89 34 d8  eb 10 0c 4f 52 50 bc 1e  |?.,a..4....ORP..|
000001a0  86 b9 6e 57 1a 33 02 46  ad c5 9f 3a 06 be 57 44  |..nW.3.F...:..WD|
000001b0  17 61 33 40 95 5f 88 b1  c7 77 1d 65 04 8e 00 fe  |.a3@._...w.e....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 41 00 00 fe  |............A...|
000001d0  ff ff 05 fe ff ff 02 88  41 00 00 c0 cc 38 00 00  |........A....8..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Hope this does the trick. Grateful for assistance.

---

### Post by sikander3786 on 2011-01-30
From a booted Live CD, go to Applications > Accessories > Terminal and follow the commands below.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Note for the second command it is just sdb without an integer and not sdb1.

After the completion of those commands, shutdown your computer and unplug the Windows drive and boot your PC. Hopefully, it would load Ubuntu successfully.

---

### Post by BorisPlankton on 2011-01-30
It does exactly that. Many thanks Sikander.

---

