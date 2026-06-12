---
title: "Installation Assistance Please, Will Not Boot Without USB and No Options !"
date: 2012-02-15
forum: General Help
---

### Post by Cuzuaintme on 2012-02-15
Okay so I've downloaded Ubuntu 11.10 today and I used universal usb installer and had it onto my flash drive ready to install. I then booted from the flash drive and proceeded to install Ubuntu from my flash drive. I did the partitioning from within the installer and I am sure that I did not overwrite my windows partition as it asked to have me create another. Back on track, the installation went smooth and asked me if I wanted to merge some information from a windows user account to my Ubuntu OS for easy access and I agreed. The process took a while and I left the PC. I don't know what happened after but someone in the house apparently went on the computer and finished the installation. I don't know if they messed up something, but I'm guessing that is what it was.

My main dilemma is that Ubuntu seems fine on my computer, however when I take out my USB and start the computer it fails to boot up into anything. It needs the USB to even boot into Ubuntu, and there is no menu for me to select which operating system. It should be red I think? However, all I get is a black screen. I would very much appreciate any help I can get because I feel a lot of unnecessary pressure from the ones I live with.

I did some googling and came across something called "GRUB" but I was confused because the various tutorials I have watched before attempting had nothing to do with that. It was just partitioning, installation, and that red menu to choose the OS. I am really lost and any help is appreciated by myself. Please help. Any ideas you have :/

---

### Post by mikewhatever on 2012-02-15
Can you post the output of **sudo fdisk -l** #(thats a small L there). Not sure what's the 'red menu', but the boot problem should be easily fixable.

---

### Post by Cuzuaintme on 2012-02-17
Sorry for this late reply, but this is what I get when running the command. Also, the install Ubuntu program is still on the desktop.

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1070440357   535220147+   7  HPFS/NTFS/exFAT
/dev/sda2      1070440446  1226833919    78196737    5  Extended
/dev/sda3      1226835855  1250258624    11711385    7  HPFS/NTFS/exFAT
/dev/sda5      1070440448  1218711551    74135552   83  Linux
/dev/sda6      1218713600  1226833919     4060160   82  Linux swap / Solaris

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7837695     3918832    b  W95 FAT32

---

### Post by 23dornot23d on 2012-02-17
Can you follow the instructions here >>> [Bootinfoscript]("http://bootinfoscript.sourceforge.net/")

It give more information - I think you may have installed the boot to the USB Flash Drive
whatever you do keep the flash drive as it is .... and have it inserted when you run
the bootinfoscript


as it should show if the partition info has gone to that instead of sda

---

