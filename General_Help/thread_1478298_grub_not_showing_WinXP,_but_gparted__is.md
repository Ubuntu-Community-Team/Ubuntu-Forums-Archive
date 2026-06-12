---
title: "grub not showing WinXP, but gparted  is"
date: 2010-05-09
forum: General Help
---

### Post by DougieFresh4U on 2010-05-09
Don't know what happened to my dual boot but all was good then after some updates, WinXP 'vanished' from grub.
Dual boot with WinXP & Lucid

---

### Post by dcstar on 2010-05-10
> **DougieFresh4U said:**
> Don't know what happened to my dual boot but all was good then after some updates, WinXP 'vanished' from grub.
Dual boot with WinXP & Lucid

And what do you suppose that yellow warning marker in gparted means?

---

### Post by wilee-nilee on 2010-05-10
Post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DougieFresh4U on 2010-05-10
> **dcstar said:**
> And what do you suppose that yellow warning marker in gparted means?
Actually, that's what I am trying to find out as there is an obvious problem. :confused::P

> **wilee-nilee said:**
> Post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Thanks. 
Here ya go.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 533480344 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid  
                      
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
160 heads, 6 sectors/track, 651190 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              6   323,440,414   323,440,409   7 HPFS/NTFS
/dev/sda2         323,440,638   625,141,759   301,701,122   5 Extended
/dev/sda5         612,810,752   625,141,759    12,331,008  82 Linux swap / Solaris
/dev/sda6         323,440,640   612,808,703   289,368,064  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92A8CA86A8CA67F5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5eec7203-5900-46e9-8517-43d427806936   swap                                     
/dev/sda6        0aa5591e-eca0-426b-9bba-d872e0991836   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
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
search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
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
menuentry 'Ubuntu, with Linux 2.6.34-020634rc6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	linux	/boot/vmlinuz-2.6.34-020634rc6-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro   quiet splash
	initrd	/boot/initrd.img-2.6.34-020634rc6-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634rc6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	echo	'Loading Linux 2.6.34-020634rc6-generic ...'
	linux	/boot/vmlinuz-2.6.34-020634rc6-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-020634rc6-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634rc5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	linux	/boot/vmlinuz-2.6.34-020634rc5-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro   quiet splash
	initrd	/boot/initrd.img-2.6.34-020634rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634rc5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	echo	'Loading Linux 2.6.34-020634rc5-generic ...'
	linux	/boot/vmlinuz-2.6.34-020634rc5-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-020634rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-996-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	linux	/boot/vmlinuz-2.6.34-996-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro   quiet splash
	initrd	/boot/initrd.img-2.6.34-996-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-996-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	echo	'Loading Linux 2.6.34-996-generic ...'
	linux	/boot/vmlinuz-2.6.34-996-generic root=UUID=0aa5591e-eca0-426b-9bba-d872e0991836 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-996-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0aa5591e-eca0-426b-9bba-d872e0991836
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 165.8GB: boot/grub/core.img
 174.3GB: boot/grub/grub.cfg
 165.8GB: boot/initrd.img-2.6.34-020634rc5-generic
 165.8GB: boot/initrd.img-2.6.34-020634rc6-generic
 273.1GB: boot/initrd.img-2.6.34-996-generic
 167.0GB: boot/vmlinuz-2.6.34-020634rc5-generic
 168.9GB: boot/vmlinuz-2.6.34-020634rc6-generic
 182.0GB: boot/vmlinuz-2.6.34-996-generic
 273.1GB: initrd.img
 165.8GB: initrd.img.old
 182.0GB: vmlinuz
 168.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b2 b8 3e 60 25 01 c0 55  1d 6b d5 34 cd 40 59 5d  |..>`%..U.k.4.@Y]|
00000010  c7 bd 48 46 20 fd 2b a2  3d cc f9 7d fb 1e d9 a6  |..HF .+.=..}....|
00000020  45 65 ad 58 21 21 0e 54  76 cf 35 c7 78 87 49 93  |Ee.X!!.Tv.5.x.I.|
00000030  4b 91 91 72 60 6e 57 d8  d7 b6 e2 9d 15 24 75 42  |K..r`nW......$uB|
00000040  29 ab 1c 6a 29 79 9d 00  c3 0a cd d7 52 34 b2 9e  |)..j)y......R4..|
00000050  39 97 21 c7 07 d2 bc 7e  6f 65 27 70 97 63 cc 64  |9.!....~oe'p.c.d|
00000060  63 e6 34 63 38 cf 04 0e  82 ab c2 64 8a 66 76 3b  |c.4c8......d.fv;|
00000070  86 7a fa 8a f3 f1 2d 46  17 39 ea 2d 49 6e 03 b8  |.z....-F.9.-In..|
00000080  57 e7 81 c9 23 ad 4f 06  e6 5e 41 20 af dd af 26  |W...#.O..^A ...&|
00000090  a4 f9 96 a4 a9 b4 ac 73  9a 86 94 ef 23 3c 40 e0  |.......s....#<@.|
000000a0  f6 ff 00 1a d8 f0 7e 81  25 f5 fc 6a 5d 81 3f c3  |......~.%..j].?.|
000000b0  8e 95 ed e5 d5 d4 94 53  2b 9b da 5d 9e b5 3f c2  |.......S+..]..?.|
000000c0  ab ab c8 04 98 05 31 d0  0c 91 56 fc 37 e1 7f f8  |......1...V.7...|
000000d0  46 e6 56 60 78 6c 82 c2  be 8a b4 1d 93 66 f1 5e  |F.V`xl.......f.^|
000000e0  ed 91 d5 6a b7 16 42 1f  3e 3d a1 c0 e4 f1 9a f3  |...j..B.>=......|
000000f0  dd 4f c6 09 13 34 48 cc  46 7f 84 74 ae 1a 92 d7  |.O...4H.F..t....|
00000100  41 46 1a 6a 64 db df c1  7f 2a 34 8c 30 7a 83 fc  |AF.jd....*4.0z..|
00000110  eb 17 c4 be 1d 48 e4 5b  9b 50 32 79 20 57 9b 5a  |.....H.[.P2y W.Z|
00000120  a3 48 4a 77 9f 2b d8 cf  b5 e1 00 6c 8f 6c f1 56  |.HJw.+.....l.l.V|
00000130  8c f3 29 42 57 70 1e 9e  95 cd 5e a5 a9 b4 63 25  |..)BWp....^...c%|
00000140  ad 98 b3 9c fc e4 b0 e7  bd 73 fa d4 12 4b 04 b1  |.........s...K..|
00000150  ba 83 83 d8 57 0e 09 a8  d5 4c 70 97 be 91 cf e8  |....W....Lp.....|
00000160  7a 50 6b b5 2f b8 73 c7  b7 bd 7a 33 69 b1 d9 aa  |zPk./.s...z3i...|
00000170  ac 4c b8 e3 23 d7 8a fa  08 b4 d3 16 2a 6b da 59  |.L..#.......*k.Y|
00000180  1b fa 31 64 8b 05 01 61  f7 7f 2a e7 3c 44 f7 5a  |..1d...a..*.<D.Z|
00000190  5e a5 1c b0 93 e5 c8 47  ca 3b 55 51 5e e5 c2 82  |^......G.;UQ^...|
000001a0  bc ec cb 10 c8 da ba 05  e5 24 c7 27 1c fd 6b 65  |.........$.'..ke|
000001b0  f4 ed 46 d2 cb 32 c6 65  83 1f 2b 0e 95 9d 00 9f  |..F..2.e..+.....|
000001c0  c6 ff 82 9f c6 ff 02 70  3f 11 00 28 bc 00 00 9f  |.......p?..(....|
000001d0  c6 ff 05 9f c6 ff 01 00  00 00 01 68 3f 11 00 00  |...........h?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-05-10
First try the chkdsk:

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C: 
chkdsk C: /R
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by DougieFresh4U on 2010-05-10
WinXp is not a choice in grub, as in 'not there'

---

### Post by wilee-nilee on 2010-05-10
> **DougieFresh4U said:**
> WinXp is not a choice in grub, as in 'not there'
Follow the post above you with a XP install disc, it is the correct path grasshopper.;)

---

### Post by wilee-nilee on 2010-05-10
So if you do not have a XP disc here is a oem download do not install with it but it will get you to the area oldfred suggests.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by DougieFresh4U on 2010-05-11
So I pop in WinXP cd and I fixboot & fixmbr.
Now I can boot into Windows but I have no grub for my Ubuntu install

---

### Post by oldfred on 2010-05-11
If your Lucid is a new install you have grub2, if an upgrade you may have grub legacy, be sure to follow the correct version of grub.
[U]
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[/U]

---

### Post by DougieFresh4U on 2010-05-11
> **oldfred said:**
> If your Lucid is a new install you have grub2, if an upgrade you may have grub legacy, be sure to follow the correct version of grub.
[U]
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[/U]

Thank you

---

### Post by DougieFresh4U on 2010-05-11
Here is how I managed to fix:
I first fixed WinXP with Windows cd, fixboot & fixmbr, which left me with being able to boot WinXP, no grub
My machine was a dual boot, hard drive is 320GB, split between WinXP and Ubuntu. I popped in live-cd and I shrunk the Ubuntu partition to half it's size. I installed Ubuntu using the 'new' free space. Grub was installed on the new partition. When I rebooted, I was presented with grub menu, which was missing before.
I now have a triple boot machine, which is what I wanted any ways

---

