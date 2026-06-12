---
title: "GRUB Won't Start"
date: 2011-01-03
forum: General Help
---

### Post by Sanchenzo on 2011-01-03
I have recently re-installed Ubuntu and this time GRUB won't show up and will automatically start Windows. How do I fix this?

---

### Post by drs305 on 2011-01-03
Please boot the Ubuntu  LiveCD/install CD and download/run the boot info script from the following site. Then post the RESULTS.txt here so we can look at your boot file situation.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Sanchenzo on 2011-01-03
I'm so sorry it took so long...

```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 927621176 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,712,309    31,710,262   7 HPFS/NTFS
/dev/sda2    *     31,712,310    32,740,469     1,028,160   7 HPFS/NTFS
/dev/sda3          32,740,470   558,240,250   525,499,781   7 HPFS/NTFS
/dev/sda4         558,241,790   976,771,071   418,529,282   5 Extended
/dev/sda5         558,241,792   959,719,423   401,477,632  83 Linux
/dev/sda6         959,721,472   976,771,071    17,049,600  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       468ee1f9-84e8-8545-989d-9068c45091c3   ext2       casper-rw                     
/dev/sda1        5E064D80064D59E3                       ntfs       PQSERVICE                     
/dev/sda2        906C4DE36C4DC526                       ntfs       SYSTEM RESERVED               
/dev/sda3        82CE4F51CE4F3D23                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9773a742-7249-4bdb-a2cf-1d05a722cd27   ext4                                     
/dev/sda6        69b5b763-ad0c-4dda-a4a6-5cf3a9e43867   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60C6-5E16                              vfat       PENDRIVE                      
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
search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
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
    search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9773a742-7249-4bdb-a2cf-1d05a722cd27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9773a742-7249-4bdb-a2cf-1d05a722cd27 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9773a742-7249-4bdb-a2cf-1d05a722cd27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5e064d80064d59e3
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 906c4de36c4dc526
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
UUID=9773a742-7249-4bdb-a2cf-1d05a722cd27 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=69b5b763-ad0c-4dda-a4a6-5cf3a9e43867 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 474.9GB: boot/grub/core.img
 346.1GB: boot/grub/grub.cfg
 350.9GB: boot/initrd.img-2.6.35-22-generic
 474.9GB: boot/vmlinuz-2.6.35-22-generic
 350.9GB: initrd.img
 474.9GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 01 8c 01 e5 01 01 79  00 01 77 71 02 a7 01 17  |.......y..wq....|
00000010  01 94 03 00 01 8c 01 3f  01 85 01 00 01 6b 00 01  |.......?.....k..|
00000020  7f c3 01 01 a9 01 00 01  b9 01 00 01 a7 01 80 01  |................|
00000030  01 a6 01 00 01 5b 00 01  9f 01 00 01 b6 01 00 01  |.....[..........|
00000040  a1 01 00 01 a5 01 00 01  71 00 01 ad 01 00 01 85  |........q.......|
00000050  02 00 01 3d 00 01 97 01  00 01 97 01 00 01 8b 01  |...=............|
00000060  00 01 5f 00 02 b9 01 00  02 8d 01 00 02 93 01 14  |.._.............|
00000070  01 ed 01 87 02 01 d1 01  00 01 db 01 00 01 e3 01  |................|
00000080  2f 01 85 01 00 01 86 01  00 01 88 01 24 01 57 00  |/...........$.W.|
00000090  01 5f 09 01 61 03 03 99  01 00 03 91 01 00 03 9d  |._..a...........|
000000a0  01 25 01 b7 01 00 01 b9  01 00 01 bb 01 18 03 71  |.%.............q|
000000b0  00 03 69 00 03 75 37 01  3f 00 01 40 07 01 ec 02  |..i..u7.?..@....|
000000c0  00 01 83 01 00 01 bd 01  28 02 cb 02 00 02 ab 02  |........(.......|
000000d0  00 02 bf 02 1f 01 a6 01  01 01 9e 01 00 02 9f 01  |................|
000000e0  00 02 97 01 df 02 01 85  01 00 01 86 01 00 01 81  |................|
000000f0  01 bb 02 01 bf 02 00 01  b9 02 00 01 b5 02 32 01  |..............2.|
00000100  f9 01 00 01 8f 02 00 01  8f 02 00 01 91 02 00 01  |................|
00000110  8f 02 00 01 8f 02 9f 01  01 c3 01 00 01 d1 01 00  |................|
00000120  01 d8 01 00 01 c0 01 b2  01 01 8d 01 0f 01 6d 04  |..............m.|
00000130  01 df 01 00 01 dd 01 00  01 cf 01 00 01 cd 01 45  |...............E|
00000140  01 a3 01 00 01 a2 01 c4  01 01 92 02 00 01 84 02  |................|
00000150  00 01 9b 02 34 01 6b ab  01 01 77 00 01 af 01 00  |....4.k...w.....|
00000160  01 b5 01 00 01 8f 01 00  01 b5 01 13 01 b9 01 00  |................|
00000170  01 cd 01 00 01 c9 01 5a  01 dc 01 9a 01 01 84 01  |.......Z........|
00000180  00 01 64 6e 01 6b 00 01  52 00 01 63 3e 01 8a 01  |..dn.k..R..c>...|
00000190  94 01 01 44 4f 01 97 02  1e 01 64 00 01 43 40 02  |...DO.....d..C@.|
000001a0  8f 02 00 02 eb 01 f6 01  01 a7 01 00 01 d1 01 20  |............... |
000001b0  01 91 02 00 01 88 02 33  01 db 01 00 01 e3 00 fe  |.......3........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 ee 17 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  ee 17 00 30 04 01 00 00  |...........0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 60 04  |.X.SYSLINUX...`.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 30 00 00 00  |........?...0...|
00000020  d0 7f 77 00 d0 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 16 5e c6 60 4e  4f 20 4e 41 4d 45 20 20  |..).^.`NO NAME  |
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
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
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

---

### Post by Sanchenzo on 2011-01-03
What action do I take now?

---

### Post by damphoud on 2011-01-04
Perhaps try to reinstall grub

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

drs305 has a howto purge and reinstall grub (but the above howto may be sufficient):

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1581099](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1581099)


When you're finished, it may help to run sudo update-grub2, to ensure your windows 7 partition boots properly.


Edit: So judging from your output, your grub restore would follow (after booting from the live cd) in the terminal:

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
Reboot to hdd ubuntu
sudo update-grub2


In addition, drs304 knows a lot more about grub than I do, and so take his word over mine if what I say differs to his response!

---

### Post by Sanchenzo on 2011-01-04
> **damphoud said:**
> Perhaps try to reinstall grub

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

drs305 has a howto purge and reinstall grub (but the above howto may be sufficient):

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1581099](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1581099)


When you're finished, it may help to run sudo update-grub2, to ensure your windows 7 partition boots properly.

Thank You

---

