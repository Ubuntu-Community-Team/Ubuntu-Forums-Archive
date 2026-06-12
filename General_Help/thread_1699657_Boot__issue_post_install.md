---
title: "Boot  issue post install"
date: 2011-03-04
forum: General Help
---

### Post by Ilusionist2124 on 2011-03-04
i have a working Windows 7/xp dual boot prior and post to having installing ubuntu,  after installation i removed the usb thumb drive then preformed a reboot. when i got to boot loader where i normally pick Win7/Xp/Linux  and pick linux it then runs grub.
I get the boot loader screen, select Ubuntu 10.10


" Gave up waiting for root device. Common problems:
- boot args (Cal /proc/cmdline)
- check rootdelay= ( Did the system wait long enough?)

From booting back of live usb

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntdetect.com

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          8,064    15,874,047    15,865,984   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sdd2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdd5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1C08-0612                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        28D48C28D48BF67A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1ABE1BE3BE1BB66B                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        6e965f39-cccb-4fb6-825f-82497f0bb737   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        8d308edb-c482-4f8f-87d9-16b56141e6a2   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/6e965f39-cccb-4fb6-825f-82497f0bb737 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=6e965f39-cccb-4fb6-825f-82497f0bb737 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=6e965f39-cccb-4fb6-825f-82497f0bb737 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6e965f39-cccb-4fb6-825f-82497f0bb737
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1abe1be3be1bb66b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 28d48c28d48bf67a
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6e965f39-cccb-4fb6-825f-82497f0bb737 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8d308edb-c482-4f8f-87d9-16b56141e6a2 none            swap    sw              0       0

=================== sdd1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  75.3GB: boot/grub/grub.cfg
  58.4GB: boot/initrd.img-2.6.35-27-generic-pae
  30.2GB: boot/vmlinuz-2.6.35-27-generic-pae
  58.4GB: initrd.img
  30.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 18 f2 00 94 78 00 00  00 00 00 00 02 00 00 00  |.....x..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 12 06 08 1c 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 4c f1 00 00  66 ba 00 00 00 00 bb 00  |}.f.L...f.......|
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

Unknown BootLoader  on sdd2

00000000  00 00 00 01 e1 01 9e 03  00 ba 26 a2 7f 98 81 74  |..........&....t|
00000010  89 ee 99 35 d8 c4 f3 55  47 ae 5f 80 32 97 72 8e  |...5...UG._.2.r.|
00000020  d7 86 15 05 d8 cf 75 5f  9b aa 0c 61 d0 45 d8 a6  |......u_...a.E..|
00000030  7e 10 eb 44 18 d5 36 7a  4a d7 0e 53 10 3f 00 8a  |~..D..6zJ..S.?..|
00000040  4e 98 65 90 03 0c 50 b3  0b d9 73 33 af 7d e8 c6  |N.e...P...s3.}..|
00000050  d0 f2 ec fe dd 2a 56 9d  be 9e a1 1f 7f 3e 4c b1  |.....*V......>L.|
00000060  fe b6 7d da 96 48 dd 00  3d 52 28 47 c9 b1 95 91  |..}..H..=R(G....|
00000070  7a 99 04 48 0b 60 cf 69  8a 2a e1 cb 19 37 47 b3  |z..H.`.i.*...7G.|
00000080  9e 66 07 af 6b bc 83 ea  f5 04 1c 18 e9 52 6e 98  |.f..k........Rn.|
00000090  86 c9 ec 64 c1 94 2c 57  c9 76 fe 73 62 01 0d bf  |...d..,W.v.sb...|
000000a0  62 09 99 92 eb a9 ff 21  1f 3a ea 4f 63 51 ed d5  |b......!.:.OcQ..|
000000b0  4c a7 39 c0 98 96 3b bd  7a 6d 0f 86 88 5d db 2a  |L.9...;.zm...].*|
000000c0  c2 5d 95 0c fc de a3 be  16 0d ed 57 e2 e7 88 d0  |.].........W....|
000000d0  9b 13 d1 76 13 a5 61 05  c2 7b b0 a4 8d 5d 74 ed  |...v..a..{...]t.|
000000e0  c3 5d 68 0a 88 9f de da  ab 71 44 ab bc d1 f5 f5  |.]h......qD.....|
000000f0  07 f3 64 79 63 47 2e 48  49 cf 9d 38 4c 03 39 94  |..dycG.HI..8L.9.|
00000100  5f d8 a0 72 00 0c c9 c0  46 ff e1 7c cd 5e c2 eb  |_..r....F..|.^..|
00000110  29 0a ff 27 ea 39 ae 28  85 a0 e1 14 1a 4e a7 4d  |)..'.9.(.....N.M|
00000120  a2 83 3a 8a 73 ca 99 5d  79 29 5a 76 7a e0 73 b1  |..:.s..]y)Zvz.s.|
00000130  91 ec 5b 3a a3 29 6d 20  61 e0 01 a1 73 82 30 8c  |..[:.)m a...s.0.|
00000140  0f f9 36 7a c1 49 45 67  2b 07 7e 88 c2 3b 12 bf  |..6z.IEg+.~..;..|
00000150  2a 7f dd b4 e9 02 02 74  cb d7 24 a8 f1 19 45 8d  |*......t..$...E.|
00000160  15 39 32 e9 9c f8 a7 5a  e8 ab 5e 42 e2 56 94 82  |.92....Z..^B.V..|
00000170  ce ae 8c 20 bb 00 6d 6e  2d be 32 6d 39 c4 f2 b2  |... ..mn-.2m9...|
00000180  2d 58 3b dc cd ac 44 c2  2c 47 ab e2 09 9a 7d 09  |-X;...D.,G....}.|
00000190  6a 0f 21 3e 6c 09 8f 4e  8a ce ab fb c4 87 eb 73  |j.!>l..N.......s|
000001a0  cc 5c 89 60 3a c4 a5 0c  fd 5e 7a 56 c8 d3 b7 36  |.\.`:....^zV...6|
000001b0  27 ed 66 fe 6f 8b ae 45  ea c1 48 b6 13 00 00 fe  |'.f.o..E..H.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


``` i tried  hitting e and changing (there was more before this)linux    /vmlinuz **root=/dev/sdd1** ro quiet splash
which kicked me back to same point saying it could not find it at sdd1

---

### Post by Ilusionist2124 on 2011-03-04
Solved my problem :)

---

