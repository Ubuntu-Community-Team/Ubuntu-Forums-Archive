---
title: "Frequently get grub rescue prompt, have to reinstall grub."
date: 2011-03-12
forum: General Help
---

### Post by Rikeshar on 2011-03-12
Hello, I hope you don't mind me jumping in. I'm having a similar issue.  It first started a few nights ago, and after booting from the live cd  and reading around, I saw it mentioned somewhere that it might help to  update GRUB. I did this using sudo update-grub. This took care of the  issue, with an unexpected, but not altogether unwanted result: instead  of having to choose a temporary boot device to boot on to the external  drive Ubuntu is on, I got a grub menu which showed the the OSs for both  HDDS.

I thought all was fine, but a few days later, same thing. Updated grub again, and all was okay. Tonight, it happened again. When I try to update grub now it says: 

 ```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

I was hoping someone could help me resolve this issue once for and all. Here's the result of the boot info script. 
```
                      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
95 heads, 54 sectors/track, 95204 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,930,175    10,928,128  27 Hidden HPFS/NTFS
/dev/sda2    *     10,930,176   488,392,695   477,462,520   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C024E03224E02D5A                       ntfs       ServiceV002                   
/dev/sda2        9216E2AC16E29111                       ntfs       SW_Preload                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        29c7bf08-f489-41a5-ba12-d69badbc5924   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9c4560ff-c3e9-431b-8ae2-11abbedbce5f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c024e03224e02d5a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9216e2ac16e29111
    chainloader +1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
# Commented out by Dropbox
# UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9c4560ff-c3e9-431b-8ae2-11abbedbce5f none            swap    sw              0       0
UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 / ext4 errors=remount-ro,user_xattr 0 1

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  64.6GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
  64.6GB: boot/initrd.img-2.6.35-27-generic
  34.6GB: boot/vmlinuz-2.6.35-22-generic
  34.6GB: boot/vmlinuz-2.6.35-27-generic
  64.6GB: initrd.img
   1.5GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  7d 6c 95 09 a1 5d 4c 69  79 aa 68 2b 29 38 48 7d  |}l...]Liy.h+)8H}|
00000010  ee 11 16 46 e2 1c 46 76  41 af 99 95 58 9e e2 36  |...F..FvA...X..6|
00000020  5d 43 4b ff 68 0c 29 12  4d 17 4d 9b ff de 1a 34  |]CK.h.).M.M....4|
00000030  b0 90 3f 2a bf bc c3 cb  53 c2 b4 a1 34 25 2b b1  |..?*....S...4%+.|
00000040  eb 23 a2 b0 9a 9f df 51  29 ec 3d 99 9d 88 f7 ad  |.#.....Q).=.....|
00000050  9b c3 ab e6 cd 46 e4 b4  8f 9f 24 4c da af df da  |.....F....$L....|
00000060  61 da e5 df 5b 1a 51 e1  3f 0f b4 f7 0d a8 e8 5c  |a...[.Q.?......\|
00000070  54 6f ea 95 60 51 7c 51  b5 85 45 86 e3 0d fa a4  |To..`Q|Q..E.....|
00000080  c3 36 1e e2 85 06 7f 18  3c b4 e5 c4 36 30 21 4b  |.6......<...60!K|
00000090  58 37 9f a0 0a 90 b7 e5  d0 da ea 8e 12 01 df c5  |X7..............|
000000a0  53 8a 6a 9b e8 be 47 10  eb 14 8c 3f 2d f5 f3 09  |S.j...G....?-...|
000000b0  7c 84 77 ac 94 03 dd bf  c8 07 a5 a2 fb 06 2c c0  ||.w...........,.|
000000c0  51 99 ca a7 24 4d bc ed  fa 1d c2 bc b5 fd 41 29  |Q...$M........A)|
000000d0  a2 eb ad 63 ef 22 5e a2  7e 55 80 a1 a0 b3 d7 34  |...c."^.~U.....4|
000000e0  0a 71 01 fd bd b9 06 d9  86 6d ab 47 34 fb 04 af  |.q.......m.G4...|
000000f0  50 b9 eb 82 64 ae 19 2c  e3 78 3d 49 d6 9c 04 cf  |P...d..,.x=I....|
00000100  42 dc ca b9 33 8b 87 0e  c2 26 d1 e2 61 8d e0 5e  |B...3....&..a..^|
00000110  0b 13 7d 17 53 28 e2 3e  a6 28 a5 2f 26 55 45 7a  |..}.S(.>.(./&UEz|
00000120  4f 10 94 6b 0e b8 6a c8  32 70 b1 87 37 02 8a 79  |O..k..j.2p..7..y|
00000130  b4 25 6e 0f b5 db 66 de  1c 83 4e d0 9e 15 af 3f  |.%n...f...N....?|
00000140  15 0c 28 e2 f6 0e 12 e1  8d 4b e1 3f bd 41 23 2c  |..(......K.?.A#,|
00000150  40 a3 c3 5a 71 34 d2 f6  33 8b 8d 62 17 3b 96 a5  |@..Zq4..3..b.;..|
00000160  02 f6 37 57 f4 84 b0 7b  12 94 33 67 35 25 8a 6d  |..7W...{..3g5%.m|
00000170  de f9 e1 16 6a 70 a6 98  f1 72 b1 16 6e 14 69 6a  |....jp...r..n.ij|
00000180  b6 f8 da 99 98 9d bc 3d  41 f7 91 c8 f6 25 71 a4  |.......=A....%q.|
00000190  79 e7 c9 1c 2d a1 1b 22  4f d5 8d ea c5 e6 7a 4e  |y...-.."O.....zN|
000001a0  87 72 3d b0 ee af 24 b3  7e 78 28 70 b8 67 2b 2d  |.r=...$.~x(p.g+-|
000001b0  c8 3c 44 79 fb c3 00 17  b5 09 87 e3 47 69 00 fe  |.<Dy........Gi..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```

It looks like the problem is that there's no boot loader on the drive Ubuntu's installed on. Any ideas?
                                                                                                            

**UPDATE** So I removed grub-pc and reinstalled legacy grub. I then did  sudo apt-get install grub-pc and it's at a screen asking me which  devices I want to install grub to. I choose both sda and sdb and it  comes up saying it failed to install to both. On the terminal I get 

 ```
    Setting up grub-pc (1.98+20100804-5ubuntu3) ...
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?). 
```

**UPDATE 2** Well, it looks like it's NOT grub legacy... but I rebooted the computer after this and was able to get the grub menu again.  I just ran the boot info script again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
95 heads, 54 sectors/track, 95204 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,930,175    10,928,128  27 Hidden HPFS/NTFS
/dev/sda2    *     10,930,176   488,392,695   477,462,520   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C024E03224E02D5A                       ntfs       ServiceV002                   
/dev/sda2        9216E2AC16E29111                       ntfs       SW_Preload                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        29c7bf08-f489-41a5-ba12-d69badbc5924   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9c4560ff-c3e9-431b-8ae2-11abbedbce5f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c024e03224e02d5a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9216e2ac16e29111
    chainloader +1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
# Commented out by Dropbox
# UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9c4560ff-c3e9-431b-8ae2-11abbedbce5f none            swap    sw              0       0
UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 / ext4 errors=remount-ro,user_xattr 0 1

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  19.4GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
  64.6GB: boot/initrd.img-2.6.35-27-generic
  34.6GB: boot/vmlinuz-2.6.35-22-generic
  34.6GB: boot/vmlinuz-2.6.35-27-generic
  64.6GB: initrd.img
   1.5GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  7d 6c 95 09 a1 5d 4c 69  79 aa 68 2b 29 38 48 7d  |}l...]Liy.h+)8H}|
