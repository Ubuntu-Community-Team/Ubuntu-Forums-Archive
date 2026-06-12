---
title: "Partition messed up after resizing - need help with fsck.ext4."
date: 2011-12-17
forum: General Help
---

### Post by joshj70 on 2011-12-17
So I was trying to resize my partition with GParted and I accidentally resized the whole drive instead of just the ext4 partition that ubuntu was on and now it won't boot and when I do a fsck this is what I get

```
ubuntu@ubuntu:~$ sudo fsck.ext4 -v /dev/sda2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
```Here is my fdisk info

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f97cefe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           17203       30395   105956935+   5  Extended
/dev/sda5           17204       30023   102976650   83  Linux
/dev/sda6           30024       30395     2974720   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1        9546    76678213+   7  HPFS/NTFS
/dev/sdb3            9547        9730     1467393    5  Extended
/dev/sdb5            9547        9730     1467392   82  Linux swap / Solaris

Disk /dev/sdc: 2032 MB, 2032664576 bytes
16 heads, 24 sectors/track, 10338 cylinders
Units = cylinders of 384 * 512 = 196608 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9bc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           6       10336     1983488    b  W95 FAT32

```I was trying to manipulate /dev/sda2
Any advise?

---

### Post by coffeecat on 2011-12-17
You attempted a file-system check on your extended partition, which won't work. That's why you are getting that error. Extended partitions do not have filesystems; they simply serve as containers for logical partitions which have filesystems (if formatted). You need to do the fsck on sda5.

There are approximately 140GB unallocated on sda before the sda2 extended partition. Were you trying to enlarge your partitions into this space? Also - I presume your Ubuntu root partition is sda5. Is this correct?

It might be useful to see the output of the boot info script. Boot up the live (L)Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by joshj70 on 2011-12-17
Yes it is, I was trying to enlarge it, I originally had it split with Windows XP on the smaller half but I decided to install my little 80gb hard drive and use that for Windows and keep the 250 for Linux.

Sorry, I misread the partitions, the fsck for sda5 is
```
ubuntu@ubuntu:~$ sudo fsck.ext4 sda5
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: No such file or directory while trying to open sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```And here is the boot info script results
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 368840 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 2048.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2         276,366,193   488,280,063   211,913,871   5 Extended
/dev/sda5         276,366,195   482,319,494   205,953,300  83 Linux
/dev/sda6         482,330,624   488,280,063     5,949,440  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2    *             63   153,356,489   153,356,427   7 NTFS / exFAT / HPFS
/dev/sdb3         153,366,526   156,301,311     2,934,786   5 Extended
/dev/sdb5         153,366,528   156,301,311     2,934,784  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2032 MB, 2032664576 bytes
16 heads, 24 sectors/track, 10338 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     3,969,023     3,966,976   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        3d36c23a-127c-4332-8e37-c739e9fadca4   ext4       
/dev/sda6        414fa00b-44b2-4b77-965b-995a03b3cecd   swap       
/dev/sdb2        6E8874AD88747585                       ntfs       
/dev/sdb5        7da5b174-1db6-4861-8c09-d3c4fa4df74c   swap       
/dev/sdc1        00E0-5A82                              vfat       joshs 2gbmi

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
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
search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
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
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    echo    'Loading Linux 2.6.32-35-generic ...'
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=3d36c23a-127c-4332-8e37-c739e9fadca4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3d36c23a-127c-4332-8e37-c739e9fadca4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 6E8874AD88747585
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
# / was on /dev/sda1 during installation
UUID=f998adab-58aa-4f26-9a69-4895a4851525 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7da5b174-1db6-4861-8c09-d3c4fa4df74c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 131.836152554 = 141.557990912  boot/grub/core.img                             1
 159.896913052 = 171.688003072  boot/grub/grub.cfg                             1
 133.661172390 = 143.517591040  boot/initrd.img-2.6.32-33-generic              2
 133.614293575 = 143.467255296  boot/initrd.img-2.6.32-34-generic              1
 133.629918575 = 143.484032512  boot/initrd.img-2.6.32-35-generic              1
 133.601983547 = 143.454037504  boot/initrd.img-2.6.32-36-generic              2
 131.851815701 = 141.574809088  boot/vmlinuz-2.6.32-33-generic                 1
 131.861531734 = 141.585241600  boot/vmlinuz-2.6.32-34-generic                 1
 131.867394924 = 141.591537152  boot/vmlinuz-2.6.32-35-generic                 1
 131.855580807 = 141.578851840  boot/vmlinuz-2.6.32-36-generic                 1
 133.601983547 = 143.454037504  initrd.img                                     2
 133.629918575 = 143.484032512  initrd.img.old                                 1
 131.855580807 = 141.578851840  vmlinuz                                        1
 131.867394924 = 141.591537152  vmlinuz.old                                    1

================================ sdb2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             vesamenu.c32                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 vesamenu.c32                       :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  50 45 59 0a 46 53 80 ff  24 d6 9c 4c 69 9e 49 3f  |PEY.FS..$..Li.I?|
00000010  d6 ac f2 b4 35 77 7a ea  73 b1 a0 82 69 c7 16 87  |....5wz.s...i...|
00000020  0e f4 39 50 7a 2a bb 15  4d e8 ba 1b b3 dc bc 16  |..9Pz*..M.......|
00000030  1e 89 29 de 23 87 2e 61  dc 0b 3e 1f 7a 29 9a 37  |..).#..a..>.z).7|
00000040  12 69 3b 07 d4 83 be 60  45 e5 17 d0 66 34 66 84  |.i;....`E...f4f.|
00000050  90 5c 8c 5b 9b b3 af 2c  62 bd ab 94 31 7c 14 31  |.\.[...,b...1|.1|
00000060  b4 7d a7 0e 8b 13 8f 2d  cf 85 2d 5a 6d 7f 49 1b  |.}.....-..-Zm.I.|
00000070  18 5f 24 43 d5 6a fb 20  b3 4a 3a 99 4e fe fc 1c  |._$C.j. .J:.N...|
00000080  bd 4f b3 7d b6 32 45 95  e3 9b 20 25 eb a6 85 bc  |.O.}.2E... %....|
00000090  5d 46 84 d6 7a 3f 0f 3c  64 7b a1 30 6b 68 e7 7d  |]F..z?.<d{.0kh.}|
000000a0  d2 be bc f2 b3 95 55 b1  8a 06 f2 f5 f4 ce 87 63  |......U........c|
000000b0  d7 07 d6 02 9c 26 82 0a  e9 53 f6 05 4c 94 c6 48  |.....&...S..L..H|
000000c0  eb 92 87 d7 1a 35 19 e0  16 57 4a 79 8b 26 15 ba  |.....5...WJy.&..|
000000d0  de 6a e0 51 be a3 92 3d  a1 67 0d a8 6e 12 6b 93  |.j.Q...=.g..n.k.|
000000e0  06 bd 84 02 d7 5b c2 ca  25 d4 67 1c e1 1c d3 e5  |.....[..%.g.....|
000000f0  e0 57 50 2c 18 a2 a6 24  75 f5 76 5b 64 1c 20 72  |.WP,...$u.v[d. r|
00000100  ea 03 ce 83 f4 34 77 7e  2a fd bb 6e ce 97 7c ca  |.....4w~*..n..|.|
00000110  31 76 e6 4b 17 16 0f 83  ce cb e2 78 97 14 ed 32  |1v.K.......x...2|
00000120  9a 02 c4 8c f9 62 53 b7  76 13 4b 3f 61 68 49 02  |.....bS.v.K?ahI.|
00000130  ca cb 24 a3 cc 37 ca 72  9a a1 2a 8e 5b 2a 79 23  |..$..7.r..*.[*y#|
00000140  f3 df b2 8c 36 df 82 93  0c fd ce 87 20 65 a9 37  |....6....... e.7|
00000150  7e 0f e6 fb 62 90 b9 7e  ec ad 57 6d 43 d2 db 2b  |~...b..~..WmC..+|
00000160  d1 df e5 f5 9f 77 1a d5  e6 4d d4 ce fd d4 5f 36  |.....w...M...._6|
00000170  21 a2 5e c9 37 61 90 79  ba ee d8 6d 4b c9 62 75  |!.^.7a.y...mK.bu|
00000180  52 47 56 22 40 d4 7d 0e  c2 8e ac fc 49 33 c4 42  |RGV"@.}.....I3.B|
00000190  27 4e 8d 41 da 1e cd bc  76 40 03 fa 26 8e d8 1e  |'N.A....v@..&...|
000001a0  17 2d d1 6a 61 96 a5 bf  a0 f8 44 4a 84 65 7d 2b  |.-.ja.....DJ.e}+|
000001b0  16 bf f1 8e 57 d9 08 2f  4f 74 d2 f5 2f 80 00 fe  |....W../Ot../...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 2c 00 00 00  |............,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by coffeecat on 2011-12-17
The boot script results are probably encouraging in that the filesystem on sda5 is still readable, or at least the boot script was able to read the boot, kernel and /etc/fstab files on sda5. So, hopefully, the sda5 filesystem should be fixable.

To be honest, I don't have enough experience of fsck to be able to confidently advise you how to proceed with that. If you wish I can edit your thread title to include "need help with fsck.ext4" in order to attract the attention of someone better able to help. Let me know if you want that.

Or - if you can rescue your personal files with a live CD, it might be quicker and easier to reformat the whole of sda and re-install. Since you are wanting to resize your sda2 and sda5 partitions, you need to repair the sda5 filesystem before you resize, and resizing always carries the (small) risk of further filesystem corruption anyway

---

### Post by joshj70 on 2011-12-17
Yes that would be appreciated. I thought about that and I can rescue my things, but I have a lot of stuff installed that I would rather not get rid of, so a reinstall would be my last option. Is there a way I could backup everything as is and then reinstall and just restore over the fresh install?

---

### Post by coffeecat on 2011-12-17
> **joshj70 said:**
> Yes that would be appreciated.

Done!

> **joshj70 said:**
>  I thought about that and I can rescue my things, but I have a lot of stuff installed that I would rather not get rid of, so a reinstall would be my last option. Is there a way I could backup everything as is and then reinstall and just restore over the fresh install?

Using something like clonezilla would almost certainly clone the filesystem problem. You can backup the contents of your home folder to include hidden files and folders in order to backup your configurations but there is no easy or practical way that I know of to backup installed applications, apart from backing up the cached deb packages. And anyway, something in the filesystem is not being read - Ubuntu is not booting - and this may include stuff that you want to backup. I think you are right that repairing the filesystem is your first option.

---

### Post by joshj70 on 2011-12-17
I was afraid of that, thank you for your help though. I am going to try to back up a few things and hope for the best for now. Thanks again.

---

### Post by joshj70 on 2011-12-17
Alright I was able to fix it, I ran a fsck on /dev/sda5 and then I reinstalled grub and it booted just fine. Thanks for the help

---

