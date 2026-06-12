---
title: "Re: Unable to boot windows after ubuntu install"
date: 2010-09-30
forum: General Help
---

### Post by erenganathan on 2010-09-30
hello,
 
I do face the same problem with dual boot. but with a dirrent result for the "boot_info_script055.sh" run. pasted the result below.
 
please help me to solve this issue & enjoy using windos vista & ubuntu.
 
with Thanks & Regards,
Renganathan E
 
====================Start of Result.txt=======================
 
```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #6 for /boot/grub.
=> No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
File system: vfat
Boot sector type: Dell Utility: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /COMMAND.COM
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /Windows/System32/winload.exe
sda3: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda4: _________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sda5: _________________________________________________________________________
File system: vfat
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /ntldr /NTDETECT.COM
sda6: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda7: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 
sda8: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: -
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 63 192,779 192,717 de Dell Utility
/dev/sda2 194,560 21,166,079 20,971,520 7 HPFS/NTFS
/dev/sda3 * 21,166,080 431,955,719 410,789,640 7 HPFS/NTFS
/dev/sda4 431,955,966 488,394,751 56,438,786 f W95 Ext d (LBA)
/dev/sda5 483,153,920 488,394,751 5,240,832 dd Dell Media Direct
/dev/sda6 431,955,968 461,668,351 29,712,384 83 Linux
/dev/sda7 461,670,400 479,229,951 17,559,552 83 Linux
/dev/sda8 479,232,000 483,137,535 3,905,536 82 Linux swap / Solaris
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sdb1 44 15,679,439 15,679,396 b W95 FAT32
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/sda1 07D8-0716 vfat DellUtility 
/dev/sda2 C29E44399E44286D ntfs RECOVERY 
/dev/sda3 6C5A47955A475B4A ntfs OS 
/dev/sda4: PTTYPE="dos" 
/dev/sda5 A04C-CBDC vfat MEDIADIRECT 
/dev/sda6 942b7539-54bd-475a-9ca4-d291d5168560 ext4 
/dev/sda7 aea4ecd9-7611-4454-8030-6d227bd1881d ext4 
/dev/sda8 4fa5a23f-0016-47db-a62c-d214834e1abf swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 8023-52FF vfat RENGA'S_8GB 
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
/dev/sda6 / ext4 (rw,errors=remount-ro)
/dev/sda7 /home ext4 (rw)
/dev/sdb1 /media/RENGA'S_8GB vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
 
================================ sda5/boot.ini: ================================
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
=========================== sda6/boot/grub/grub.cfg: ===========================
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=942b7539-54bd-475a-9ca4-d291d5168560 ro quiet splash
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
echo 'Loading Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=942b7539-54bd-475a-9ca4-d291d5168560 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6c5a47955a475b4a
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
insmod fat
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a04c-cbdc
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda6/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=942b7539-54bd-475a-9ca4-d291d5168560 / ext4 errors=remount-ro 0 1
# /home was on /dev/sda7 during installation
UUID=aea4ecd9-7611-4454-8030-6d227bd1881d /home ext4 defaults 0 2
# swap was on /dev/sda8 during installation
UUID=4fa5a23f-0016-47db-a62c-d214834e1abf none swap sw 0 0
=================== sda6: Location of files loaded by Grub: ===================
 
232.2GB: boot/grub/core.img
223.6GB: boot/grub/grub.cfg
232.2GB: boot/initrd.img-2.6.32-24-generic
232.2GB: boot/vmlinuz-2.6.32-24-generic
232.2GB: initrd.img
232.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader on sda4
00000000 39 00 32 00 62 00 37 00 7d 00 22 00 20 00 57 00 |9.2.b.7.}.". .W.|
00000010 4d 00 49 00 44 00 3d 00 22 00 7b 00 62 00 34 00 |M.I.D.=.".{.b.4.|
00000020 61 00 63 00 65 00 33 00 34 00 36 00 2d 00 33 00 |a.c.e.3.4.6.-.3.|
00000030 31 00 64 00 31 00 2d 00 34 00 34 00 32 00 30 00 |1.d.1.-.4.4.2.0.|
00000040 2d 00 62 00 31 00 39 00 30 00 2d 00 31 00 63 00 |-.b.1.9.0.-.1.c.|
00000050 35 00 38 00 64 00 35 00 32 00 34 00 30 00 35 00 |5.8.d.5.2.4.0.5.|
00000060 61 00 62 00 7d 00 22 00 3e 00 0d 00 0a 00 20 00 |a.b.}.".>..... .|
00000070 20 00 20 00 20 00 20 00 20 00 20 00 20 00 3c 00 | . . . . . . .<.|
00000080 56 00 65 00 72 00 73 00 69 00 6f 00 6e 00 3e 00 |V.e.r.s.i.o.n.>.|
00000090 0d 00 0a 00 20 00 20 00 20 00 20 00 20 00 20 00 |.... . . . . . .|
000000a0 20 00 20 00 20 00 20 00 20 00 20 00 3c 00 56 00 | . . . . . .<.V.|
000000b0 65 00 72 00 73 00 69 00 6f 00 6e 00 4e 00 75 00 |e.r.s.i.o.n.N.u.|
000000c0 6d 00 62 00 65 00 72 00 20 00 76 00 65 00 72 00 |m.b.e.r. .v.e.r.|
000000d0 73 00 69 00 6f 00 6e 00 4e 00 75 00 6d 00 62 00 |s.i.o.n.N.u.m.b.|
000000e0 65 00 72 00 3d 00 22 00 31 00 2e 00 33 00 2e 00 |e.r.=.".1...3...|
000000f0 30 00 2e 00 30 00 22 00 20 00 2f 00 3e 00 0d 00 |0...0.". ./.>...|
00000100 0a 00 20 00 20 00 20 00 20 00 20 00 20 00 20 00 |.. . . . . . . .|
00000110 20 00 3c 00 2f 00 56 00 65 00 72 00 73 00 69 00 | .<./.V.e.r.s.i.|
00000120 6f 00 6e 00 3e 00 0d 00 0a 00 20 00 20 00 20 00 |o.n.>..... . . .|
00000130 20 00 20 00 20 00 20 00 20 00 3c 00 4e 00 61 00 | . . . . .<.N.a.|
00000140 6d 00 65 00 3e 00 4d 00 79 00 74 00 68 00 22 21 |m.e.>.M.y.t.h."!|
00000150 3a 00 20 00 54 00 68 00 65 00 20 00 46 00 61 00 |:. .T.h.e. .F.a.|
00000160 6c 00 6c 00 65 00 6e 00 20 00 4c 00 6f 00 72 00 |l.l.e.n. .L.o.r.|
00000170 64 00 73 00 3c 00 2f 00 4e 00 61 00 6d 00 65 00 |d.s.<./.N.a.m.e.|
00000180 3e 00 0d 00 0a 00 20 00 20 00 20 00 20 00 20 00 |>..... . . . . .|
00000190 20 00 20 00 20 00 3c 00 52 00 61 00 74 00 69 00 | . . .<.R.a.t.i.|
000001a0 6e 00 67 00 73 00 3e 00 0d 00 0a 00 20 00 20 00 |n.g.s.>..... . .|
000001b0 20 00 20 00 20 00 20 00 20 00 20 00 20 00 00 fe | . . . . . . ...|
000001c0 ff ff dd fe ff ff 02 38 0d 03 00 f8 4f 00 00 fe |.......8....O...|
000001d0 ff ff 05 fe ff ff 01 00 00 00 01 60 c5 01 00 00 |...........`....|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200

