---
title: "DUAL BOOT Problem after WIN Reinstall"
date: 2011-10-10
forum: General Help
---

### Post by MrBonsai on 2011-10-10
Until yesterday I had Windows 7 and Ubuntu installed, but I wanted to  get rid of Win 7. Some programs just didn't want to work, so I installed  Windows XP on this partition via WinToFlash.
 
After the install I haven't been able to boot any OS, but the Win XP with the USB Device.  With Ubuntu Live CD I finally got Ubuntu and Grub working and booting.
 
But now I can't boot Windows XP out of GRUB, at the moment i get the error "no such disk".  I have to say, I am still able to boot the Windows XP on my partition from the USB Device, but not from Grub.

I just can't figure out what I have to change, already tried some stuff....

At the moment I get the error  "no such disk" and after pressing space "failed to boot both default and fallback entries"


Here is my boot info script result.

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             211,680    87,756,479    87,544,800   7 NTFS / exFAT / HPFS
/dev/sda3          87,760,894   156,301,311    68,540,418   5 Extended
/dev/sda5          87,760,896   152,107,007    64,346,112  83 Linux
/dev/sda6         152,109,056   156,301,311     4,192,256  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1AA48B69A48B45EB                       ntfs       System Reserved
/dev/sda2        3648EBA748EB6459                       ntfs       
/dev/sda5        97f31094-7111-48a8-93b4-e013a0170919   ext4       
/dev/sda6        8ac259ee-fa7f-4f0a-b1e1-b71572defe6e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader] 
Timeout=30 
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
menuentry "Windows XP Pro" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    chainloader +1
}

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=97f31094-7111-48a8-93b4-e013a0170919 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=97f31094-7111-48a8-93b4-e013a0170919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}

menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 97f31094-7111-48a8-93b4-e013a0170919
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}




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
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=97f31094-7111-48a8-93b4-e013a0170919 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8ac259ee-fa7f-4f0a-b1e1-b71572defe6e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.070095062 = 75.237191680   boot/grub/core.img                             1
  48.127075195 = 51.676053504   boot/grub/grub.cfg                             1
  43.253906250 = 46.443528192   boot/initrd.img-2.6.38-8-generic               2
  70.101867676 = 75.271307264   boot/vmlinuz-2.6.38-8-generic                  1
  43.253906250 = 46.443528192   initrd.img                                     2
  70.101867676 = 75.271307264   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  92 bd f1 ad 19 f7 dc 5f  f5 83 eb c9 00 9d f6 df  |......._........|
