---
title: "Installed Win7 after Ubuntu 10.4, so how do I fix grub_"
date: 2010-07-25
forum: General Help
---

### Post by colobix on 2010-07-25
So how do I fix grub now_

Thanks in advance

---

### Post by Bachstelze on 2010-07-25
Boot your Live CD

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Of course change /dev/sd* if needed.

---

### Post by colobix on 2010-07-25
but I am using the live cd now. is it possible to do from the live cd_

---

### Post by prodigy_ on 2010-07-25
Use Boot Info Script from my sig and post the results here. Then we'll be able to give you more precise guidelines.

---

### Post by colobix on 2010-07-25
What?
I tried the command above but it didnt work.
Can I do this from windows 7? maybe that will work better.

---

### Post by colobix on 2010-07-25
Not to complain but ubuntu should really (after more then 10 versions) make a program or something on the live CD so that people can fix this problem. Because windows is really something that needs to be reinstalled from time to time.
So this should really have an easy solution.

So, any other ideas?

---

### Post by wilee-nilee on 2010-07-25
The commands given are subject to the correct partitions and user understanding here is a link to this. You install grub back to the mbr of the HD probably sda and mount the Ubuntu partition; from a live Ubuntu cd, at least karmic or later.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If your still stuck post the bootscript in my signature in code tag as described for a closer look at you setup.

---

### Post by colobix on 2010-07-25
Hmm. Thanks but maybe I should call a pc expert instead.
This guide was very confusing and I didn\t understand all that pc language stuff. But on the other hand, a pc guy is very expensive and it would be way better just to fix this right here right now for free.
Could someone please explain this without all those scary techn words_ 
Thanks.
Also, if I follow that guide, can I simply just copy/paste the sudo commands into the terminal and just ignore all the other text that doesn\t tell me anything_

---

### Post by colobix on 2010-07-25
here\s the script output>


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    30,732,287    30,525,440   7 HPFS/NTFS
/dev/sda3          30,732,345   697,770,560   667,038,216   7 HPFS/NTFS
/dev/sda4         697,772,030   976,773,119   279,001,090   5 Extended
/dev/sda5         697,772,032   965,357,567   267,585,536  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D43004B430049F9A                       ntfs       Reservert av systemet         
/dev/sda2        FE5C091E5C08D377                       ntfs                                     
/dev/sda3        36680C9B680C5C4D                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0747c4c0-843a-4ddd-95e6-51f5ff447e88   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
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
search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
set locale_dir=($root)/boot/grub/locale
set lang=nb
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0747c4c0-843a-4ddd-95e6-51f5ff447e88 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0747c4c0-843a-4ddd-95e6-51f5ff447e88 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0747c4c0-843a-4ddd-95e6-51f5ff447e88
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4cb4ff3bb4ff25dc
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0747c4c0-843a-4ddd-95e6-51f5ff447e88 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=87dca524-47f1-4703-ab13-7708f90974e5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 474.1GB: boot/grub/core.img
 460.5GB: boot/grub/grub.cfg
 473.8GB: boot/initrd.img-2.6.32-21-generic
 474.1GB: boot/vmlinuz-2.6.32-21-generic
 473.8GB: initrd.img
 474.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  3e 24 13 04 25 79 3f 72  ec 61 ef 70 08 c0 e3 6c  |>$..%y?r.a.p...l|
