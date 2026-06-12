---
title: "trouble with installation..."
date: 2010-12-06
forum: General Help
---

### Post by -RYknow on 2010-12-06
Hey all. I'm having an issue getting Ubuntu 10.10 installed on my computer. The computer has an Asus A8N-SLI Premium board, with an Opteron 170. The machine has 1 Raptor X (OS), 2 160gb, and 3x 1TB drives. 

I'm trying to install to the Raptor. I have the three 1TB drives on one raid controller (silicon), and the Raptor on the other (Nvidia) by itself. I've been able to boot up with the live disc, and install Ubuntu. After a restart, the machine won't boot, and it just gives me an error 

"*error: no such device: 09b8c2af.......grub rescue>*"

If I restart, and hit F8 to pick which device I want to boot to, I can select the raptor, and ubuntu will boot up just fine. But if I don't choose the device, I get the same error over and over. Hopefully someone can give me some input here to get this machine to boot normal. 

Thanks in advance, 
-RYknow

---

### Post by ronparent on 2010-12-07
I suspect that the grub boot loader is located on the raptor. You can either change the boot in bios to boot from the raptor (assuming the raptor is not a raid) or reinstall grub to boot from another disk of choice? You might got to this site - [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) - and run the script to produce a results.txt on the desktop. This will give a clear picture of your setup and make it easier to help you.

---

### Post by -RYknow on 2010-12-07
Here are the results from the script you gave me.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   281,063,423   281,061,376  83 Linux
/dev/sdd2         281,065,470   293,046,271    11,980,802   5 Extended
/dev/sdd5         281,065,472   293,046,271    11,980,800  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2C8DF30C70DC3312                       ntfs       TV Shows 2                    
/dev/sda                                                silicon_medley_raid_member                               
/dev/sdb1        2D4A1DD30C09D020                       ntfs       1TB Storage                   
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc1        C004A1D104A1CB2C                       ntfs       TV Shows 1                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        65dce69e-a99c-43e7-a1ca-77ba2a0a2321   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        27a9dc57-a322-4cff-98ce-9295c487ab2a   swap                                     
/dev/sdd                                                nvidia_raid_member                               
/dev/sde1        4E2BAE224D232EC7                       ntfs       Torrents Drive                
/dev/sde: PTTYPE="dos" 
/dev/sdf1        9410D60810D5F16A                       ntfs       Linux Backup                  
/dev/sdf: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=65dce69e-a99c-43e7-a1ca-77ba2a0a2321 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=65dce69e-a99c-43e7-a1ca-77ba2a0a2321 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=65dce69e-a99c-43e7-a1ca-77ba2a0a2321 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=65dce69e-a99c-43e7-a1ca-77ba2a0a2321 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 65dce69e-a99c-43e7-a1ca-77ba2a0a2321
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_fcdfcdbg1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_fcdfcdbg5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  64.6GB: boot/grub/core.img
  88.1GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-23-generic
  64.6GB: boot/vmlinuz-2.6.35-22-generic
  64.6GB: boot/vmlinuz-2.6.35-23-generic
    .9GB: initrd.img
    .8GB: initrd.img.old
  64.6GB: vmlinuz
  64.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdf

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  20 5d 05 0d 00 00 80 01  |........ ]......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd2

