---
title: "Vista - Ubuntu help needed!"
date: 2011-02-15
forum: General Help
---

### Post by the_recruit on 2011-02-15
Hey guys! 
This is my first post, I'm quite new to ubuntu, i'm really enjoying getting to know the system ... but I have a few programs still on my vista partition. My problem is that after updating ubuntu a couple of days ago I could no longer access the vista part from the grub bootloader. Instead it is taking me to the Vaio Recovery Centre, from which I still can't access vista. I have been searching for answers and I think that the problem is it is trying to boot /dev/sda1 but the NTFS partition is on /dev/sda2 . I think this is right... here are the fdisk -lu results:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d834104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    15087615     7542784   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    15087616   296509863   140711124    7  HPFS/NTFS
/dev/sda3       296511486   390721535    47105025    5  Extended
/dev/sda5       296511488   386772991    45130752   83  Linux
/dev/sda6       386775040   390721535     1973248   82  Linux swap / Solaris

Am I right in thinking that the vista partition is the /dev/sda2 and that the * means this should be the one that boots?

Any help would be great, sorry to be a pain!
Cheers :)

---

### Post by the_recruit on 2011-02-15
Oh and I have successfully been booting vista since i installed Ubuntu, its strange that it has changed just after the update.

---

### Post by the_recruit on 2011-02-15
If it helps here are the results of the Boot Script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    15,087,615    15,085,568  27 Hidden HPFS/NTFS
/dev/sda2    *     15,087,616   296,509,863   281,422,248   7 HPFS/NTFS
/dev/sda3         296,511,486   390,721,535    94,210,050   5 Extended
/dev/sda5         296,511,488   386,772,991    90,261,504  83 Linux
/dev/sda6         386,775,040   390,721,535     3,946,496  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        16AAC704AAC6DEFD                       ntfs       Recovery                      
/dev/sda2        3056CB7D56CB4278                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8d7734fc-a985-4ca9-b70c-45fed40ae9c9   ext4                                     
/dev/sda6        7147c580-2bc3-4882-8a68-dafa164f3a6a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
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
search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8d7734fc-a985-4ca9-b70c-45fed40ae9c9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 16aac704aac6defd
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3056cb7d56cb4278
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8d7734fc-a985-4ca9-b70c-45fed40ae9c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7147c580-2bc3-4882-8a68-dafa164f3a6a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 156.2GB: boot/grub/core.img
 156.7GB: boot/grub/grub.cfg
 156.5GB: boot/initrd.img-2.6.32-21-generic
 156.7GB: boot/initrd.img-2.6.32-22-generic
 157.0GB: boot/initrd.img-2.6.32-23-generic
 157.1GB: boot/initrd.img-2.6.32-24-generic
 157.1GB: boot/initrd.img-2.6.32-25-generic
 157.4GB: boot/initrd.img-2.6.32-28-generic
 156.4GB: boot/vmlinuz-2.6.32-21-generic
 156.6GB: boot/vmlinuz-2.6.32-22-generic
 156.9GB: boot/vmlinuz-2.6.32-23-generic
 157.1GB: boot/vmlinuz-2.6.32-24-generic
 157.0GB: boot/vmlinuz-2.6.32-25-generic
 157.2GB: boot/vmlinuz-2.6.32-28-generic
 157.4GB: initrd.img
 157.1GB: initrd.img.old
 157.2GB: vmlinuz
 157.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e2 da 66 6d 66 05 1d 0c  30 55 22 5a 1b eb ba b9  |..fmf...0U"Z....|
