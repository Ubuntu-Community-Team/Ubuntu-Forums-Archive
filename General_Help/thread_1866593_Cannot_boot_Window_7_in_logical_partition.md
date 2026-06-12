---
title: "Cannot boot Window 7 in logical partition"
date: 2011-10-21
forum: General Help
---

### Post by siva5 on 2011-10-21
hi 
i have a similar problem. I also have windows 7 and ubuntu 11.10 loaded onto my laptop. but the grub menu does not show the windows OS itself during boot up.
i have put up the results file of the bootscript also.

anyone plz help!!

---

### Post by siva5 on 2011-10-21
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 33177600.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 25310346 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             160,650    33,176,955    33,016,306  83 Linux
/dev/sda3          33,177,598   234,420,479   201,242,882   f W95 Extended (LBA)
/dev/sda5    *     33,177,600    41,123,839     7,946,240   7 NTFS / exFAT / HPFS
/dev/sda6          41,126,463   102,555,630    61,429,168   7 NTFS / exFAT / HPFS
/dev/sda7         102,559,023   163,991,519    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda8         163,991,583   234,420,479    70,428,897   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0B01                              vfat       DellUtility
/dev/sda2        93c09071-d0a7-4321-9bb6-36b433f0c99a   ext4       
/dev/sda5        F88449DE8449A04C                       ntfs       Local Disk
/dev/sda6        544CE9B14CE98DD4                       ntfs       Local Disk
/dev/sda7        56A8F188A8F166C1                       ntfs       
/dev/sda8        EC3005003004D40C                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=93c09071-d0a7-4321-9bb6-36b433f0c99a ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=93c09071-d0a7-4321-9bb6-36b433f0c99a ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=93c09071-d0a7-4321-9bb6-36b433f0c99a ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=93c09071-d0a7-4321-9bb6-36b433f0c99a ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 93c09071-d0a7-4321-9bb6-36b433f0c99a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  16 24 3d 3b 1b c2 ed 3b  58 c9 55 6a 6c 5b 16 51  |.$=;...;X.Ujl[.Q|
00000010  32 05 40 63 eb f0 00 84  cc de 62 b8 d1 b0 bd 24  |2.@c......b....$|
00000020  9b a8 82 fd 61 bc ba 8e  5e de 0b d9 5d d3 9a 63  |....a...^...]..c|
00000030  36 ff 4b 08 c3 91 b8 62  55 e7 19 d6 0c 1f ef 2a  |6.K....bU......*|
00000040  f9 42 f8 d5 b7 34 13 86  aa 64 ca 13 57 b1 b0 1f  |.B...4...d..W...|
00000050  21 44 e1 25 24 84 35 cf  4d 02 e7 ec bc a1 27 cb  |!D.%$.5.M.....'.|
00000060  ba 1b ca c6 6b 75 f5 63  d9 83 06 87 ba a0 58 63  |....ku.c......Xc|
00000070  19 8c fd 79 31 b9 14 44  c9 4f e8 d7 49 86 a7 7e  |...y1..D.O..I..~|
00000080  fa f2 30 22 68 71 33 36  1f 3d 18 21 ed 31 31 50  |..0"hq36.=.!.11P|
00000090  58 9d 9a 24 c0 05 1d 8b  00 7d 72 27 86 fe 4c f0  |X..$.....}r'..L.|
000000a0  99 e4 af 27 0b 4e ee 7d  88 38 e3 e8 56 6f 4c be  |...'.N.}.8..VoL.|
000000b0  23 22 66 ef 59 b1 e8 a6  c5 99 25 45 bc 52 3f 53  |#"f.Y.....%E.R?S|
000000c0  5b e5 08 7b 57 31 60 5e  70 49 c1 c4 ba 73 c1 7a  |[..{W1`^pI...s.z|
000000d0  c4 e8 39 30 ae c6 31 9c  90 9f 3c 63 63 90 b1 3f  |..90..1...<cc..?|
000000e0  30 83 96 44 91 35 39 9d  98 44 c4 6f 9c f8 6e 1a  |0..D.59..D.o..n.|
000000f0  ba a9 25 bb 08 b6 cd 8f  df b2 8d 14 46 ad 35 35  |..%.........F.55|
00000100  0c dd 59 c2 68 ac a3 61  7a 4d ff 84 d2 5f 2d 62  |..Y.h..azM..._-b|
00000110  13 72 72 ca 61 38 43 25  9b 67 a9 10 4f b5 86 4d  |.rr.a8C%.g..O..M|
00000120  0a d8 c1 23 ab 28 4d 07  ed 9e a4 43 98 d0 fe ac  |...#.(M....C....|
00000130  df 62 9c b0 21 95 68 91  55 86 17 e2 c6 5f 2d f3  |.b..!.h.U...._-.|
00000140  76 87 77 eb e6 0a fa 1d  3e c9 67 b0 42 eb b6 29  |v.w.....>.g.B..)|
00000150  13 a9 ad 8e d7 4f 05 94  df ff 7f 57 b8 39 3a 0a  |.....O.....W.9:.|
00000160  18 4d 76 97 45 3b 3b c4  dd d8 a2 e7 86 61 76 ed  |.Mv.E;;......av.|
00000170  01 86 9f 2e 81 4e 20 ac  a6 91 d8 42 7a 3b 74 e8  |.....N ....Bz;t.|
00000180  c3 59 8a 65 8d 1b c7 21  43 00 e1 62 4c 0c a6 db  |.Y.e...!C..bL...|
00000190  28 4c 20 f7 31 94 99 06  ec 3e 7f 70 85 72 c6 0f  |(L .1....>.p.r..|
000001a0  e6 1e 1a 2b 15 47 9f 34  0b 11 76 d5 67 92 c2 f7  |...+.G.4..v.g...|
000001b0  1e bf 61 d4 1a e2 03 52  22 0c fd fe e3 0e 80 fe  |..a....R".......|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 40 79 00 00 fe  |...........@y...|
000001d0  ff ff 05 fe ff ff 02 4a  79 00 ef 55 a9 03 00 00  |.......Jy..U....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2011-10-21
@siva5
You issues are even more complex.

You can only boot windows from a primary partition. You must have deleted another install of Windows that had the boot files for the install in sda6 (logical partition). Second installs of Windows literally move boot files to first install in a primary partition. And the boot flag which you now have on sda5 has to be on the primary partition that you boot from.

You also then installed grub2's boot loader to the PBR - partition boot sector of sda6, Window has to have its boot code in the PBR to be able to boot. 

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You may be able to convert sda5 to a primary and do a Windows repair to make that the boot partition.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo sfdisk -d /dev/sdc > parts.txt

Not sure if this works for logical partitions or not.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You then have to run Windows repairs from a Windows repairCD to fix Windows.

Moving to your own thread to avoid confusion.

---