### Post by Cuzuaintme on 2012-02-17
Thanks for the help, this is what I've gotten.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 8224 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,070,440,357 1,070,440,295   7 NTFS / exFAT / HPFS
/dev/sda2       1,070,440,446 1,226,833,919   156,393,474   5 Extended
/dev/sda5       1,070,440,448 1,218,711,551   148,271,104  83 Linux
/dev/sda6       1,218,713,600 1,226,833,919     8,120,320  82 Linux swap / Solaris
/dev/sda3       1,226,835,855 1,250,258,624    23,422,770   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,837,695     7,837,664   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        963E63DE3E63B641                       ntfs       HP
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda5        67069b68-8bb1-406e-a8f3-8b7b22b0bb1a   ext4       
/dev/sda6        45766b40-ef85-4fe1-bc5c-83e80ccfc416   swap       
/dev/sdb1        CA2B-BCAE                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=67069b68-8bb1-406e-a8f3-8b7b22b0bb1a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=67069b68-8bb1-406e-a8f3-8b7b22b0bb1a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 67069b68-8bb1-406e-a8f3-8b7b22b0bb1a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 963E63DE3E63B641
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=67069b68-8bb1-406e-a8f3-8b7b22b0bb1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=45766b40-ef85-4fe1-bc5c-83e80ccfc416 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  49 21 1e 40 e8 f9 8c 37  e9 e5 63 92 44 37 6b 0c  |I!.@...7..c.D7k.|
00000010  0d 73 29 39 1e 9c 77 be  51 88 86 0c 89 a4 ad d5  |.s)9..w.Q.......|
00000020  24 2b d7 1a 59 3d 16 c1  cc 7c 48 ae 32 56 df 6b  |$+..Y=...|H.2V.k|
00000030  ee 4a 5b c2 26 41 c9 06  2a 40 82 c6 b1 59 4c 54  |.J[.&A..*@...YLT|
00000040  a0 29 0c 22 c8 97 1e d8  bf 1d b3 57 9c 37 d4 77  |.).".......W.7.w|
00000050  d3 15 63 0e 6b 80 38 b9  70 04 ab 5f 0a 8e 1f 33  |..c.k.8.p.._...3|
00000060  14 24 01 0f af c2 22 6d  10 20 3c 08 d5 6b 45 52  |.$...."m. <..kER|
00000070  08 41 49 65 11 25 06 04  ff 17 80 24 66 e9 1a 2e  |.AIe.%.....$f...|
00000080  6b 24 ba db a4 07 76 49  79 49 4c b5 92 e4 82 06  |k$....vIyIL.....|
00000090  e8 7a 2d 54 00 92 63 8e  97 95 7e 93 b3 7c fc 88  |.z-T..c...~..|..|
000000a0  64 7b ba b5 b9 03 7c d6  e5 ae ee 97 29 74 6f 84  |d{....|.....)to.|
000000b0  2f 16 bf 46 31 1c c6 e0  e7 e7 2a 9c 63 a5 96 e7  |/..F1.....*.c...|
000000c0  f8 60 59 cc 9c 5c 74 62  8a 14 f5 fb da 2e 09 69  |.`Y..\tb.......i|
000000d0  2a 9a 79 be 35 2e 4e 10  8d 4d 94 55 3a 89 a2 eb  |*.y.5.N..M.U:...|
000000e0  f5 ce 8d 7a 53 0c 8d 32  e4 d5 a5 11 03 7a 0d fa  |...zS..2.....z..|
000000f0  8a f1 e2 7b dd cc c6 2f  2d bd 02 95 64 33 f2 b3  |...{.../-...d3..|
00000100  e7 8a d1 25 83 d8 6d 8f  8b 3c e7 e9 3d a8 2a 10  |...%..m..<..=.*.|
00000110  81 93 96 e9 6c d2 ee 9a  95 ea 6a e6 60 c7 ef 87  |....l.....j.`...|
00000120  93 c2 48 1f 3a c8 a6 b3  52 6a 36 86 95 1e e1 ca  |..H.:...Rj6.....|
00000130  b3 c1 3a 60 73 ba be 36  bb 3d da a8 fc 7d 37 63  |..:`s..6.=...}7c|
00000140  c9 a8 06 3f e6 97 7a a0  00 2d 21 f0 1f 3e 94 70  |...?..z..-!..>.p|
00000150  a2 0f d7 8a 26 5a cc f9  7c f8 4a 90 27 22 91 10  |....&Z..|.J.'"..|
00000160  d8 96 bf cf 98 52 47 77  b0 9b f4 f4 0b 20 d3 f8  |.....RGw..... ..|
00000170  e4 27 9f 5d 50 59 0b 70  e5 d9 c4 26 f2 61 12 5a  |.'.]PY.p...&.a.Z|
00000180  b9 61 f9 fb d0 6b d5 a8  28 b4 7b f8 64 38 7e 48  |.a...k..(.{.d8~H|
00000190  94 a1 6a 5e 36 aa e2 dd  21 81 b9 06 a5 dd b3 41  |..j^6...!......A|
000001a0  35 43 95 d1 83 f4 cc 4f  d8 0f 5e f6 3f 2f 7f 2d  |5C.....O..^.?/.-|
000001b0  5e 04 58 cc 1c 25 14 d8  b8 93 77 c8 ac 72 00 fe  |^.X..%....w..r..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 d6 08 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 02 70  d6 08 00 f0 7b 00 00 00  |.......p....{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by forrestcupp on 2012-02-17
You can keep going with this, but I think it's probably more likely that someone didn't complete the installation, but it got aborted before it got to the point that Grub was set up. So you probably have an incomplete installation. Since you haven't invested any time into setting things up how you want it, I'd just reinstall Ubuntu using the partition that it already made for it, and this time make sure it completes the installation.

By the way, you're not booting to your new installation with the USB; you're probably just booting to the LiveCD/USB.

---

### Post by 23dornot23d on 2012-02-17
I agree with what you are saying ......  [forrestcupp]("http://ubuntuforums.org/member.php?u=18807")         

> 
I don't know what happened after but someone in the house apparently  went on the computer and finished the installation. I don't know if they  messed up something, but I'm guessing that is what it was.
                                      
               
Just read this bit again and as you say its booting the installation.

> 
Sorry for this late reply, but this is what I get when running the  command. Also, **[COLOR=Red]the install Ubuntu program is still on the desktop[/COLOR]**.

For the 20 to 30 mins it takes to re-install fully - then that is the option that would ensure that you have a full system .....

---

### Post by Cuzuaintme on 2012-02-17
How would I go about reinstalling Ubuntu? I want to use the partition that I had made before.

When I go to install it again, I select the third choice, which is a custom installation. I select the Ubuntu partition and get a root error of some sort. Am I supposed to format it to Fat32 or something? I am not sure what to do with the options and don't want to do random things to the partition.

---

### Post by 23dornot23d on 2012-02-17
Can you explain this in more detail or get a screenshot or something .....

> 
I select the Ubuntu partition and get a root error of some sort. 


Only sda5 needs to be formatted to ext4 ....

[COLOR=Red]**do not format anything else .....**[/COLOR]

once you choose to use sda5 then you can continue .... 

as the swap is already set up as sda6 ( this will be used automatically )

then continue the install .... 

Choosing where you want the boot loader to go to sda

> 
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for  on this drive.



---

### Post by Cuzuaintme on 2012-02-17
Here are my two screenshots, if anything else is needed please let me know,

[IMG]http://i39.tinypic.com/24q73tl.png[/IMG]
[IMG]http://i41.tinypic.com/3585180.png[/IMG]

This is after I double click and choose to format to ext4. Don't understand where the error is coming from.

---

### Post by 23dornot23d on 2012-02-17
You have to choose the partition type .... 
click on the change option .... and choose as shown below .... for sda5

[IMG]http://img42.imageshack.us/img42/1108/35851802.jpg[/IMG]

as below the forward slash defines root

[B]/


and the device for the bootloader needs to be sda ..... (not sda5 - otherwise its not going to update the boot menu)
[COLOR=Red]device for boot loader installation[/COLOR]
This needs to be /dev/sda     for it to boot up ...... from your msin drive.
[/B]

---

### Post by Cuzuaintme on 2012-02-18
Alright, I had tried again to reinstall Ubuntu and it seemed to go smoothly. Told me to reboot, remove flash drive and press enter. Upon doing so my computer restarts and then the point where I would expect a dual boot menu there is a black screen that says "Mode Not Supported" I don't even know how to get into my Vista partition which sucks. If any methods, please let me know.

I don't know whats wrong. I go through installation, I used /dev/sda instead of sda5. I feel like a sitting duck, not knowing what to do to solve this.

[IMG]http://i42.tinypic.com/dz886v.jpg[/IMG]

Why am I even getting that?

------------------
Edit: I found some commands said to work for people, however I did not achieve the same result. Instead I was moved from the image above to this

[IMG]http://i44.tinypic.com/157gr3p.jpg[/IMG]

When will my PC decide to dual boot :/

---

### Post by 23dornot23d on 2012-02-18
Have a look here ......

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

and this

[https://answers.launchpad.net/ubuntu/+source/grub2/+question/164527](https://answers.launchpad.net/ubuntu/+source/grub2/+question/164527)


If you have no success with the above - please boot from the flash drive again and run
the bootinfoscript so that we can see more information .....

---

### Post by Cuzuaintme on 2012-02-18
I am in the process of trying this stuff out now, however I am having issues running "sudo update-grub"

I get the following

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I know I've done it before, but I just can't find the same command to mount. And when I use "sudo mount /dev" I get this

ubuntu@ubuntu:~$ sudo mount /dev
mount: udev already mounted or /dev busy
mount: according to mtab, udev is already mounted on /dev

---

### Post by 23dornot23d on 2012-02-18
From what you are saying there .... there is no root device ......

Did you choose it as said ..... using the change command there is a tab or option in there to set the root  using this marker      /


Go through the install procedure again ..... and ensure that root is set.

That was why you got the error on your previous screenshot as far as I can see ....

At the moment all the data on your hard drive is still intact ...... and the only thing missing
is the root partition sda5 ..... to boot from ......

Run the install again ensuring that you set root as sda5

[IMG]http://www.muktware.com/sites/default/files/images/manual/ubuntu-11-04/fresh_install_root.png[/IMG]

Set mount point as root ..... [COLOR=Red]**this example above is only to show you how to set root **[/COLOR].... do not alter anything else.

This is the only way you can boot it ...... (from the hard disk ....)

---

### Post by Cuzuaintme on 2012-02-18
Okay, so you need me to install Ubuntu through sda5 now? The last thing I've done to that was the format and mount / ,yesterday. After formatting I installed on sda

So if I need to install on sda5 I'll be sure to do that now, but I'd rather wait for confirmation from you before spending an hour installing just to do it somewhere else :p

---

### Post by 23dornot23d on 2012-02-18
I never said install on sda ...... 

I said install on sda5 ... and put the boot loader on sda

thats it .....

---

### Post by Cuzuaintme on 2012-02-18
Alright, I have /dev/sda as the boot loader installation and /dev/sda5 is ext4 and has the "/" mount. Didn't touch anything else and the other partitions have blank mounts. So I'll have that install itself again and see where I end up.

Thanks for you help so far!

---

### Post by 23dornot23d on 2012-02-18
Its sda for the bootloader

Its sda5 for the installation 

sorted once its run through it should just boot to a grub boot menu .....

That looks ok ...... just a double confirmation .

---

### Post by Cuzuaintme on 2012-02-18
Thanks for everything! I was finally able to boot into the OS, but I did not see a grub menu. Instead the same black screen with "Mode Not Supported" yet after about 10-20 seconds it boot into Ubuntu and had me at the login screen.

I will now try a hardboot and see if the Grub menu comes this time

---

### Post by 23dornot23d on 2012-02-18
Do not reboot yet

Lets check some things out first


See what drives you can see from file manager .... and post back what it looks like .... 

after going into a terminal and do .......

**sudo update-grub **

post back the output ..... you get please ...... we can work from here now .... if its ok ....... 

may need some graphics drivers installing too ..... what graphics card is in it - in a terminal do .... 

[B]lspci


cut and paste back the output please

as an example it should return something like this

[/B]> 
keith@keith-Aspire-7730ZG:~$ sudo update-grub
[sudo] password for keith: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-14-generic
Found initrd image: /boot/initrd.img-3.2.0-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 9 Isadora (9) on /dev/sda5
grep: input file `/boot/grub/grub.cfg.new' is also the output
done

keith@keith-Aspire-7730ZG:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
keith@keith-Aspire-7730ZG:~$ 



---

### Post by Cuzuaintme on 2012-02-18
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo update-grub
[sudo] password for trayvont: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax M

Thats what I get, hopefully I didn't take TOO long

---

