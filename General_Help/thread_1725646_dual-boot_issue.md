---
title: "dual-boot issue"
date: 2011-04-10
forum: General Help
---

### Post by vd8drum on 2011-04-10
I installed Lubuntu on my little brother's desktop, using the installer in the live USB, I went with the recommended settings, and then it installed the Linux partition.

Now, whenever he tries to boot into Windows, he can't, when he starts the computer and the GRUB menu pops up, and he can't find Vista.

Help? C:

---

### Post by mikewhatever on 2011-04-10
Can you post the output of **sudo fdisk -l** from that computer. Just want to make sure there is still a Windows partition there.

---

### Post by vd8drum on 2011-04-10
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82265aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1233     9904041    7  HPFS/NTFS
/dev/sda2   *        1234       19619   147678709    7  HPFS/NTFS
/dev/sda3           19619       30402    86615041    5  Extended
/dev/sda5           19619       30211    85079040   83  Linux
/dev/sda6           30211       30402     1534976   82  Linux swap / Solaris

---

### Post by garvinrick4 on 2011-04-10
Looks like it is there, what is:
```
grep menuentry /boot/grub/grub.cfg
```# I am sorry I just noticed it says Lubuntu. Do not know if code will
pick up menu entrys in grub config. If it does post it. Looking to see
what menu entrys Vista has in grub. 

# Head on mikewhatever have never installed Lubuntu.

---

### Post by mikewhatever on 2011-04-10
Yep, two NTFS partitions there. Looks like you need to run the [bootinfo script]("http://bootinfoscript.sourceforge.net/") and post the output.

---

### Post by vd8drum on 2011-04-10
Okay it showed me to the Winloader.exe, what do I do now?

---

### Post by vd8drum on 2011-04-10
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,808,144    19,808,082   7 HPFS/NTFS
/dev/sda2    *     19,808,145   315,165,562   295,357,418   7 HPFS/NTFS
/dev/sda3         315,166,718   488,396,799   173,230,082   5 Extended
/dev/sda5         315,166,720   485,324,799   170,158,080  83 Linux
/dev/sda6         485,326,848   488,396,799     3,069,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        90A47F4DA47F3536                       ntfs                                     
/dev/sda2        0EE2826DE28258BB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        c5ce652f-be25-4026-a80a-768e551b8b9d   ext4                                     
/dev/sda6        87f96ff1-afce-4e91-adae-563f6488d35a   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/0EE2826DE28258BB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/90A47F4DA47F3536  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=c5ce652f-be25-4026-a80a-768e551b8b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=c5ce652f-be25-4026-a80a-768e551b8b9d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c5ce652f-be25-4026-a80a-768e551b8b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c5ce652f-be25-4026-a80a-768e551b8b9d ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c5ce652f-be25-4026-a80a-768e551b8b9d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=c5ce652f-be25-4026-a80a-768e551b8b9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=87f96ff1-afce-4e91-adae-563f6488d35a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 195.8GB: boot/grub/core.img
 195.8GB: boot/grub/grub.cfg
 162.2GB: boot/initrd.img-2.6.35-22-generic
 163.2GB: boot/initrd.img-2.6.35-28-generic
 195.8GB: boot/vmlinuz-2.6.35-22-generic
 195.8GB: boot/vmlinuz-2.6.35-28-generic
 163.2GB: initrd.img
 162.2GB: initrd.img.old
 195.8GB: vmlinuz
 195.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  62 98 e3 d0 64 39 c7 3b  0a 23 04 bd 65 d1 c1 da  |b...d9.;.#..e...|
