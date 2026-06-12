---
title: "Can't boot XP but can boot Ubuntu"
date: 2011-01-28
forum: General Help
---

### Post by thanksinadvance on 2011-01-28
Hi everyone,
 
I wonder if there's anyone here who can help me. I have had Windows XP and Linux installed on the same partion for 6 months and, until this morning, had no problems. Now I can't boot from XP and I can't even use the Windows recovery disks to repair windows. I haven't deleted/moved any system files so I can't understand what happened. I have also tried to boot in safety mode by hitting F8 but that doesn't work either. What can I do now? I can boot Linux but what I want is my Windows XP back. Can you help? Thanks in advance.
 
Paulo

---

### Post by dhysk on 2011-01-28
How does Windows not boot?  What happens when you select Winows from the boot menue?  Winows splash screen than black, just black, or what?

Other usfull info

1. Version of ubuntu?
2. Have you updated recently?
3. What was the last thing you did/saw before it quite working?
4. grub version? In a terminal type: 
```
grub --version

```
5. How do you have your partisions set up? In a terminal type:
```
fdisk -l
```
copy past output in the forum using the # for code tag.

---

### Post by sikander3786 on 2011-01-28
> **dhysk said:**
> How does Windows not boot?  What happens when you select Winows from the boot menue?  Winows splash screen than black, just black, or what?

Other usfull info

1. Version of ubuntu?
2. Have you updated recently?
3. What was the last thing you did/saw before it quite working?
4. grub version? In a terminal type: 
```
grub --version

```
5. How do you have your partisions set up? In a terminal type:
```
fdisk -l
```
copy past output in the forum using the # for code tag.
Yes all that information is definitely needed. And it would be even better if we can see the output of bootinfoscript instead of those commands separately.

To the OP:

Please boot Ubuntu and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your boot/device/grub setup and thus help us advise more efficiently.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Rubi1200 on 2011-01-28
As sikander3786 pointed out, we definitely need to see the results of the script.

Thanks.

---

### Post by thanksinadvance on 2011-01-28
Hi,
 
I am using Ubuntu 10.04 LTS (Lucid Lynx) and GRUB version 1.98. 
when i select Windows XP from the boot menu the computer just restarts and after a few seconds goes back to the boot menu. When things started to go wrong in Windows I started to see a blue screen with a message saying something like "A problem has been detected and windows has been shut down to prevent damage to your computer"... I can't remember the whole message.
 
when I type fdisk -l in the command line nothing happens. It just jumps to a new command line. 
 
I installed Ubuntu to learn it but I haven't learned much. If you now what the problem is could you please let me know what to do step by step? I am less than a beginner in Ubuntu.
 
Thank you for your help.
Paulo

---

### Post by dhysk on 2011-01-28
Sounds like Windows decided to die on you.  So this may be more of a restore windows thing.  The bootscript would still be usfull possibly though and is well worth d/l runing and posting the output of the generated file here on the forum.

As a farly compitent user what I would do is try to restor windows boot than re-install windows.  Do you have a winodws CD?  If so backing up your files to another disk would be advisable and the output of that script would help us find ware windows is so we could get you to mount the windows partition to copy over your valuable files if need be.

What I've done in the past, and admitidly is more of a general fix is boot windows cd and go to the restore option.  Once there I do a fixmbr than a fixboot.  This will kill grub though and you will have to re install grub by doing something like this:

