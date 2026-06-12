---
title: "no grub menu, computer boots to windows after ububtu install?"
date: 2011-08-31
forum: General Help
---

### Post by boarder428 on 2011-08-31
So I have encountered a strange problem.  I re-partitioned my hd to do a fresh install of win 7 and the latest ubuntu after a failed upgrade from natty to oneric left my ubuntu distro unbootable.  I decided to go from 32 bit win 7 to the 64 bit version since 32 bit no longer supports Adobe premier pro after cs4.  Anyhow my pc is booting strait to Windows, no grub menu and no ubuntu to choose from.  When I try to re-install ubuntu it gives me the option to repair it and I can see it in gparted so I know it's there.  I need some advice as to what may have happened and how to go about repairing.  I have always dual booted this pc and the only thing I have done differently is switch from 32 bit Windows to 64 bit!

---

### Post by Enigmapond on 2011-08-31
Try running:

```
grub-update
```

on a liveCD...you may have to cd into your ubuntu installation...not sure.

---

### Post by oldfred on 2011-08-31
Windows always puts its boot loader into the MBR. Often you just need to reinstall grub2's boot loader. But to be sure lets run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by seawolf167 on 2011-08-31
Here is the Ubuntu [how-to ]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2")for re-installing Grub2 in place of the Windows MBR.

Edit: This is the same link oldfred already posted - I left this Window open while I was eating so the reply took too long :P

---

### Post by boarder428 on 2011-08-31
Not sure exactly what happened here, I meant to install win 7 on sda1 but it appears it may have gotten installed on sdb1? or I did'nt format the right drive.  I'm showing windows on both drives for some reason
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   277,764,095   277,762,048   7 NTFS / exFAT / HPFS
/dev/sda2         277,766,142   312,580,095    34,813,954   5 Extended
/dev/sda5         277,766,144   281,669,631     3,903,488  82 Linux swap / Solaris
/dev/sda6         281,671,680   312,580,095    30,908,416  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,465,145,343 1,465,143,296   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        082046612046563A                       ntfs       
/dev/sda5        869a6f0e-f4e0-46c8-8bb2-36564319b660   swap       
/dev/sda6        f3b8242d-9b49-4df6-86ea-331469573b63   ext4       
/dev/sdb1        CED8950AD894F1C7                       ntfs       Swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	linux	/boot/vmlinuz-2.6.35-30-generic-pae root=UUID=f3b8242d-9b49-4df6-86ea-331469573b63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	echo	'Loading Linux 2.6.35-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-30-generic-pae root=UUID=f3b8242d-9b49-4df6-86ea-331469573b63 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f3b8242d-9b49-4df6-86ea-331469573b63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f3b8242d-9b49-4df6-86ea-331469573b63 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f3b8242d-9b49-4df6-86ea-331469573b63
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ced8950ad894f1c7
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f3b8242d-9b49-4df6-86ea-331469573b63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=869a6f0e-f4e0-46c8-8bb2-36564319b660 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 148.105319977 = 159.026876416  boot/grub/core.img                             1
 143.016586304 = 153.562890240  boot/grub/grub.cfg                             1
 134.475177765 = 144.391622656  boot/initrd.img-2.6.35-28-generic-pae          1
 145.241077423 = 155.951419392  boot/initrd.img-2.6.35-30-generic-pae          1
 137.305664062 = 147.430834176  boot/vmlinuz-2.6.35-28-generic-pae             2
 148.074741364 = 158.994042880  boot/vmlinuz-2.6.35-30-generic-pae             1
 145.241077423 = 155.951419392  initrd.img                                     1
 134.475177765 = 144.391622656  initrd.img.old                                 1
 148.074741364 = 158.994042880  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  37 db 2f a1 56 1c 99 89  b6 eb df 80 6a f0 6c 8f  |7./.V.......j.l.|
