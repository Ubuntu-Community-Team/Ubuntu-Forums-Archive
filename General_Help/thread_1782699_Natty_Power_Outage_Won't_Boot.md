---
title: "Natty Power Outage Won't Boot"
date: 2011-06-14
forum: General Help
---

### Post by appalbarry on 2011-06-14
The circuit breaker popped on my UPS (!) causing my system to shut down with extreme prejudice.  Now Natty won't boot - keeps defaulting to Memtest.  Neither the regular Natty boot or the Recovery mode go anywhere.

It's a dual Windows Vista/Natty install, separate partitions,very recent, flawless til now.

Booted with live USB, ran *sudo fsck* on every drive.  All come up clean except for **/dev/sda3/** which faults with **fsck.ntfs: not found** 

According to *fdisk -l* this should be the boot disk.

I also see **/dev/sdb1/** listed with a *, indicating that it too is a boot disk? It tells me that there are differences between the boot sector and its backup.

Should I restore this from the backup?

---

### Post by wildmanne39 on 2011-06-14
> **appalbarry said:**
> The circuit breaker popped on my UPS (!) causing my system to shut down with extreme prejudice.  Now Natty won't boot - keeps defaulting to Memtest.  Neither the regular Natty boot or the Recovery mode go anywhere.

It's a dual Windows Vista/Natty install, separate partitions,very recent, flawless til now.

Booted with live USB, ran *sudo fsck* on every drive.  All come up clean except for **/dev/sda3/** which faults with **fsck.ntfs: not found** 

According to *fdisk -l* this should be the boot disk.

I also see **/dev/sdb1/** listed with a *, indicating that it too is a boot disk? It tells me that there are differences between the boot sector and its backup.

Should I restore this from the backup?Hi, post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by appalbarry on 2011-06-15
Many thanks!

Needless to say,** CLIP_IT /  /dev/sdb** is the USB stick running a live USB install.

Barry

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda4: __________________________________________________________________________

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

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 1725560 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024     8,820,631     8,691,608   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,100,544   853,891,071   832,790,528   7 NTFS / exFAT / HPFS
/dev/sda4         853,893,118   976,771,071   122,877,954   5 Extended
/dev/sda5         853,893,120   970,485,759   116,592,640  83 Linux
/dev/sda6         970,487,808   976,771,071     6,283,264  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8053 MB, 8053063680 bytes
256 heads, 60 sectors/track, 1024 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,728,639    15,728,608   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       fdfa0030-1513-4bde-a939-51a828fff2bc   ext3       
/dev/sda1        07D8-0812                              vfat       DellUtility
/dev/sda2        0696E67B96E66A9F                       ntfs       RECOVERY
/dev/sda3        5EDEE964DEE934C5                       ntfs       OS
/dev/sda5        1a69837c-e597-41c6-8a2d-437b671f5e28   ext4       
/dev/sda6        a9648b30-b232-46ea-8b6d-015bf9f97316   swap       
/dev/sdb1        4C12-DFF4                              vfat       CLIP-IT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
[operating systems] 
[boot loader] 
timeout=15 
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
set default="4"
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
search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.39-020639rc3-generic ...'
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.38-02063808-generic ...'
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 5EDEE964DEE934C5
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a9648b30-b232-46ea-8b6d-015bf9f97316 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.351348877 = 473.897402368  boot/grub/core.img                             1
 459.515399933 = 493.400903680  boot/grub/grub.cfg                             1
 412.090034485 = 442.478305280  boot/initrd.img-2.6.38-02063808-generic        2
 459.672389984 = 493.569470464  boot/initrd.img-2.6.38-8-generic               1
 412.094612122 = 442.483220480  boot/initrd.img-2.6.39-020639rc3-generic       2
 411.082344055 = 441.396305920  boot/vmlinuz-2.6.38-02063808-generic           1
 441.349620819 = 473.895546880  boot/vmlinuz-2.6.38-8-generic                  1
 410.730823517 = 441.018863616  boot/vmlinuz-2.6.39-020639rc3-generic          2
 412.090034485 = 442.478305280  initrd.img                                     2
 459.672389984 = 493.569470464  initrd.img.old                                 1
 411.082344055 = 441.396305920  vmlinuz                                        1
 441.349620819 = 473.895546880  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  0c 3e f1 3e 15 3f 47 3f  7d 3f aa 3f d7 3f 00 00  |.>.>.?G?}?.?.?..|
00000010  00 50 49 00 40 00 00 00  04 30 31 30 62 30 a3 31  |.PI.@....010b0.1|
00000020  c9 31 e0 31 c3 32 29 33  49 34 23 35 83 35 d9 38  |.1.1.2)3I4#5.5.8|
00000030  2b 39 36 39 47 39 78 39  83 39 94 39 22 3a 67 3a  |+969G9x9.9.9":g:|
00000040  72 3a 83 3a fa 3a 05 3b  16 3b d3 3b ce 3f e9 3f  |r:.:.:.;.;.;.?.?|
00000050  00 60 49 00 4c 00 00 00  56 30 d3 31 a3 32 f0 39  |.`I.L...V0.1.2.9|
00000060  15 3a 3a 3a 11 3c 1a 3c  1f 3c a6 3c 08 3d 25 3d  |.:::.<.<.<.<.=%=|
00000070  2c 3d 32 3d 50 3d 56 3d  a5 3d ac 3d b2 3d d5 3d  |,=2=P=V=.=.=.=.=|
00000080  db 3d 43 3e 5c 3e 86 3e  8d 3e a9 3e b0 3e 76 3f  |.=C>\>.>.>.>.>v?|
00000090  7d 3f 83 3f a6 3f ad 3f  b3 3f 00 00 00 70 49 00  |}?.?.?.?.?...pI.|
000000a0  50 00 00 00 e3 35 fc 35  22 36 2d 36 83 36 9c 36  |P....5.5"6-6.6.6|
000000b0  c2 36 cd 36 b3 37 23 38  ba 39 b1 3a e8 3a f8 3a  |.6.6.7#8.9.:.:.:|
000000c0  20 3b df 3b eb 3b f6 3b  17 3c 27 3c 53 3c ba 3c  | ;.;.;.;.<'<S<.<|
000000d0  cb 3c d7 3c e2 3c 03 3d  13 3d 3e 3d 53 3d 5f 3d  |.<.<.<.=.=>=S=_=|
000000e0  6b 3d 13 3f 36 3f 4a 3f  c1 3f d3 3f 00 80 49 00  |k=.?6?J?.?.?..I.|
000000f0  20 00 00 00 33 30 a9 31  f9 32 e3 37 29 38 ee 3b  | ...30.1.2.7)8.;|
00000100  f9 3b 0a 3c b5 3c c5 3c  d6 3c 00 00 00 90 49 00  |.;.<.<.<.<....I.|
00000110  44 00 00 00 c3 30 f1 30  85 31 8b 31 51 32 5c 32  |D....0.0.1.1Q2\2|
00000120  6d 32 ce 32 d9 32 ea 32  fc 32 07 33 18 33 21 35  |m2.2.2.2.2.3.3!5|
00000130  1b 36 96 36 a3 36 09 37  3b 37 68 37 95 37 c8 37  |.6.6.6.7;7h7.7.7|
00000140  09 3d 14 3d 2c 3d 63 3d  a1 3d c6 3d eb 3d 00 00  |.=.=,=c=.=.=.=..|
00000150  00 a0 49 00 30 00 00 00  e6 31 f1 31 03 32 33 36  |..I.0....1.1.236|
00000160  56 36 63 36 d1 36 f5 36  27 37 54 37 81 37 b4 37  |V6c6.6.6'7T7.7.7|
00000170  03 38 26 38 37 38 b3 38  13 39 59 3b c3 3d 00 00  |.8&878.8.9Y;.=..|
00000180  00 b0 49 00 28 00 00 00  f9 31 93 32 b5 34 c0 34  |..I.(....1.2.4.4|
00000190  d1 34 a3 35 03 36 63 36  43 38 95 3a 9f 3a b7 3a  |.4.5.6c6C8.:.:.:|
000001a0  e9 3a 63 3f e1 3f 00 00  00 c0 49 00 44 00 00 00  |.:c?.?....I.D...|
000001b0  03 30 28 30 c8 31 d5 31  59 32 61 32 90 32 00 fe  |.0(0.1.1Y2a2.2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 f3 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 7c 13  f3 06 86 e4 5f 00 00 00  |......|....._...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by wildmanne39 on 2011-06-15
> **appalbarry said:**
> Many thanks!

Needless to say,** CLIP_IT /  /dev/sdb** is the USB stick running a live USB install.

Barry

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda4: __________________________________________________________________________

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

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 1725560 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024     8,820,631     8,691,608   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,100,544   853,891,071   832,790,528   7 NTFS / exFAT / HPFS
/dev/sda4         853,893,118   976,771,071   122,877,954   5 Extended
/dev/sda5         853,893,120   970,485,759   116,592,640  83 Linux
/dev/sda6         970,487,808   976,771,071     6,283,264  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8053 MB, 8053063680 bytes
256 heads, 60 sectors/track, 1024 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,728,639    15,728,608   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       fdfa0030-1513-4bde-a939-51a828fff2bc   ext3       
/dev/sda1        07D8-0812                              vfat       DellUtility
/dev/sda2        0696E67B96E66A9F                       ntfs       RECOVERY
/dev/sda3        5EDEE964DEE934C5                       ntfs       OS
/dev/sda5        1a69837c-e597-41c6-8a2d-437b671f5e28   ext4       
/dev/sda6        a9648b30-b232-46ea-8b6d-015bf9f97316   swap       
/dev/sdb1        4C12-DFF4                              vfat       CLIP-IT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
[operating systems] 
[boot loader] 
timeout=15 
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
set default="4"
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
search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.39-020639rc3-generic ...'
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.38-02063808-generic ...'
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a69837c-e597-41c6-8a2d-437b671f5e28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 5EDEE964DEE934C5
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1a69837c-e597-41c6-8a2d-437b671f5e28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a9648b30-b232-46ea-8b6d-015bf9f97316 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.351348877 = 473.897402368  boot/grub/core.img                             1
 459.515399933 = 493.400903680  boot/grub/grub.cfg                             1
 412.090034485 = 442.478305280  boot/initrd.img-2.6.38-02063808-generic        2
 459.672389984 = 493.569470464  boot/initrd.img-2.6.38-8-generic               1
 412.094612122 = 442.483220480  boot/initrd.img-2.6.39-020639rc3-generic       2
 411.082344055 = 441.396305920  boot/vmlinuz-2.6.38-02063808-generic           1
 441.349620819 = 473.895546880  boot/vmlinuz-2.6.38-8-generic                  1
 410.730823517 = 441.018863616  boot/vmlinuz-2.6.39-020639rc3-generic          2
 412.090034485 = 442.478305280  initrd.img                                     2
 459.672389984 = 493.569470464  initrd.img.old                                 1
 411.082344055 = 441.396305920  vmlinuz                                        1
 441.349620819 = 473.895546880  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  0c 3e f1 3e 15 3f 47 3f  7d 3f aa 3f d7 3f 00 00  |.>.>.?G?}?.?.?..|
00000010  00 50 49 00 40 00 00 00  04 30 31 30 62 30 a3 31  |.PI.@....010b0.1|
00000020  c9 31 e0 31 c3 32 29 33  49 34 23 35 83 35 d9 38  |.1.1.2)3I4#5.5.8|
00000030  2b 39 36 39 47 39 78 39  83 39 94 39 22 3a 67 3a  |+969G9x9.9.9":g:|
00000040  72 3a 83 3a fa 3a 05 3b  16 3b d3 3b ce 3f e9 3f  |r:.:.:.;.;.;.?.?|
00000050  00 60 49 00 4c 00 00 00  56 30 d3 31 a3 32 f0 39  |.`I.L...V0.1.2.9|
00000060  15 3a 3a 3a 11 3c 1a 3c  1f 3c a6 3c 08 3d 25 3d  |.:::.<.<.<.<.=%=|
00000070  2c 3d 32 3d 50 3d 56 3d  a5 3d ac 3d b2 3d d5 3d  |,=2=P=V=.=.=.=.=|
00000080  db 3d 43 3e 5c 3e 86 3e  8d 3e a9 3e b0 3e 76 3f  |.=C>\>.>.>.>.>v?|
00000090  7d 3f 83 3f a6 3f ad 3f  b3 3f 00 00 00 70 49 00  |}?.?.?.?.?...pI.|
000000a0  50 00 00 00 e3 35 fc 35  22 36 2d 36 83 36 9c 36  |P....5.5"6-6.6.6|
000000b0  c2 36 cd 36 b3 37 23 38  ba 39 b1 3a e8 3a f8 3a  |.6.6.7#8.9.:.:.:|
000000c0  20 3b df 3b eb 3b f6 3b  17 3c 27 3c 53 3c ba 3c  | ;.;.;.;.<'<S<.<|
000000d0  cb 3c d7 3c e2 3c 03 3d  13 3d 3e 3d 53 3d 5f 3d  |.<.<.<.=.=>=S=_=|
000000e0  6b 3d 13 3f 36 3f 4a 3f  c1 3f d3 3f 00 80 49 00  |k=.?6?J?.?.?..I.|
000000f0  20 00 00 00 33 30 a9 31  f9 32 e3 37 29 38 ee 3b  | ...30.1.2.7)8.;|
00000100  f9 3b 0a 3c b5 3c c5 3c  d6 3c 00 00 00 90 49 00  |.;.<.<.<.<....I.|
00000110  44 00 00 00 c3 30 f1 30  85 31 8b 31 51 32 5c 32  |D....0.0.1.1Q2\2|
00000120  6d 32 ce 32 d9 32 ea 32  fc 32 07 33 18 33 21 35  |m2.2.2.2.2.3.3!5|
00000130  1b 36 96 36 a3 36 09 37  3b 37 68 37 95 37 c8 37  |.6.6.6.7;7h7.7.7|
00000140  09 3d 14 3d 2c 3d 63 3d  a1 3d c6 3d eb 3d 00 00  |.=.=,=c=.=.=.=..|
00000150  00 a0 49 00 30 00 00 00  e6 31 f1 31 03 32 33 36  |..I.0....1.1.236|
00000160  56 36 63 36 d1 36 f5 36  27 37 54 37 81 37 b4 37  |V6c6.6.6'7T7.7.7|
00000170  03 38 26 38 37 38 b3 38  13 39 59 3b c3 3d 00 00  |.8&878.8.9Y;.=..|
00000180  00 b0 49 00 28 00 00 00  f9 31 93 32 b5 34 c0 34  |..I.(....1.2.4.4|
00000190  d1 34 a3 35 03 36 63 36  43 38 95 3a 9f 3a b7 3a  |.4.5.6c6C8.:.:.:|
000001a0  e9 3a 63 3f e1 3f 00 00  00 c0 49 00 44 00 00 00  |.:c?.?....I.D...|
000001b0  03 30 28 30 c8 31 d5 31  59 32 61 32 90 32 00 fe  |.0(0.1.1Y2a2.2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 f3 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 7c 13  f3 06 86 e4 5f 00 00 00  |......|....._...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```
Hi,try this from your live usb drive.
```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
If you see no errors reported, please reboot and see if Ubuntu boots up.

---

### Post by appalbarry on 2011-06-15
grub-install yields:

install_device not specified

---

### Post by wildmanne39 on 2011-06-15
> **appalbarry said:**
> grub-install yields:

install_device not specifiedHi, ok I think you need to follow this guide, you will use the livecd and do a complete grup removal and reinstall, you will need the instructions that say chroot method or livecd method. I also noticed that you are using the kernel for oneiric did you install it on purpose? If you have more questions go ahead and ask them.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Also further down the page of the instructions if you can not understand them there is a link to click on for instructions with pictures.

---

### Post by drs305 on 2011-06-15
You might want to run an fsck check on sda5 in case errors were introduced by the power failure. You can run this from the LiveCD. Make sure sda5 is NOT mounted when you run it:
```
sudo e2fsck -f -y -v /dev/sda5
```
Running it with the -v so you can see if there were any errors. I don't know if e2fsck would be more effective than fsck but at least the -v option would show any errors.

---

### Post by appalbarry on 2011-06-15
hmmmm-  my instinct is to just do a reinstall.  my data is on another partition, so I'll just nuke it and start over - which is pretty painless with natty.

---

### Post by wildmanne39 on 2011-06-15
> **appalbarry said:**
> hmmmm-  my instinct is to just do a reinstall.  my data is on another partition, so I'll just nuke it and start over - which is pretty painless with natty.
Hi, I understand that, however is less painful for you.

---

### Post by tgalati4 on 2011-06-15
And what caused the circuit breaker to pop?  Usually, it's a power supply that's drawing too much current.  So I would check the power supply voltages and be prepared when it farts again.  The UPS will protect you from outages and wonky power from the Utility, but nothing protects you from a failing power supply.  Give a sniff, if you smell that burned, bakelite smell, then your PS is right above Milk on your shopping list.

---

### Post by appalbarry on 2011-06-16
By way of background, I had a lapse of judgement and plugged a Samsung laser into a power bar attached to the UPS.  When I powered up the laser the initial surge popped the breaker on the UPS.

Yeah, self inflicted....

Interestingly the Ubuntu reinstall from Live USB hasn't done the job.  I opted for "Upgrade from 11.04 to 11.04" and it looks fine except for:

- it claimed that my hardware won't run Unity (an improvement in my mind)
- wireless is completely gone.  It worked an hour ago when booting off the Live USB.

My next step is to nuke the partition and go with a virgin natty install.

*> I also noticed that you are using the kernel for oneiric *

Ah yes - wireless networking in Natty is pretty damaged, and it was suggested to upgrade kernel to fix it.  Forgot about that.

I have to say that I'm disappointed.  I've had power outages in the past with Windows boxes and they were always able to recover with grace after a reboot.  I am REALLY surprised how badly Ubuntu has crashed.

---

