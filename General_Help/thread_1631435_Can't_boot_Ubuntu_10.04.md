---
title: "Can't boot Ubuntu 10.04"
date: 2010-11-26
forum: General Help
---

### Post by anton1756 on 2010-11-26
Hi,
 
For no reason i can think of, my Ubuntu stoped working.
 
I get this when i try to boot in the debug mode:
[http://www.renfors.org/misc/IMG_0054b.jpg](http://www.renfors.org/misc/IMG_0054b.jpg)
 
Could it be a hardware problem? 
Everything was working earlier and i haven't changed anything.
My Windows partition on the same computer works fine.
 
If i try to boot in normal mode, it will boot incredibly slow and it wont beusable after boot.
 
/Anton

---

### Post by Hippytaff on 2010-11-26
Welcome to the forums :-)

Can you boot with a liveCD or USB and post the results.txt of this script - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

will give info to help us diagnose the problem

---

### Post by ivarn on 2010-11-26
sounds like a broken update or something. These things can happen if you turn off the computer and there's a system updating process going on in the background.
Do this:
You can access recover mode, right? If yes, go to "fix broken packages", and if not, in the terminal prompt type in sudo apt-get install ubuntu-desktop.

---

### Post by anton1756 on 2010-11-26
Here is the results from the bootscript: [http://www.renfors.org/misc/RESULTS.txt](http://www.renfors.org/misc/RESULTS.txt)
 
When i tried repairing the packages, i got error messages about failed http-connections. The ubuntu-desktop reinstallation didn't work either, nothing was effected.

---

### Post by Hippytaff on 2010-11-26
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    28,534,783    28,532,736  27 Hidden HPFS/NTFS
/dev/sda2    *     28,534,784   310,382,642   281,847,859   7 HPFS/NTFS
/dev/sda3         310,391,865   625,137,344   314,745,480   5 Extended
/dev/sda5         310,391,928   612,269,279   301,877,352  83 Linux
/dev/sda6         612,269,343   625,137,344    12,868,002  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,831,550     7,831,519   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        264833B34833811B                       ntfs       Recovery                      
/dev/sda2        BCA2AA34A2A9F356                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ba621d4a-0b29-43cb-839f-da1c90b1c5b2   ext4                                     
/dev/sda6        71f6fe35-a954-4cfa-8b4e-a83188f96e6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7C97-100F                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
set locale_dir=($root)/boot/grub/locale
set lang=sv
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
menuentry 'Ubuntu, med Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-25-generic-pae (Ã¥terstÃ¤llningslÃ¤ge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	echo	'LÃ¤ser in Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro single 
	echo	'LÃ¤ser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-24-generic-pae (Ã¥terstÃ¤llningslÃ¤ge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	echo	'LÃ¤ser in Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro single 
	echo	'LÃ¤ser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-23-generic-pae (Ã¥terstÃ¤llningslÃ¤ge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	echo	'LÃ¤ser in Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro single 
	echo	'LÃ¤ser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-22-generic-pae (Ã¥terstÃ¤llningslÃ¤ge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	echo	'LÃ¤ser in Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro single 
	echo	'LÃ¤ser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.31-21-generic-pae (Ã¥terstÃ¤llningslÃ¤ge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	echo	'LÃ¤ser in Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 ro single 
	echo	'LÃ¤ser in initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ba621d4a-0b29-43cb-839f-da1c90b1c5b2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 264833b34833811b
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bca2aa34a2a9f356
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ba621d4a-0b29-43cb-839f-da1c90b1c5b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=71f6fe35-a954-4cfa-8b4e-a83188f96e6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.1.2/media /mnt/media cifs username=anton,password=citronsoda 0 0

=================== sda5: Location of files loaded by Grub: ===================


 159.2GB: boot/grub/core.img
 162.0GB: boot/grub/grub.cfg
 186.9GB: boot/initrd.img-2.6.31-21-generic-pae
 195.5GB: boot/initrd.img-2.6.32-22-generic-pae
 197.6GB: boot/initrd.img-2.6.32-23-generic-pae
 270.7GB: boot/initrd.img-2.6.32-24-generic-pae
 273.7GB: boot/initrd.img-2.6.32-25-generic-pae
 171.8GB: boot/vmlinuz-2.6.31-21-generic-pae
 186.9GB: boot/vmlinuz-2.6.32-22-generic-pae
 184.7GB: boot/vmlinuz-2.6.32-23-generic-pae
 189.0GB: boot/vmlinuz-2.6.32-24-generic-pae
 191.1GB: boot/vmlinuz-2.6.32-25-generic-pae
 273.7GB: initrd.img
 270.7GB: initrd.img.old
 191.1GB: vmlinuz
 189.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 28 00  |.X.SYSLINUX..@(.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  df 7f 77 00 bc 03 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 0f 10 97 7c 4e  4f 20 4e 41 4d 45 20 20  |..)...|NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 20 29 16 00  66 ba 00 00 00 00 bb 00  |}.f. )..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
for ease of use...having a look :-)

---