00000010  8d eb 9d 19 d4 7e f3 e9  c1 41 93 2f bf 50 f5 9e  |.....~...A./.P..|
00000020  48 36 56 ae 34 57 d4 32  f4 d0 bc db 5d b3 b7 2a  |H6V.4W.2....]..*|
00000030  c3 66 e5 cd f7 b7 88 90  36 75 49 44 54 24 78 d7  |.f......6uIDT$x.|
00000040  a9 66 40 20 23 a2 9a e3  78 27 48 9d 02 71 33 e0  |.f@ #...x'H..q3.|
00000050  f3 d9 d9 40 1f 27 27 f0  77 65 6d 9b eb 10 b5 14  |...@.''.wem.....|
00000060  e7 e0 89 99 41 c8 82 17  f1 44 6a ce c2 83 ae 9a  |....A....Dj.....|
00000070  07 4f 17 19 80 61 73 87  8f 45 58 b0 ab 8c 8f e7  |.O...as..EX.....|
00000080  e6 b0 23 f9 63 89 fc 7b  bb a3 78 4a 20 8c da 1f  |..#.c..{..xJ ...|
00000090  d1 f2 fc fc 50 e1 3d 7d  c5 88 79 f6 3b 2b d6 37  |....P.=}..y.;+.7|
000000a0  75 12 20 d7 88 7a 27 6c  5e 69 77 f2 d5 49 f5 ba  |u. ..z'l^iw..I..|
000000b0  7c 32 fe 48 3b a4 7e 1a  4a ab 6e fb 61 b7 ef e8  ||2.H;.~.J.n.a...|
000000c0  a5 c4 ce b2 b9 cb c6 64  1e 3e b2 13 a5 8a bd bf  |.......d.>......|
000000d0  30 e2 4b ac 69 cc 7c 70  3a 16 d6 5d ea bc 6c fe  |0.K.i.|p:..]..l.|
000000e0  ef f2 a0 59 fd f9 0c c1  60 f8 05 1e 8d b9 d7 81  |...Y....`.......|
000000f0  9c 5c 38 d7 6b 0b 7f 04  6e fe 64 ec db 25 97 61  |.\8.k...n.d..%.a|
00000100  dd c4 22 cd 8a 58 f6 2f  85 d0 60 22 7c 9f 21 90  |.."..X./..`"|.!.|
00000110  0f 1a 33 4f 9d 3c 4c 1e  b5 6a 90 35 ae c2 60 25  |..3O.<L..j.5..`%|
00000120  98 ec ad 3a 03 7a 7f 52  78 43 6d da e6 21 08 66  |...:.z.RxCm..!.f|
00000130  c5 2e c7 da 68 54 0d d3  3a f3 83 9f c3 a6 b1 41  |....hT..:......A|
00000140  bf 61 11 54 6d 52 ee 43  42 e0 1f 66 dd 57 63 c5  |.a.TmR.CB..f.Wc.|
00000150  3c e6 91 88 ee ec 92 0e  7d e9 3d b1 a1 6e 97 97  |<.......}.=..n..|
00000160  01 c3 b5 4f 9a 4d 43 b4  e3 33 72 6b 63 ee ff b7  |...O.MC..3rkc...|
00000170  7f 5f db d5 e6 6a bf 02  f6 10 64 7f 13 a2 46 e0  |._...j....d...F.|
00000180  dd f7 78 6c c4 57 db 59  56 66 de 38 8d 9e 0e 32  |..xl.W.YVf.8...2|
00000190  09 0d 58 0e d7 d9 c3 41  04 4d 38 0b e5 2c cd fa  |..X....A.M8..,..|
000001a0  9e 5e 18 a8 d2 6b 89 c8  4e b4 4c 11 c7 74 e9 21  |.^...k..N.L..t.!|
000001b0  ee e9 a3 b1 df bc ad dd  3e 5f 6a d0 63 fc 00 ef  |........>_j.c...|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 d8 d5 03 00 ef  |................|
000001d0  ff ff 05 ef ff ff 02 d8  d5 03 00 00 40 00 00 00  |............@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by garvinrick4 on 2011-10-10
You have a Windows /boot partition in sda1 it has got windows 7 boot files in there also.

/BOOT/BCD and /bootmgr 

Get rid of them with a live CD mount your  sda1 SYSYEM. Take them and put them
on flash drive or get rid of them. Now see if you boot. Boot into Ubuntu and then:
```
sudo update-grub
```
see now if both do not boot.

---

### Post by MrBonsai on 2011-10-10
I deleted both files, and tried to reinstall grub via live cd.

But all I get now is the "Minimal Bash-like line editing"


Don't know what to do now....:confused:


///Edit

With   configfile (hd0,5)/boot/grub/grub.cfg  i was able to boot Linux, but I have to type this out every time to get the grub menu, also I tried to boot from windows, where I now get a hal.dl file missing

---

### Post by garvinrick4 on 2011-10-10
grub was fine, it was already installed in mbr.
Here is for Live CD: Open a terminal and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot
```Boot into Ubuntu and:
```
sudo update-grub
```

---

### Post by garvinrick4 on 2011-10-10
If you have anymore problems with windows take your XP cd and:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Get your windows booting then run the previous posts for grub2 to be installed
so both windows and Ubuntu boot.
Your machine still has the windows 7 /boot partition if worse comes to worse have
to get rid of that partition and run your windows cd to recover boot from xp CD and
then run the Ubuntu cd to get both booting.
##XP does not come with a boot partition but you have one still from windows 7.

#Just taking one step at a time until you are working.

---

### Post by MrBonsai on 2011-10-10
Thanks alot, Ubuntu and Grub menu just boot fine.

I don't have a CD anymore, just my USB Stick with the WinToFlash or .Iso on it.

So I assume getting rid of the System Reserved Partition was meant with the extra Win 7 partition?

---

### Post by garvinrick4 on 2011-10-10
> **MrBonsai said:**
> Thanks alot, Ubuntu and Grub menu just boot fine.

I don't have a CD anymore, just my USB Stick with the WinToFlash or .Iso on it.

So I assume getting rid of the System Reserved Partition was meant with the extra Win 7 partition?
The partition sda1 was for your Windows 7 and still had its boot files in there along with
the XP boot files. Since you removed Windows 7 has or had no use. Glad you are booting
Mr.Bonsai enjoy your Ubuntu and welcome to The Ubuntu Forums.

---

### Post by MrBonsai on 2011-10-10
Just had to update the boot.ini on the windows partition.

Now everything works!



Thanks

---