### Post by 23dornot23d on 2012-02-18
Good to see .... looks like Nvidia Graphics ......

> 00:0d.0 VGA compatible controller: nVidia Corporation C61 [[COLOR=Blue]**GeForce 6150SE nForce 430**[/COLOR]] (rev a2)

and the boot has Vista in it ..... so its looking good .....

> 
Found [COLOR=Blue]**Windows Vista**[/COLOR] (loader) on /dev/sda1
Found [COLOR=Blue]**Windows Vista **[/COLOR](loader) on /dev/sda3


give me a moment will just have a quick check on the graphics card .. and drivers
and see what the state of play is ....


ok just looking through these to see if there are any known problems .... 

[https://www.google.com/search?client=ubuntu&channel=fs&q=nVidia+GeForce+6150SE+nForce+430&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=unu&channel=fs&sclient=psy-ab&q=ubuntu+nVidia+GeForce+6150SE+nForce+430&pbx=1&oq=ubuntu+nVidia+GeForce+6150SE+nForce+430&aq=f&aqi=&aql=&gs_sm=3&gs_upl=20554l22698l0l22848l7l6l0l0l0l1l800l1275l4-1.0.1l2l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=496](https://www.google.com/search?client=ubuntu&channel=fs&q=nVidia+GeForce+6150SE+nForce+430&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=unu&channel=fs&sclient=psy-ab&q=ubuntu+nVidia+GeForce+6150SE+nForce+430&pbx=1&oq=ubuntu+nVidia+GeForce+6150SE+nForce+430&aq=f&aqi=&aql=&gs_sm=3&gs_upl=20554l22698l0l22848l7l6l0l0l0l1l800l1275l4-1.0.1l2l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=496)

may just be a case of going into additional drivers  and adding for the nvidia ..... but will look through these then post back
should not be too long ..... check out the drives you can see in the file manager and post a screen shot back

if you would please ......

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717)

Looking at that it is saying people had more success with the Nvidia 173 driver ......  for Compiz and UNITY
what are you going to run on it ?

have a look through too to make sure it applies to your machine as some of the later drivers seem to make it
laggy .....

Will read some more .... but the 173 driver may be the one ..... can you get to the

additional hardware drivers ..... and see what options it shows you please

---

### Post by Cuzuaintme on 2012-02-18
I'll be waiting :) Thanks a bunch for this.

---

### Post by 23dornot23d on 2012-02-18
whoops ... it double posted.

---

### Post by 23dornot23d on 2012-02-18
Ok a lot of those reports are old ones ..... but I would like to see what the 

additional drivers offers you .....

open the dash and type in additional ..... 

hopefully a icon will be there - it may already have notified you in the top right as you opened the desktop ....

[COLOR=RoyalBlue]**Post a screenshot when you find it please like before**[/COLOR]

---

### Post by Cuzuaintme on 2012-02-18
Here's the screenie

[IMG]http://i40.tinypic.com/21ms2eg.png[/IMG]

---

### Post by 23dornot23d on 2012-02-18
Ok that looks good it is already using it .....

Unity and the 3D effects are they working ok ...... 

Workspace Switcher on the left and just before all the drives .... if you press it what happens ..... will look 


also paste this in to see the output


