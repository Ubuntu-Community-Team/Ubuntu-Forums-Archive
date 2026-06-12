---
title: "Newbi - Ubuntu no boot after update"
date: 2011-02-04
forum: General Help
---

### Post by alleny87 on 2011-02-04
One day ubuntu popped up that updates where available, so i left it overnight to download and install. come morning it needed to restart. i restarted and nothing happens. Im running a toshiba tablet/laptop. and it shows the toshiba bios screen allowing me to select where i want to boot from by pressing F2 (cd/usb/HD/or network). but if i leave it alone like a normal boot, once it passes the bios screen it goes black i hear the hard drive spinning up and then it sounds as if power was cut and it begins to re boot back at the bios screen. tried loading a live cd but laptop freezes up at the ubuntu loading screen with the dots below the name.

any help would be appreciated.

i am running a dual boot setup with windows being the original factory install and i installed ubuntu 10.10 later. it has worked fine for me for months, till now.

---

### Post by alleny87 on 2011-02-04
these are my boot info script results
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

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
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   179,593,256   179,593,194   7 HPFS/NTFS
/dev/sda2         179,595,262   195,371,007    15,775,746   5 Extended
/dev/sda5         179,595,264   194,590,719    14,995,456  83 Linux
/dev/sda6         194,592,768   195,371,007       778,240  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b4eec79d-a001-6147-89a8-31dcb66cd3e9   ext2       casper-rw                     
/dev/loop2       e5e1a67e-8b6e-41e1-8514-453680a819be   ext4                                     
/dev/sda1        969482D99482BB6F                       ntfs       SQ004125P03                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        60617f43-00da-47ff-b95e-19ef37e87ae9   ext4                                     
/dev/sda6        99bd7961-ab8b-4be2-a762-68eb06e62d27   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1BE4-1814                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/60617f43-00da-47ff-b95e-19ef37e87ae9 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /forceresetreg 
C:\wubildr.mbr = "Ubuntu" 

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
search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=60617f43-00da-47ff-b95e-19ef37e87ae9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=60617f43-00da-47ff-b95e-19ef37e87ae9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=60617f43-00da-47ff-b95e-19ef37e87ae9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=60617f43-00da-47ff-b95e-19ef37e87ae9 ro single 
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
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 60617f43-00da-47ff-b95e-19ef37e87ae9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 969482d99482bb6f
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
UUID=60617f43-00da-47ff-b95e-19ef37e87ae9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=99bd7961-ab8b-4be2-a762-68eb06e62d27 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  96.8GB: boot/grub/core.img
  97.0GB: boot/grub/grub.cfg
  93.5GB: boot/initrd.img-2.6.35-22-generic
  95.9GB: boot/initrd.img-2.6.35-24-generic
  97.1GB: boot/vmlinuz-2.6.35-22-generic
  97.1GB: boot/vmlinuz-2.6.35-24-generic
  95.9GB: initrd.img
  93.5GB: initrd.img.old
  97.1GB: vmlinuz
  97.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  69 00 70 00 62 00 6f 00  61 00 72 00 64 00 44 00  |i.p.b.o.a.r.d.D.|
