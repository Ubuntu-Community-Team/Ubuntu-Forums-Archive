---
title: "Ubuntu not showing up in boot loader menu(hp dv7)"
date: 2012-09-14
forum: General Help
---

### Post by b2580x on 2012-09-14
Hi,

I am new here.I wanted to try ubuntu if it is for me or not. I have dv7 hp notebook and currently have windows 7.I have 2 hard drives.Windows is installed on the first one. Today I shrinked second drive for ubuntu installation. It went well but after restart I can't see ubuntu on bootloader. I tried easybcd but no luck.I couldn't see ubuntu.

I saw one topic here and did the following:

Booted from cd again and selected try ubuntu and later I downloaded boot info script and run.

Here is the result, What sould I do to see both windows 7 and ubuntu on bootloader? :

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 407551 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       450457599 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 1919657984. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 33654783 sectors, 
                       but according to the info from fdisk, it has 450457599 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 1953312768. But according to the info from 
                       fdisk, sda4 starts at sector 450867200. According to 
                       the info in the boot sector, sda4 has 210352 sectors.. 
                       But according to the info from the partition table, it 
                       has 1502655919 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   450,867,199   450,457,600  42 SFS
/dev/sda4         450,867,200 1,953,523,119 1,502,655,920  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,912,561,663 1,912,559,616   7 NTFS / exFAT / HPFS
/dev/sdb2       1,912,563,710 1,914,515,455     1,951,746   5 Extended
/dev/sdb5       1,912,563,712 1,914,515,455     1,951,744  82 Linux swap / Solaris
/dev/sdb3    *  1,914,515,456 1,953,523,711    39,008,256  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C21A79001A78F2B1                       ntfs       SYSTEM
/dev/sda2        20A8C228A8C1FC72                       ntfs       
/dev/sda3        7A589AA5589A6025                       ntfs       RECOVERY
/dev/sda4        8209-AEEE                              vfat       HP_TOOLS
/dev/sdb1        9A06BA3A06BA176B                       ntfs       
/dev/sdb3        321cbe6c-6b03-4441-9fc5-c962f5bce172   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos3)'
  search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=321cbe6c-6b03-4441-9fc5-c962f5bce172 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=321cbe6c-6b03-4441-9fc5-c962f5bce172 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set=root 321cbe6c-6b03-4441-9fc5-c962f5bce172
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root C21A79001A78F2B1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9A06BA3A06BA176B
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=321cbe6c-6b03-4441-9fc5-c962f5bce172 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=d0ab19bc-c85d-4d54-8eee-2701bb872dd3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-29-generic               1
               =                boot/vmlinuz-3.2.0-29-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 4d 8f 00 00 00 00  10 00 00 00 60 00 00 00  |..M.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  ad fa d5 78 60 0b cc 01  ad fa d5 78 60 0b cc 01  |...x`......x`...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  ad fa d5 78 60 0b cc 01  |...........x`...|
000000c0  ad fa d5 78 60 0b cc 01  ad fa d5 78 60 0b cc 01  |...x`......x`...|
000000d0  ad fa d5 78 60 0b cc 01  00 40 00 00 00 00 00 00  |...x`....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 42 00 01 20 8f  b0 00 00 00 50 00 00 00  |!@UB.. .....P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 42 21 01 fd fd  |........!.TB!...|
00000190  00 00 01 00 00 00 4d 8f  ff ff ff ff 00 00 00 00  |......M.........|
000001a0  00 00 04 00 00 00 00 00  21 40 55 42 00 01 20 8f  |........!@UB.. .|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 42 21 01 fd fd  00 00 01 00 00 00 02 00  |!.TB!...........|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  89 ab 7f c9 03 00 00 00  |FILE0...........|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  cc 24 ff ff 00 00 00 00  10 00 00 00 60 00 00 00  |.$..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  c1 48 21 c1 16 ff cc 01  c1 48 21 c1 16 ff cc 01  |.H!......H!.....|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  c1 48 21 c1 16 ff cc 01  |.........H!.....|
000000c0  c1 48 21 c1 16 ff cc 01  c1 48 21 c1 16 ff cc 01  |.H!......H!.....|
000000d0  c1 48 21 c1 16 ff cc 01  00 40 00 00 00 00 00 00  |.H!......@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  7f b4 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 48 0b 00 00 00 00  |@.........H.....|
00000130  00 00 48 0b 00 00 00 00  00 00 48 0b 00 00 00 00  |..H.......H.....|
00000140  33 80 b4 00 00 00 0c 00  b0 00 00 00 50 00 00 00  |3...........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  06 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 70 00 00 00 00 00 00  08 60 00 00 00 00 00 00  |.p.......`......|
00000180  08 60 00 00 00 00 00 00  31 01 ff ff 0b 31 06 3b  |.`......1....1.;|
00000190  30 04 00 08 80 fa ff ff  ff ff ff ff 00 00 00 00  |0...............|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 f0 88 07 80 fa cc 24  |1..............$|
00000200
Unknown BootLoader on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by kaytrance on 2012-09-14
Correct me if I am wrong but since you have 2 HDD, the boot order will be SDA, and then SDB. It means that you would probably need to install boot loader in the SDA.

