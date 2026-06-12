---
title: "Installation problem:  NTFS5 error prefix is not set"
date: 2011-11-18
forum: General Help
---

### Post by silicone on 2011-11-18
Hello everybody and glad to join your community!

I'am hardly trying to install Ubuntu 11.10 on my XP Home Edition but I still have some problems.

I have launched th installation cd from XP and asked to install aside of it. The Ubuntu asked to reboot, and then I got the following error:

Try (hd,0,0): NTFS5: error: "prefix is not set

Then I got another message saying: Completing the Ubuntu installation for more info press ESC. If I do not press ESC the installation continue and suddenly stop. I can't go further.

I tried to boot directly from the cd, installing it, tryied to launch "try Ubuntu" but it doesn't work. 

I have verified the M5D key and it matches. My cd has also been verified by Ubuntu and there is no error.

What can I do? Thank in advance for you help :P

---

### Post by silicone on 2011-11-18
Just to mention, I am not able to boot into the "Ubuntu try before install" even if I boot from the cd... So I can not use the boot's log tool! :(

---

### Post by Rubi1200 on 2011-11-18
Hi and welcome to the forums :)

Please post the computer specifications, especially graphics card.

Also, check the Windows Disk Management utility and tell us if the disks are labeled as Basic or Dynamic.

Finally, post the results of the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by silicone on 2011-11-21
Hello,

By now I have not successed in booting Ubuntu direct form the cd. I have tried a couple of times and there are always problems. I can go until the panel where you enter the name, password etc, but then the Ubuntu miss to boot! 

My pc is a: 

Pentium 4, 2.4GHZ
2 GB Ram
Radeon 9200 Pro Family, 128 Mb Ram graphic card
XP Home Edition SP3
Alle the disks are mentioned as Basic

---

### Post by silicone on 2011-11-21
I finnaly successed in booting form an USB flash drive} :D No way from the cd