00000010  3b cb e5 9d 1a a3 32 d7  73 f5 78 4e de 34 d9 a9  |;.....2.s.xN.4..|
00000020  cf 1b 7c 03 ca 56 19 bd  4d 1e 4b 75 e0 16 77 45  |..|..V..M.Ku..wE|
00000030  18 6c 94 a6 4c 46 19 0e  c6 b0 99 d6 a9 2d ca b3  |.l..LF.......-..|
00000040  e1 f9 a0 b1 2c 3a 80 37  0b 4b b5 00 63 5b e9 ba  |....,:.7.K..c[..|
00000050  df 56 64 55 bb 7a 9f 89  dc 45 58 99 93 54 ac 63  |.VdU.z...EX..T.c|
00000060  06 9f 3d 0a 19 0e c6 e3  17 d6 d2 c6 c0 bc 1c c2  |..=.............|
00000070  d7 01 d5 3d 69 b3 19 95  00 d1 4d c7 a5 8d 95 a5  |...=i.....M.....|
00000080  1c 98 a6 30 d8 1d b6 79  6a 23 2f c5 8a 06 80 76  |...0...yj#/....v|
00000090  22 60 1a 5a 4a cf 4b 0a  c2 b8 a3 2e b7 01 ac 51  |"`.ZJ.K........Q|
000000a0  51 fa 72 71 16 8e b9 fe  a7 82 ec 3d bd e6 a1 33  |Q.rq.......=...3|
000000b0  2a cb 19 3d 04 ef ad a5  2c 79 f7 41 c1 5f 9a 7b  |*..=....,y.A._.{|
000000c0  cb 79 fb 4e 43 32 a8 88  f7 aa b8 ec 79 d0 36 09  |.y.NC2......y.6.|
000000d0  d3 ae 95 68 a6 8f 1e 7a  4a 10 1b 8f 41 f3 ef 03  |...h...zJ...A...|
000000e0  54 3a 39 f0 7a 1e f8 24  a7 d4 1c 79 64 d8 6c f3  |T:9.z..$...yd.l.|
000000f0  f6 1e 77 7b cb 24 31 d1  6f 4c 02 8f 37 1c 2e 94  |..w{.$1.oL..7...|
00000100  c4 e6 ef 0f 0a d9 c2 3f  93 9e 03 bf f8 39 af 09  |.......?.....9..|
00000110  73 55 62 93 7b cd 4f c0  1f e5 7e 3e fa 7e 74 88  |sUb.{.O...~>.~t.|
00000120  77 87 8e 4a d0 e7 42 91  3d 06 64 e5 c7 1f 98 74  |w..J..B.=.d....t|
00000130  e0 33 0b 1a 51 0c 97 d7  37 bc 65 80 59 7c 51 79  |.3..Q...7.e.Y|Qy|
00000140  4a 01 af ae 11 e1 86 19  e5 2c 4c 8c c4 92 77 ca  |J........,L...w.|
00000150  ab ce 10 bc 0e b2 f3 fa  20 26 4c ba 41 a2 8e e8  |........ &L.A...|
00000160  a5 cf 2e 24 98 52 5a 28  ba dc 88 da e0 2b c6 06  |...$.RZ(.....+..|
00000170  18 ea f7 12 a6 14 4e 49  28 1b 06 8c 17 28 63 0a  |......NI(....(c.|
00000180  4f 29 e3 02 39 5a e9 02  42 20 3b 6c 4e d1 59 a9  |O)..9Z..B ;lN.Y.|
00000190  83 a1 8f d8 d0 23 11 8c  29 92 27 14 30 04 6f 4e  |.....#..).'.0.oN|
000001a0  32 84 04 36 2d 2c e3 ce  8c 40 b3 69 6e 10 34 c0  |2..6-,...@.in.4.|
000001b0  ba 92 93 b8 0b 7e 6f b1  f1 af 64 61 c7 dc 00 fe  |.....~o...da....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 24 0a 00 fe  |...........h$...|
000001d0  ff ff 05 fe ff ff 02 68  24 0a 00 e0 2e 00 00 00  |.......h$.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by mikewhatever on 2011-04-10
OK, the script shows some Windows boot files on sda2, not quite sure why it wasn't added to the menu.
Try running **sudo update-grub** from the Ubuntu installation.

---

### Post by vd8drum on 2011-04-10
Okay, just tried that, didn't work, same old GRUB menu /:

---

### Post by garvinrick4 on 2011-04-10
Try to install grub to mbr and see if that will let OS-prober go out and find Windows for you
and put in config and as a menu entry.
While in Ubuntu:
```
sudo grub-install /dev/sda
``````
sudo update-grub
```

---

### Post by vd8drum on 2011-04-10
Still nothing D:

---

### Post by oldfred on 2011-04-10
I have seen that the default install of Lubuntu does not include the grub2 os-prober.

sudo apt-get install os-prober
sudo update-grub

---

### Post by vd8drum on 2011-04-11
That almost worked, it added the Vista loader to the GRUB menu, but it won't let me boot into it! D:

---

### Post by oldfred on 2011-04-11
If the os-prober found it, the windows partition has to have most of the windows boot files & be readable. But Vista could still have some windows issue.

It could be related to your /grldr in your windows boot, but one poster said that that file is to get around MS license issues? We normally recommend you delete it. But you may have to run windows repairs.

---

### Post by vd8drum on 2011-04-11
My bro wants Lubuntu off now, is there a way to rollback all of this and go back to Vista?

---

### Post by vd8drum on 2011-04-11
This keeps getting worse, I didn't realize it until now, but after using the last guy's suggestion, I'm not able to view the files in the Windows partition! It only shows the "87gb filesystem"

HELP

---

### Post by vd8drum on 2011-04-11
I seeeeriously need help with this, I don't want to reformat his harddrive D:

---

### Post by oldfred on 2011-04-11
Have you run windows repairs?

Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by vd8drum on 2011-04-11
Don't have a Windows Vista DVD, nor a CD/DVD drive.

---

### Post by oldfred on 2011-04-11
You have to create a Windows repair USB then.

Repair USBs
Post #25 w/pendrive yumi
[http://ubuntuforums.org/showthread.php?t=1711323](http://ubuntuforums.org/showthread.php?t=1711323)
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/](http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/)

Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by vd8drum on 2011-04-12
Forget it, he just decided to install Ubuntu :D

---