00000010  61 00 74 00 61 00 50 00  61 00 73 00 74 00 65 00  |a.t.a.P.a.s.t.e.|
00000020  61 00 62 00 6c 00 65 00  00 00 04 00 00 00 17 00  |a.b.l.e.........|
00000030  00 00 5f 00 62 00 75 00  69 00 6c 00 64 00 53 00  |.._.b.u.i.l.d.S.|
00000040  65 00 6c 00 65 00 63 00  74 00 69 00 6f 00 6e 00  |e.l.e.c.t.i.o.n.|
00000050  4d 00 65 00 74 00 61 00  64 00 61 00 74 00 61 00  |M.e.t.a.d.a.t.a.|
00000060  00 00 04 00 00 00 13 00  00 00 5f 00 73 00 68 00  |.........._.s.h.|
00000070  6f 00 75 00 6c 00 64 00  53 00 68 00 6f 00 77 00  |o.u.l.d.S.h.o.w.|
00000080  4d 00 65 00 6e 00 75 00  49 00 74 00 65 00 6d 00  |M.e.n.u.I.t.e.m.|
00000090  00 00 04 00 00 00 10 00  00 00 62 00 75 00 69 00  |..........b.u.i.|
000000a0  6c 00 64 00 43 00 6f 00  6e 00 74 00 65 00 78 00  |l.d.C.o.n.t.e.x.|
000000b0  74 00 4d 00 65 00 6e 00  75 00 04 00 00 00 09 00  |t.M.e.n.u.......|
000000c0  00 00 73 00 65 00 6c 00  65 00 63 00 74 00 41 00  |..s.e.l.e.c.t.A.|
000000d0  6c 00 6c 00 00 00 04 00  00 00 22 00 00 00 73 00  |l.l......."...s.|
000000e0  68 00 6f 00 77 00 42 00  6f 00 6f 00 6b 00 6d 00  |h.o.w.B.o.o.k.m.|
000000f0  61 00 72 00 6b 00 50 00  72 00 6f 00 70 00 65 00  |a.r.k.P.r.o.p.e.|
00000100  72 00 74 00 69 00 65 00  73 00 46 00 6f 00 72 00  |r.t.i.e.s.F.o.r.|
00000110  53 00 65 00 6c 00 65 00  63 00 74 00 69 00 6f 00  |S.e.l.e.c.t.i.o.|
00000120  6e 00 04 00 00 00 13 00  00 00 5f 00 61 00 73 00  |n........._.a.s.|
00000130  73 00 65 00 72 00 74 00  55 00 52 00 49 00 4e 00  |s.e.r.t.U.R.I.N.|
00000140  6f 00 74 00 53 00 74 00  72 00 69 00 6e 00 67 00  |o.t.S.t.r.i.n.g.|
00000150  00 00 04 00 00 00 16 00  00 00 72 00 65 00 6c 00  |..........r.e.l.|
00000160  6f 00 61 00 64 00 53 00  65 00 6c 00 65 00 63 00  |o.a.d.S.e.l.e.c.|
00000170  74 00 65 00 64 00 4c 00  69 00 76 00 65 00 6d 00  |t.e.d.L.i.v.e.m.|
00000180  61 00 72 00 6b 00 04 00  00 00 1a 00 00 00 72 00  |a.r.k.........r.|
00000190  65 00 6c 00 6f 00 61 00  64 00 53 00 65 00 6c 00  |e.l.o.a.d.S.e.l.|
000001a0  65 00 63 00 74 00 65 00  64 00 4d 00 69 00 63 00  |e.c.t.e.d.M.i.c.|
000001b0  72 00 6f 00 73 00 75 00  6d 00 6d 00 61 00 00 fe  |r.o.s.u.m.m.a...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 e4 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d0  e4 00 00 e8 0b 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 95 3b 00 00  00 00 00 00 02 00 00 00  |..w..;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 14 18 e4 1b 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 4e 77 00 00  66 ba 00 00 00 00 bb 00  |}.f.Nw..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|a
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

### Post by lindsay7 on 2011-02-04
looks like you have or had a wubi installation and there is confusion with the type of file system sda1 has on it.

sorry but I do not know how to fix this.

this is what looks funny > => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by bcbc on 2011-02-05
Boot from the live CD again, hit the space bar as soon as you see the little keyboard icon at the bottom. This will give you an extended menu. Press F6, scroll to nomodeset, hit Enter, Esc, then select "Try without installing" and hit Enter to boot.
Hopefully that will get you to the desktop. Then try reinstalling grub:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by alleny87 on 2011-02-05
bcbc - thanks that worked i have my desktop back, but i cant access my windows partition thru ubuntu i get "Unable to mount 92gb file system" "Error mounting: mount:/dev/sda1: cant read superblock" any ideas? I love ubuntu, and it a great deal faster than windows, especiall since i only install what i need, but i need my windows as well i have some programs that i need on that side

---

### Post by bcbc on 2011-02-05
> **alleny87 said:**
> bcbc - thanks that worked i have my desktop back, but i cant access my windows partition thru ubuntu i get "Unable to mount 92gb file system" "Error mounting: mount:/dev/sda1: cant read superblock" any ideas? I love ubuntu, and it a great deal faster than windows, especiall since i only install what i need, but i need my windows as well i have some programs that i need on that side