Here is the boot login:

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15730 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    67,585,454    67,585,392   7 NTFS / exFAT / HPFS
/dev/sda2          67,585,455   156,296,384    88,710,930   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    67,585,454    67,585,392   7 NTFS / exFAT / HPFS
/dev/sdb2          67,585,455   128,943,848    61,358,394   7 NTFS / exFAT / HPFS
/dev/sdb3         128,944,126   156,301,311    27,357,186   5 Extended
/dev/sdb5         128,944,128   152,109,055    23,164,928  83 Linux
/dev/sdb6         152,111,104   156,301,311     4,190,208  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4120 MB, 4120903680 bytes
2 heads, 63 sectors/track, 63878 cylinders, total 8048640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             64     8,048,639     8,048,576   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E4B0C2AEB0C28690                       ntfs       
/dev/sda2        04A4DADAA4DACCF4                       ntfs       Fichiers
/dev/sdb1        D6B0AC43B0AC2C45                       ntfs       Raid
/dev/sdb2        EA80F0E680F0BA61                       ntfs       Video
/dev/sdb5        8cd6fe91-1c28-4ccd-add0-970cfdad07b8   ext4       
/dev/sdb6        7a5cf1d3-f711-47d7-b14e-c1457e999c92   swap       
/dev/sdc1        70D8-D590                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
  set locale_dir=($root)/boot/grub/locale
  set lang=fr_BE
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
menuentry 'Ubuntu, avec Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=8cd6fe91-1c28-4ccd-add0-970cfdad07b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, avec Linux 3.0.0-13-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    echo    'Chargement de Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=8cd6fe91-1c28-4ccd-add0-970cfdad07b8 ro recovery nomodeset 
    echo    'Chargement du disque mémoire initial ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, avec Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8cd6fe91-1c28-4ccd-add0-970cfdad07b8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, avec Linux 3.0.0-12-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    echo    'Chargement de Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8cd6fe91-1c28-4ccd-add0-970cfdad07b8 ro recovery nomodeset 
    echo    'Chargement du disque mémoire initial ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cd6fe91-1c28-4ccd-add0-970cfdad07b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root E4B0C2AEB0C28690
    drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8cd6fe91-1c28-4ccd-add0-970cfdad07b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7a5cf1d3-f711-47d7-b14e-c1457e999c92 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                initrd.img.old                                 1
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  1b 7b d8 f9 dc 8f d1 ab  2e a0 ce 65 2a 6e 5c 11  |.{.........e*n\.|
00000010  60 5b 27 3d 79 7c bd cb  1b f0 95 ea 0d 70 50 45  |`['=y|.......pPE|
00000020  9c 28 3e 7a 3d c5 24 cd  73 d0 3d 1e f3 3a 7e 18  |.(>z=.$.s.=..:~.|
00000030  07 38 1e ac 30 51 56 bd  0f b4 66 1d 85 d0 d8 b9  |.8..0QV...f.....|
00000040  1a 1f 08 10 9b 42 e4 ea  07 53 f1 46 ad 77 8f 94  |.....B...S.F.w..|
00000050  8e b2 7d 24 08 00 9f df  b6 a1 ff 35 92 b4 13 56  |..}$.......5...V|
00000060  5c 07 3e a5 40 2e 98 69  b3 d2 f2 c6 9e 4c 15 ed  |\.>.@..i.....L..|
00000070  be 72 4b 8f 4a b1 21 97  d7 5d 6a 18 7a 44 87 84  |.rK.J.!..]j.zD..|
00000080  2c 89 e6 20 72 b0 c9 b4  3d f5 49 87 0e e2 9a 8a  |,.. r...=.I.....|
00000090  5f 20 90 d4 3f 8e 62 4e  3c 90 af b0 85 aa be ac  |_ ..?.bN<.......|
000000a0  50 4d 0a 68 7a f0 fe 32  6d 63 fd 70 47 60 a5 d5  |PM.hz..2mc.pG`..|
000000b0  39 64 55 db 2c bc ec 6d  ab e3 d4 e3 fd 0b 40 34  |9dU.,..m......@4|
000000c0  91 fa b1 67 a0 17 bf 4b  0d c5 16 68 90 ef bf 35  |...g...K...h...5|
000000d0  13 e4 a1 8c 5c 66 47 5a  ed fd e3 9b 28 92 93 86  |....\fGZ....(...|
000000e0  b7 38 e4 04 2b 4d 95 67  e3 c2 9d 59 30 b7 6e 12  |.8..+M.g...Y0.n.|
000000f0  b6 4b 7c cf 16 b2 f9 7f  ca 88 e3 bf 50 64 41 08  |.K|.........PdA.|
00000100  8a b1 aa 27 65 b9 06 ee  b9 03 99 2a 70 df 3d d5  |...'e......*p.=.|
00000110  eb 3f ee 8c a1 c8 8c 43  09 29 dd 37 bb ac d2 24  |.?.....C.).7...$|
00000120  d2 0a 0b b8 94 84 9c 48  55 2f 12 c3 98 90 b1 e4  |.......HU/......|
00000130  78 68 00 ab 46 d1 88 0d  74 8a d8 eb b1 90 cc 41  |xh..F...t......A|
00000140  56 ee 0f a0 01 d5 df de  7f ef 10 0c f0 f1 54 a8  |V.............T.|
00000150  25 70 b9 14 4d f5 73 47  d1 53 dc c3 7c 38 b9 c6  |%p..M.sG.S..|8..|
00000160  df 03 bf c5 f4 d5 56 16  01 eb 9c ed bf 2b ad 89  |......V......+..|
00000170  bc fc 22 af fe 5b d7 58  e9 2c f2 a7 63 cd 20 1d  |.."..[.X.,..c. .|
00000180  35 f1 22 10 b4 ac 89 59  a2 ca bd 4e 4f 65 44 f0  |5."....Y...NOeD.|
00000190  03 b7 41 65 a0 2c 3b a8  84 bb 20 7f ad 77 8a ad  |..Ae.,;... ..w..|
000001a0  20 61 40 69 8b 81 00 10  29 35 7c 17 e6 c8 a2 43  | a@i....)5|....C|
000001b0  c4 46 20 1c 7d 8f 28 9f  6a ab 70 33 a3 5d 00 fe  |.F .}.(.j.p3.]..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 61 01 00 fe  |...........xa...|
000001d0  ff ff 05 fe ff ff 02 78  61 01 00 f8 3f 00 00 00  |.......xa...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by silicone on 2011-11-25
Nobody can help me to resolve this issue???

---