---

### Post by b2580x on 2012-09-14
I installed ubuntu on SDB I don't know where bootloader was installed. Is it possible ubuntu's bootloader installed on SDB and my bootloader looks only SDA?

---

### Post by oldfred on 2012-09-14
If you change BIOS to boot sdb, Ubuntu should boot. At top of bootinfoscript it shows the MBR and which boot loader is installed.  You should also have a one time boot key (f12 on my system) to boot once and choose a different hard drive to test if you want.

You also tried to create more than 4 partitions in Windows on sda. Ubuntu will not be able to read those partitions as they were converted from basic to dynamic. Microsoft is using dynamic partitions rather than the extended partition with logical partitions when creating more than the 4 primary partitions that MBR allows.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion (updated version may not be free??)
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by kaytrance on 2012-09-14
> **b2580x said:**
> I installed ubuntu on SDB I don't know where bootloader was installed. Is it possible ubuntu's bootloader installed on SDB and my bootloader looks only SDA?
Well, the option where to put the boot loader can be reached when you choose how to partition your drive(s) during install. Did you choose automatic partition of free space or manual?
Also, check out [this info]("https://help.ubuntu.com/12.04/installation-guide/i386/module-details.html#di-make-bootable"), maybe you will find some answers there.

---

### Post by b2580x on 2012-09-14
@oldfred I accessed my boot menu but shows only First drive and cd/dvdrom boot.Not showing second drive.I should look your other suggestions later.I am a little confused about partition :)

@kaytrance I chose free space.

Followed [this]("http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/") article before installation

---

### Post by kaytrance on 2012-09-14
> **b2580x said:**
> 
@kaytrance I chose free space.

Then, I believe, you can [do this]("http://ubuntuforums.org/showthread.php?t=224351"). The idea is to reinstall grub loader to SDA.
EDIT. The guide you have followed suggests you have 1 HDD. In that case everything will work just fine since grub will be installed in it's mba, overwriting the one that windows have put there.
EDIT 2. On [this]("http://www.liberiangeek.net/wp-content/uploads/2012/04/dualboot_windows_precise_7_thumb.png") picture from the guide you linked you can see in the bottom of it "device for bootloader installation". In your case you need also to leave it to /dev/sda.

---

### Post by b2580x on 2012-09-14
> **kaytrance said:**
> Then, I believe, you can [do this]("http://ubuntuforums.org/showthread.php?t=224351"). The idea is to reinstall grub loader to SDA.
EDIT. The guide you have followed suggests you have 1 HDD. In that case everything will work just fine since grub will be installed in it's mba, overwriting the one that windows have put there.
EDIT 2. On [this]("http://www.liberiangeek.net/wp-content/uploads/2012/04/dualboot_windows_precise_7_thumb.png") picture from the guide you linked you can see in the bottom of it "device for bootloader installation". In your case you need also to leave it to /dev/sda.

@kaytrance Thank you for your interest I solved the issue by reinstalling ubuntu but this time choosing bootloader installation on sda like you showed that picture. I must have chosen sdb while installing it to second drive :-?

On startup now grub loader appears and allow me to choose ubuntu or windows 7.Thanks again.

---