[http://ubuntuforums.org/showthread.php?t=114332](http://ubuntuforums.org/showthread.php?t=114332)

Although at this stage this may be a bit of a shotgun approuch.

What happens when you boot into the windows restor exactly?  Can it not find windows what kind of error messages do you get?

---

### Post by thanksinadvance on 2011-01-28
> **dhysk said:**
> Sounds like Windows decided to die on you. So this may be more of a restore windows thing. The bootscript would still be usfull possibly though and is well worth d/l runing and posting the output of the generated file here on the forum.
 
As a farly compitent user what I would do is try to restor windows boot than re-install windows. Do you have a winodws CD? If so backing up your files to another disk would be advisable and the output of that script would help us find ware windows is so we could get you to mount the windows partition to copy over your valuable files if need be.
 
What I've done in the past, and admitidly is more of a general fix is boot windows cd and go to the restore option. Once there I do a fixmbr than a fixboot. This will kill grub though and you will have to re install grub by doing something like this:
 
[http://ubuntuforums.org/showthread.php?t=114332](http://ubuntuforums.org/showthread.php?t=114332)
 
Although at this stage this may be a bit of a shotgun approuch.
 
What happens when you boot into the windows restor exactly? Can it not find windows what kind of error messages do you get?
My apologies, I am a complete ignorant. After a long struggle I've managed to download the bootinfoscript file to a machine running Windows and then copied it to Ubuntu in my laptop (I don't have the internet configured on my laptop and I have no clue how to do it in Ubuntu, hence why I am freaking out because of not having Windows working. 
I do have a Recovery CD for Windows but the laptop won't boot from it although the CD/DVD device comes first in the booting order and when I choose Windows XP from the booting menu the machine just turns off and then on again and after a few seconds goes back to the booting menu.
It's like it restarts each time I select XP. I really need to restore Windows. 
Please see below the Results.txt file generated in Ubuntu. Thank you so much.
 
 
 
```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #6 for /boot/grub.
=> No boot loader? is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
File system: vfat
Boot sector type: MSWIN4.1: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 98
Boot files/dirs: /IO.SYS /MSDOS.SYS /COMMAND.COM
sda2: _________________________________________________________________________
File system: 
Boot sector type: -
Boot sector info: 
Mounting failed:
mount: unknown filesystem type ''
sda3: _________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sda5: _________________________________________________________________________
File system: 
Boot sector type: Unknown
Boot sector info: 
Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
sda6: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda7: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 63 4,096,574 4,096,512 12 Compaq diagnostics
/dev/sda2 * 4,096,575 51,391,934 47,295,360 c W95 FAT32 (LBA)
/dev/sda3 51,384,318 117,210,239 65,825,922 f W95 Ext d (LBA)
/dev/sda5 75,778,668 117,210,239 41,431,572 b W95 FAT32
/dev/sda6 51,384,320 74,651,647 23,267,328 83 Linux
/dev/sda7 74,653,696 75,778,047 1,124,352 82 Linux swap / Solaris
/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda6
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 1031 MB, 1031274496 bytes
16 heads, 32 sectors/track, 3934 cylinders, total 2014208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sdb1 * 32 2,014,207 2,014,176 e W95 FAT16 (LBA)
&#12288;
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/sda1 3007-17F2 vfat PQSERVICE 
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda6 1423e2aa-057e-42fc-9375-68204e9f0d7b ext4 
/dev/sda7 b8424434-c953-4107-a135-85870d269f7b swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 685C-9859 vfat USB DISK 
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
/dev/sda6 / ext4 (rw,errors=remount-ro)
/dev/sdb1 /media/USB DISK vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
&#12288;
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
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
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
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1423e2aa-057e-42fc-9375-68204e9f0d7b ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1423e2aa-057e-42fc-9375-68204e9f0d7b ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1423e2aa-057e-42fc-9375-68204e9f0d7b
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
insmod fat
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 260d-18fe
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
UUID=1423e2aa-057e-42fc-9375-68204e9f0d7b / ext4 errors=remount-ro 0 1
# swap was on /dev/sda7 during installation
UUID=b8424434-c953-4107-a135-85870d269f7b none swap sw 0 0
=================== sda6: Location of files loaded by Grub: ===================
&#12288;
31.4GB: boot/grub/core.img
35.3GB: boot/grub/grub.cfg
31.8GB: boot/initrd.img-2.6.32-21-generic
31.7GB: boot/vmlinuz-2.6.32-21-generic
31.8GB: initrd.img
31.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader on sda3
00000000 af 61 0f 30 8f b4 7b 24 53 56 45 c9 ea 8b 24 e7 |.a.0..{$SVE...$.|
00000010 d1 cd 51 a2 bb 6d 3b 58 1a 19 54 8a a3 92 30 fe |..Q..m;X..T...0.|
00000020 27 89 c5 81 26 21 2a c6 34 7b 64 57 51 5f 8b 3c |'...&!*.4{dWQ_.<|
00000030 b2 1f 29 13 c7 a8 bb 26 51 22 44 51 02 6d 09 db |..)....&Q"DQ.m..|
00000040 93 46 8e 28 e1 58 82 4f 4a 32 24 eb a6 c6 35 db |.F.(.X.OJ2$...5.|
00000050 8b 4c d4 20 83 ee d4 3b bf ef ad 8c 75 5f ad 42 |.L. ...;....u_.B|
00000060 b7 72 b5 ba 57 71 08 63 6d dc 36 a6 66 67 c2 91 |.r..Wq.cm.6.fg..|
00000070 dd ac f0 ce 1b a2 40 7b d9 61 d2 ca 88 b3 d9 fa |......@{.a......|
00000080 e7 4f 7b 4f ef 45 28 a4 08 80 e9 fc 3a d0 31 d9 |.O{O.E(.....:.1.|
00000090 13 b2 f8 47 dd 24 e0 a1 a9 0c 0e 16 bc 84 6b 0d |...G.$........k.|
000000a0 06 ff fb b3 00 e1 0e e4 44 63 d8 8b 0c 1d 34 85 |........Dc....4.|
000000b0 6c 0b 32 3d 83 6e 13 89 97 5e 4c 3c cd 8a 73 33 |l.2=.n...^L<..s3|
000000c0 ac 49 87 99 b0 19 16 5e be 82 d5 44 ea b9 0d 32 |.I.....^...D...2|
000000d0 4d 4b 50 7e 4a fd 58 7e d5 42 94 aa 1c ae 4e 30 |MKP~J.X~.B....N0|
000000e0 0b b3 a7 89 f7 6c 2a 09 9e 23 cf 74 e8 d0 a4 b0 |.....l*..#.t....|
000000f0 99 ae 46 ec 08 91 21 28 88 a7 56 bc 9a 35 2a 62 |..F...!(..V..5*b|
00000100 a1 54 fb 86 43 98 ed f1 8d 78 e0 69 9b 10 63 f5 |.T..C....x.i..c.|
00000110 b4 3c bd f7 d6 c8 2b 6f 6b a9 2e 9c 6e b3 a5 76 |.<....+ok...n..v|
00000120 42 21 98 f2 77 0d 69 99 8f d4 52 2e 92 58 c6 15 |B!..w.i...R..X..|
00000130 61 2b 90 21 ef a5 a6 39 55 1f 4f 63 6c 39 a9 93 |a+.!...9U.Ocl9..|
00000140 75 8f ad 65 24 ee 40 40 d4 53 00 58 49 bc 84 42 |u..e$.@@.S.XI..B|
00000150 b0 d9 ef c0 b0 5a 31 cb 21 da 05 04 76 a9 0d c3 |.....Z1.!...v...|
00000160 a2 d5 13 98 aa f3 a2 c2 d5 07 55 58 1e 99 96 84 |..........UX....|
00000170 b3 b5 11 05 83 91 10 fd a5 a4 5b 19 80 30 ec e2 |..........[..0..|
00000180 35 8e d2 14 8b 95 e6 c5 1b 11 34 e3 fc 61 83 a8 |5.........4..a..|
00000190 c2 48 3b de 18 51 68 d4 29 da b0 1c 35 3f e9 74 |.H;..Qh.)...5?.t|
000001a0 b8 a5 34 7e 9c e3 99 e9 79 1d d7 cc e0 38 f9 b3 |..4~....y....8..|
000001b0 31 67 3b 10 d7 dc 36 0f 09 9f 31 25 0a 51 00 01 |1g;...6...1%.Q..|
000001c0 c1 ff 0b fe ff ff 6e 3a 74 01 14 32 78 02 00 fe |......n:t..2x...|
000001d0 ff ff 05 d8 f2 ff 01 00 00 00 01 08 63 01 00 00 |............c...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
Unknown BootLoader on sda5
00000000 01 1e 01 00 30 1d 0c 00 ff ff ff 0f ff ff ff 0f |....0...........|
00000010 05 1e 01 00 07 1e 01 00 ac 1f 01 00 08 1e 01 00 |................|
00000020 aa 1f 01 00 2d 1e 01 00 0b 1e 01 00 0c 1e 01 00 |....-...........|
00000030 0d 1e 01 00 0e 1e 01 00 0f 1e 01 00 10 1e 01 00 |................|
00000040 11 1e 01 00 12 1e 01 00 13 1e 01 00 14 1e 01 00 |................|
00000050 15 1e 01 00 16 1e 01 00 17 1e 01 00 18 1e 01 00 |................|
00000060 19 1e 01 00 1a 1e 01 00 1b 1e 01 00 1c 1e 01 00 |................|
00000070 1d 1e 01 00 1e 1e 01 00 1f 1e 01 00 20 1e 01 00 |............ ...|
00000080 21 1e 01 00 22 1e 01 00 23 1e 01 00 24 1e 01 00 |!..."...#...$...|
00000090 25 1e 01 00 26 1e 01 00 27 1e 01 00 28 1e 01 00 |%...&...'...(...|
000000a0 29 1e 01 00 ff ff ff 0f ff ff ff 0f ff ff ff 0f |)...............|
000000b0 ff ff ff 0f 2f 1e 01 00 ff ff ff 0f 31 1e 01 00 |..../.......1...|
000000c0 ff ff ff 0f b7 1e 01 00 ff ff ff 0f ff ff ff 0f |................|
000000d0 35 1e 01 00 36 1e 01 00 37 1e 01 00 38 1e 01 00 |5...6...7...8...|
000000e0 39 1e 01 00 3a 1e 01 00 3b 1e 01 00 3c 1e 01 00 |9...:...;...<...|
000000f0 3d 1e 01 00 3e 1e 01 00 3f 1e 01 00 40 1e 01 00 |=...>...?...@...|
00000100 41 1e 01 00 42 1e 01 00 43 1e 01 00 44 1e 01 00 |A...B...C...D...|
00000110 45 1e 01 00 46 1e 01 00 47 1e 01 00 48 1e 01 00 |E...F...G...H...|
00000120 49 1e 01 00 4a 1e 01 00 4b 1e 01 00 4c 1e 01 00 |I...J...K...L...|
00000130 4d 1e 01 00 4e 1e 01 00 4f 1e 01 00 50 1e 01 00 |M...N...O...P...|
00000140 51 1e 01 00 52 1e 01 00 53 1e 01 00 54 1e 01 00 |Q...R...S...T...|
00000150 55 1e 01 00 56 1e 01 00 57 1e 01 00 58 1e 01 00 |U...V...W...X...|
00000160 59 1e 01 00 5a 1e 01 00 5b 1e 01 00 5c 1e 01 00 |Y...Z...[...\...|
00000170 5d 1e 01 00 5e 1e 01 00 5f 1e 01 00 60 1e 01 00 |]...^..._...`...|
00000180 61 1e 01 00 62 1e 01 00 63 1e 01 00 64 1e 01 00 |a...b...c...d...|
00000190 65 1e 01 00 66 1e 01 00 ff ff ff 0f ff ff ff 0f |e...f...........|
000001a0 69 1e 01 00 6a 1e 01 00 6b 1e 01 00 6c 1e 01 00 |i...j...k...l...|
000001b0 6d 1e 01 00 6e 1e 01 00 6f 1e 01 00 70 1e 01 00 |m...n...o...p...|
000001c0 71 1e 01 00 72 1e 01 00 73 1e 01 00 74 1e 01 00 |q...r...s...t...|
000001d0 75 1e 01 00 76 1e 01 00 77 1e 01 00 78 1e 01 00 |u...v...w...x...|
000001e0 79 1e 01 00 7a 1e 01 00 7b 1e 01 00 7c 1e 01 00 |y...z...{...|...|
000001f0 7d 1e 01 00 7e 1e 01 00 7f 1e 01 00 80 1e 01 00 |}...~...........|
00000200
&#12288;
&#12288;

```

---

### Post by dhysk on 2011-01-28
XP boot cd:

Does your computer have a boot selector.  For instance allot of computers you can push F2 or something simular and choose from a list of what to boot from either the hard drive or CD drive.  You would do this as soon as the computer turns on and you see the bios flash or whatever the first screen you see is before the grub boot menu.  I would try this first.  Normaly the XP cd when it starts to load it will display 'press any key to boot from CD' so you will have to push a key or you will be taken back to the grub boot menu.

---

### Post by thanksinadvance on 2011-01-29
> **dhysk said:**
> XP boot cd:

Does your computer have a boot selector.  For instance allot of computers you can push F2 or something simular and choose from a list of what to boot from either the hard drive or CD drive.  You would do this as soon as the computer turns on and you see the bios flash or whatever the first screen you see is before the grub boot menu.  I would try this first.  Normaly the XP cd when it starts to load it will display 'press any key to boot from CD' so you will have to push a key or you will be taken back to the grub boot menu.
Hi dhysk,
Yes, my laptop has a boot selector and I have already selected the CD drive as the device from which the computer should boot, but it doesn't work. The Windows recovery CD starts spinning inside the CD drive but nothing happens. It just goes back to the GRUB menu. What else do you recommend? Thanks again for you interest.

---

### Post by Rubi1200 on 2011-01-29
Right now I think you need to be more concerned about this:

> /dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda6I am going to PM someone who really knows his stuff about partitions and ask him to take a look.

Until then, I suggest you wait and try to be patient about this (not easy I know).

EDIT: for the sake of readability, please go back to your post with the script results and edit > go advanced.

Highlight the part with the results and then click on the # sign in the toolbar to wrap code tags around the text, then save.

---

### Post by thanksinadvance on 2011-01-29
> **Rubi1200 said:**
> Right now I think you need to be more concerned about this:

I am going to PM someone who really knows his stuff about partitions and ask him to take a look.

Until then, I suggest you wait and try to be patient about this (not easy I know).

EDIT: for the sake of readability, please go back to your post with the script results and edit > go advanced.

Highlight the part with the results and then click on the # sign in the toolbar to wrap code tags around the text, then save.
Thanks Rubi1200,
I have just edited the script results. Hope it is as it should be.
Thanks.

---

### Post by TheHackOps on 2011-01-29
I am pretty sure overlapping means it has the same mount point. Why so many partitions BTW

---

### Post by coffeecat on 2011-01-29
> **TheHackOps said:**
> I am pretty sure overlapping means it has the same mount point. 

If only that were so, but it isn't. Have a look at the fdisk output under 'Drive/Partition Info' in the OP's boot script output. The end sector of sda2 comes after the start sector of sda3, which is serious. It also comes after the first sector of sda6, because sda6 is the first logical partition within the extended partition sda3. Hence the message about overlapping partitions. The problem is in the partition table.

Rubi1200 has pm'd someone who will be able to give definitive advice. We should await that.

---

### Post by thanksinadvance on 2011-01-29
> **coffeecat said:**
> If only that were so, but it isn't. Have a look at the fdisk output under 'Drive/Partition Info' in the OP's boot script output. The end sector of sda2 comes after the start sector of sda3, which is serious. It also comes after the first sector of sda6, because sda6 is the first logical partition within the extended partition sda3. Hence the message about overlapping partitions. The problem is in the partition table.

Rubi1200 has pm'd someone who will be able to give definitive advice. We should await that.
Thanks guys. If the solution involves losing Windows and Linux that's fine for me. I just want to be able to format the partion and run windows again because I need it for work. 
Thank you very much!

---

### Post by coffeecat on 2011-01-29
> **thanksinadvance said:**
> I just want to be able to format the partion and run windows again because I need it for work.

Unfortunately, simply reformatting the partition won't solve the underlying problem which is an illegal entry in the partition table. All you'd be doing would be writing a new filesystem to a partition that still overlaps its neighbour. 

If you are prepared to reinstall Ubuntu and Windows, one option would be to delete primary partition #2, all the logical partitions (#5 upwards), and then the extended partition sda3. You could then create a new set of partitions and reinstall. But that's a fairly drastic way to go about things. In theory, it is possible to edit the partition table to solve the overlapping issue, but I'm reluctant to give advice because I'm not sure whether you should move the sda2 or sda3 boundary. Which is why I suggest awaiting Rubi1200's contact.

Out of interest, can you remember what might have happened just before this problem arose? One would expect a partition table corruption to occur only if you were using partitioning tools or recovery software.

---

### Post by thanksinadvance on 2011-01-29
> **coffeecat said:**
> Unfortunately, simply reformatting the partition won't solve the underlying problem which is an illegal entry in the partition table. All you'd be doing would be writing a new filesystem to a partition that still overlaps its neighbour. 

If you are prepared to reinstall Ubuntu and Windows, one option would be to delete primary partition #2, all the logical partitions (#5 upwards), and then the extended partition sda3. You could then create a new set of partitions and reinstall. But that's a fairly drastic way to go about things. In theory, it is possible to edit the partition table to solve the overlapping issue, but I'm reluctant to give advice because I'm not sure whether you should move the sda2 or sda3 boundary. Which is why I suggest awaiting Rubi1200's contact.

Out of interest, can you remember what might have happened just before this problem arose? One would expect a partition table corruption to occur only if you were using partitioning tools or recovery software.
The only thing that occurs to me is that Windows might have installed some update and after that I started getting a blue screen showing the message "an error has been found on your computer. Windows is going to shut down" (I can't rember the rest). When that happened a couple of times I thought I should format the partition and so i installed Partion Magic to do this and have only one OS. I couldn't do this because at the end of the instalation a message appeared saying something like "C drive not detected" (or recognized... sorry, I can't remeber exactly what it said).  The day after I turned the computer on, booted Windows and the blue screen appeared again. When I tried to restart windows it simply didn't work anymore. I get to the GRUB menu and that's how far i can go now as far as Windows is concerned. Ubuntu still works.

---

### Post by coffeecat on 2011-01-29
Aha!

> **thanksinadvance said:**
> When that happened a couple of times I thought I should format the partition and so i installed Partion Magic

I have no experience of Partition Magic, but I've seen posts on this forum criticising it. Whether fairly or not I don't know. One poster referred to it as "Partition Tragic" - which may or may not be fair comment.  I don't know.

This doesn't help your immediate situation but I recommend that you use Gparted in Ubuntu (or other Linux) for all your partitioning needs in future, but with one exception. You can run Gparted from the live Ubuntu CD which is very convenient. The one exception is that if you ever run Vista or Windows 7 and need to shrink the Windows C: partition, this is better done with the Windows Disk Management utility.

---

### Post by TheHackOps on 2011-01-29
Yep just wait for the pm, but i was just voicing an idea

---

### Post by srs5694 on 2011-01-29
In principle, the bad partition table could have existed for a long time and not caused problems just because they OSes didn't happen to try storing data in the same part of the disk (the overlap is just 7,614 sectors, or 3.7 MiB). According to this hypothesis, Windows tried storing some critical data there first, then Linux overwrote it, and ***bam*** -- unbootable Windows.

I don't see any way to recover your system short of repartitioning and restoring from a backup or re-installing. Whatever you do, ***do not attempt to write anything to /dev/sda!*** To recover your system, you should:


[LIST=1]
[*]Back up any user data from /dev/sda2.
[*]Use Linux's fdisk utility to delete /dev/sda2.
[*]Use Linux's fdisk utility to create a new /dev/sda2.
[*]Use Linux's fdisk utility to change the type code of /dev/sda2 to 0x0c (for FAT) or 0x07 (for NTFS), whichever you plan to use.
[*]Type "sudo mkdosfs -n newfat /dev/sda2" at a Linux shell prompt to create a fresh FAT filesystem in /dev/sda2 with a name of "newfat" (change that however you like). Alternatively, you could use "sudo mkfs.ntfs -L newntfs -Q /dev/sda2" to use NTFS rather than FAT.
[*]Boot your Windows install disc and install Windows to /dev/sda2 (it will of course use its own identification system, so use the partition size or the name you gave it to identify it). Alternatively, use any system backup tools you might have used to restore a backup to /dev/sda2.
[/LIST]


You'll then need to re-install GRUB, which you can do using the Ubuntu install disc (although I don't recall the details) or by using [Super GRUB 2 Disc]("http://www.supergrubdisk.org") to boot into Ubuntu and then typing "sudo grub-install /dev/sda" in a shell.

There's no need to delete all the logical partitions; however, there is a danger that Windows may have overwritten some files or data structures in /dev/sda6. Therefore, at the very least I advise running e2fsck, with its -f option, on that drive from a Linux emergency disc (assuming you're using ext2/3/4fs). For instance, "sudo e2fsck -f /dev/sda6". This will check for and correct filesystem corruption; however, it won't detect corrupted files. If the system is booting, Windows clearly hasn't completely trashed Linux; however, there could be some important user or system file that's been damaged and that will cause problems in the future. If it's a user file, you'll discover it sooner or later -- say, when you load the novel you've been writing and discover that it's filled with Windows Registry entries! If it's a system file, you might find that some program won't launch, fonts are weird or missing, or what have you. In that case, re-installing the affected package should fix the problem. You could re-install Ubuntu to avoid the possibility of running into system problems, but you won't be able to do anything about user file damage except keep any backups you might have made before this problem began in the hope that they're still clean. If you re-install Ubuntu, remember to back up your user data.

Edit: Oh, BTW, I'm the person Rubi1200 PMed to ask for advice.

---

### Post by thanksinadvance on 2011-01-29
Hi guys,
I just came back from an IT shop where I expect my laptop can be fixed. I thought it would be too complicated for me to fix it even with your assistance. Sorry for making you spend time on this. I will ask the people from the store what was the solution and will post it here.
Thank you srs5694 for your long email. 
Thank you all for your guidance.
All the best!

---

### Post by Rubi1200 on 2011-01-29
Definitely let us know what the solution was.

We are all here to help and I am sure we all wish you the best in getting your system up and running again.

Special thanks to srs5694 for the detailed guidance.

Good luck!

---

### Post by thanksinadvance on 2011-02-08
Hi everyone,
 
£129 later and my laptop is functional again, as far as windows is concerned! Regarding the solution to the problem, I was told the hardrive was physically damaged and had to be replaced. That being the case I can't understand how Ubuntu was still working. Anyway, I can only thank you for the time you dedicated to this problem. Thanks.
regards,
PR

---

### Post by Rubi1200 on 2011-02-08
Excellent! I am really glad you got things worked out in the end.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