00000010  6b b4 61 a8 8f ff ff 5c  2c fd 33 bd 2b fb 0f ab  |k.a....\,.3.+...|
00000020  84 b7 55 ae a6 65 a2 4a  1a 23 75 1b f4 95 ff 4c  |..U..e.J.#u....L|
00000030  99 aa c3 47 6f 23 16 13  26 00 ec 82 75 42 6c 34  |...Go#..&...uBl4|
00000040  1c 20 6d a0 30 38 29 ed  a5 92 de 25 39 50 73 e5  |. m.08)....%9Ps.|
00000050  55 31 aa be dc d7 0a 5b  66 69 8f 69 d0 81 53 eb  |U1.....[fi.i..S.|
00000060  60 50 1f 87 50 a5 09 87  9e f6 20 98 84 5c 4a d3  |`P..P..... ..\J.|
00000070  31 cb f3 53 5a 88 b7 6c  fb 47 36 bc 3f 47 9c 38  |1..SZ..l.G6.?G.8|
00000080  25 17 80 53 6f 7a 2f c5  f5 2b 5f f0 1d 8f 5e 68  |%..Soz/..+_...^h|
00000090  ef 98 a6 88 a9 0e 86 0c  3e 05 47 d4 58 96 c6 58  |........>.G.X..X|
000000a0  d5 74 2c 6d 35 7f ff ff  ff c6 9f 2f 94 69 fb e6  |.t,m5....../.i..|
000000b0  ad 58 c5 69 4e 6b 98 ee  92 eb af 9f 8f e1 ab 36  |.X.iNk.........6|
000000c0  38 6b a5 28 6b 4a 17 f1  1c 22 73 56 f6 59 87 4d  |8k.(kJ..."sV.Y.M|
000000d0  6d eb 51 9a d0 9d 14 56  60 e8 8a 32 0b a7 42 c7  |m.Q....V`..2..B.|
000000e0  40 00 ec 27 54 42 bf 4f  4a 16 5c 04 01 00 83 f5  |@..'TB.OJ.\.....|
000000f0  b9 24 f9 81 e8 32 c5 d8  eb 50 ed 70 1c b1 6a 86  |.$...2...P.p..j.|
00000100  00 21 a8 2e d0 50 79 03  a0 48 5d b9 ea ef c1 9a  |.!...Py..H].....|
00000110  4d fe 34 f3 46 8e 41 ac  42 73 f3 90 c9 51 a4 c5  |M.4.F.A.Bs...Q..|
00000120  5d 54 57 36 af e2 18 b6  b1 1f ff f3 ff 33 42 87  |]TW6.........3B.|
00000130  51 80 d9 2b 5b 2f 1e ab  5c 48 f0 52 27 b9 17 2c  |Q..+[/..\H.R'..,|
00000140  72 9e 28 2a 75 34 8f 20  f1 55 4b 4b ff ff ff bf  |r.(*u4. .UKK....|
00000150  7b e7 18 7c a4 8b 14 e4  96 32 0d 57 58 74 a2 52  |{..|.....2.WXt.R|
00000160  ed ee be 7f ff e1 35 99  8a 56 af a8 ba e3 ad ef  |......5..V......|
00000170  2e ca b4 ba d7 c5 9b b4  46 e6 6a 73 ab 73 86 b2  |........F.js.s..|
00000180  0c a8 a6 76 9a 38 ca c4  00 ec 82 9f c3 eb f5 86  |...v.8..........|
00000190  20 ad e0 30 01 20 3f 65  92 5f 86 7f 5c 74 aa 44  | ..0. ?e._..\t.D|
000001a0  d6 d6 0e 87 e5 da da ab  62 d7 87 27 a3 b7 68 16  |........b..'..h.|
000001b0  94 0f 4a 8d cf 87 91 bc  9a 61 63 aa 26 4b 00 fe  |..J......ac.&K..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 61 05 00 fe  |...........Ha...|
000001d0  ff ff 05 fe ff ff 02 48  61 05 00 40 3c 00 00 00  |.......Ha..@<...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Hope this makes it easier!

---

### Post by coffeecat on 2011-02-15
Hi and welcome to the forum. I just happen to be posting from my Sony Vaio with the recovery partition on sda1 and Vista on sda2, except that I'm using the Alpha of Natty Narwhal (11.04) at the moment.

Don't worry - that's a known bug in the grub that came with Lucid/10.04, or perhaps in an update as you have seen.  Just choose the recovery on sda2 menu entry to get into Vista or Vista on sda1 to get into the recovery partition. That's what I had to do.

This bug has been resolved, but I can't remember if it has been sorted out in a subsequent Lucid update or whether it was fixed in the version of grub that came with Maverick. Either way, you won't do any harm to the system choosing the so-called recovery in sda2 to get into Vista.

Have fun! :)

---

