---
title: "Error On Running update-grub"
date: 2010-10-10
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-10-10
I have an Acer Aspire One D250 with Ubuntu 10.10 Desktop installed on it, coexisting with a 12 GB Windows Vista restore partition

The restore partition does not show up in GRUB like it used to, when I run sudo update-grub, I get:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
BOOT: No such file or directory
done

```

Here is an output of fdisk -l if it helps

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5cc951fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1448    11624159   27  Unknown
/dev/sda2            1448       30402   232572929    5  Extended
/dev/sda5            1448       30159   230621184   83  Linux
/dev/sda6           30159       30402     1950720   82  Linux swap / Solaris

```

Thanks In Advance

---

### Post by drs305 on 2010-10-11
Your first partition appears messed up but is flagged as bootable.

Just an educated guess - there may be a /boot or /Boot folder within it. Linux doesn't use the 'boot' flag so I really can't say for sure what's triggering the problem with sda1. You can run the boot info script from the following site and post the contents of the RESULTS.txt here. For formatting, please press the # icon in the post's menubar and copy the info between the 'code' tags. Most likely it will show us what the problem is.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by ..::| Dave89 |::.. on 2010-10-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /boot/grub/core.img

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    23,248,380    23,248,318  27 Hidden HPFS/NTFS
/dev/sda2          23,248,894   488,394,751   465,145,858   5 Extended
/dev/sda5          23,248,896   484,491,263   461,242,368  83 Linux
/dev/sda6         484,493,312   488,394,751     3,901,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C8E0BE26E0BE1AA0                       ntfs       PQSERVICE                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5cc273f8-1d2c-4b98-911d-860fab2f36d8   ext4                                     
/dev/sda6        7e6ed8b6-cef7-466a-8c5c-c90b81a85817   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5cc273f8-1d2c-4b98-911d-860fab2f36d8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5cc273f8-1d2c-4b98-911d-860fab2f36d8 ro single 
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
	search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5cc273f8-1d2c-4b98-911d-860fab2f36d8
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
# / was on /dev/sdb5 during installation
UUID=5cc273f8-1d2c-4b98-911d-860fab2f36d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7e6ed8b6-cef7-466a-8c5c-c90b81a85817 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.7GB: boot/grub/core.img
 153.9GB: boot/grub/grub.cfg
  12.8GB: boot/initrd.img-2.6.35-22-generic
  80.7GB: boot/vmlinuz-2.6.35-22-generic
  12.8GB: initrd.img
  80.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  dd 8a 19 20 2d 96 60 e7  86 5e 5f 7c 4f a1 7f a5  |... -.`..^_|O...|
00000010  6f 7b 5b 1d d3 c2 80 2d  03 bb 91 8a 84 a3 f5 91  |o{[....-........|
00000020  9a 25 a9 2e c0 b6 4e 78  15 46 5d ec 34 fe 3e fc  |.%....Nx.F].4.>.|
00000030  d2 6a d0 78 1c 62 af 9d  98 ed bf 37 25 5b fd be  |.j.x.b.....7%[..|
00000040  2a a0 3d 67 42 03 fd 84  45 af c7 58 9c 90 6e a8  |*.=gB...E..X..n.|
00000050  a9 25 bc b2 0a 98 0b 63  0c 6f 2e e5 ff c0 49 83  |.%.....c.o....I.|
00000060  4c 6e 44 20 f5 43 46 5a  2b 1f 5a 22 37 1e 1e 44  |LnD .CFZ+.Z"7..D|
00000070  d4 1e 24 39 1b 96 e2 06  89 6e 75 6b 44 28 f0 9d  |..$9.....nukD(..|
00000080  83 8f 98 0c 51 d4 71 15  b5 11 40 c2 5b a9 03 de  |....Q.q...@.[...|
00000090  02 09 3a 7f e4 cd 5d c8  94 9b 70 57 2d ba a2 79  |..:...]...pW-..y|
000000a0  b1 2a 51 61 1c 78 bd 2c  fb 89 9f ec 32 d4 a1 13  |.*Qa.x.,....2...|
000000b0  f0 62 4a 71 c4 95 2d b8  da 5b 7e e7 df 86 40 99  |.bJq..-..[~...@.|
000000c0  e9 3a 48 27 ef 20 cb b6  94 c2 79 c7 47 fa b1 39  |.:H'. ....y.G..9|
000000d0  74 8b 91 13 10 cd c8 0a  0e 08 34 32 18 66 dc a3  |t.........42.f..|
000000e0  a1 b2 dc 00 ce 4a 11 55  a7 a0 8b 12 3a 28 3d 95  |.....J.U....:(=.|
000000f0  5c 3a fe a9 73 1a 10 71  88 3e 7b 3d e8 97 1d b5  |\:..s..q.>{=....|
00000100  85 41 66 a0 80 ad 38 42  31 f8 ce 59 47 42 7f cb  |.Af...8B1..YGB..|
00000110  cb 4a ee af ad 51 22 17  d5 b8 b4 70 72 0d ff a2  |.J...Q"....pr...|
00000120  81 ac a0 22 04 73 f9 35  45 28 ff 6d f5 55 f0 6b  |...".s.5E(.m.U.k|
00000130  5a c5 c4 9e dd 99 90 44  86 05 16 f4 16 42 ce 8e  |Z......D.....B..|
00000140  8e 42 54 d0 62 36 7d c7  46 90 34 ef d2 dc 2c 3b  |.BT.b6}.F.4...,;|
00000150  2f 13 20 bc 9b d4 41 b2  27 70 dd 36 8e 97 c8 d4  |/. ...A.'p.6....|
00000160  7d 90 da 5c 53 0a 38 3d  d5 2d 0d 8b 31 3c 3b 83  |}..\S.8=.-..1<;.|
00000170  fd 10 2f 8a ec af e8 05  c0 74 82 4c aa a3 16 45  |../......t.L...E|
00000180  1e 95 3c 4e 9a d3 b8 d0  ff 83 50 43 79 9b 40 ac  |..<N......PCy.@.|
00000190  46 7e 9d 05 1d 12 2c 6a  0e 1c d2 7f cc 0a 47 6b  |F~....,j......Gk|
000001a0  72 a5 aa ea 08 f4 8b 3a  16 52 c4 65 61 a9 6b ee  |r......:.R.ea.k.|
000001b0  ef 6d 2d 01 fb b1 13 fe  dc e4 57 46 66 ce 00 fe  |.m-.......WFf...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 7e 1b 00 fe  |............~...|
000001d0  ff ff 05 fe ff ff 02 00  7e 1b 00 90 3b 00 00 00  |........~...;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2010-10-11
You do have dual "boot" folders in sda1:
> 
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR [COLOR="Red"]/BOOT[/COLOR]/BCD [COLOR="Red"]/boot[/COLOR]/grub/core.img



The /boot/grub/core.img file is doing nothing and should be removed. You can do this from within Ubuntu.

Mount your Windows/sda1 partition and with a file browser rename or move the /boot/grub folder elsewhere (you can eve delete it):

> mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
gksu nautilus /mnt/temp
Now rename, move or delete the /boot (LOWER CASE) folder and it's contents.
Then run:
> 
sudo update-grub
sudo umount /mnt/temp

And see if os-prober is now working correctly.

---

### Post by ..::| Dave89 |::.. on 2010-10-11
That worked.  Thanks for your help, drs305!

---

