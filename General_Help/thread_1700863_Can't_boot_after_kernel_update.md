---
title: "Can't boot after kernel update"
date: 2011-03-05
forum: General Help
---

### Post by ximhot on 2011-03-05
I have used Ubuntu since 8.04 LTS on my IBM T30 and A31 for almost three years now but recently all of them have problems with kernel updates(? maybe I am wrong but it was very clear that they failed after a kernel update). I have tried all three solutions provided by [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) but none worked for me. My last A31 failed to boot yesterday after some updates (I noticed that there was a kernel update). It has 10.04 LTS on sda5. Dual boot (Windows XP on sda1 but rarely use it). Now it can't load kernel. What shows on the screen is:

GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

-----
On the other T30 I had the same problem. I installed Windows XP and clean installed Linux Mint 8 and so far it is working alright. But on this machine I have an unfinished project that I really want to save it. What can I do? Please help!

---

### Post by TeoBigusGeekus on 2011-03-05
Choose your previous kernel from grub and wait for the next kernel update to see how it goes.
In any case, you can boot with a live cd and save your project.

---

### Post by ximhot on 2011-03-05
I can't even choose the previous kernel. Grub is not loading. All I can see is this screen:

GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

---

### Post by TeoBigusGeekus on 2011-03-05
> **ximhot said:**
> I can't even choose the previous kernel. Grub is not loading. All I can see is this screen:

GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

Yes of course, sorry for the silly answer.
The only thing I can think of is reinstalling grub 2:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")
It's things like this that make me still use grub legacy...

---

### Post by ximhot on 2011-03-06
I used Windows XP repair console to fix MBR and Boot, now I can boot to Windows XP. Can I reinstall GRUB?

---

### Post by TeoBigusGeekus on 2011-03-06
Of course. See the link I gave you.

---

### Post by ximhot on 2011-03-06
Still can't load kernel. I guess I have to have a clean install and avoid kernel 2.6.32-29. I am pretty sure that it caused the crash.

---

### Post by ximhot on 2011-03-06
My guess is, your method will work on a machine that has a working Ubuntu system but corrupt GRUB2, but my machine failed because of the version of kernel didn't work. Therefore, fixing GRUB won't do any good?

---

### Post by TeoBigusGeekus on 2011-03-06
Perhaps the newest kernel corrupted grub, you can't know.
Reinstalling grub is less time consuming than reinstalling and configuring your system all over again anyway.
You have nothing to lose.

---

### Post by ximhot on 2011-03-06
I tried your method but it only wiped out the Windows XP MBR and Boot, the machine went back to the no booting state like before. I guess I will use Windows XP repair console to repair MBR and Boot and then have a clean installation of Linux Mint 8 and try to avoid kernel 2.6.32-29.

](*,)

---

### Post by ximhot on 2011-03-06
Any help? Here is the boot info.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

sdb4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,744,273    78,744,211   7 HPFS/NTFS
/dev/sda2          78,745,598   488,396,799   409,651,202   5 Extended
/dev/sda5          78,745,600   483,903,487   405,157,888  83 Linux
/dev/sda6         483,905,536   488,396,799     4,491,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders, total 196608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb4    *             32       196,607       196,576   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3000633600630268                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8549f833-4cb6-4057-8884-88569463ba03   ext4                                     
/dev/sda6        fa296ad6-e7be-4024-b2ae-bf07c145d681   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb4        0FF6-090A                              vfat       ZIP-100                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb4        /media/ZIP-100           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
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
search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
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
menuentry 'Ubuntu&#65292;Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-29-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    echo    '&#36733;&#20837; Linux ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro single 
    echo    '&#36733;&#20837;&#24341;&#23548;&#34394;&#25311;&#30913;&#30424; ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-28-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    echo    '&#36733;&#20837; Linux ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro single 
    echo    '&#36733;&#20837;&#24341;&#23548;&#34394;&#25311;&#30913;&#30424; ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu&#65292;Linux 2.6.32-24-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    echo    '&#36733;&#20837; Linux ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8549f833-4cb6-4057-8884-88569463ba03 ro single 
    echo    '&#36733;&#20837;&#24341;&#23548;&#34394;&#25311;&#30913;&#30424; ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8549f833-4cb6-4057-8884-88569463ba03
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3000633600630268
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
UUID=8549f833-4cb6-4057-8884-88569463ba03 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fa296ad6-e7be-4024-b2ae-bf07c145d681 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 126.3GB: boot/grub/core.img
 190.8GB: boot/grub/grub.cfg
 126.4GB: boot/initrd.img-2.6.32-24-generic
 126.5GB: boot/initrd.img-2.6.32-28-generic
 126.5GB: boot/initrd.img-2.6.32-29-generic
 126.4GB: boot/vmlinuz-2.6.32-24-generic
 126.4GB: boot/vmlinuz-2.6.32-28-generic
 126.5GB: boot/vmlinuz-2.6.32-29-generic
 126.5GB: initrd.img
 126.5GB: initrd.img.old
 126.5GB: vmlinuz
 126.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 2e 49 50 41 52 54 20  63 6f 64 65 20 30 30 39  |..IPART code 009|