00000010  ee 11 16 46 e2 1c 46 76  41 af 99 95 58 9e e2 36  |...F..FvA...X..6|
00000020  5d 43 4b ff 68 0c 29 12  4d 17 4d 9b ff de 1a 34  |]CK.h.).M.M....4|
00000030  b0 90 3f 2a bf bc c3 cb  53 c2 b4 a1 34 25 2b b1  |..?*....S...4%+.|
00000040  eb 23 a2 b0 9a 9f df 51  29 ec 3d 99 9d 88 f7 ad  |.#.....Q).=.....|
00000050  9b c3 ab e6 cd 46 e4 b4  8f 9f 24 4c da af df da  |.....F....$L....|
00000060  61 da e5 df 5b 1a 51 e1  3f 0f b4 f7 0d a8 e8 5c  |a...[.Q.?......\|
00000070  54 6f ea 95 60 51 7c 51  b5 85 45 86 e3 0d fa a4  |To..`Q|Q..E.....|
00000080  c3 36 1e e2 85 06 7f 18  3c b4 e5 c4 36 30 21 4b  |.6......<...60!K|
00000090  58 37 9f a0 0a 90 b7 e5  d0 da ea 8e 12 01 df c5  |X7..............|
000000a0  53 8a 6a 9b e8 be 47 10  eb 14 8c 3f 2d f5 f3 09  |S.j...G....?-...|
000000b0  7c 84 77 ac 94 03 dd bf  c8 07 a5 a2 fb 06 2c c0  ||.w...........,.|
000000c0  51 99 ca a7 24 4d bc ed  fa 1d c2 bc b5 fd 41 29  |Q...$M........A)|
000000d0  a2 eb ad 63 ef 22 5e a2  7e 55 80 a1 a0 b3 d7 34  |...c."^.~U.....4|
000000e0  0a 71 01 fd bd b9 06 d9  86 6d ab 47 34 fb 04 af  |.q.......m.G4...|
000000f0  50 b9 eb 82 64 ae 19 2c  e3 78 3d 49 d6 9c 04 cf  |P...d..,.x=I....|
00000100  42 dc ca b9 33 8b 87 0e  c2 26 d1 e2 61 8d e0 5e  |B...3....&..a..^|
00000110  0b 13 7d 17 53 28 e2 3e  a6 28 a5 2f 26 55 45 7a  |..}.S(.>.(./&UEz|
00000120  4f 10 94 6b 0e b8 6a c8  32 70 b1 87 37 02 8a 79  |O..k..j.2p..7..y|
00000130  b4 25 6e 0f b5 db 66 de  1c 83 4e d0 9e 15 af 3f  |.%n...f...N....?|
00000140  15 0c 28 e2 f6 0e 12 e1  8d 4b e1 3f bd 41 23 2c  |..(......K.?.A#,|
00000150  40 a3 c3 5a 71 34 d2 f6  33 8b 8d 62 17 3b 96 a5  |@..Zq4..3..b.;..|
00000160  02 f6 37 57 f4 84 b0 7b  12 94 33 67 35 25 8a 6d  |..7W...{..3g5%.m|
00000170  de f9 e1 16 6a 70 a6 98  f1 72 b1 16 6e 14 69 6a  |....jp...r..n.ij|
00000180  b6 f8 da 99 98 9d bc 3d  41 f7 91 c8 f6 25 71 a4  |.......=A....%q.|
00000190  79 e7 c9 1c 2d a1 1b 22  4f d5 8d ea c5 e6 7a 4e  |y...-.."O.....zN|
000001a0  87 72 3d b0 ee af 24 b3  7e 78 28 70 b8 67 2b 2d  |.r=...$.~x(p.g+-|
000001b0  c8 3c 44 79 fb c3 00 17  b5 09 87 e3 47 69 00 fe  |.<Dy........Gi..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```I'm hopeing for some help in keeping from having to do this again! If any more information is needed, please let me know.

---

### Post by wilee-nilee on 2011-03-12
Yeah you don't need grub-legacy and you saw the problem that grub is not in sdb, so boot the live cd again and run these commands. Make sure the sdb hd is first to be read in the bios.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```
reboot to the installed Ubuntu and run in its terminal
```
sudo update-grub
```

Here is the commands link as well, for reference.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Rikeshar on 2011-03-12
Thanks, I'll give it a try. How can I make sure sdb is first in the bios? You mean in the boot order? sdb is an external hdd, so I'd swap it around so that it is first, ahead of the actual internal hdd?

---

### Post by wilee-nilee on 2011-03-12
> **Rikeshar said:**
> Thanks, I'll give it a try. How can I make sure sdb is first in the bios? You mean in the boot order? sdb is an external hdd, so I'd swap it around so that it is first, ahead of the actual internal hdd?

Yeah if you put it first it will boot Ubuntu or Windows. The only problem is that for windows to boot without the hd plugged in we can slip the MS bootloader back into the sda=mbr.

Looks like windows 7 here is a recovery disc if needed for that.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

So you would boot the recovery disc and follow these instructions and look at the W7 forums visual for help if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Fix grub first to make sure it works then run this to put the windows bootloader back in its hd's mbr

---

### Post by Rikeshar on 2011-03-12
Okay, so I've gone to the live cd and installed grub. Got the message:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdb
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
```Should I be worried about this? I'm about to reboot into the installed Ubuntu to finish it there.

Also, do I -need- fix the Windows MBR? I kind of like having grub show Ubuntu and Windows. Or rather, i guess I should ask, if I fix the MBR, will grub continue to control things as long as the external hdd is plugged in?

---

### Post by wilee-nilee on 2011-03-12
As far as I know grub is supposed to have the flexnet which is proprietary software stuff written around or a built in fix. We wont know until you boot, I guess. See post 2 in this thread this is a person that knows.
[http://ubuntuforums.org/showthread.php?p=10503782#post10503782](http://ubuntuforums.org/showthread.php?p=10503782#post10503782)

So putting the MS bootloader back in the sda mbr will not effect your grub boot. It only makes sure that windows can boot without the external plugged in.

---

### Post by Rikeshar on 2011-03-12
Alright! Thank you so much for your help. I just ran the boot info script again and it's showing grub2 on both drives now. I think I'll hold off on fixing the mbr for now, it's getting late. Hopefully it coming up to the grub rescue prompt has been fixed. Thank you again, I really do appreciate your time!

---

### Post by garvinrick4 on 2011-03-12
*If OP will notice after you get your grub in place with Wilee-Nilee's help then read this.

```
##In your original post you were trying to update-grub using Live CD without
mounting any /.
Must mount / and /dev and /dev/pts and /sys and /proc then chroot and update-grub
such as:
[CODE]sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev
``````
sudo mount -o bind /dev/pts /mnt/dev/pts
``````
sudo mount -o bind /sys /mnt/sys
``````
sudo mount -o bind /proc /mnt/proc
``````
sudo chroot /mnt
``````
update-grub
``````
exit
```                         ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```# I used sda5 use the partition you want to chroot into.
# Can make the first 6 pieces of code one line to make easier just wanted to show you
   want needs to be mounted to update-grub while in chroot in Live CD. Can fix and or 
   repair and update and upgrade from after the chroot command also, just puts you in
   root of that particular install, mine being sda5 for this.
# Used one line of code to unmount the partition sda5 that was mounted in /mnt[/CODE]
Before chroot code must get internet connection to /mnt if want to use repositories:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
This copies the internet connection you are using to the /mnt

---

