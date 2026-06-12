---
title: "Grub Not showing Windows 7"
date: 2012-05-16
forum: General Help
---

### Post by pranjalsaxena on 2012-05-16
Hi,

I recently installed ubuntu 12.04 along my Win7. But the grub is not showing win 7 entry and I am unable to login to windows.

I have gone through many posts in this forum but couldn't find a working solution.

Please help.

Here is what all I have tried:

```

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

```

```

fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25de25dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    21434367    10716160   83  Linux
/dev/sda2        21436414   488390655   233477121    f  W95 Ext'd (LBA)
/dev/sda5        40965813   163846934    61440561    7  HPFS/NTFS/exFAT
/dev/sda6       163846998   286728119    61440561    7  HPFS/NTFS/exFAT
/dev/sda7       286728183   430092179    71681998+   7  HPFS/NTFS/exFAT
/dev/sda8       430092288   488390655    29149184    7  HPFS/NTFS/exFAT
/dev/sda9        21436416    23388159      975872   82  Linux swap / Solaris
/dev/sda10       23390208    40964095     8786944   83  Linux

Partition table entries are not in disk order


```

I tried fixing boot issues by [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), but to no help.

Output from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) is 
```


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 108. But according to the info from fdisk, 
                       sda8 starts at sector 430092288.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    21,434,367    21,432,320  83 Linux
/dev/sda2          21,436,414   488,390,655   466,954,242   f W95 Extended (LBA)
/dev/sda5          40,965,813   163,846,934   122,881,122   7 NTFS / exFAT / HPFS
/dev/sda6         163,846,998   286,728,119   122,881,122   7 NTFS / exFAT / HPFS
/dev/sda7         286,728,183   430,092,179   143,363,997   7 NTFS / exFAT / HPFS
/dev/sda8         430,092,288   488,390,655    58,298,368   7 NTFS / exFAT / HPFS
/dev/sda9          21,436,416    23,388,159     1,951,744  82 Linux swap / Solaris
/dev/sda10         23,390,208    40,964,095    17,573,888  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        499d65c2-edb7-45d8-861e-c46556fca741   ext4       
/dev/sda10       8a630801-bff3-4df8-8cd5-2469a09b8b07   ext4       
/dev/sda5        58A4E3D8A4E3B6A2                       ntfs       Games
/dev/sda6        1E94F3F694F3CE71                       ntfs       Personal
/dev/sda7        5600FB1400FAFA37                       ntfs       Shared
/dev/sda8        96DC9E5DDC9E3807                       ntfs       
/dev/sda9        4bc599cb-0ed9-4693-ab08-90a7a596fee8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /home                    ext4       (rw)
/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=499d65c2-edb7-45d8-861e-c46556fca741 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=499d65c2-edb7-45d8-861e-c46556fca741 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=499d65c2-edb7-45d8-861e-c46556fca741 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=499d65c2-edb7-45d8-861e-c46556fca741 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 499d65c2-edb7-45d8-861e-c46556fca741
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=499d65c2-edb7-45d8-861e-c46556fca741 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=8a630801-bff3-4df8-8cd5-2469a09b8b07 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=4bc599cb-0ed9-4693-ab08-90a7a596fee8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.404708862 = 9.024487424    boot/grub/core.img                             1
   2.370285034 = 2.545074176    boot/grub/grub.cfg                             1
   0.883823395 = 0.948998144    boot/initrd.img-3.2.0-23-generic-pae           3
   2.057445526 = 2.209165312    boot/initrd.img-3.2.0-24-generic-pae           2
   8.712425232 = 9.354895360    boot/vmlinuz-3.2.0-23-generic-pae              1
   1.591587067 = 1.708953600    boot/vmlinuz-3.2.0-24-generic-pae              1
   2.057445526 = 2.209165312    initrd.img                                     2
   0.883823395 = 0.948998144    initrd.img.old                                 3
   1.591587067 = 1.708953600    vmlinuz                                        1
   8.712425232 = 9.354895360    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  31 00 a4 4e dc 9b 2e ad  72 d1 c7 5c 42 17 e4 2b  |1..N....r..\B..+|
00000010  50 8f 42 d1 4e b1 69 e1  82 70 46 9c 35 a4 69 15  |P.B.N.i..pF.5.i.|
00000020  44 be ee f2 99 91 42 cd  dc 53 7a 58 90 34 9e 05  |D.....B..SzX.4..|
00000030  de 52 e2 e9 c9 29 e2 38  ca b8 dd 03 1a f7 ee ba  |.R...).8........|
00000040  c9 48 7d 14 c5 7e d6 9e  5f 3f fa b9 eb 44 96 fd  |.H}..~.._?...D..|
00000050  bc aa 04 97 96 7a 3a 1b  f3 70 1c 92 5a 49 7a 17  |.....z:..p..ZIz.|
00000060  49 78 06 95 c6 9e 03 7c  f4 0c b4 00 7a 79 89 53  |Ix.....|....zy.S|
00000070  33 b2 f4 52 89 4b 44 72  b1 c9 ce c6 25 a6 54 80  |3..R.KDr....%.T.|
00000080  be 0c 80 c3 81 77 ca 8a  93 ed 16 58 d6 e2 96 af  |.....w.....X....|
00000090  ed bf 51 a8 9c 9d 37 92  30 ac 44 84 12 c0 62 56  |..Q...7.0.D...bV|
000000a0  9d df 38 25 9d 8b 82 15  fd 1e 93 14 17 6c 3f b9  |..8%.........l?.|
000000b0  77 59 fa b3 65 0e 1e 12  11 e8 0f f3 c0 68 8d a9  |wY..e........h..|
000000c0  d1 f8 8b 87 10 c5 56 35  16 2c c4 e9 fb 69 cf f5  |......V5.,...i..|
000000d0  35 43 3d e1 ad 77 93 a3  d9 6a 66 2b 1a 76 4a ec  |5C=..w...jf+.vJ.|
000000e0  77 97 84 17 68 ff 92 65  55 11 b5 f0 bc ca c2 20  |w...h..eU...... |
000000f0  a3 0e 1d 35 7d d6 1a 54  04 c0 7f 30 cc bf 4f 1a  |...5}..T...0..O.|
00000100  e6 39 39 38 b0 29 bf 79  bf 5c b0 1b b5 ed 2f 57  |.998.).y.\..../W|
00000110  48 e0 1b 5b 1f f0 5f 7e  57 a5 f8 71 94 6d 31 ff  |H..[.._~W..q.m1.|
00000120  4d 23 f2 d5 7c 5b a0 d4  52 4a 96 7f 67 52 ba 37  |M#..|[..RJ..gR.7|
00000130  92 7b 54 86 32 11 23 2d  a3 27 33 e7 5c 89 0d cf  |.{T.2.#-.'3.\...|
00000140  c7 24 e6 20 f6 0c 79 ef  2d 99 f2 12 f6 5d 5c 13  |.$. ..y.-....]\.|
00000150  e5 89 2c 7d 01 89 0e 17  66 db bd b5 7a 45 2e 9a  |..,}....f...zE..|
00000160  0b f8 21 a2 10 32 b0 22  3a 44 0e 7e b6 36 65 5f  |..!..2.":D.~.6e_|
00000170  36 1c 71 97 ce 91 5c 40  68 dc c0 73 13 6e b8 49  |6.q...\@h..s.n.I|
00000180  80 f7 fa cb de c6 bb c1  57 9a e5 49 c4 f8 3b 8e  |........W..I..;.|
00000190  e4 42 6e d9 f9 76 37 01  30 87 7a 99 82 e0 35 da  |.Bn..v7.0.z...5.|
000001a0  99 08 41 20 58 c8 1d db  4d b4 50 e7 10 2c 97 4c  |..A X...M.P..,.L|
000001b0  52 f1 3e 69 a5 86 56 d9  2f c2 71 db 94 59 00 01  |R.>i..V./.q..Y..|
000001c0  c1 ff 07 fe ff ff b7 fe  29 01 62 04 53 07 00 fe  |........).b.S...|
000001d0  ff ff 05 fe ff ff 19 03  7d 08 a1 04 53 07 00 00  |........}...S...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

---

### Post by wilee-nilee on 2012-05-16
You are missing this from the Windows setup /Boot/BCD

Do you have a windows recovery or install disc?

Also the boot flag is not on that sda8  partition.

Looks like you have the windows in a extended as well this a dd or a clone inserted in?

Windows needs a primary partition.

---

### Post by pranjalsaxena on 2012-05-16
No, I don't have a recovery/install disc..What should I do ?

---

### Post by wilee-nilee on 2012-05-16
> **pranjalsaxena said:**
> No, I don't have a recovery/install disc..What should I do ?

First windows wont run in a extended, can with some geek work I doubt anyone here knows, or will respond with in any due time.

Second you need a disc to fix it if it was in a primary partition.

I would reinstall it in a primary, and if possible just re-set up your whole HD set up and get windows in a sda1 partition. Windows really needs to be at the front of the HD to be easily dealt with, and in a primary partition.

---

### Post by pranjalsaxena on 2012-05-16
ok,then I gues only opton is to re-install both linux and win to get them working.
Thanks for the responses.

---

### Post by hal8000 on 2012-05-16
When you re-install windows, remember to leave some space for Ubuntu, so if asked if you want create a 100% NTFS drive, answer no and set its size to 60% or whatever you require for linux.

---