```
[SIZE=2] 
 
[/SIZE]=======================end of result.txt======================

---

### Post by erenganathan on 2010-10-04
hello,

I do face the same problem with dual boot. result for the "boot_info_script055.sh" run is pasted below.

Points to note:
 
1) Windows Vista is installed in the machine, but the boot menu it is given as "Microsoft Windows XP Embedded (on /dev/sda5)".
2) Booting Windows Vitsa 32Bit OS from CD/DVD drive is not working.
3) I Could Boot "Ubuntu 10.0.4" without any issue.
 
please help me to solve this issue & enjoy using windos vista & ubuntu.

with Thanks & Regards,
Renganathan E

 
```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #6 for /boot/grub.
=> No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
File system: vfat
Boot sector type: Dell Utility: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /COMMAND.COM
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /Windows/System32/winload.exe
sda3: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda4: _________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sda5: _________________________________________________________________________
File system: vfat
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /ntldr /NTDETECT.COM
sda6: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda7: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 
sda8: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: -
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 63 192,779 192,717 de Dell Utility
/dev/sda2 194,560 21,166,079 20,971,520 7 HPFS/NTFS
/dev/sda3 * 21,166,080 431,955,719 410,789,640 7 HPFS/NTFS
/dev/sda4 431,955,966 488,394,751 56,438,786 f W95 Ext d (LBA)
/dev/sda5 483,153,920 488,394,751 5,240,832 dd Dell Media Direct
/dev/sda6 431,955,968 461,668,351 29,712,384 83 Linux
/dev/sda7 461,670,400 479,229,951 17,559,552 83 Linux
/dev/sda8 479,232,000 483,137,535 3,905,536 82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sdb1 44 15,679,439 15,679,396 b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/sda1 07D8-0716 vfat DellUtility 
/dev/sda2 C29E44399E44286D ntfs RECOVERY 
/dev/sda3 6C5A47955A475B4A ntfs OS 
/dev/sda4: PTTYPE="dos" 
/dev/sda5 A04C-CBDC vfat MEDIADIRECT 
/dev/sda6 942b7539-54bd-475a-9ca4-d291d5168560 ext4 
/dev/sda7 aea4ecd9-7611-4454-8030-6d227bd1881d ext4 
/dev/sda8 4fa5a23f-0016-47db-a62c-d214834e1abf swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 8023-52FF vfat RENGA'S_8GB 
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
/dev/sda6 / ext4 (rw,errors=remount-ro)
/dev/sda7 /home ext4 (rw)
/dev/sdb1 /media/RENGA'S_8GB vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