**date && lsb_release -sd || cat /etc/*release &&  uname    -s -r && unity --version &&    /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils**


for example mine shows this

> 
keith@keith-Aspire-7730ZG:~$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sun Feb 19 01:04:40 CET 2012
Ubuntu precise (development branch)
Linux 3.2.0-14-generic
unity 5.2.0
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL version string:  2.1 Mesa 8.0-rc2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package `mesa-utils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
keith@keith-Aspire-7730ZG:~$ 



---

### Post by Cuzuaintme on 2012-02-18
I'm getting this:

> trayvont@trayvont-KQ496AA-ABA-a6530f:~$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sat Feb 18 19:07:18 EST 2012
Ubuntu 11.10
Linux 3.0.0-16-generic
unity 4.28.0
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package `mesa-utils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


And Workspace Switcher gives me four tiles to choose from

---

### Post by 23dornot23d on 2012-02-18
Yep all is looking good ......

Try a reboot .... we could check other things out .... but I could go on all night .....

The thing is to see if it now boots ok ..... best of luck .... as most things look ok.

---

### Post by Cuzuaintme on 2012-02-18
Commencing reboot :)

Hopefully all goes well

---

### Post by 23dornot23d on 2012-02-18
Ok hopefully all the 3D will work too like in this video

[http://www.youtube.com/watch?v=-8Xje1OoqKU&feature=related](http://www.youtube.com/watch?v=-8Xje1OoqKU&feature=related)

---

### Post by Cuzuaintme on 2012-02-18
The video went through with no flaws.

Separately, when rebooting I ended up in some type of menu. I'm not too sure what it was but it had to do with recovery and I went through some of the options and saw grub, but it was not a dual boot menu as I didn't get the option to boot into windows. I believe it only comes up when I press buttons on my keyboard also. Is that anything that would bring up grub? I'll show a pic.

Eh... Can't figure out how to get back in there. Another headache, and if I ever get there again I'll be sure to snap a picture of it.

---

### Post by 23dornot23d on 2012-02-18
Sometimes people have to adjust the boot .....

( Holding down the *SHIFT key allows you* to display the boot options. )

to include things like nomodeset

will have a search ... as its not something I have to do .... and Nvidia is usually ok ....
but in the search I did for your card there were some people mentioning problems ...

Will now search on

Nvidia nomodeset GeForce 6150SE


Just looking here .... for options at boot
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

seems there is a way to make it easier on this page to change things .... but I have never tried it out ....
as its a problem I have never encountered with Nvidia before.

[http://ubuntuforums.org/showthread.php?t=1613132&page=5](http://ubuntuforums.org/showthread.php?t=1613132&page=5)






Can you get back in safe graphics mode again .... at reboot ... press the down arrow once then press return

The recovery menu has one option on it for safe-graphics mode .... if its still there ....

if you can get back in again let me know what you see ..... ty

I just came across this ....

in this search .... [https://www.google.com/search?client=ubuntu&channel=fs&q=Nvidia+nomodeset+GeForce+6150SE&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=zJH&channel=fs&sclient=psy-ab&q=ubuntu+Nvidia+nomodeset+GeForce+6150SE&pbx=1&oq=ubuntu+Nvidia+nomodeset+GeForce+6150SE&aq=f&aqi=&aql=&gs_sm=3&gs_upl=8629l11234l0l11579l7l7l0l0l0l3l755l1873l0.4.1.1.6-1l7l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=485](https://www.google.com/search?client=ubuntu&channel=fs&q=Nvidia+nomodeset+GeForce+6150SE&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=zJH&channel=fs&sclient=psy-ab&q=ubuntu+Nvidia+nomodeset+GeForce+6150SE&pbx=1&oq=ubuntu+Nvidia+nomodeset+GeForce+6150SE&aq=f&aqi=&aql=&gs_sm=3&gs_upl=8629l11234l0l11579l7l7l0l0l0l3l755l1873l0.4.1.1.6-1l7l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=485)
> 
The only way I can see a display is to F6, and add *nomodeset* to the startup string. **...** I have a *NVIDIA GeForce 6150 SE* intregrated graphics.


---

### Post by Cuzuaintme on 2012-02-18
When I input a command when Ubuntu is booting up, it gives me that green "Mode Not Supported" message. Its pretty frustrating.

I have no idea how to edit nomodeset or anything. I don't even see menus anymore, just black screen -> "Mode Not Supported" -> Ubuntu

Am I supposed to rely on the Usb Again?

The Down and Return(Or Enter in my case) does the same Mode Not Supported, so I'm not sure how I'll get into that safe-graphics.

---

### Post by 23dornot23d on 2012-02-18
I have not come across this before ... with any of my installs ....
the thing is now we know ..... what is happening ...

we could re-install again ..... knowing that once we get in again ..... we set the
nomodeset while you have a graphical user interface ....

I think its all related to the graphics card you have ..... but unless someone else can pop
up and give you a better suggestion ....


I would do the re-install one more time ..... knowing we get one chance to set it up properly ......

holding the **shift key** down at boot is not working for you 

( then all I can think is one more install - and when we are in to set up for nomodeset )

or

See this and see if you can do as it says ..... [http://ubuntuforums.org/showthread.php?t=1730149](http://ubuntuforums.org/showthread.php?t=1730149)

[COLOR=Red]**you have to hold shift down all the time as its booting up**[/COLOR]

2 options ..... thats all I can give you ....... unless someone else can help .....

We have proved it runs ok once booted .... * ( its the grub boot loader thats the pain now .... as it sets the graphics ......)

---

### Post by Cuzuaintme on 2012-02-18
What exactly does the "nomodeset" do? And I don't recall a time during the installation that asked for it, unless it is hidden somewhere.

Thanks again for giving me so many options.

---

### Post by 23dornot23d on 2012-02-18
This explains it ...... better than I can 

[http://wiki.sugarlabs.org/go/Nomodeset](http://wiki.sugarlabs.org/go/Nomodeset)

The problem with the black screen .... is one that I see on the forums a lot
but no definitive answer seems to come up .... if I could give you a simple 
solution to how grub sorts all the many graphics cards and monitors that they
use ..... 


Pressing the** esc **key repetitively  .... was mentioned too as its booting up .... 

( removed text - as referred to safe mode - which only applies once we have got by the grub2 boot )

---

### Post by 23dornot23d on 2012-02-19
The more I read on this .... the more I believe its to do with 

KMS and the Framebuffer ...... but maybe someone that knows more about how
grub uses these .... could help here .....

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Almost appears to use xorg.conf ..... for speed .... so after the first boot .... which may
work correctly as we found out ....

The next boot may go directly to the [COLOR=RoyalBlue]xorg.conf[/COLOR] for setup information ......

But this needs claryfying as I know the devs have been making less use of xorg.conf
but if its there it gets used and seems to override other settings.

So if that is correct ...... booting using the Flash drive .... going into sda5 

rm /etc/X11/[COLOR=Red]**xorg.conf**[/COLOR]

( may allow it to boot ok ...... but the problem then may lie in which graphics driver is used ...... there was another 173 post mod or something .... maybe that would be better ..... is this trial and error .... or can we find a success story on the NET ) 

*( I am now convinced nomodeset makes it can make a difference at bootup - as this may affect what happens when grub2 needs to be displayed )

so is that what nomodeset does - turns KMS off as described in the link above quote below from it ......

> 
**Turning it off**

 If you need to turn KMS *off* do the following depending on the hardware in question: 

# ATI Radeon: echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf  
# Intel: echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf  
# Nvidia (this should revert you to using -nv or -vesa): echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf


The [COLOR=Red]**grub.cfg**[/COLOR] ..... is where the monitor resolution is set ..... and this seems to get passed back to the kernel ....... for use at boot up .... reading the link above.

The monitor resolution ..... and the graphics ....... at boot need to be identified
correctly otherwise the black screen occurs ...... so if I read it correctly then [COLOR=Red]grub.cfg[/COLOR] and [COLOR=Red]xorg.conf [/COLOR]are the two main things affecting the outcome at boot up ....


Thought I would share this ..... *( as its something that I have not really had problems with myself - but have seen many others complain about it )

---

### Post by forrestcupp on 2012-02-19
If you end up doing a reinstall, instead of choosing to use custom partitions, choose the option to Upgrade Ubuntu 11.10 to Ubuntu 11.10. It sounds kind of silly, but it will end up doing what you would try to do with custom partitions, only it would do it right.

I suspect that when you "pressed a key" to get into a boot menu, that it was your BIOS's boot menu and it had nothing to do with Linux. One of the choices on your BIOS's boot menu is to boot to the recovery partition, which is what came on your computer to reinstall it to factory settings. I think when you installed Ubuntu, you may not have set up Grub correctly, and if you do it again and let Ubuntu do all of that automatically for you like I said above, it may take care of your problems.

---

### Post by 23dornot23d on 2012-02-19
From what he says here .... he got into the recovery menu

as the BIOS .... does not have [COLOR=Red]**grub**[/COLOR] in there as a option ...... 

> 
Separately, when rebooting I ended up in some type of menu. 
I'm not too  sure what it was but it had to do with recovery and 
I went through some  of the options and [COLOR=Red]**saw grub**[/COLOR]

I suspect that this menu popped up - but I suppose the only way to be 
sure is if this can be verified as being the case. 

[IMG]https://encrypted-tbn3.google.com/images?q=tbn:ANd9GcT-FI3v_ahQu2G8V49ljKmFWQeGLWa9Xr1DXVh7lGSrOA1tUFef[/IMG]

Not sure what you are saying in the 2nd quote following - [forrestcupp]("http://ubuntuforums.org/member.php?u=18807") ..... if his partitions were wrong and the boot menu was not working .....
he would not have been able to boot into the OS in the first place and to do all the checks that I asked for.

Reason I did not want to reboot before doing the checks was that the user had already indicated that
the boot menu never showed up

> 
Thanks for everything! I was finally able to boot into the OS, but I did  not see a grub menu. Instead the same black screen with "Mode Not  Supported" yet after about 10-20 seconds it boot into Ubuntu and had me  at the login screen.

I will now try a hardboot and see if the Grub menu comes this time
[[COLOR=Red]**See post 21**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11699583&postcount=21") ..... I stopped the user re-booting here to do more checks ......

> This the quote that I refer to above - from [forrestcupp]("http://ubuntuforums.org/member.php?u=18807")

If you end up doing a reinstall, instead of choosing to use custom  partitions, choose the option to Upgrade Ubuntu 11.10 to Ubuntu 11.10.  It sounds kind of silly, but it will end up doing what you would try to  do with custom partitions, [COLOR=Red]**only it would do it right.**[/COLOR]
[COLOR=Red][B][COLOR=Black]

What do you see wrong with the way the custom partitions have been set up[/COLOR]
Boot install loader sda - installation on sda5 *sda5 being root /.
[/B][/COLOR]
The problem lies with displaying the grub boot menu properly at boot up .... 

But interesting and glad you added some more input ..... 
The graphics ..... and how to display the grub ..... when only a black screen shows up

**Grub worked as the means to get the user into his system the first time** ..... its just no displaying.

When he did **update-grub** ..... it showed that the right options were in there too.

> 
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo update-grub
[sudo] password for trayvont: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
What I did find interesting here was that there were two versions .... of the kernel for boot .....
3.0.0-16-generic
3.0.0-12-generic

This indicated a upgrade may have already taken place at some point .......

I remain convinced that the problem here lies with grub2 and the menu not showing - 
as the functionality to get it to boot worked the first time .....
also
The user could not possibly have booted in and run UNITY in 3D mode and done the tests

1 ..... Checking that grub updated  ..... ok ( worked no errors )
2 ..... Checking that UNITY was installed and working in 3D mode ( worked and the results were shown )
3 ..... Checking for the Graphics Driver after first checking the web for known problems ( working fine in the desktop )
4 ..... Only way I then know to check it boots ok and displays grub - is to do it ..... this is where it comes to a black screen


  >>>> if the custom partition (sda5) was not set up properly it would never have allowed me to do all of the above
without flagging up some errors ...

I suspect from what he said if he presses no keys at all and waits .... it will automatically run the boot procedure
for the first option .....

> 
"Mode Not  Supported" [COLOR=Red]**yet after about 10-20 seconds it boot into Ubuntu**[/COLOR] and had me  at the login screen.
So you could try the same again ..... waiting .....
( the only thing is getting by [Plymouth]("https://www.google.com/search?client=ubuntu&channel=fs&q=Plymouth&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=WIU&channel=fs&sclient=psy-ab&q=plymouth+black+screen+ubuntu&pbx=1&oq=Plymouth+black+sc&aq=1j&aqi=g-v1g-j1&aql=&gs_sm=1&gs_upl=835l11426l1l14599l16l11l4l1l1l1l2050l5503l0.6.2.6-1.1.0.1l15l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=496") then as that too seems to use the same graphical setup and driver info as grub )

[COLOR=Red]**SO JUST WAIT PRESS NOTHING**[/COLOR] = it should choose the first option itself after 10 secs .... and get to the login again

( Let me know if it boots up and gets to the login screen again - here is a similar [_[COLOR=Blue]**problem still occurring in 12.04**[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1927708") )

---

### Post by Cuzuaintme on 2012-02-19
Just posting to let you know I am currently on the forums. I will be reading through all the posts thoroughly.

And yes, that is the menu I was talking about ^_^
Sorry for not being able to give proper details on this

---

### Post by 23dornot23d on 2012-02-19
No problems - the information you gave was just fine ..... you described what you saw and added screenshots plus the cut and paste of the information I asked for .....

Did you try just waiting at the start ..... not pressing anything ...... as this may still work

---

### Post by Cuzuaintme on 2012-02-19
I'll start trying more methods, Don't think I've done the Esc properly as it worked for others with Nvidia, but not me, and shift didn't work either. I'll leave it alone on boot and see what happens.

Also, I read to disable by using this :set gfxpayload=text
However, I don't know where to input that, doesn't seem like a terminal command.

--------------------

A way into that grub menu that works is shift holding. It then shows me "Grub loading..." then I get that green screen which is when I pressed down then enter and I got into it. Aside from that, I think I'll look on how this f6 thing works.

---

### Post by 23dornot23d on 2012-02-19
I know where it goes .... its in the grub.cfg file /boot/grub/**grub.cfg**

How we get to that ... and edit it ...... is the bit I am hoping can be made simpler

The way we could do it is to boot from the flash drive

Go into a terminal ......

Chroot into the HD system ........ navigate to grub.cfg and then edit the grub.cfg changing the gfxmode or gfxpayload

[http://www.gnu.org/software/grub/manual/html_node/gfxpayload.html#gfxpayload](http://www.gnu.org/software/grub/manual/html_node/gfxpayload.html#gfxpayload)

* ( but I am not confident of you doing this ...... and it still needs update-grub to be run to have any effect on the next boot up )

If you can get in another way then things become so much easier .......

Almost wish afer getting in the first time I had prior knowledge and could have done this then ...... but ..... 

If you get in let me know .......

________________________________________________________

> I think I'll look on how this f6 thing works. that is relative when booting from livecd or flash drive as
far as I know ...... but feel free to find other options ...... ( as once you are back into a desktop things become much easier )


> 
A way into that grub menu that works is shift holding. It then shows me  "Grub loading..." then [COLOR=SeaGreen]**I get that green screen**[/COLOR] which is when I pressed  down then enter and I got into it. Aside from that, I think I'll look on  how this f6 thing works.
What green screen .... 

do you mean this with the green information icon .... not seen a green screen shot yet 
[IMG]http://img198.imageshack.us/img198/7114/modenotsup.jpg[/IMG]

[COLOR=Red]**If you have now got into grub ..... using the shift key**[/COLOR] ...... just choose the first option one and press return.

---

### Post by Cuzuaintme on 2012-02-19
I'll do anything that you suggest, if another clean install is necessary so be it.

And when I use my USB I don't have function options, so I guess the f6 is moot in my case.

I do remember reading somewhere that I can change the order of which OS will boot first. It looks like for me that Ubuntu is the first, now what if I'd like it to be Windows?

I looked on the net and thought Wubi was a lite installation of Ubuntu, but now it seems like the full and same thing that I have now. If possible, setting windows to the default, or primary OS to boot from then maybe I could install Wubi onto that and format everything and resize partitions? I don't know.... Is Wubi worth anything?

------------

When I say green screen I am talking about the "Mode Not Supported" Thing, sorry about that

On this website:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) I found something telling me to add nomodeset after putting this into terminal sudo gedit /etc/default/grub
I continue to get my black screen with the green box on-screen reading "Mode Not Supported", is this my graphics card's way of saying it cannot handle it?

---

### Post by 23dornot23d on 2012-02-19
We need to get by the   "Mode Not Supported" message
> 
On this website:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) I found something telling me to add nomodeset after putting this into terminal sudo gedit /etc/default/grub
I continue to get my black screen with the green box on-screen reading  "Mode Not Supported", is this my graphics card's way of saying it cannot  handle it?


Your graphics card can handle - it once it gets by the grub boot screen into the Desktop ..... ( UNITY 3D works ) 

[COLOR=Red]Shame grub2 does not[/COLOR]  ..... grub2 seems to need more work - to allow for the Nomodeset and Gfxpayload =Text 
at the time when the     "Mode Not Supported"   message gets displayed.



Try a clean install again doing as we did before ...... 

( As you now know the routine for that ...... ) 

It will allow us to get in again - without having to do any manual editing of things .....

Just takes a bit of time ....

---

### Post by Cuzuaintme on 2012-02-19
Alright expect me in a half hour or how ever long this takes.

And yeah, the green badge xD turns out that prompt is really blue.... But yeah, I'm reinstalling again.

---

### Post by forrestcupp on 2012-02-19
Sorry, I missed the part where he said grub was an option. Usually when I hear about people pressing a key to get into a boot menu, it reminds me of the BIOS boot menu. Between that and the past time when he booted to Ubuntu using the USB instead of his installation, I just made some wrong assumptions.

It's all yours; you know what you're doing. However, if you're telling him to install again, I really would suggest letting Ubuntu do the partitioning automatically. Even if your instructions are perfect, there's still the element of human error. If you're going to take the time to install yet another time, why risk it when the installer can do it perfectly, automatically?

---

### Post by Cuzuaintme on 2012-02-19
I'm running Ubuntu off of my USB now and the installer is just about complete. If there is anything to be done when its complete, I am all ears.
-----------------------------------
Actually, its done now. It is giving me a reboot prompt and I haven't done anything to it, nor plan to until replied.

---

### Post by 23dornot23d on 2012-02-19
You have just installed it now you have to boot into it ..... the first time it goes in stay in
the desktop ...... we will work from there

Let me know once you are in the Desktop

---

### Post by Cuzuaintme on 2012-02-19
Alright, I've reached my desktop. Ready for instruction

---

### Post by 23dornot23d on 2012-02-19
Excellent ....

Lets have a look at the display ..... first ......

Go into the Dash

System Settings ......

Display

Do me a screenshot if you would please

---

### Post by Cuzuaintme on 2012-02-19
Here you are:

[IMG]http://i41.tinypic.com/2ljgxi0.png[/IMG]

---

### Post by 23dornot23d on 2012-02-19
ok do this in a terminal ....
[B]
xrandr[/B]

I just want to see what modes you have available

This is a example of mine .....

> 
keith@keith-Aspire-7730ZG:~/Documents$ xrandr
Screen 0: minimum 320 x 200, current 1282 x 722, maximum 8192 x 8192
LVDS-1 connected (normal left inverted right x axis y axis)
   1440x900       60.0 +
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
DVI-D-1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       50.0*+
   720x576        50.0  
VGA-1 disconnected (normal left inverted right x axis y axis)


---

### Post by Cuzuaintme on 2012-02-19
I got an error?

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0* 
   1680x1050      51.0     52.0  
   1600x1024      53.0  
   1440x900       54.0  
   1400x1050      55.0     56.0     57.0  
   1360x768       58.0     59.0  
   1280x1024      60.0     61.0  
   1280x960       62.0  
   1280x800       63.0  
   1152x864       64.0     65.0     66.0     67.0  
   1024x768       68.0     69.0     70.0  
   960x600        71.0  
   960x540        72.0  
   840x525        73.0     74.0     75.0  
   832x624        76.0  
   800x600        77.0     78.0     79.0     80.0     81.0     82.0  
   800x512        83.0  
   720x450        84.0  
   680x384        85.0     86.0  
   640x512        87.0     88.0  
   640x480        89.0     90.0     91.0     92.0  
   576x432        93.0     94.0     95.0     96.0  
   512x384        97.0     98.0     99.0  
   416x312       100.0  
   400x300       101.0    102.0    103.0    104.0  
   320x240       105.0    106.0    107.0

---

### Post by 23dornot23d on 2012-02-19
Ok we are doing a bit of recon ,,, here before we actually change anything ...


Now check for the xorg.conf 

gedit /etc/X11/xorg.conf

post the results back please

---

### Post by Cuzuaintme on 2012-02-19
_ gedit /etc/X11/xorg.conf_


Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

---

### Post by 23dornot23d on 2012-02-19
ok now look in this file ... post the results ....

gedit /etc/default/grub

---

### Post by Cuzuaintme on 2012-02-19
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by 23dornot23d on 2012-02-19
One more .....

gedit /etc/grub.d/00_header

---

### Post by Cuzuaintme on 2012-02-19
This one is kinda huge so I'll put it in code (Just wanted to do something :p)


```

#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
locale_dir=`echo ${GRUB_PREFIX}/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d . -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=auto ; fi

if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAULT" ; fi
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOUT" ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
set default="${GRUB_DEFAULT}"
EOF
fi
cat <<EOF
if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
    # Insert all available backends; GRUB will use the most appropriate.
    have_video=0;
    for backend in $(cat "${GRUB_PREFIX}/video.lst"); do
    have_video=1;
    cat <<EOF
  insmod ${backend}
EOF
    done
    if [ x$have_video = x0 ]; then
    echo "true"
    fi
fi
cat <<EOF
}

EOF

serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
    serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
    gfxterm=1;
    fi
done

if [ "x$serial" = x1 ]; then
    if ! test -e ${GRUB_PREFIX}/serial.mod ; then
    echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
    grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
    GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi

if [ "x$gfxterm" = x1 ]; then
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT_PATH}"`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
EOF

# Gettext variables and module
if [ "x${LANG}" != "xC" ] && [ -d "${locale_dir}" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir}) | sed -e "s/^/  /"
  cat << EOF
  set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
  set lang=${grub_lang}
  insmod gettext
EOF
fi

cat <<EOF
fi
EOF
fi

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_output ${GRUB_TERMINAL_OUTPUT}
EOF
  ;;
esac

if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
    && is_path_readable_by_grub "$GRUB_THEME"; then
    echo "Found theme: $GRUB_THEME" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THEME"`
    cat << EOF
insmod gfxmenu
EOF
    themedir="`dirname "$GRUB_THEME"`"
    for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
        if [ -f "$x" ]; then
        cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
        fi
    done
    if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$themedir"/*.jpeg`" != x"$themedir/*.jpeg" ]; then
        cat << EOF
insmod jpeg
EOF
    fi
    if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
        cat << EOF
insmod png
EOF
    fi
    if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
        cat << EOF
insmod tga
EOF
    fi
        
    cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
        && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
    echo "Found background: $GRUB_BACKGROUND" >&2
    case "$GRUB_BACKGROUND" in 
        *.png)         reader=png ;;
        *.tga)         reader=tga ;;
        *.jpg|*.jpeg)  reader=jpeg ;;
        *)             echo "Unsupported image format" >&2; exit 1 ;;
    esac
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BACKGROUND"`
    cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKGROUND"`
EOF
    fi
fi

make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi
EOF
}

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
fi

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ] && [ "x$GRUB_BUTTON_CMOS_CLEAN" = "xyes" ]; then
    cat <<EOF
cmosclean $GRUB_BUTTON_CMOS_ADDRESS
EOF
fi

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi

if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi

```

---

### Post by 23dornot23d on 2012-02-19
ok ....

we can set NOMODESET 

following this link

[http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)

______________________________________________________

It worries me that xrandr gives the error though ,,,,, we need to check other
threads on this ..... as some I have looked do not solve it .....

and I am also wondering if we can force the mode GFXmode to one that suits
your screen size ......

I do not want to be in the position as we were before , and the things we discussed earlier'

or setting NOMODESET seems a good idea .....

but once we finish what we do ..... is the only time we will know for sure .....

I am tempted to create a new xorg.conf ......

Check the graphic drivers please ..... additional hardware 

in the Dash type

additional ...

see if its still using the 173 driver .... just a yes or no is suffice .... 
but a screen shot will show the other options - should imagine its the
same as it was before ....

---

### Post by 23dornot23d on 2012-02-19
once you have the information ....

we will do four things ...


1 ...... set nomodeset
[URL="http://ubuntuforums.org/showthread.php?t=1675337"]
http://ubuntuforums.org/showthread.php?t=1675337[/URL]

and then

[COLOR=Red][B]update-grub
[/B][/COLOR] 
2 ...... recreate the xorg.conf   

[COLOR=Red]**nvidia-xconfig**[/COLOR]

then to check the output after we re-create it 

3 ...... do some more research to check what we have done is going to work

just to make double sure we have not missed anything obvious

4 ..... re-boot and fingers crossed ..... all that I can think



unless you can think of something ..... 
I have missed ....... we really do not
want to have to do this again

we could uncomment the GFXMODE .... in this but will nomodeset negate the need for that * ( not sure on this )
but I do know from earlier the two files that matter are ,,,, xorg.conf and grub.cfg
[http://ubuntuforums.org/showpost.php?p=11701695&postcount=60](http://ubuntuforums.org/showpost.php?p=11701695&postcount=60)

---

### Post by Cuzuaintme on 2012-02-19
When I enter sudo gedit /etc/default/grub the terminal gives me this:

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo gedit /etc/default/grub

(gedit:3520): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7RFAAW': No such file or directory

(gedit:3520): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

And when I save the changes it gives me this again

(gedit:3520): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J89FAW': No such file or directory

(gedit:3520): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
-------------------------------------------------------

The 173 driver is active, yes. And here is an image of everything.:

[IMG]http://i39.tinypic.com/t4xw2b.png[/IMG]

------------------

GFX Mode? New xorg.conf?

--------------

Nothing comes to mind, but I've done a sudo update-grub after posting this, and I'm really just taking my time doing this.

---

### Post by 23dornot23d on 2012-02-19
yep you need gksudo ,,,, in front of the gedit commands ....

before we commit to anything .....

not wanting to make any mistakes here .... ;)

---

### Post by Cuzuaintme on 2012-02-19
I am getting lost :O
Am I to use this: gksudo gedit /etc/default/grub ?
If so, I am still getting errors.

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ gksudo gedit /etc/default/grub

(gksudo:5075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5077): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BQP99V': No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.120X9V': No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.P8M19V': No such file or directory

(gedit:5077): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Why is the first reboot so vital, by the way?

---

### Post by 23dornot23d on 2012-02-19
Do this in a terminal and post back please ....

**df**


The first reboot the graphics are set ..... to Nvidia .... and that seems to be where the problem lays ..

post the results of above please .... just want to check whats going on here

---

### Post by Cuzuaintme on 2012-02-19
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             72971544   3172152  66092616   5% /
udev                   1922684        12   1922672   1% /dev
tmpfs                   785428       788    784640   1% /run
none                      5120         0      5120   0% /run/lock
none                   1963568       116   1963452   1% /run/shm

---

### Post by 23dornot23d on 2012-02-19
Do 

**sudo apt-get update**

**sudo apt-get install aptitude**


see what it shows

---

### Post by Cuzuaintme on 2012-02-19
That went through well, my computer is downloading and installing stuff now.

If you need me to post it, I can do that

---

### Post by 23dornot23d on 2012-02-19
ok the update is just updating some lists ...

then do

 
sudo aptitude install gparted

---

### Post by Cuzuaintme on 2012-02-19
Its completed

---

### Post by 23dornot23d on 2012-02-19
ok

do 

**sudo gparted **

just get a screen shot and then leave it ..... 

I want to check the drive layout

---

### Post by Cuzuaintme on 2012-02-19
Nice Big Vista Partition :-)

[IMG]http://i42.tinypic.com/2wf5nix.png[/IMG]

---

### Post by 23dornot23d on 2012-02-19
ok that looks good ty .....

now we need to work out why you could not use gedit
[B]
aptitude install gedit[/B]

just to make sure its installed ok

---

### Post by Cuzuaintme on 2012-02-19
Should be good. This is the process though

```

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ aptitude install gedit
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo aptitude install gedit
The following packages will be upgraded: 
  gedit 
1 packages upgraded, 0 newly installed, 0 to remove and 331 not upgraded.
Need to get 537 kB of archives. After unpacking 8,192 B will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main gedit amd64 3.2.3-0ubuntu0.1 [537 kB]
Fetched 537 kB in 0s (549 kB/s)
(Reading database ... 127289 files and directories currently installed.)
Preparing to replace gedit 3.2.0-0ubuntu1 (using .../gedit_3.2.3-0ubuntu0.1_amd64.deb) ...
Unpacking replacement gedit ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up gedit (3.2.3-0ubuntu0.1) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 331 updates [-1].

```

---

### Post by 23dornot23d on 2012-02-19
sorry 

sudo aptitude install gedit

my fault


ok now to try again with the grub and nomodeset option ....

gksudo gedit /etc/default/grub

---

### Post by Cuzuaintme on 2012-02-19
When I run sudo gedit /etc/default/grub or gksudo gedit /etc/default/grub

I continue to get errors

```

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo gedit /etc/default/grub

(gedit:7691): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G9079V': No such file or directory

(gedit:7691): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:7691): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NR739V': No such file or directory

(gedit:7691): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:7691): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.U1NW9V': No such file or directory

(gedit:7691): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ gksudo gedit /etc/default/grub

(gksudo:8228): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8228): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8228): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8228): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:8230): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.1BN19V': No such file or directory

(gedit:8230): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by 23dornot23d on 2012-02-19
Thats odd and I am not sure why its happening !!!

will search for a answer shortly

---

### Post by Cuzuaintme on 2012-02-19
Alright, I'll standby as you do

---

### Post by 23dornot23d on 2012-02-19
ok this thread seems to say it happens .... all the time ....

[http://ubuntuforums.org/showthread.php?t=1788133](http://ubuntuforums.org/showthread.php?t=1788133)

Does the gedit window open to work in ?

solution seems to be to create the missing directory

sudo mkdir /root/.local /root/.local/share



______________________________________________



gksudo gedit /etc/default/grub
ok then try again and add this line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"                      

and do 

sudo update-grub

post the results ..... please .... keeps a record in case someone else wants to check it or try
what we did ( all the info is then in one place .....

---

### Post by Cuzuaintme on 2012-02-19
Yes! All errors are gone, thanks again.

-------------

There is no error with sudo gedit /etc/default/grub
Yet there is this when I use gksudo

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ gksudo gedit /etc/default/grub

(gksudo:8893): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8893): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8893): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8893): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by 23dornot23d on 2012-02-19
Welcome .... I do not like seeing errors and the xrandr one is still bothering me

ok they are warnings .... but not errors as such ..... (we can live with them)
as long as the gedit process works and we can alter the file as required.

ok we have done stage 1

> 1 ...... set nomodeset
[URL="http://ubuntuforums.org/showthread.php?t=1675337"]
http://ubuntuforums.org/showthread.php?t=1675337[/URL]

and then

[COLOR=Red]**update-grub**[/COLOR]

---

### Post by Cuzuaintme on 2012-02-19
Yes, that has been done a while ago actually. It would save, but give me the error about directory. That's all gone now. but I'll run update-grub once more

---

### Post by 23dornot23d on 2012-02-19
ok

part 2

> 

2 ...... recreate the xorg.conf   

do

[COLOR=Black]**sudo nvidia-xconfig**[/COLOR]

then to check the output after we re-create it 

[B]gedit /etc/X11/xorg.conf
[/B] 


---

### Post by Cuzuaintme on 2012-02-19
#1:
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

#2:
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ gedit /etc/X11/xorg.conf

**Then this comes up**

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Sat Apr 16 22:49:04 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by 23dornot23d on 2012-02-19
What monitor are you using by the way and how is it connected ..... ?


**Part 3**

> 

3 ...... do some more research to check what we have done is going to work

just to make double sure we have not missed anything obvious

[COLOR=RoyalBlue]Only thing I can think of now is the GFXMODE .... and the GFXPAYLOAD 
But if Nomodeset ignores these then we need not bother ....
How can we be sure though .... !!!


Do a search

[https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+....+and+the+GFXPAYLOAD+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=bsb&channel=fs&sclient=psy-ab&q=GFXMODE+GFXPAYLOAD+nomodeset&pbx=1&oq=GFXMODE+GFXPAYLOAD+nomodeset&aq=f&aqi=&aql=&gs_sm=3&gs_upl=2830l22171l0l22738l43l29l12l0l0l4l1072l6430l0.23.1.2.2.7-1l41l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=496](https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+....+and+the+GFXPAYLOAD+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=bsb&channel=fs&sclient=psy-ab&q=GFXMODE+GFXPAYLOAD+nomodeset&pbx=1&oq=GFXMODE+GFXPAYLOAD+nomodeset&aq=f&aqi=&aql=&gs_sm=3&gs_upl=2830l22171l0l22738l43l29l12l0l0l4l1072l6430l0.23.1.2.2.7-1l41l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=1154&bih=496)

[/COLOR][B]

[https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+....+and+the+GFXPAYLOAD+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=UFH&channel=fs&biw=1154&bih=496&sclient=psy-ab&q=GFXMODE+GFXPAYLOAD+nomodeset+6150&pbx=1&oq=GFXMODE+GFXPAYLOAD+nomodeset+6150&aq=f&aqi=&aql=&gs_sm=3&gs_upl=117470l123451l1l124225l11l8l3l0l0l0l404l1888l0.3.3.1.1l11l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75](https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+....+and+the+GFXPAYLOAD+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=UFH&channel=fs&biw=1154&bih=496&sclient=psy-ab&q=GFXMODE+GFXPAYLOAD+nomodeset+6150&pbx=1&oq=GFXMODE+GFXPAYLOAD+nomodeset+6150&aq=f&aqi=&aql=&gs_sm=3&gs_upl=117470l123451l1l124225l11l8l3l0l0l0l404l1888l0.3.3.1.1l11l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75)


sudo aptitude install hwinfo

sudo hwinfo --framebuffer[/B]
[COLOR=RoyalBlue]
[/COLOR]> 
keith@keith-Aspire-7730ZG:~$ sudo hwinfo --framebuffer
[sudo] password for keith: 
> hal.1: read hal dataprocess 3913: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.dIPO6Luq6B9
  Hardware Class: framebuffer
  Model: "NVIDIA G98 Board - 06210004"
  Vendor: "NVIDIA Corporation"
  Device: "G98 Board - 06210004"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcd000000-0xcddfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
keith@keith-Aspire-7730ZG:~$ 
                                              



---

### Post by Cuzuaintme on 2012-02-19
Samsung syncmaster 2333hd

And I suppose there is a cord, not sure what to say.

------------
Can we use them to be sure? Or would it cancel out something?
The GFX Stuff

-----------------
trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo aptitude install hwinfo
[sudo] password for trayvont: 
The following NEW packages will be installed:
  hwinfo libhal1{a} libhd16{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 331 not upgraded.
Need to get 768 kB of archives. After unpacking 2,327 kB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe libhal1 amd64 0.5.14-6 [79.2 kB]
Get: 2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe libhd16 amd64 16.0-2ubuntu1 [671 kB]
Get: 3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe hwinfo amd64 16.0-2ubuntu1 [18.5 kB]
Fetched 768 kB in 6s (118 kB/s)                                                 
Selecting previously deselected package libhal1.
(Reading database ... 127289 files and directories currently installed.)
Unpacking libhal1 (from .../libhal1_0.5.14-6_amd64.deb) ...
Selecting previously deselected package libhd16.
Unpacking libhd16 (from .../libhd16_16.0-2ubuntu1_amd64.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libhal1 (0.5.14-6) ...
Setting up libhd16 (16.0-2ubuntu1) ...
Setting up hwinfo (16.0-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

-----------------

trayvont@trayvont-KQ496AA-ABA-a6530f:~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 10001: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.N24uLIh7rp3
  Hardware Class: framebuffer
  Model: "Build    061010.3
 MCP61 - mcp61-85"
  Vendor: "Build    061010.3
"
  Device: "MCP61 - mcp61-85"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 128 MB
  Memory Range: 0xe0000000-0xe7ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by 23dornot23d on 2012-02-19
Probably VGA .....

If it was a TV ... it could have been HDMI or VGA .....



[https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+Samsung+syncmaster+2333hd+&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=GFXMODE+Samsung+syncmaster+2333hd+&ie=utf-8&oe=utf-8)

---

### Post by Cuzuaintme on 2012-02-19
Its both I believe, but its used solely for a computer monitor. It came with a remote and all, and has a button labeled "TV" if that helps any.

---

### Post by 23dornot23d on 2012-02-19
I am not positive on this ...... as with us setting nomodeset earler does it then bypass this 

 ...... we can set it ..... and it can use it .......  or we can leave it ......

* I think to set this then it goes to a resolution it can handle ..... that we know is ok
in your listing .... right down to 8 bit ..... choices .... ?

gksudo gedit /etc/default/grub

set gfxmode=1024x768

and try that ..... as it forces a mode your TV can handle .


Then update-grub


Upto you whether we include this or not .....  and the final part is to just make sure we think
that this is the best we can do under the circumstances ......

---

### Post by Cuzuaintme on 2012-02-19
I don't see "set gfxmode" within the gedit

The only thing related to GFX mode is commented and is this "#GRUB_GFXMODE=640x480"

---

### Post by 23dornot23d on 2012-02-19
Yep thats the line ,,,,
'
remove the comment marker  ..... and by setting the h x v forces it to use that 
resolution as far as I know ..... 

I have done it on mine before ,,,,

here is a old blog I did on setting the picture at boot - its about half way down the
page .... explaining it .....


[https://sites.google.com/site/linuxbootubuntu/](https://sites.google.com/site/linuxbootubuntu/)


There is also the part to set

set gfxpayload=keep

---

### Post by Cuzuaintme on 2012-02-19
I've switched 640x480 with 1024x768

I've also done the sudo update-grub

Anything else we need to consider?
----------
You want me to run those commands?

---

### Post by 23dornot23d on 2012-02-19
Your call on this  ...... as you know the routine if things do not go as we want them to


The only other thing is setting which OS it boots into .......

But that .... could cause more problems .....

If the nomodeset works ..... and the alteration of the xorg.conf

Then we may be ok ...... as usual if anyone else is watching this thread 
please speak out ..... now ....

as we are getting close to reboot time .... long journey too .....

but we gathered lots of information and obviously UNITY is up and running ....

> Why the grub2 menu ...... is a stopping point ..... amazes me ..... but there is
a lot more going on than we can see ..... have looked at many bootcharts ...
where they try to reduce boot up times .....


Yep finish it off with the last bit .... gfxpayload=keep

as I think it takes the resolution settings through to plymouth.

then

update-grub



There is little else I can think of ...... its your call as you are doing all the work here.

But best of luck ... with it ..... ( you could do more searches on [**nomodeset gfxpayload=keep Nvidia 6150**]("https://www.google.com/search?client=ubuntu&channel=fs&q=nomodeset+gfxpayload%3Dkeep+Nvidia+6150&ie=utf-8&oe=utf-8") )

spend a little time looking through and considering if we may have missed something .....

---

### Post by Cuzuaintme on 2012-02-19
I feel ready to reboot. If I am right, the problem lies within the graphics and that all has to do with the resolution and all. If the modifications I've done were good(Which it should be as no errors came through), then we should notice progress.

---

### Post by 23dornot23d on 2012-02-19
Good Luck ..... really do hope it is a success ..... not sure there is anything else
I know that could change things .... but there are far more experienced people
on here than me ..... ;)

---

### Post by Cuzuaintme on 2012-02-19
Okay lets see how this goes.

*Takes Deep Breath*

I'll shutdown and start from there.
I'll wait out a few minutes before doing it just in case anything pops up.

---

### Post by 23dornot23d on 2012-02-19
Wait -

 log out to the login menu and test the xserver .... you can do that at the login

restart xserver .... will check the xorg.conf is ok ..... * just ensures that is not a prioblem

Still the ultimate thing is a full reboot .... we need a countdown too .... 10 .... 9 ...... 8 ..... 7 ....

ok ... you could leave the computer running forever ,,,, LINUX rarely crashes ...

some peoples **[uptime is amazing too]("http://en.wikipedia.org/wiki/Uptime")** ...... options .... !!

---

### Post by Cuzuaintme on 2012-02-19
Erm? How do I check the xserver now?

---

### Post by 23dornot23d on 2012-02-19
Go out to the login screen ..... logout ...takes you to it

and one of the options used to be restart xserver ....

if its still there .....

---

### Post by Cuzuaintme on 2012-02-19
Okay, going to look for that then reboot.
------

Yeah, don't see anything for that. Only options aside from shutting down was something about 2D, if that is it, let us cross our fingers.

---

### Post by 23dornot23d on 2012-02-19
Ok good luck ... :D

---

### Post by Cuzuaintme on 2012-02-19
Because of you 23dornot23d I have been able to boot into my grub menu. I am VERY thankful and the entire process was a good experience for the both of us I believe. If anything, I did learn a bit on terminal commands. 

I just want you to know how thankful to have been tended to :) thanks a bunch.

I am gonna edit the OP just in case someone else falls into the same issue and so they'll get results faster.

When the grub menu came up I chose windows and its undergoing a check disk. I am using my ipod to enlighten you kn the current matter.

Once again, thank you, you're awesome :)
And thank you to the others who gave input as well.

---

### Post by 23dornot23d on 2012-02-19
Your very welcome and it was a good trip ty .... :D

Hope you have some good Ubuntu-ing .... in the future too ,,, ;)

---

### Post by 23dornot23d on 2012-02-20
Can you mark this thread as SOLVED .... in thread tools at the top of the page ...

If you do have any more problems ... please let us know . ty

---

