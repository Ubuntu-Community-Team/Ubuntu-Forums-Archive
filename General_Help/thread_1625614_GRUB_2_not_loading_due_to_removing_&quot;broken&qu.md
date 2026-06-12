---
title: "GRUB 2 not loading due to removing &quot;broken&quot; USB"
date: 2010-11-19
forum: General Help
---

### Post by Jetro on 2010-11-19
**First of all, the title is wrong. It's supposed to say "broken Ubuntu installation", not USB.**

Okay, so I have read a dozen threads, but none of them have offered me a solution:

I was supposed to install Ubuntu 10.10 alongside Windows. I got _[stuck on the keyboard selection screen](http://ubuntuforums.org/showpost.php?p=10133488&postcount=4)_, and had to abort and install again.

Then I booted from the Ubuntu USB and used GParted to delete the broken Ubuntu 10.10 installation, and the swap associated with this.

The next time I rebooted, GRUB 2 was gone. I got a saying:
```
error: no such partition
grub rescue>
```

A lot of searches on Google has not been satisfying, and the most results I get are "How to fix GRUB 2 after installing Windows", which is not my problem.

I tried some of the "solutions" I found, most of them did nothing, but I did
```
grub-install /dev/sda
```
from _[this page](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)_, which worked successfully, and now, whenever I boot the PC, this comes up:
```
GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
```

No way of me switching between Windows and Ubuntu yet.

I also tried installing grub in both the Ubuntu partition and a clean one, only to get these errors:
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: if you really want blocklists, use --force...

```

When the terminal warns me like that, I decided not to try to forcespoon anything. :P So... what should I do?

---

### Post by Quackers on 2010-11-19
Please boot into the Live cd/usb and select "try ubuntu" then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Jetro on 2010-11-19
I would love to try that, unfortunately I am lost on what the path to my desktop is. >_> It's not /home/ubuntu/desktop.

---

### Post by Quackers on 2010-11-19
If the boot script downloaded to your desktop use
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```
If the file is somewhere else you can just copy/paste it to the desktop then run that command in the terminal.

---

### Post by Jetro on 2010-11-19
Haha, now I got it: I wrote Desktop with a lower case d. :|

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /grub/core.img

sda2: _________________________________________________________________________

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   106,513,992   106,513,930   7 HPFS/NTFS
/dev/sda2         106,514,430   271,001,599   164,487,170   5 Extended
/dev/sda5         106,514,432   268,859,391   162,344,960  83 Linux
/dev/sda6         268,861,440   271,001,599     2,140,160  82 Linux swap / Solaris
/dev/sda3         271,001,600   312,580,095    41,578,496   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16047407104 bytes
94 heads, 30 sectors/track, 11114 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    31,342,591    31,334,528   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        D0141A43141A2D4A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        397BCD174307DB29                       ntfs                                     
/dev/sda5        e1d5f3e4-bb01-494a-a40e-e4b6b94555f5   ext4                                     
/dev/sda6        b6d82fa8-8db6-4583-95fa-83de95e9a343   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8B92-B79A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=e1d5f3e4-bb01-494a-a40e-e4b6b94555f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=e1d5f3e4-bb01-494a-a40e-e4b6b94555f5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set e1d5f3e4-bb01-494a-a40e-e4b6b94555f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d0141a43141a2d4a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.04.3 LTS (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1129c576-a236-4c3d-9bed-b48917b7d8f4
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=1129c576-a236-4c3d-9bed-b48917b7d8f4 ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5c49c575-a720-4c68-891d-ca361af4d44a
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda7
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
# / was on /dev/sda9 during installation
UUID=e1d5f3e4-bb01-494a-a40e-e4b6b94555f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=b6d82fa8-8db6-4583-95fa-83de95e9a343 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  56.8GB: boot/grub/core.img
  65.7GB: boot/grub/grub.cfg
  55.1GB: boot/initrd.img-2.6.35-22-generic-pae
  56.9GB: boot/vmlinuz-2.6.35-22-generic-pae
  55.1GB: initrd.img
  56.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4e 51 21 a6 96 33 e6 d9  84 34 f4 b9 46 71 a5 37  |NQ!..3...4..Fq.7|
00000010  06 f9 dd 75 93 d2 ff 7d  97 48 b8 92 05 c3 6a 07  |...u...}.H....j.|
00000020  50 87 3b c8 a1 02 9f fa  d0 3d e5 d1 e5 74 80 41  |P.;......=...t.A|
00000030  b4 a4 34 82 16 07 8e 3b  07 2e 79 bc 5b 34 e7 39  |..4....;..y.[4.9|
00000040  35 7e c5 ca 5a 4c b1 e6  ad 55 98 bb 18 47 a1 18  |5~..ZL...U...G..|
00000050  93 36 6a 05 ca a4 a6 8a  57 10 93 4b a8 98 d3 26  |.6j.....W..K...&|
00000060  51 26 9e 88 a2 a1 1e ff  fb 92 40 99 0e e2 93 2b  |Q&........@....+|
00000070  d8 07 61 a0 00 51 e5 7a  e0 ec 34 00 0b 10 65 58  |..a..Q.z..4...eX|
00000080  55 9c 00 01 4f 0c aa 86  b3 80 00 53 48 68 4e eb  |U...O......SHhN.|
00000090  8c 67 1c 1d 0a 3f bf a5  f9 28 b8 6c 71 a2 82 8e  |.g...?...(.lq...|
000000a0  fa 50 be ef 4e ca ff fa  d2 95 31 7e 60 d7 a5 93  |.P..N.....1~`...|
000000b0  08 0c 4d 36 9e 32 dd e8  3a ec ce cc 14 03 43 e8  |..M6.2..:.....C.|
000000c0  f8 90 e5 bd ae be 93 7c  b0 02 8d c5 93 9c bb b2  |.......|........|
000000d0  37 9d 94 2c 09 a7 ca 18  79 20 00 0b d9 20 08 48  |7..,....y ... .H|
000000e0  00 09 32 0f 0b 8a 4f e3  1e 10 b1 8d 01 4b 95 74  |..2...O......K.t|
000000f0  98 23 6e 84 06 a0 e3 84  4d 08 e2 86 f0 bd 62 a0  |.#n.....M.....b.|
00000100  ac c3 58 d4 75 1e 69 6d  aa 08 0e 25 5e 8e 9e 5d  |..X.u.im...%^..]|
00000110  28 93 6a 8e 2d 12 9a d6  5b de a3 d6 2c cb 11 01  |(.j.-...[...,...|
00000120  9b 26 b4 07 1a 76 61 b9  3b 04 72 b1 ad 9e 36 ec  |.&...va.;.r...6.|
00000130  c3 4d c5 f5 6f 6a 3e 55  62 8e 5c 0d 48 aa cc f5  |.M..oj>Ub.\.H...|
00000140  31 96 8b 88 96 aa 58 98  52 59 4d 2e 36 2a e5 94  |1.....X.RYM.6*..|
00000150  d2 97 c1 0c d5 c0 96 c7  d9 c3 cf a6 9f 69 65 23  |.............ie#|
00000160  92 36 ce 2f 16 a0 9c b1  86 b4 e8 2e ac ee e1 dc  |.6./............|
00000170  f9 ca f6 ea 5a 8c 3f 15  63 6f fd ac 25 92 cd 5e  |....Z.?.co..%..^|
00000180  a7 cf fd 54 74 aa a8 31  2c 87 a3 70 d5 dd 4e ce  |...Tt..1,..p..N.|
00000190  56 ff a5 e7 2b 65 7e cc  99 64 04 00 00 00 06 31  |V...+e~..d.....1|
000001a0  0f 0d 66 40 cb 04 eb 72  ce f2 a3 b5 5a a6 73 5b  |..f@...r....Z.s[|
000001b0  f3 c9 18 e2 02 c0 be 33  20 11 d4 8c 66 58 00 fe  |.......3 ...fX..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 ad 09 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  ad 09 00 b0 20 00 00 00  |.......0.... ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by Quackers on 2010-11-19
Some of grub's boot files are in sda1 and that is where grub is looking for them in order to boot Ubuntu. However your Ubuntu installation is in sda5 and grub should be looking there for the files.
To get Ubuntu booting I would suggest entering these 2 commands one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
This may work, or it may be necessary to chroot into your installation, but it's worth a try.
It will also be necessary to repair your Windows installation later.

---

### Post by Jetro on 2010-11-19
Thanks, it worked! :D

Windows also works normally, except I had to check the disk on startup (which was no surprise).

There are still some old entries there, though, such as Ubuntu 8.04 and the broken 10.10. How can I (easily) remove those? (I don't get GRUB 2 at all, I've read the official guideline, but I get no wiser. The old GRUB was so much easier! :P) Anyhow, I will try to read into it a bit more.

---

### Post by Quackers on 2010-11-19
Happy to hear things are up and running again :-) And Windows too, is a bonus :-)
For all things grub I always refer to drs305's guides below

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Jetro on 2010-11-19
Thanks for those. I will look into it. ;)
I'll just mark this as solved and then I will be on my way.

---

