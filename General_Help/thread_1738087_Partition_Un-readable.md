---
title: "Partition Un-readable"
date: 2011-04-24
forum: General Help
---

### Post by DA14 on 2011-04-24
Fist of all I would like to say I'm relatively new to Ubuntu and not exactly a programmer, I have been using it since Dec 2010, and several weeks ago I updated to the 11.04 alpha 3 release (I think this could have something to do with it).

I am meant to be dual booting Ubuntu and Windoze XP. My Problem is, my old windows partition is "un-readable" (if this is the correct terminology) and basically it says it has 39.1gb used and 11.5gb free space, yet it contains nothing, While using 10.04/10.10 ubuntu I used to be able to read all the files and modify it's contents but since I got 11.04 (I am now on beta release) the partition has been unreadable. Whenever I try to boot windows at grub it starts but just before the XP boot screen it stops working and goes quiet (it crashes as it only takes one press of the off button). I have searched all over the internet for my problem but it doesn't seem anyone else has had it :(,either that or it's extremely simple and I'm just a noob.

I have checked the disk using disk utility many times and it says it's fine and healthy. Before someone says "Have you mounted it?" Yes I have. I also have the necessary permissions to view and edit it and they are not hidden files. I have considered reformating it but that is not exactly ideal as I have several important pieces of school work on there. The partition is bootable NTFS. Please help :confused:

---

### Post by kiyop on 2011-04-24
I am not sure the reason is related to 11.04 beta.
How about booting with Ubuntu live CD (version under 10.10) and getting the result of boot info script and submitting to "reply" in this thread?

Boot info script can be obtained from:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

And I wonder if the permission of your windows partition has problem.
Please boot Ubuntu 11.04 beta and open terminal:
"Application" -> "Accessory" -> "Terminal"
and type:
```
mount
```and copy and paste the result into "reply" and submit.

---

### Post by DA14 on 2011-04-24
Okay I did the script on the Live CD copied the Results.txt over to my partition that worked and the file is empty for whatever reason so I will do it on my 11.04 in the interest of saving time...

---

### Post by DA14 on 2011-04-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,578,894    12,578,832  83 Linux
/dev/sda2    *     12,578,895   118,623,959   106,045,065   b W95 FAT32
/dev/sda3         118,624,254   156,301,311    37,677,058   5 Extended
/dev/sda5         118,624,256   154,636,287    36,012,032  83 Linux


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ?             0            -1                   Unknown
/dev/sdb2     ?             0            -1                   Unknown
/dev/sdb3     ?             0            -1                   Unknown
/dev/sdb4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6a036438-3d00-4b7f-8f07-9bde6ce87c19   ext4       Linux Storage                 
/dev/sda2        A0B45169B4514348                       ntfs       PRESARIO                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        49aaa35a-2962-4f26-9262-22b3b2bffcb3   ext4       Linux                         
/dev/sda: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory
error: /dev/sdb2: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Linux Storage     ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-7-generic ...'
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-5-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-5-generic ...'
	linux	/boot/vmlinuz-2.6.38-5-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 43e9-d933
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root A0B45169B4514348
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
UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2c231f45-31f6-4215-8893-94b78968d1b6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  63.0GB: boot/grub/core.img
  70.3GB: boot/grub/grub.cfg
  63.5GB: boot/initrd.img-2.6.32-28-generic
  60.8GB: boot/initrd.img-2.6.38-5-generic
  74.6GB: boot/initrd.img-2.6.38-7-generic
  62.9GB: boot/initrd.img-2.6.38-8-generic
  63.4GB: boot/vmlinuz-2.6.32-28-generic
  71.9GB: boot/vmlinuz-2.6.38-5-generic
  74.0GB: boot/vmlinuz-2.6.38-7-generic
  63.9GB: boot/vmlinuz-2.6.38-8-generic
  62.9GB: initrd.img
  74.6GB: initrd.img.old
  63.9GB: vmlinuz
  74.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb


Unknown BootLoader  on sda3

00000000  2b 32 32 1b 71 bd 58 e3  31 e9 29 76 8e 26 bd ee  |+22.q.X.1.)v.&..|
00000010  10 15 fc 68 ef a7 c4 5b  14 f5 d6 f5 23 25 fd b7  |...h...[....#%..|
00000020  3d 47 b5 a6 c9 58 d6 d1  a9 6f 26 aa 21 83 f7 0b  |=G...X...o&.!...|
00000030  09 ba 05 38 1b 68 df df  dd 50 4d 67 b7 78 51 c8  |...8.h...PMg.xQ.|
00000040  19 39 d0 c5 18 75 06 90  42 6a 68 ee e0 83 be 44  |.9...u..Bjh....D|
00000050  e2 f1 b6 44 7e 1d f4 d6  8a 9b 15 87 5a 99 4d cb  |...D~.......Z.M.|
00000060  74 fd 62 ff c7 90 f2 7e  b1 8a 4f 00 ea 42 3a 1f  |t.b....~..O..B:.|
00000070  bf 92 fb 9f 31 40 ed 41  fc 6a d7 f9 cb 7f 35 8d  |....1@.A.j....5.|
00000080  da 43 9b 4e f9 7c 2f bd  a7 ba ba cf 5b 2d 7e 00  |.C.N.|/.....[-~.|
00000090  c2 c5 6c bc f9 49 47 46  b8 37 e0 aa 47 ff 2a 6f  |..l..IGF.7..G.*o|
000000a0  0a 67 22 0f 07 19 93 17  5e 9a 9b 2d 3b 15 ea 3a  |.g".....^..-;..:|
000000b0  e2 a3 17 0a 4d 6f 6c 11  8d 6e bb 5f 98 f9 5a bf  |....Mol..n._..Z.|
000000c0  ca 74 7b 0e ce 0d 29 e0  70 04 44 0b 20 3b ca e7  |.t{...).p.D. ;..|
000000d0  5a ad 7b 19 75 79 ad d6  cb de bd a4 8b ad 27 2d  |Z.{.uy........'-|
000000e0  de 80 ad f5 87 c1 ff 74  ac 0b d8 6f 5a 91 eb fa  |.......t...oZ...|
000000f0  da 16 e5 7d f2 65 7c a5  be fe 50 9d d9 aa 2f 32  |...}.e|...P.../2|
00000100  99 bb aa 5f d3 c2 8f 8c  1b cb b6 5f dc c3 3e 5a  |..._......._..>Z|
00000110  7a ed 5d ef 30 8e 3c 96  dd 71 e5 74 dc 57 a4 0c  |z.].0.<..q.t.W..|
00000120  15 f4 69 f0 1b 10 83 e2  d1 79 f5 f7 ab c2 0b 98  |..i......y......|
00000130  84 6b a1 60 63 dc 65 1d  46 67 0b 20 9b 1d d9 18  |.k.`c.e.Fg. ....|
00000140  21 43 1d a8 ec 72 4b ea  0e f5 34 7d 38 75 e5 17  |!C...rK...4}8u..|
00000150  b0 22 32 38 91 cf d0 3c  83 14 cd 7d 49 5a 4d 2c  |."28...<...}IZM,|
00000160  87 ae 2a 81 d1 24 e4 5f  a1 17 0e 70 9f 7e 4d c0  |..*..$._...p.~M.|
00000170  40 d9 ca 3f f7 52 73 3e  cd be a1 ff c8 3b a2 91  |@..?.Rs>.....;..|
00000180  3b e9 83 5e aa 52 9f 72  ea c8 33 73 e0 91 3b 12  |;..^.R.r..3s..;.|
00000190  83 89 ea 62 d1 99 6f 07  05 23 6d 05 1e 38 b5 74  |...b..o..#m..8.t|
000001a0  73 ab b6 07 99 40 c4 a2  97 83 dc db 6c 57 a2 61  |s....@......lW.a|
000001b0  61 14 a1 1b 6f 59 89 4e  4d d5 e9 54 39 e8 00 fe  |a...oY.NM..T9...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 25 02 00 00  |............%...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
ls: reading directory sda2/: Input/output error
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory 
```

---

### Post by DA14 on 2011-04-24
Any ideas? Or will I have to reformat and set about doing some coursework? :(

---

### Post by kiyop on 2011-04-24
Now, I do not have enough time to tell you many things.
I think you need not reformat /dev/sda2 (Windows System Partition).
There may be some way to recover files, including testdisk and photorec.

Please wait until I or another person give you some hint.

---

### Post by oldfred on 2011-04-24
What is sdb? Boot script does not parse it.

Your windows in sda2 looks ok, but the grub menu shows a windows install in sda1 which is now a Linux partition. Is that correct or not?

Boot script v0.55 does not parse Natty's grub1.99 well. They are working on an updated version.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by kiyop on 2011-04-25
Thanks oldfred.

DA14,

Please get the newer version of boot info script as written in [#8]("http://ubuntuforums.org/showthread.php?p=10716490#post10716490") and use it and submit the result.

By the way, did you change the filesystem (format) of /dev/sda1?

Could you see any files and directories if you boot with Ubuntu LiveCD and type in terminal:
```
sudo mount -t ntfs-3g /dev/sda2 /mnt -o ro && sudo nautilus /mnt
```

---

### Post by DA14 on 2011-04-25
Sbd is an old hard drive which for some reason cannot be formatted and I have not yet got round to removing it :P , XP was installed in sda2 and sda1 used to be a recovery windows 2000/nt, a long time ago before I formatted it to Ext4, I figured why would I ever want to recover into windows when I could just use a Ubuntu Live CD and I needed storage so it seemed a good idea. I found that sda2 has a Superblock error but I really don't know what effect that could have.```
               Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    12,578,894    12,578,832  83 Linux
/dev/sda2    *     12,578,895   118,623,959   106,045,065   b W95 FAT32
/dev/sda3         118,624,254   156,301,311    37,677,058   5 Extended
/dev/sda5         118,624,256   154,636,287    36,012,032  83 Linux


Drive: sdb _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6a036438-3d00-4b7f-8f07-9bde6ce87c19   ext4       Linux Storage
/dev/sda2        A0B45169B4514348                       ntfs       PRESARIO
/dev/sda5        49aaa35a-2962-4f26-9262-22b3b2bffcb3   ext4       Linux

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Linux Storage     ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-7-generic ...'
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.38-5-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.38-5-generic ...'
	linux	/boot/vmlinuz-2.6.38-5-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 49aaa35a-2962-4f26-9262-22b3b2bffcb3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 43e9-d933
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root A0B45169B4514348
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=49aaa35a-2962-4f26-9262-22b3b2bffcb3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2c231f45-31f6-4215-8893-94b78968d1b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  58.696449280 = 63.024832512   boot/grub/core.img                             1
  65.511230469 = 70.342148096   boot/grub/grub.cfg                             2
  59.149188995 = 63.510958080   boot/initrd.img-2.6.32-28-generic              1
  73.619140625 = 79.047950336   boot/initrd.img-2.6.38-5-generic               2
  69.516696930 = 74.642984960   boot/initrd.img-2.6.38-7-generic               2
  58.638881683 = 62.963019776   boot/initrd.img-2.6.38-8-generic               2
  59.073474884 = 63.429660672   boot/vmlinuz-2.6.32-28-generic                 1
  67.010074615 = 71.951519744   boot/vmlinuz-2.6.38-5-generic                  1
  68.955383301 = 74.040279040   boot/vmlinuz-2.6.38-7-generic                  1
  59.596008301 = 63.990726656   boot/vmlinuz-2.6.38-8-generic                  2
  58.638881683 = 62.963019776   initrd.img                                     2
  69.516696930 = 74.642984960   initrd.img.old                                 2
  59.596008301 = 63.990726656   vmlinuz                                        2
  68.955383301 = 74.040279040   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb


Unknown BootLoader on sda3

00000000  2b 32 32 1b 71 bd 58 e3  31 e9 29 76 8e 26 bd ee  |+22.q.X.1.)v.&..|
00000010  10 15 fc 68 ef a7 c4 5b  14 f5 d6 f5 23 25 fd b7  |...h...[....#%..|
00000020  3d 47 b5 a6 c9 58 d6 d1  a9 6f 26 aa 21 83 f7 0b  |=G...X...o&.!...|
00000030  09 ba 05 38 1b 68 df df  dd 50 4d 67 b7 78 51 c8  |...8.h...PMg.xQ.|
00000040  19 39 d0 c5 18 75 06 90  42 6a 68 ee e0 83 be 44  |.9...u..Bjh....D|
00000050  e2 f1 b6 44 7e 1d f4 d6  8a 9b 15 87 5a 99 4d cb  |...D~.......Z.M.|
00000060  74 fd 62 ff c7 90 f2 7e  b1 8a 4f 00 ea 42 3a 1f  |t.b....~..O..B:.|
00000070  bf 92 fb 9f 31 40 ed 41  fc 6a d7 f9 cb 7f 35 8d  |....1@.A.j....5.|
00000080  da 43 9b 4e f9 7c 2f bd  a7 ba ba cf 5b 2d 7e 00  |.C.N.|/.....[-~.|
00000090  c2 c5 6c bc f9 49 47 46  b8 37 e0 aa 47 ff 2a 6f  |..l..IGF.7..G.*o|
000000a0  0a 67 22 0f 07 19 93 17  5e 9a 9b 2d 3b 15 ea 3a  |.g".....^..-;..:|
000000b0  e2 a3 17 0a 4d 6f 6c 11  8d 6e bb 5f 98 f9 5a bf  |....Mol..n._..Z.|
000000c0  ca 74 7b 0e ce 0d 29 e0  70 04 44 0b 20 3b ca e7  |.t{...).p.D. ;..|
000000d0  5a ad 7b 19 75 79 ad d6  cb de bd a4 8b ad 27 2d  |Z.{.uy........'-|
000000e0  de 80 ad f5 87 c1 ff 74  ac 0b d8 6f 5a 91 eb fa  |.......t...oZ...|
000000f0  da 16 e5 7d f2 65 7c a5  be fe 50 9d d9 aa 2f 32  |...}.e|...P.../2|
00000100  99 bb aa 5f d3 c2 8f 8c  1b cb b6 5f dc c3 3e 5a  |..._......._..>Z|
00000110  7a ed 5d ef 30 8e 3c 96  dd 71 e5 74 dc 57 a4 0c  |z.].0.<..q.t.W..|
00000120  15 f4 69 f0 1b 10 83 e2  d1 79 f5 f7 ab c2 0b 98  |..i......y......|
00000130  84 6b a1 60 63 dc 65 1d  46 67 0b 20 9b 1d d9 18  |.k.`c.e.Fg. ....|
00000140  21 43 1d a8 ec 72 4b ea  0e f5 34 7d 38 75 e5 17  |!C...rK...4}8u..|
00000150  b0 22 32 38 91 cf d0 3c  83 14 cd 7d 49 5a 4d 2c  |."28...<...}IZM,|
00000160  87 ae 2a 81 d1 24 e4 5f  a1 17 0e 70 9f 7e 4d c0  |..*..$._...p.~M.|
00000170  40 d9 ca 3f f7 52 73 3e  cd be a1 ff c8 3b a2 91  |@..?.Rs>.....;..|
00000180  3b e9 83 5e aa 52 9f 72  ea c8 33 73 e0 91 3b 12  |;..^.R.r..3s..;.|
00000190  83 89 ea 62 d1 99 6f 07  05 23 6d 05 1e 38 b5 74  |...b..o..#m..8.t|
000001a0  73 ab b6 07 99 40 c4 a2  97 83 dc db 6c 57 a2 61  |s....@......lW.a|
000001b0  61 14 a1 1b 6f 59 89 4e  4d d5 e9 54 39 e8 00 fe  |a...oY.NM..T9...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 25 02 00 00  |............%...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sdb: Input/output error
unlzma: Decoder error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
ls: reading directory sda2/: Input/output error

```
Oh and thankyou guys for helping me and persevering with my useless skill :)

---

### Post by kiyop on 2011-04-25
I do not know well about the result of boot info script.
But, there are many symptoms showing that /dev/sda2 got some problems.
[quote=DA14 #1]my old windows partition is "un-readable" (if this is the correct  terminology) and basically it says it has 39.1gb used and 11.5gb free  space, yet it contains nothing, While using 10.04/10.10 ubuntu I used to be able to read all the files  and modify it's contents but since I got 11.04 (I am now on beta  release) the partition has been unreadable. Whenever I try to boot  windows at grub it starts but just before the XP boot screen it stops  working and goes quiet[/quote]
[quote=DA14 #10]Sbd is an old hard drive which for some reason cannot be formatted and I have not yet got round to removing it.
...
 I found that sda2 has a Superblock error
...
ls: reading directory sda2/: Input/output error[/quote]

Is there any more detail information on error on /dev/sda2?

How about executing the following?
```
sudo mount -t ntfs-3g /dev/sda2 /mnt -o ro && sudo nautilus /mnt
```

I may suggest you to check disk (chdsk) by booting with Windows XP install CD and dropping into recovery console.
But I am not sure if it can solve the problem.

If you want to recover important files, photorec may be able to recover.
photorec can be used in booting with Ubuntu Live CD, by
```
sudo apt-get update
sudo apt-get install testdisk
sudo photorec
```Refer to
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by oldfred on 2011-04-25
If you do not have good backups photorec is a way to recover data. But it just scans drives for parts that look like a file. It does not recovery file names. I used it and got huge amounts of data. I had saved a text file many times and have room on drive so it recovered all the old versions. I was never sure I recovered the last saved version, but between backups & versions recovered got most of my data back.

I would run chkdsk on the NTFS partition.
To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Usually chkdsk works, but occasionally testdisk can fix a partition that chkdsk does not.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by kiyop on 2011-04-25
Thanks oldfred (again).
Not "chdsk", but "chkdsk".

---

### Post by btindie on 2011-04-25
I'm not sure if this is the cause of your problem or how it could have happened but I did notice that your Windows partition is marked as FAT32

> /dev/sda2    *     12,578,895   118,623,959   106,045,065   b W95 FAT32when it's reported as being NTFS by the output from blkid. I don't know if this could be causing Windows XP to be getting confused?

I think for an NTFS partition it should have an ID of 7, for example
> /dev/sda1   *           1       14731   111366328+   7  HPFS/NTFSSo I don't know if by changing the partition ID from B to 7 could fix it for you?

```
$ sudo fdisk /dev/sda
  p  # print partition table
  t  # toggle partition id
  2  # partition 2
  7  # set partition id to 7 NTFS
  p  # print partition table
  w  # write partition table to disk and exit
```

---

### Post by oldfred on 2011-04-25
XP used to install to FAT partitions, so it could be an install to FAT32?

Vista & 7 only install to NTFS partitions.

---

### Post by DA14 on 2011-04-25
Basically heres where it gets more complex for me, to access the internet i have to use a wireless adapter, this has windows drivers but it doesn't quite run right and takes around half an hour to connect(if it will even do that sometimes i have to repeatedly reboot) and booting into a Live CD normally takes around 40 minutes, so anything in a live CD is quite a tiresome process for me.
I would use the XP recovery disk if I had one, I brought this PC from "PC World" in 2005 and it came with XP all ready installed and they did not give me an install/recovery disk as they probably should have done. I have just tried nautilus again and the exact same results: 0 files. I changed the partition type to NTFS instead of W95 Fat32 and same results. I may just give up on this entire thing and reformat it, I've had some time to redo the majority of my coursework so all I will really be losing is XP and that's not real loss is it? :D ,unless you guys want to keep looking for a solution for your own education and the sake of the Ubu-movement then be my guest to keep helping (: .
Since my last post I've had the friend of mine who introduced me to linux trying to help but he can't seem to find the solution either, I think he executed chkdsk (or a similar command in terminal) and there was nothing out of the ordinary.
I can also tell you if I use disk Utility to "check file system" it says:
"**File system check on "PRESARIO" (Partition 2 of ATA HDS728080PLAT20) completed**
File system is clean."
Seems it's fine just that I can't look at the contents even though I have permissions.
I won't start reformatting yet but if you think that would be an easier idea and do not mind admitting defeat then I will oblige.

---

### Post by kiyop on 2011-04-25
If you do not need Windows XP nor data in /dev/sda2, formatiing /dev/sda2 is simple way to use /dev/sda2.

Thanks to btindie, I noticed that inconsistent reports on filesystem of /dev/sda2 (ntfs or fat32).
I am not sure whether the inconsistency is due to boot info script or not.

If you run chkdsk or checking by disk utility (in Ubuntu?) when the filesystem of /dev/sda2 is ntfs, how about using testdisk to change it to fat32 and then run "check disk" again. 
Or vice versa.

There are many information on filesystem, for example, on MBR partition table, partition boot record, and sectors after the partition boot record.
If you accidentally changed any of the above without changing others, you would have "apparently" lost all files and directories in the partition maybe.

You can distinguish between fat32 and ntfs by dd.
```
sudo dd if=/dev/sda2 bs=512 count=1|hd
```

Refer to 
[http://iss.x0.com/Useful/Partition_Boot_Record.html](http://iss.x0.com/Useful/Partition_Boot_Record.html)
(written in Japanese)

---

### Post by DA14 on 2011-04-26
Thank you for the help everyone but I think I'll just format it now because I don't need XP or the files on it any more, If it were more simple I wouldn't mind getting the files back but all I would really want now is my music collection (around 900 songs) but I can start another one :)

Kiyop, "disk utility (in Ubuntu?) when the filesystem of /dev/sda2 is ntfs, how about using testdisk to change it to fat32 and then run "check disk" again. " First of all, disk utility is in ubuntu, not sure if it's exclusive to 11.04 but it is in ubuntu and I shall post a screen shot of it below to show you what I used to check the disks and what I will use to format it. Also I have done check disk while it was Fat32 and NTFS and they both report the same. 

So thanks everyone, you have all showed me what a nice and helpful community ubuntu has and I probably would've broken my computer by now if you guys wasn't here to help. :)

---

### Post by kiyop on 2011-04-26
Yes I think it is simple to format although you will lose your files in /dev/sda2.

But,
> **DA14 said:**
> all I would really want now is my music collection (around 900 songs) but I can start another one :)

You may be able to recover songs files in /dev/sda2 by photorec, which is able to be installed by "sudo apt-get install testdisk" on ubuntu, as written in [#11](http://ubuntuforums.org/showpost.php?p=10718153&postcount=11)

---