00000010  e2 d6 89 fd 3d 45 ae f5  bb 11 49 c1 58 f8 41 4e  |....=E....I.X.AN|
00000020  06 d8 5a ed 36 80 9b d6  e9 1b 8d a3 e9 a3 9e 04  |..Z.6...........|
00000030  fb 6a 80 4c c4 53 32 e7  20 66 ed 2f 29 ef 27 02  |.j.L.S2. f./).'.|
00000040  3d 29 a8 2e 3d a5 e9 c7  d4 53 b5 77 cf ac 07 1e  |=)..=....S.w....|
00000050  e4 e6 90 01 1e 13 6c 7c  fa f6 0a 25 4b b9 2c 8e  |......l|...%K.,.|
00000060  5f 79 e5 f7 39 26 f7 bf  61 c6 2f bd 5d 5f 6f 7a  |_y..9&..a./.]_oz|
00000070  d4 62 e9 be 87 54 e3 ab  ab 89 9f 73 6e ad ef 45  |.b...T.....sn..E|
00000080  bc 60 40 14 f0 c8 48 7a  aa 46 24 51 00 5f c3 ce  |.`@...Hz.F$Q._..|
00000090  02 30 df f2 2a fb fe e8  af ff 42 71 f0 5f db de  |.0..*.....Bq._..|
000000a0  c8 68 84 05 3b 00 c7 83  4a f0 40 3e 0c 5c 7d e0  |.h..;...J.@>.\}.|
000000b0  ce 07 31 41 81 02 bc 1e  02 03 73 e0 f0 10 1b ff  |..1A......s.....|
000000c0  3d ff c5 3b 25 6e 4b 95  0f 70 8c 1e 02 04 5b f2  |=..;%nK..p....[.|
000000d0  50 84 7c 09 c3 c7 fa 52  2a 70 a2 41 9b 94 02 fc  |P.|....R*p.A....|
000000e0  09 77 63 87 c2 21 68 1b  d9 b4 64 43 38 d8 9f 63  |.wc..!h...dC8..c|
000000f0  71 12 33 f3 ef a0 ea f0  ef 42 99 37 a7 86 68 28  |q.3......B.7..h(|
00000100  18 ba 53 e0 80 e0 60 84  e0 7c 08 07 c7 c4 a1 4d  |..S...`..|.....M|
00000110  42 13 95 4e b4 29 00 c8  f5 51 5f 14 34 9e 14 93  |B..N.)...Q_.4...|
00000120  9b 50 9c c9 c4 ae 63 7c  bf d7 36 2d e3 85 7d 35  |.P....c|..6-..}5|
00000130  8c ae 71 ef 04 97 b6 8d  d7 5f 73 bd 5d bb 74 f6  |..q......_s.].t.|
00000140  b7 a1 61 19 3a 4c 8a 53  fa 4a 14 f2 ea db 46 c2  |..a.:L.S.J....F.|
00000150  15 36 0c e0 81 56 3d f3  60 14 0e 76 10 9e 08 0f  |.6...V=.`..v....|
00000160  08 0f 06 8f 0c 82 9e 0c  5c 60 18 48 78 30 fa eb  |........\`.Hx0..|
00000170  81 80 39 ef 2e 78 14 d5  bb c1 82 11 7f 94 33 e5  |..9..x........3.|
00000180  7e dc 53 e2 ab 2e 5f 55  e3 c1 e0 20 39 3e 0c 08  |~.S..._U... 9>..|
00000190  15 57 95 4a aa 4f 01 ff  01 d5 60 7a 7a 4a bd 03  |.W.J.O....`zzJ..|
000001a0  83 a6 a7 8d 03 c0 40 8f  7e 79 5b c2 11 f0 a7 60  |......@.~y[....`|
000001b0  f0 10 1e 9f 07 80 80 e6  6d 9a 4c 0f 01 02 00 fe  |........m.L.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 f3 0f 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by wilee-nilee on 2010-07-25
This grub install is straight from the link to the live cd install I gave you, so from the live cd in the terminal.
```
sudo mount /dev/sda5 /mnt
```
Then run in the terminal.
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Boot Ubuntu and run ```
sudo update-grub
```

If you look this is the same command set given you first but with a different partition. In the grub 2 link there is a command to find the partitions.
sudo fdisk -l
This will tell you which partition is which, the boot script also shows the partitions.

---

### Post by colobix on 2010-07-25
oh thanks alot man
It totally worked!
Awesome :) Thanks again.

---

### Post by wilee-nilee on 2010-07-25
> **colobix said:**
> oh thanks alot man
It totally worked!
Awesome :) Thanks again.

I know that the grub2 link and others, and threads can be very confusing, but all you really have to know is how to identify your partitions with the,[COLOR="Red"]sudo fdisk l[/COLOR] command then if some how grub gets put somewhere other then the mbr=sda then how to run the bootscript to see this, and post it.

---