00000010  20 2d 20 49 6f 6d 65 67  61 20 43 6f 72 70 6f 72  | - Iomega Corpor|
00000020  61 74 69 6f 6e 20 2d 20  31 31 2f 32 33 2f 39 30  |ation - 11/23/90|
00000030  fa fc 8c c8 8e d0 bc 00  7c 8e d8 8e c0 b9 00 02  |........|.......|
00000040  bf 00 7e be 00 7c f3 a4  e9 00 02 fb bd 00 7e 8b  |..~..|........~.|
00000050  fd be be 01 b9 04 00 80  3a 80 74 0b 83 c6 10 e2  |........:.t.....|
00000060  f6 8b b5 b2 01 eb 51 56  83 c6 10 49 e3 0b 80 3a  |......QV...I...:|
00000070  80 75 f5 8b b5 b0 01 eb  3f 5e 56 8a 12 8a 72 01  |.u......?^V...r.|
00000080  8a 4a 02 8a 6a 03 bb 00  7c be 05 00 56 b8 01 02  |.J..j...|...V...|
00000090  cd 13 73 0e 33 c0 cd 13  5e 4e 75 f0 8b b5 b4 01  |..s.3...^Nu.....|
000000a0  eb 16 5e be fe 7d 81 3c  55 aa 74 06 8b b5 b6 01  |..^..}.<U.t.....|
000000b0  eb 06 5e 03 f5 e9 48 fd  e8 1b 00 8b b5 b8 01 e8  |..^...H.........|
000000c0  14 00 b4 00 cd 16 33 c0  8e c0 26 c7 06 72 04 34  |......3...&..r.4|
000000d0  12 ea f0 ff 00 f0 03 f5  ac 3c 00 74 0b 56 b4 0e  |.........<.t.V..|
000000e0  bb 07 00 cd 10 5e eb f0  c3 49 6e 76 61 6c 69 64  |.....^...Invalid|
000000f0  20 70 61 72 74 69 74 69  6f 6e 20 74 61 62 6c 65  | partition table|
00000100  00 44 69 73 6b 20 69 73  20 6e 6f 74 20 62 6f 6f  |.Disk is not boo|
00000110  74 61 62 6c 65 00 45 72  72 6f 72 20 6c 6f 61 64  |table.Error load|
00000120  69 6e 67 20 6f 70 65 72  61 74 69 6e 67 20 73 79  |ing operating sy|
00000130  73 74 65 6d 00 4d 69 73  73 69 6e 67 20 6f 70 65  |stem.Missing ope|
00000140  72 61 74 69 6e 67 20 73  79 73 74 65 6d 00 0d 0a  |rating system...|
00000150  52 65 70 6c 61 63 65 20  61 6e 64 20 73 74 72 69  |Replace and stri|
00000160  6b 65 20 61 6e 79 20 6b  65 79 20 77 68 65 6e 20  |ke any key when |
00000170  72 65 61 64 79 0d 0a 00  00 00 00 00 00 00 00 00  |ready...........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 e9 00  |................|
000001b0  e9 00 01 01 16 01 35 01  4e 01 94 4b db 4e 00 00  |......5.N..K.N..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 01  |................|
000001f0  01 00 06 3f 20 5f 20 00  00 00 e0 ff 02 00 55 aa  |...? _ .......U.|
00000200

Unknown BootLoader  on sda2

