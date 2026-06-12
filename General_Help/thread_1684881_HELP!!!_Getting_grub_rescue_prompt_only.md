---
title: "HELP!!! Getting grub rescue prompt only"
date: 2011-02-09
forum: General Help
---

### Post by scpatl4now on 2011-02-09
The power flick off/on causing pc to reboot.  When it came back only have grub rescue prompt. 

```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in
partition #6 for (,msdos6)/boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in
partition #6 for (,msdos6)/boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in
partition #6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdh

sde1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sde2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sde5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sdf1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdf1 and
looks at sector 62583712 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sdf3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdf5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdf6: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot/grub/core.img

sdg2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sdg5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sdg5 starts
at sector 63.
Operating System:
Boot files/dirs:

sdh1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdh2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ __________________________________________________ ___

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sde1 * 2,048 103,714,815 103,712,768 83 Linux
/dev/sde2 103,715,640 240,107,489 136,391,850 f W95 Ext d (LBA)
/dev/sde5 103,718,912 240,105,471 136,386,560 83 Linux


Drive: sdf ___________________ __________________________________________________ ___

Disk /dev/sdf: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdf1 * 63 45,496,079 45,496,017 7 HPFS/NTFS
/dev/sdf3 45,496,318 117,258,434 71,762,117 f W95 Ext d (LBA)
/dev/sdf5 115,314,633 117,258,434 1,943,802 82 Linux swap / Solaris
/dev/sdf6 45,496,320 115,312,639 69,816,320 83 Linux


Drive: sdg ___________________ __________________________________________________ ___

Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdg1 * 63 485,532,494 485,532,432 7 HPFS/NTFS
/dev/sdg2 485,532,495 488,392,064 2,859,570 f W95 Ext d (LBA)
/dev/sdg5 485,532,558 488,392,064 2,859,507 7 HPFS/NTFS


Drive: sdh ___________________ __________________________________________________ ___

Disk /dev/sdh: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdh1 63 163,846,934 163,846,872 7 HPFS/NTFS
/dev/sdh2 163,846,935 586,099,394 422,252,460 7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sde1 91723d09-5538-406d-b92d-6e7980ef7078 ext4 EXT4PART
/dev/sde2: PTTYPE="dos"
/dev/sde5 8db724f6-30b4-4ef0-8dc9-307772bd98d5 ext4 LIN4
/dev/sde promise_fasttrack_raid_member
/dev/sdf1 DE047F5B047F359D ntfs Windows System
/dev/sdf3: PTTYPE="dos"
/dev/sdf5 61c5620e-6122-4b0e-994d-4ce764196fc5 swap
/dev/sdf6 130e12e1-7a08-4388-af56-03f0d16477c3 ext4
/dev/sdf: PTTYPE="dos"
/dev/sdg1 ECD4909BD4906A1A ntfs BigOlE
/dev/sdg2: PTTYPE="dos"
/dev/sdg5 06B4AE7EB4AE6FBB ntfs page 2
/dev/sdg: PTTYPE="dos"
/dev/sdh1 BC0854340853EBC0 ntfs SATA Work
/dev/sdh2 56A477F4A477D549 ntfs SATA J
/dev/sdh: PTTYPE="dos"
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)


================================ sdf1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sdf6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro quiet splash
initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
echo 'Loading Linux 2.6.35-25-generic ...'
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro quiet splash
initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
echo 'Loading Linux 2.6.35-24-generic ...'
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro quiet splash
initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
echo 'Loading Linux 2.6.35-23-generic ...'
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
echo 'Loading Linux 2.6.35-22-generic ...'
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=130e12e1-7a08-4388-af56-03f0d16477c3 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 130e12e1-7a08-4388-af56-03f0d16477c3
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdf1)" {
insmod part_msdos
insmod ntfs
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set de047f5b047f359d
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdf6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda6 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=61c5620e-6122-4b0e-994d-4ce764196fc5 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdf6: Location of files loaded by Grub: ===================


36.5GB: boot/grub/core.img
43.0GB: boot/grub/grub.cfg
29.7GB: boot/initrd.img-2.6.35-22-generic
43.2GB: boot/initrd.img-2.6.35-23-generic
43.5GB: boot/initrd.img-2.6.35-24-generic
44.0GB: boot/initrd.img-2.6.35-25-generic
36.5GB: boot/vmlinuz-2.6.35-22-generic
36.4GB: boot/vmlinuz-2.6.35-23-generic
36.7GB: boot/vmlinuz-2.6.35-24-generic
36.8GB: boot/vmlinuz-2.6.35-25-generic
44.0GB: initrd.img
43.5GB: initrd.img.old
36.8GB: vmlinuz
36.7GB: vmlinuz.old

=================== sdg1: Location of files loaded by Grub: ===================


??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sdf3

00000000 70 0d 45 aa 5f 3a 9e fb d9 f7 6d 63 2f 7d 22 9c |p.E._:....mc/}".|
00000010 69 7a 18 68 b9 14 2a b5 c9 81 b5 a3 9f fa cd 98 |iz.h..*.........|
00000020 93 cf 96 02 12 94 0b f6 91 12 72 75 e7 ec d9 c6 |..........ru....|
00000030 62 39 8d da 01 ce 1a 58 3b 6c c6 20 f7 27 f1 b4 |b9.....X;l. .'..|
00000040 2c 03 21 a0 86 47 8e 20 8c 96 54 1d 28 37 ec 5b |,.!..G. ..T.(7.[|
00000050 5f b2 cd 02 ef 01 83 da 7d fe 53 aa 32 6b 0f 5a |_.......}.S.2k.Z|
00000060 a3 3a ec 24 46 ad a8 2c 14 7e d9 37 03 45 32 20 |.:.$F..,.~.7.E2 |
00000070 11 aa a6 2a 6b 26 05 94 21 03 0f 69 e3 0d 0e 6c |...*k&..!..i...l|
00000080 2b 60 0d 6e b3 22 79 21 df b0 e0 1d 3d 28 a6 c7 |+`.n."y!....=(..|
00000090 b5 89 6d ac 69 9a 5d b9 88 7d 5f 12 fe 82 b5 a4 |..m.i.]..}_.....|
000000a0 16 c1 d2 37 7e 28 13 ab 65 37 b3 03 54 0b aa 57 |...7~(..e7..T..W|
000000b0 c8 6f dd 56 21 63 d3 0b 6e 09 e2 a0 e2 b1 50 60 |.o.V!c..n.....P`|
000000c0 ea 1f 97 03 e8 28 e1 5f da 65 03 1b 2a 57 75 3b |.....(._.e..*Wu;|
000000d0 3e b6 d6 b9 8f c8 45 93 32 fe bd aa fc 63 41 35 |>.....E.2....cA5|
000000e0 3a f8 39 9f ce 8b 02 4b 82 93 b0 86 e7 c1 fe c8 |:.9....K........|
000000f0 e1 d2 20 04 0e 17 71 1a 91 84 35 38 34 98 81 9f |.. ...q...584...|
00000100 3c f0 bf ee 76 94 83 c8 a2 82 07 0d 62 37 a1 a5 |<...v.......b7..|
00000110 f8 ae 8a 37 df d2 62 1b 3b da de bc 5f b3 77 68 |...7..b.;..._.wh|
00000120 95 f0 fc 8e 1d 4a 9e 15 ec 03 0c 1c 51 a0 12 57 |.....J......Q..W|
00000130 a8 6b a8 9a 46 ff 9e 01 dd 04 db 72 35 15 9f 7a |.k..F......r5..z|
00000140 53 d5 33 9b af dc 32 0e 38 b7 64 2c 4a 66 f3 b2 |S.3...2.8.d,Jf..|
00000150 2b e6 e0 01 cc cc 9c be d1 d7 b1 d0 cb f4 0d 8d |+...............|
00000160 05 0d c7 4b 4a b2 e1 68 dd 05 59 0a 4f 7c b5 88 |...KJ..h..Y.O|..|
00000170 0f 95 6e 35 a2 13 49 65 0c 10 9a ff ec 72 c2 68 |..n5..Ie.....r.h|
00000180 c8 1f 89 f5 83 8d 6c df 0f cd 34 30 a5 c2 f1 37 |......l...40...7|
00000190 76 e1 f0 20 1a 16 e8 5b 67 ec 80 56 7d 6f 49 17 |v.. ...[g..V}oI.|
000001a0 f0 ea 00 61 16 77 eb a1 4c bf 25 66 72 13 65 62 |...a.w..L.%fr.eb|
000001b0 a1 6b 5a c7 a0 25 25 f7 17 44 63 e2 aa 18 00 fe |.kZ..%%..Dc.....|
000001c0 ff ff 82 fe ff ff cb 57 29 04 fa a8 1d 00 00 fe |.......W).......|
000001d0 ff ff 05 fe ff ff 01 00 00 00 01 50 29 04 00 00 |...........P)...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd
```

---

