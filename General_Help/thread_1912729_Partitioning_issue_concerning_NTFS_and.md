---
title: "Partitioning issue concerning NTFS and /"
date: 2012-01-21
forum: General Help
---

### Post by hal_jordan on 2012-01-21
Good morning!  
Attached is a screenshot displaying my Disk Utility output.  Initially, I had dual booted with XP (Data2) and Win7 (Data3).  Both were NTFS, and in an effort to run nothing but Linux, I changed the file system on both of these partitions to what I thought they should be.  I noticed that the boot partition is located on Data2.
The first question I have, is when I boot, will the boot record be blown away?
Ideally, I would like to merge Data2 and Data 3, making them into 1 partition, with Linux as the file system.
I would also like to more my home folder to this newly created partition.

Did I seriously screw up something that will render my PC into a paper weight?

Thank you in advance!

---

### Post by coffeecat on 2012-01-21
> **hal_jordan said:**
> 
Ideally, I would like to merge Data2 and Data 3, making them into 1 partition, with Linux as the file system.

Sorry - not possible. Your Data2 and Data3 partitions are at the opposite ends of the drive. You can only "merge" partitions that are contiguous, that is, adjacent. However, they are already formatted ext4, which is a Linux filesystem.

One other comment - you still have a NTFS partition, your first logical partition. If you are running only Linux, it's best to avoid using NTFS. In the event of filesystem corruption, you need Windows' chkdsk utility to repair it. There is no Linux tool which is as comprehensive as chkdsk.

In order to answer your questions better, we really need the output of the boot info script which provides information that Disk Utility does not. I'm a bit puzzled by your:

> **hal_jordan said:**
> The first question I have, is when I boot, will the boot record be blown away?

It looks as though you have already booted because your screenshot shows a distinctive theme which could only be achieved in a permanent installation. Anyway, you can run the boot script from either your Ubuntu installation or from a live CD. 

Boot into Ubuntu or into a live Ubuntu CD session, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by hal_jordan on 2012-01-21
Thank you so much.  If I change the filesystem on the boot partition to Linux, I just want to make sure that it will boot.
Here is the output:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,812,684   204,812,622  83 Linux
/dev/sda2         819,780,885 1,250,258,624   430,477,740  83 Linux
/dev/sda3         204,812,746   819,779,583   614,966,838   f W95 Extended (LBA)
/dev/sda5         204,812,748   641,213,649   436,400,902   7 NTFS / exFAT / HPFS
/dev/sda6         641,214,464   811,403,263   170,188,800  83 Linux
/dev/sda7         811,405,312   819,779,583     8,374,272  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f2f958fa-1af3-4ca2-95d7-d138f7ab7c00   ext4       Data2
/dev/sda2        9e132392-0251-4b2c-b17b-a66966ba45e6   ext4       Data3
/dev/sda5        01C9A40363D5E870                       ntfs       DATA
/dev/sda6        a8ad76c5-f72b-4e06-83de-51c26ca1f5d7   ext4       Ubuntu 10.4
/dev/sda7        6a212b90-f1d0-4668-848b-b19b68dcafd4   swap       
/dev/sdb1        1DFF-A7E0                              vfat       My Book

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/New Volume        ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/220GB             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a8ad76c5-f72b-4e06-83de-51c26ca1f5d7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 281498341498074A
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
UUID=a8ad76c5-f72b-4e06-83de-51c26ca1f5d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6a212b90-f1d0-4668-848b-b19b68dcafd4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 307.888916016 = 330.593206272  boot/grub/core.img                             1
 370.002208710 = 397.286846464  boot/grub/grub.cfg                             1
 306.673114777 = 329.287749632  boot/initrd.img-2.6.38-11-generic              1
 311.278320312 = 334.232551424  boot/initrd.img-2.6.38-12-generic              2
 312.848632812 = 335.918661632  boot/initrd.img-2.6.38-13-generic              2
 372.134017944 = 399.575859200  boot/initrd.img-2.6.38-8-generic               2
 344.016910553 = 369.385345024  boot/vmlinuz-2.6.38-11-generic                 1
 309.415348053 = 332.232200192  boot/vmlinuz-2.6.38-12-generic                 2
 312.622070312 = 335.675392000  boot/vmlinuz-2.6.38-13-generic                 2
 307.887187958 = 330.591350784  boot/vmlinuz-2.6.38-8-generic                  1
 312.848632812 = 335.918661632  initrd.img                                     2
 311.278320312 = 334.232551424  initrd.img.old                                 2
 312.622070312 = 335.675392000  vmlinuz                                        2
 309.415348053 = 332.232200192  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.Z.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  02 4c 38 3a b4 d1 01 00  00 00 00 00 02 00 00 00  |.L8:............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e0 a7 ff 1d 4d  79 20 42 6f 6f 6b 20 20  |..)....My Book  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Double.J on 2012-01-21
Sorry I may have missed something, but if I'm right in thinking you did this partitioning from inside your current install and now you're concerned that when you restart grub won't find your install?

If this is the case, you can just update grub with the command inside the terminal (CTRL+ALT+T)
```

sudo update-grub

```

Grub will only be affected if you've deleted/created/moved partitions in a way that means that the root filesystem is not where grub expects it to be - by the sound of it you have only re formatted the partitions? if this is the case, I don't foresee any problems :)

---

### Post by oldfred on 2012-01-21
Windows has to have boot flag on active primary NTFS partition to boot. Grub does not use boot flag, but a few BIOS want to see a boot flag on a primary partition, so I would just leave the boot flag on sda1.

You cannot merge the two partitions, but can move /home to one and mount the other and use it as data for some folders. Not quite as good as merging as you have to manage how much data is in /home versus your data partition.

---

### Post by coffeecat on 2012-01-21
> **hal_jordan said:**
> Thank you so much.  If I change the filesystem on the boot partition to Linux, I just want to make sure that it will boot.
Here is the output:

You have no boot partition. Ubuntu is booting from its own root partition, sda6. If by boot partition you mean sda1 because it has the boot flag set, you can ignore that. As oldfred points out, only Windows needs a boot flag.

I don't see any problems in your boot script output. Your system should boot normally into Ubuntu on sda6. Now that you have had some feedback, what would you like to do with sda1, sda2 and sda5?

---

### Post by hal_jordan on 2012-01-22
Thanks everyone!  No more NTFS and I was able to move the home folder to a larger partition.
Again, thanks to everyone that posted replies, they worked!!

---

