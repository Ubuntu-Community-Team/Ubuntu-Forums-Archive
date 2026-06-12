---
title: "missed /var directory, after fsck, PLZ HELP!!!"
date: 2011-09-26
forum: General Help
---

### Post by LarsUb on 2011-09-26
Hi guys, 
Can you please give some directions?, this is the scenario:
While working (many days turned on) normally with my 10.04.2 Lucid amd64bit installation kernel 2.6.32, normal user activities, no sudo, the system seemed slow, so i decided to do a reboot.
But after passing the grub stage, the system sent something like
[INDENT]mounting: /dev/disk  on /root failed; invalid argument
Target filesystem doesn't have /sbin/init.
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a lit of built in commands.
(initramfs)
[/INDENT]
googling it, i found that some inodes on / must be corrected, then i started the liveDVD and runned the e2fsck on the / partition (sdb1), it found some errors and fixed them answering yes to all.
I rebooted again, but now it shows this:
[INDENT]init ureadahead main process (321) terminated with status 5[/INDENT]
That is related to a corrupted fstab file and ureadahead.conf file under /etc, so again started the liveDVD to check those files
- fstab, was using the UUIDdisknumbers, i changed to the proper partitions (/dev/sdb1).
- unreadahead, was 'normal' using the "start on starting mountall", since my installation just use 3 partitions for /, /home, and swap.
After this check, i rebooted again, but the problem persists now with process 319.
[INDENT]init ureadahead main process (319) terminated with status 5[/INDENT]
Again started the liveDVD and realize that my / partition **LACKS of the /var directory**, but in fact it existed previous to the whole problem. So thinking that it could be moved by the fsck process, i looked into the Lost+found folder but its seems empty, no file its found there.

Trying to boot in Recovery mode seems to work but suddenly stops in the same:
[INDENT][2.430449] EXT4-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
init ureadahead main process (325) terminated with status 5[/INDENT]

I've been looking hard for how to recover or reinstall the /var directory (it seems to be strictly needed for the ureadahead to work and boot properly), but no success :( I'm newbie so i'm not sure if just by manually creating (mkdir) the /var directories under / would be enough, or do i have to reinstall again the whole system???. :(
I compiled some apps so it would be hard to reinstall again my whole system  **PLEASE HELP**, my system isn't booting and /var is lost :(
Your directions would be appreciated.

---

### Post by Rubi1200 on 2011-09-26
Hi,
please post the results of the boot info script to help us diagnose the problem.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by LarsUb on 2011-09-26
Hi, thanx for your reply, and just to clarify, i have a dual boot installation with windos(sda) and ubuntu(sdb), 
This is my system's output:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    18,442,619    18,442,557   7 NTFS / exFAT / HPFS
/dev/sda2          18,442,681    39,102,209    20,659,529   f W95 Extended (LBA)
/dev/sda5          18,442,744    39,102,209    20,659,466   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    83,891,429    83,891,367  83 Linux
/dev/sdb2          83,891,491 1,953,520,064 1,869,628,574   f W95 Extended (LBA)
/dev/sdb5          83,891,493   104,856,254    20,964,762  82 Linux swap / Solaris
/dev/sdb6         104,856,318 1,953,520,064 1,848,663,747  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CCD057E7D057D5F4                       ntfs       WIN
/dev/sda5        F470AB1670AADF1C                       ntfs       DATOS
/dev/sdb1        71ecce5d-aa73-409d-b596-32452cad4541   ext4       
/dev/sdb5        2dd6e4ba-cb84-4d5a-9c1c-032c0d286bb9   swap       
/dev/sdb6        e495fe7e-daef-495e-8da2-0cf7c7b7f195   ext4       /home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=71ecce5d-aa73-409d-b596-32452cad4541 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=71ecce5d-aa73-409d-b596-32452cad4541 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 71ecce5d-aa73-409d-b596-32452cad4541
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ccd057e7d057d5f4
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
/dev/sdb1	/               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
/dev/sdb6	/home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
/dev/sdb5	none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.195765972 = 17.390071296   boot/grub/core.img                             1
  16.178119183 = 17.371123200   boot/grub/grub.cfg                             1
  16.195296764 = 17.389567488   boot/initrd.img-2.6.32-28-generic              1
  16.150531292 = 17.341500928   boot/vmlinuz-2.6.32-28-generic                 1
  16.195296764 = 17.389567488   initrd.img                                     1
  16.150531292 = 17.341500928   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  3b f7 1f 8f b5 54 93 c4  3a dc 5c 2e b5 7e 38 e3  |;....T..:.\..~8.|