So you can't mount the windows partition from Ubuntu. But can you boot windows from the Grub menu?

Try that, run check disk - make sure it's working and shutdown normally, then try again from Ubuntu. Everything looked OK from your bootinfoscript.

---

### Post by alleny87 on 2011-02-05
sorry no  windows wont boot from the grub menu, no loading screen nothing just black screen that says " A DISK READ ERROR OCCURRED PRESS CTRL ALT DEL TO RESTART"

---

### Post by alleny87 on 2011-02-05
i got this:
```
sudo ntfsfix /dev/sda1
[sudo] password for owner: 
Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.

```
after getting ubuntu back up i decided to do some research and i tried that, it was thru the synaptic packet manager, mine was pre installed, i still cant thank you enough for helping get at least this side back up, i thought this laptop was gonna need a new Hard Drive, or at worse case bricked.

---

### Post by alleny87 on 2011-02-05
on another forum somebody suggested "Hiren's Boot CD" ever heard of it?

---

### Post by bcbc on 2011-02-05
I'd let windows fix itself. Boot a repair CD and run chkdsk.

It's probably not a bad idea to backup what you can first. Note that you can copy /dev/sda1 even though you can't mount it - e.g. with "dd". And you can recover data from it as well, with e.g. photorec. So if you're looking at data loss that's important to have some insurance before trying to fix it (which could make things worse).

PS I've heard the name (Hiren's boot cd), but never had need to use it.

---

### Post by lindsay7 on 2011-02-05
I would try to fix your mrb, what i see is a problem in that area because of the wubi info that is in it.  Here is some info on doing this. If this works you should be able to boot into windows. I would then delete or clean up anything that has to do with Wubi. If you want to run Ubuntu do a true dual boot,

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by bcbc on 2011-02-05
Don't fixmbr. That will just remove the grub bootloader that you just installed. There is no Wubi in the MBR, Wubi boots through grub4dos. It's also not possible that the MBR can stop windows from booting - the bootloader just transfers control to the partition bootsector. It sounds like there is a problem with the ntfs master file table. Which would suggest that chkdsk is probably the way to go (or a starting point).

If in the course of repairing windows it happens that your reinstall the windows bootloader (i.e. fixmbr is run), just follow the same instructions earlier to get grub/ubuntu back once windows is fixed.

---

### Post by lindsay7 on 2011-02-05
bcbc,

this is why I thought wubi was installed.  Any idea why this would be in the boot files?

>  File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk


---

### Post by bcbc on 2011-02-05
> **lindsay7 said:**
> bcbc,

this is why I thought wubi was installed.  Any idea why this would be in the boot files?

Yes, you are absolutely correct there's definitely a wubi there. I suppose the OP installed Wubi first and then a proper dual boot afterwards. 

I was just saying that if Windows isn't booting, then fixmbr won't help it boot.

---

### Post by alleny87 on 2011-02-05
ok well i still have a problem because i have no window boot disc, this laptop came without one, and in order to get one i would have to order a 30 dollar disc from toshiba. so how could i go about running chkdsk without a windows boot disk?

---

### Post by lindsay7 on 2011-02-06
you could use the live ubuntu cd and run Gparted.  There is a check disk option in one of the menus.

---

### Post by lindsay7 on 2011-02-07
You could try to repair your mbr using this. Please read the support docs and download the software.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by bcbc on 2011-02-07
borrow someone else's xp disc?

or

[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair) (last topic)

But I'd try windows chkdsk first.

---

### Post by alleny87 on 2011-02-08
Well according to testdisk, both my main and backup master file tables are bad, and it cannot repair them. It repaired my backup boot sector, cuz the main was fine so now i have those fixed, but its the MFT thats bad any suggestions?

---

### Post by lindsay7 on 2011-02-08
I do not have any really good ideas. My experience on this forum tells me that after 18 or 19 posts the thread gets stale and people stop looking at it.  I would start a new post with as good a description of what your current problem is and hope you get some clean eyes on your situation. Hopefully you can get some new good advise.

---

### Post by bcbc on 2011-02-08
I would use [photorec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") to recover any important data you need.
Then I would phone a friend and borrow an xp disc and run chkdsk.
Then - if that doesn't work - I would reformat and reinstall.

---