00000000  af c4 d5 73 d2 87 a7 c8  99 f3 86 5b 1f 5f e6 0f  |...s.......[._..|
00000010  af e5 0c f9 53 3f a6 bf  e4 8f 09 a2 81 5e 91 7f  |....S?.......^..|
00000020  fc a1 b8 a9 ff fd b3 2c  b7 ec 3a d9 dd ad e1 82  |.......,..:.....|
00000030  27 75 ae 11 ca 0b 9a b5  71 f3 99 93 15 5e 73 7d  |'u......q....^s}|
00000040  5a e4 60 9a db 2e 7e 76  57 5c 0b 71 98 43 fd 16  |Z.`...~vW\.q.C..|
00000050  0d e4 4c f7 4d 7f f4 ff  f9 a3 3e 7c a9 fe b0 91  |..L.M.....>|....|
00000060  df a2 e8 88 4f a9 6c 94  22 2e 67 58 b8 6b 4e 8b  |....O.l.".gX.kN.|
00000070  84 9b 59 7b e0 1a c7 e7  72 59 63 ad 62 67 75 43  |..Y{....rYc.bguC|
00000080  c9 9d dd 6d 6e 7c 5b b1  80 c0 a1 9e f9 43 8f ff  |...mn|[......C..|
00000090  ff ff fe 58 dd a6 8f 1e  f3 e9 bf 25 82 fb f3 7b  |...X.......%...{|
000000a0  b6 4d 31 38 2f 26 cf b3  02 30 27 ed c8 dc bc 44  |.M18/&...0'....D|
000000b0  cb 8c 1d 4d 75 e7 0e c6  e3 d8 b6 c2 13 a6 bd 25  |...Mu..........%|
000000c0  ce fa e8 89 f2 c7 d8 2e  fc 24 21 6f ff fe 50 cf  |.........$!o..P.|
000000d0  ff ff 38 6b ee a6 13 7f  57 71 c3 bc 5a c7 54 9d  |..8k....Wq..Z.T.|
000000e0  77 c1 20 2b c9 9d 3f 66  32 7f ca 9c 32 7f e8 a6  |w. +..?f2...2...|
000000f0  8d 7f ff ca 1c 27 d2 bf  fc a1 9e ff ff e4 4e bf  |.....'........N.|
00000100  ff fa ff ff ff 24 67 bf  ff a5 7d 3f f5 7c 50 14  |.....$g...}?.|P.|
00000110  f4 27 4a ff fd 32 cc 19  ff 91 3c 6a 8c 7f ff ff  |.'J..2....<j....|
00000120  ff fa c3 cb ff fa 2c 37  ff ff ff ac ff f2 87 90  |......,7........|
00000130  c7 ff ff fc 99 f2 3d b4  df 18 92 36 97 3b df 00  |......=....6.;..|
00000140  30 31 77 62 50 01 00 00  ff fb 84 64 0a 01 e3 f0  |01wbP......d....|
00000150  5e 59 e9 ec 43 78 1e 60  09 e3 00 02 01 0f 01 7b  |^Y..Cx.`.......{|
00000160  7f a4 a0 fe f8 79 80 67  8c 00 88 04 92 1a 58 e8  |.....y.g......X.|
00000170  2e 21 db 48 00 40 c5 54  4b d8 52 fc 1f 17 35 67  |.!.H.@.TK.R...5g|
00000180  e2 5a f2 db b0 f3 d9 59  e9 ae 4f b8 55 14 83 12  |.Z.....Y..O.U...|
00000190  77 6b 51 3d 33 33 78 de  ac 48 3a 3f 9e ab d1 ca  |wkQ=33x..H:?....|
000001a0  8b 85 fa c5 84 20 6c 50  a9 eb f5 fc ab 0f d7 8b  |..... lP........|
000001b0  93 7f cf 19 c8 c2 e9 1c  72 8d 89 52 cc 28 00 fe  |........r..R.(..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 26 18 00 fe  |...........8&...|
000001d0  ff ff 05 fe ff ff 02 38  26 18 00 90 44 00 00 00  |.......8&...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by anoopm101 on 2011-03-06
can u please run some live cd and check the condition of your hard drive, if bad sectors accumulated, better way is to backup the data and change the harddrive, this happened to me once, try it as soon as possible

---

### Post by ximhot on 2011-03-06
Yes, I did check the physical condition and the file system on the hard drive. It is very healthy and I never had any force shut down since this hard drive was installed. No bad sector is found.

---