00000000  12 ef 15 00 22 ef 15 00  32 ef 15 00 42 ef 15 00  |...."...2...B...|
00000010  52 ef 15 00 62 ef 15 00  72 ef 15 00 82 ef 15 00  |R...b...r.......|
00000020  92 ef 15 00 a2 ef 15 00  b2 ef 15 00 c2 ef 15 00  |................|
00000030  d2 ef 15 00 e2 ef 15 00  f2 ef 15 00 02 f0 15 00  |................|
00000040  12 f0 15 00 22 f0 15 00  32 f0 15 00 42 f0 15 00  |...."...2...B...|
00000050  52 f0 15 00 62 f0 15 00  72 f0 15 00 82 f0 15 00  |R...b...r.......|
00000060  92 f0 15 00 a2 f0 15 00  b2 f0 15 00 c2 f0 15 00  |................|
00000070  d2 f0 15 00 e2 f0 15 00  f2 f0 15 00 02 f1 15 00  |................|
00000080  12 f1 15 00 22 f1 15 00  32 f1 15 00 42 f1 15 00  |...."...2...B...|
00000090  52 f1 15 00 62 f1 15 00  72 f1 15 00 82 f1 15 00  |R...b...r.......|
000000a0  a0 30 16 00 00 00 00 00  00 00 00 00 00 00 00 00  |.0..............|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  70 03 16 00 00 7d 11 00  e0 02 16 00 00 92 11 00  |p....}..........|
000000d0  50 02 16 00 b0 01 16 00  b0 a3 11 00 70 a4 11 00  |P...........p...|
000000e0  80 9d 11 00 70 00 16 00  e0 ff 15 00 40 ff 15 00  |....p.......@...|
000000f0  10 ff 15 00 e0 fe 15 00  30 fb 15 00 10 fb 15 00  |........0.......|
00000100  80 fa 15 00 60 fa 15 00  10 f9 15 00 e0 f8 15 00  |....`...........|
00000110  50 f2 15 00 00 00 00 00  00 00 00 00 00 00 00 00  |P...............|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000140  00 00 00 00 2e 67 6e 75  2e 62 75 69 6c 64 2d 69  |.....gnu.build-i|
00000150  64 00 2e 67 6e 75 2e 68  61 73 68 00 2e 64 79 6e  |d..gnu.hash..dyn|
00000160  73 79 6d 00 2e 64 79 6e  73 74 72 00 2e 67 6e 75  |sym..dynstr..gnu|
00000170  2e 76 65 72 73 69 6f 6e  00 2e 67 6e 75 2e 76 65  |.version..gnu.ve|
00000180  72 73 69 6f 6e 5f 72 00  2e 72 65 6c 2e 64 79 6e  |rsion_r..rel.dyn|
00000190  00 2e 72 65 6c 2e 70 6c  74 00 2e 69 6e 69 74 00  |..rel.plt..init.|
000001a0  2e 74 65 78 74 00 2e 66  69 6e 69 00 2e 72 6f 64  |.text..fini..rod|
000001b0  61 74 61 00 2e 65 68 5f  66 72 61 6d 65 00 00 fe  |ata..eh_frame...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 b6 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Sorry if you didn't need the whole thing...I wasn't sure what information you were going to need. Also, the Raptor is part of a raid config. I had to set it up as a spanning drive. It's the only drive on that raid controller. It's set to be used as a JBOD. I had 10.04 working with this same configuration, but 10.10 doesn't seem to like it for some reason.  

-RYknow

---

### Post by ronparent on 2010-12-07
The grub boot loader on sda (your current boot drive) is a dead end. You can either reinstall grub to that drive to boot properly or change the boot order in bios to boot on sdd (presumably your raptor). As you discovered it will boot fine on that drive if it is first in boot order in bios.

Alternatively you can reinstall grub so that it will boot on sda (see this reference - [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2). In most cases that is a simple two step process that goes like this. From the live cd open a terminal and write:
```
sudo mount /dev/sdd1 /mnt
```
Then reinstall thus:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

On completion a reboot shoud have your system booting on sda. Good luck.:)

---

### Post by -RYknow on 2010-12-07
Thanks for the replay. Just one more question. Wouldn't I want to boot loader to be installed on the same drive as the OS (the Raptor, Sdd)

If thats the case I would just use the cammands you gave me, and switch it to sdd?

Thanks, 
-RYknow

---

### Post by ronparent on 2010-12-07
It makes no real difference where it is. It's basically what your preference is. 

You already have it on sdd. To use it you just have to change your boot drive in bios. You have already done the that on a temporary basis by selecting your raptor with F8 at boot. Now if that is where you prefer it enter the key open your bios at the same point as the F8 at boot and permanently change the bios boot order. I'm not familiar with your particular bios so I can't be more specific. Post if you need to air it out.

---

### Post by -RYknow on 2010-12-07
Wow...I feel like such an idiot. I've been  in and out of the BIOS a  hundred times. Wasn't thinking I could change the boot order, other then CD-rom, HD, USB, etc. 

That fixed my issue with boot up!! So thank you very much!! Now, I have one other request. I've always used the NTFS config tool as an easy way to have all my HDD's mount on start up. I installed the NTFS tool, click on it to run it, it asks for my password...then nothing. No crash error, or report...I just get nothing. Here is the output when I try to run it from terminal. 

> ryknow@ryknow-Server:~$ sudo ntfs-config
[sudo] password for ryknow: 
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'
ryknow@ryknow-Server:~$ 



Any suggestions on getting the NTFS tool working correctly?

Thanks again!
-RYknow

---