00000010  75 c3 1f e6 6b d1 35 ed  04 4c 85 d0 10 c0 e4 11  |u...k.5..L......|
00000020  d4 1a f3 4d 7f 49 ba 57  69 2d d0 f9 df c7 12 8f  |...M.I.Wi-......|
00000030  bf fe d2 8f 5f 55 fc bd  02 2c 7c 1e 23 f1 4d d4  |...._U...,|.#.M.|
00000040  fe 44 3a d5 d9 25 49 03  cc e6 99 71 a9 6b 92 de  |.D:..%I....q.k..|
00000050  c5 65 ff 00 09 80 6b 97  63 1f 90 35 10 b2 6f 07  |.e....k.c..5..o.|
00000060  05 36 ee c8 39 e3 eb f4  35 8f e1 9d 4c 47 af db  |.6..9...5...LG..|
00000070  99 24 00 6e 1d 47 7c 8a  ec b4 17 b4 b5 8f c4 56  |.$.n.G|........V|
00000080  d7 76 d0 5b 5c 6a 3a b5  dc 91 4f 3c 23 82 58 f9  |.v.[\j:...O<#.X.|
00000090  52 02 47 2a 0e 08 23 ea  28 03 8f bf b7 d4 9e ef  |R.G*..#.(.......|
000000a0  ec 52 f8 8a 39 ef 77 94  6b 56 be dd 28 3e 9b 4b  |.R..9.w.kV..(>.K|
000000b0  67 3e dd bb d5 0b af 0f  49 6f 70 2d 6e 75 0b 28  |g>......Iop-nu.(|
000000c0  af 18 86 5b 79 6e 15 64  6c e3 1c 13 9e 72 0f e9  |...[yn.dl....r..|
000000d0  5d 14 9a 6d c5 d7 87 2d  7c 3b f6 6d 5e da 55 11  |]..m...-|;.m^.U.|
000000e0  23 da c3 a4 44 63 49 57  6e e9 c5 d9 c0 c3 30 2f  |#...DcIWn.....0/|
000000f0  bf 76 79 c5 6e d9 4f 6f  a2 58 ea 3a 5e a7 e1 6b  |.vy.n.Oo.X.:^..k|
00000100  9d 5a f2 7b c9 a5 32 ad  a0 96 1d 40 bc 85 91 8c  |.Z.{..2....@....|
00000110  a4 15 4c 29 50 43 1f 97  1d 28 b8 8f 3a 93 c3 a6  |..L)PC...(..:...|
00000120  1b 88 ed ee f5 1b 2b 59  e4 20 08 a6 9d 55 f9 e9  |......+Y. ...U..|
00000130  f2 13 9f 4f ae 7d 8d 47  73 e1 b6 b6 ba 96 d6 e7  |...O.}.Gs.......|
00000140  50 b0 82 e1 1f cb 30 cb  74 8a e1 b0 0e 30 4e 73  |P.....0.t....0Ns|
00000150  c8 fc fe b5 e9 16 d7 16  da 26 9f ac 69 ba b7 85  |.........&..i...|
00000160  ef 35 3b ab 99 e7 92 59  21 b5 f3 62 be 57 76 31  |.5;....Y!..b.Wv1|
00000170  93 28 18 4c 02 ab c9 1b  76 f1 54 7c 2d 60 9a 0e  |.(.L....v.T|-`..|
00000180  95 ac 59 6b d1 42 ba 85  e1 4b 75 bb 9e 30 e1 b6  |..Yk.B...Ku..0..|
00000190  db c6 aa c0 9f be aa e5  b9 19 c9 06 81 9c 44 de  |..............D.|
000001a0  1c b6 8e fe df 4f 3a 8d  b4 d7 93 dc 47 6c b0 43  |.....O:.....Gl.C|
000001b0  32 19 37 b1 c7 2b 9c a8  07 ae 7f fd 54 6f 00 fe  |2.7..+......To..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 0a 3d 3b 01 00 00  |......?....=;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

I guess it looks ok, right?
so if this point to a normal thing, could you suggest another workaround??.

---

