---
title: "Grub will not boot Windows Vista"
date: 2012-04-13
forum: General Help
---

### Post by kristen978 on 2012-04-13
Okay, here is the deal. I installed Ubuntu 11.10 in October or so, so that it would dual boot on my laptop along with Windows Vista. I haven't had any problems with the set up since then. It would boot using the Windows boot loader which I noted was different from my desktop which would use Grub. Last week, Windows ran an update (because Windows friggin blows) and it caused me to not be able to boot in Ubuntu at all. I was slightly peeved but whatever. I reinstalled Ubuntu 11.10, doing nothing different than before, only now it uses Grub to boot. The problem is that now I cannot get Grub to boot Windows. I don't get any errors or anything. I can still access my files on my Windows user, so they are still there. When I tell it to boot Windows, the screen goes black, like it is trying for a few seconds, then it returns back to Grub. 

In case you couldn't tell, I am not super efficient in Linux. I do know computers though! I work for an IT company, I just don't have a lot of experience with Linux. I need help with this ASAP, it is that point in the semester where I have stuff due and I need access to certain programs on my Windows partition that won't work with Ubuntu.

---

### Post by raja.genupula on 2012-04-13
look at my signature and post the Bootinfoscript output .

---

### Post by kristen978 on 2012-04-13
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe /wubildr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 419478664 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     30,801,920   380,154,235   349,352,316   7 NTFS / exFAT / HPFS
/dev/sda4         380,155,902   488,396,799   108,240,898   5 Extended
/dev/sda5         380,155,904   482,183,167   102,027,264  83 Linux
/dev/sda6         482,185,216   488,396,799     6,211,584  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        1C3A012C3A01050C                       ntfs       RECOVERY
/dev/sda3        0C86037586035F18                       ntfs       OS
/dev/sda5        5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9   ext4       
/dev/sda6        8abfae13-f0c0-48cf-8a38-1d9f2e87f7b9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0C86037586035F18
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
UUID=5bd6d376-0fd0-4dc8-93ec-58bd54a3b6d9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8abfae13-f0c0-48cf-8a38-1d9f2e87f7b9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-17-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3/Wubi


Unknown BootLoader on sda4

00000000  ee 6b fb 59 1b cd c6 2f  04 21 01 81 92 f1 b7 22  |.k.Y.../.!....."|
00000010  4c 03 e9 8c 72 0a 25 06  65 2a 35 b4 ed 6a 8c 5e  |L...r.%.e*5..j.^|
00000020  c9 51 67 9b 72 65 99 7e  5c 55 38 c0 e8 94 da dc  |.Qg.re.~\U8.....|
00000030  a9 28 b5 84 66 7f e6 2e  20 f5 23 43 3a 0d a6 34  |.(..f... .#C:..4|
00000040  2f a8 6f f5 f2 08 3d ba  90 87 9e 31 b5 92 2d f2  |/.o...=....1..-.|
00000050  91 12 68 5a db 93 8d 98  55 90 51 84 91 4c c5 2d  |..hZ....U.Q..L.-|
00000060  9e a5 58 45 1b 2f 41 85  8a b1 cc 44 8d 27 08 3c  |..XE./A....D.'.<|
00000070  50 6a 07 76 e8 2a 14 c5  05 e0 b5 0a 48 ac b1 a4  |Pj.v.*......H...|
00000080  4d 76 18 e8 9d 20 00 00  00 00 00 00 a5 32 0b 77  |Mv... .......2.w|
00000090  22 37 1c 40 e1 f8 40 3e  af ab 4d 34 d3 55 0d 76  |"7.@..@>..M4.U.v|
000000a0  17 e5 93 3e a6 9d 32 18  4f a9 42 b6 a9 f5 28 55  |...>..2.O.B...(U|
000000b0  a1 41 b8 a4 82 7d 54 f0  7e a9 ce b4 ce 62 3b 1c  |.A...}T.~....b;.|
000000c0  4f 28 70 b5 eb 75 69 da  77 34 a1 40 31 5b f8 70  |O(p..ui.w4.@1[.p|
000000d0  d5 3d af 4d cc 34 ca 93  3f 42 fb 35 28 ea 95 3e  |.=.M.4..?B.5(..>|
000000e0  4b 1d 49 aa e9 c2 a7 6d  ce 68 6e 6d be 7d aa 02  |K.I....m.hnm.}..|
000000f0  0a ee 69 be a3 5d fb 97  e9 8f f9 d7 2d e9 42 83  |..i..]......-.B.|
00000100  06 14 28 61 78 5a 0c 46  80 97 c6 49 12 51 e8 58  |..(axZ.F...I.Q.X|
00000110  91 02 91 b9 6e 29 12 87  4c 5a 4e 42 76 19 68 cf  |....n)..LZNBv.h.|
00000120  9c 37 ae 64 8c 09 0b 71  d1 e0 d3 c2 e8 9d af 1d  |.7.d...q........|
00000130  6a d0 d2 18 9c 01 37 a3  33 6e d9 b2 1d ca 77 60  |j.....7.3n....w`|
00000140  c6 55 17 76 63 07 42 d0  25 5a e8 ba c4 45 d9 56  |.U.vc.B.%Z...E.V|
00000150  6b 48 b5 26 e1 c4 ad cc  06 9e d0 81 d6 d8 b5 8e  |kH.&............|
00000160  08 62 9c 1a 6a fc a9 a0  1a ce 88 d9 84 3b ea ec  |.b..j........;..|
00000170  d6 94 ac 7b 70 2f 54 4d  ed 64 d6 bd 33 9e 0a 72  |...{p/TM.d..3..r|
00000180  34 49 ac 30 14 05 15 30  85 a5 89 c9 32 1a 9e cb  |4I.0...0....2...|
00000190  c8 8a 31 c1 20 f8 78 1a  6a 0b dd 5b 6b 92 47 b6  |..1. .x.j..[k.G.|
000001a0  28 bf 85 0a 29 32 70 58  7c 96 dc 41 96 e9 57 24  |(...)2pX|..A..W$|
000001b0  9c 05 bc 62 b6 63 06 26  ca aa f6 b9 2a dc 00 fe  |...b.c.&....*...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 14 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d0  14 06 00 d0 5e 00 00 00  |............^...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by bcbc on 2012-04-13
You somehow installed grub over your Windows boot sector (/dev/sda3). Please review this to restore: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It recommends testdisk, but if you use the Windows repair method then there is a typo in that link (bootrec instead of bootrect)

---

### Post by kristen978 on 2012-04-13
I ran the Testdisk but it did not work. I don't have a recovery disk for windows. I'm totally lost now.

---

### Post by oldfred on 2012-04-13
There used to be a free download of a Windows repair (only) cd, but due to copyright (meaning MS) they now charge $10.

But if you know someone with the same 32 or 64 bit any version you can make a repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I used the Wiondows repair USB to run chkdsk on my XP install and it worked better than the XP chkdsk. But it converted my boot sector from XP to Vista/7 type. I was able to use the repairCD to rewrite a XP boot sector.
Testdisk does have a rebuild a boot sector function. But I think it is only the XP version. That would then let you read the NTFS partition, but it would not be bootable until you repaired it with a Windows repairCD.

---