================================ sda5/boot.ini: ================================
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
=========================== sda6/boot/grub/grub.cfg: ===========================
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=942b7539-54bd-475a-9ca4-d291d5168560 ro quiet splash
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
echo 'Loading Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=942b7539-54bd-475a-9ca4-d291d5168560 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 942b7539-54bd-475a-9ca4-d291d5168560
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6c5a47955a475b4a
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
insmod fat
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a04c-cbdc
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda6/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=942b7539-54bd-475a-9ca4-d291d5168560 / ext4 errors=remount-ro 0 1
# /home was on /dev/sda7 during installation
UUID=aea4ecd9-7611-4454-8030-6d227bd1881d /home ext4 defaults 0 2
# swap was on /dev/sda8 during installation
UUID=4fa5a23f-0016-47db-a62c-d214834e1abf none swap sw 0 0
=================== sda6: Location of files loaded by Grub: ===================

232.2GB: boot/grub/core.img
223.6GB: boot/grub/grub.cfg
232.2GB: boot/initrd.img-2.6.32-24-generic
232.2GB: boot/vmlinuz-2.6.32-24-generic
232.2GB: initrd.img
232.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader on sda4
00000000 39 00 32 00 62 00 37 00 7d 00 22 00 20 00 57 00 |9.2.b.7.}.". .W.|
00000010 4d 00 49 00 44 00 3d 00 22 00 7b 00 62 00 34 00 |M.I.D.=.".{.b.4.|
00000020 61 00 63 00 65 00 33 00 34 00 36 00 2d 00 33 00 |a.c.e.3.4.6.-.3.|
00000030 31 00 64 00 31 00 2d 00 34 00 34 00 32 00 30 00 |1.d.1.-.4.4.2.0.|
00000040 2d 00 62 00 31 00 39 00 30 00 2d 00 31 00 63 00 |-.b.1.9.0.-.1.c.|
00000050 35 00 38 00 64 00 35 00 32 00 34 00 30 00 35 00 |5.8.d.5.2.4.0.5.|
00000060 61 00 62 00 7d 00 22 00 3e 00 0d 00 0a 00 20 00 |a.b.}.".>..... .|
00000070 20 00 20 00 20 00 20 00 20 00 20 00 20 00 3c 00 | . . . . . . .<.|
00000080 56 00 65 00 72 00 73 00 69 00 6f 00 6e 00 3e 00 |V.e.r.s.i.o.n.>.|
00000090 0d 00 0a 00 20 00 20 00 20 00 20 00 20 00 20 00 |.... . . . . . .|
000000a0 20 00 20 00 20 00 20 00 20 00 20 00 3c 00 56 00 | . . . . . .<.V.|
000000b0 65 00 72 00 73 00 69 00 6f 00 6e 00 4e 00 75 00 |e.r.s.i.o.n.N.u.|
000000c0 6d 00 62 00 65 00 72 00 20 00 76 00 65 00 72 00 |m.b.e.r. .v.e.r.|
000000d0 73 00 69 00 6f 00 6e 00 4e 00 75 00 6d 00 62 00 |s.i.o.n.N.u.m.b.|
000000e0 65 00 72 00 3d 00 22 00 31 00 2e 00 33 00 2e 00 |e.r.=.".1...3...|
000000f0 30 00 2e 00 30 00 22 00 20 00 2f 00 3e 00 0d 00 |0...0.". ./.>...|
00000100 0a 00 20 00 20 00 20 00 20 00 20 00 20 00 20 00 |.. . . . . . . .|
00000110 20 00 3c 00 2f 00 56 00 65 00 72 00 73 00 69 00 | .<./.V.e.r.s.i.|
00000120 6f 00 6e 00 3e 00 0d 00 0a 00 20 00 20 00 20 00 |o.n.>..... . . .|
00000130 20 00 20 00 20 00 20 00 20 00 3c 00 4e 00 61 00 | . . . . .<.N.a.|
00000140 6d 00 65 00 3e 00 4d 00 79 00 74 00 68 00 22 21 |m.e.>.M.y.t.h."!|
00000150 3a 00 20 00 54 00 68 00 65 00 20 00 46 00 61 00 |:. .T.h.e. .F.a.|
00000160 6c 00 6c 00 65 00 6e 00 20 00 4c 00 6f 00 72 00 |l.l.e.n. .L.o.r.|
00000170 64 00 73 00 3c 00 2f 00 4e 00 61 00 6d 00 65 00 |d.s.<./.N.a.m.e.|
00000180 3e 00 0d 00 0a 00 20 00 20 00 20 00 20 00 20 00 |>..... . . . . .|
00000190 20 00 20 00 20 00 3c 00 52 00 61 00 74 00 69 00 | . . .<.R.a.t.i.|
000001a0 6e 00 67 00 73 00 3e 00 0d 00 0a 00 20 00 20 00 |n.g.s.>..... . .|
000001b0 20 00 20 00 20 00 20 00 20 00 20 00 20 00 00 fe | . . . . . . ...|
000001c0 ff ff dd fe ff ff 02 38 0d 03 00 f8 4f 00 00 fe |.......8....O...|
000001d0 ff ff 05 fe ff ff 01 00 00 00 01 60 c5 01 00 00 |...........`....|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200

```

---

### Post by Iowan on 2010-10-04
I've merged posts from two other threads into this new one. 
From Code of Conduct:
> Please do not cross post, or post the same thing in multiple locations.
Previous threads:
[http://ubuntuforums.org/showthread.php?t=1101562]("http://ubuntuforums.org/showthread.php?t=1101562")
[http://ubuntuforums.org/showthread.php?t=1587195]("http://ubuntuforums.org/showthread.php?t=1587195")

---