00000010  16 ec d1 f8 ee 85 eb 23  36 b1 a5 a7 f1 14 4f ad  |.......#6.....O.|
00000020  ec d2 ea ed 8f 4f 95 14  02 6c 76 b0 c2 83 e5 9c  |.....O...lv.....|
00000030  9f 73 92 71 56 ec 89 53  20 78 aa 15 91 ab 31 db  |.s.qV..S x....1.|
00000040  31 15 2d fb bb 0a b8 3d  0e ab 35 c8 ce bd 56 6a  |1.-....=..5...Vj|
00000050  fd e3 af fe ea 37 6d ee  bb 27 b3 55 87 50 ee 1e  |.....7m..'.U.P..|
00000060  57 90 0e 95 25 af e6 0f  cd b8 9a 28 89 c4 63 0c  |W...%......(..c.|
00000070  5b 21 db 07 5a e2 d8 c1  d6 07 4d 32 32 64 ef bf  |[!..Z.....M22d..|
00000080  0e 76 65 e1 2b 02 18 43  26 26 d5 c4 ed 11 40 a3  |.ve.+..C&&....@.|
00000090  09 c0 bc ad 98 a6 4a 05  69 64 c5 53 95 0e 7a 27  |......J.id.S..z'|
000000a0  c6 01 26 ec 67 e1 3d 4e  76 17 7b e0 11 39 9d 2b  |..&.g.=Nv.{..9.+|
000000b0  33 71 81 8b 43 20 9d 6a  9a c3 47 1f 55 cd f4 6f  |3q..C .j..G.U..o|
000000c0  d3 dd 8d b9 ea 8a 48 0d  8f 9a 5a 81 b6 03 57 e7  |......H...Z...W.|
000000d0  7d ac 77 d6 c6 08 0f ed  66 3f 50 fc 03 99 e0 4a  |}.w.....f?P....J|
000000e0  80 6c df 70 72 a9 73 48  05 91 9c c7 6a e6 a7 48  |.l.pr.sH....j..H|
000000f0  15 8f fe 78 54 13 dc 98  70 f4 d9 6a a1 a4 71 68  |...xT...p..j..qh|
00000100  67 70 8f 80 3e a7 12 92  e9 1e 27 14 8e c8 42 52  |gp..>.....'...BR|
00000110  86 8e 87 23 7a 56 c8 f0  43 f3 4f 20 95 33 d4 22  |...#zV..C.O .3."|
00000120  72 72 05 7d a7 51 51 9e  bf bc d6 2f cc bd 7c 91  |rr.}.QQ..../..|.|
00000130  3a be a8 ab 4c fd ce 1f  c0 8c e3 3b 35 10 b8 53  |:...L......;5..S|
00000140  a0 c9 ff d3 a1 90 31 98  9c b8 35 82 5d 83 68 40  |......1...5.].h@|
00000150  70 16 42 7e 36 5e 3e d5  e5 a8 2a 2c 7f 75 ce 57  |p.B~6^>...*,.u.W|
00000160  3a 3e 52 35 53 45 64 09  b2 77 0d 56 c6 c2 7c 97  |:>R5SEd..w.V..|.|
00000170  56 63 98 5a 56 77 66 a1  2f 0f 94 1f a8 35 20 86  |Vc.ZVwf./....5 .|
00000180  18 6e 54 91 0e 09 43 0a  ed 7d 4f 13 ba 4e 5b 41  |.nT...C..}O..N[A|
00000190  a4 2f 9c 2a 25 e7 2b b8  99 10 a0 af 79 05 eb 08  |./.*%.+.....y...|
000001a0  24 2c 4e 34 50 7a b1 e7  78 5a 13 52 d8 33 0f 01  |$,N4Pz..xZ.R.3..|
000001b0  03 11 09 0b 1b 3b 13 96  b9 16 d5 13 0e fe 00 fe  |.....;..........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 a8 d7 01 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

EDIT: ok, booted to windows and it appears that everything is in order, windows was installed on sda1, not sure why it is showing sdb1 to be a windows install, maybe cause it is a ntfs partition?  It does have a boot folder in it but as far as I know I never installed windows on this partition.

---

### Post by oldfred on 2011-08-31
Did you ever change drives around. Just like grub defaults to sda for its boot loader, windows also installs to sda. So if you installed to sdb, it would put boot files in sda. Not sure if you installed to sda but had sdb set as default boot drive if windows would then install its boot files there or not. 

You have two of the three win7 boot files in sdb1 and windows as configured would have to boot thru sdb1. I would be sure to back up those two boot files bootmgr and BCD. BCD is configured to boot your setup and if moved you would have to reconfigure it. But it is easier to reconfigure than create from scratch.

You should have Ubuntu liveCD for current installed version and a windows repairCD.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by boarder428 on 2011-09-01
Yeah, not sure what I did, must not have paid attention when installing Windows.  Removed the boot folder from sdb and the pc would not boot.  Tried repairing boot loader with windows disc and it could not repair.  Unplugged sdb and the pc loaded the grub menu.  At this point I found it easier just to reformat and re-install both OS's leaving sdb disconnected until the installs were complete.  Thanks for the replies, I should have spent a little more time checking things out before posting.  I forgot about the boot info script!

---

