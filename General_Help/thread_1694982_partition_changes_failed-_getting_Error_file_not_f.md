---
title: "partition changes failed- getting Error: file not foud. grub rescue"
date: 2011-02-25
forum: General Help
---

### Post by davidtheduckfan on 2011-02-25
[COLOR=#000000][COLOR=#0000bb]Hi there, (i know nothing)

I running a dual boot of 10.4 and windows 7 and was trying to add a free disc space to one of the partitions using gparted and  the window 7 tool.
On restart I get this DOS-like message:

[/COLOR][/COLOR]```
  [COLOR=#000000][COLOR=#0000bb]Error[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]file not foud[/COLOR][COLOR=#007700].
[/COLOR][COLOR=#0000bb]grub rescue[/COLOR][COLOR=#007700]>  [/COLOR][/COLOR]
```From what I have gathered, from other posts I should 

1. Go here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
2. Reboot and run ubuntu from the live CD
3. Create a results.txt file

Then, by the grace of god, someone here knows how to interpret the results coach me toward a fix.
Here is the results data:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2    *        145,408    24,547,319    24,401,912   7 HPFS/NTFS
/dev/sda3          24,547,328   139,681,292   115,133,965   7 HPFS/NTFS
/dev/sda4         139,685,112   312,580,095   172,894,984   5 Extended
/dev/sda5         139,685,175   303,516,044   163,830,870  83 Linux
/dev/sda6         303,517,696   312,580,095     9,062,400  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 32.1 GB, 32128368640 bytes
14 heads, 11 sectors/track, 407472 cylinders, total 62750720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192    62,750,719    62,742,528   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D9-0A01                              vfat       DellUtility                   
/dev/sda2        88DA083DDA082A50                       ntfs       RECOVERY                      
/dev/sda3        CE06E2A606E28F31                       ntfs                                     
/dev/sda5        f9f88d97-260d-496b-ab88-cd24a2960145   ext4                                     
/dev/sda6        f5878397-2806-4669-abc6-35f7a2dbeddc   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        31EA-0735                              vfat       S_MATCH_H*/                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/S_MATCH_H*_       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/f9f88d97-260d-496b-ab88-cd24a2960145 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/CE06E2A606E28F31  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
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
search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f9f88d97-260d-496b-ab88-cd24a2960145 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f9f88d97-260d-496b-ab88-cd24a2960145
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 88da083dda082a50
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=f9f88d97-260d-496b-ab88-cd24a2960145 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f5878397-2806-4669-abc6-35f7a2dbeddc none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 106.0GB: boot/grub/core.img
 106.5GB: boot/grub/grub.cfg
 106.1GB: boot/initrd.img-2.6.32-21-generic
 106.4GB: boot/initrd.img-2.6.32-23-generic
 107.1GB: boot/initrd.img-2.6.32-28-generic
 106.0GB: boot/vmlinuz-2.6.32-21-generic
 106.4GB: boot/vmlinuz-2.6.32-23-generic
 107.0GB: boot/vmlinuz-2.6.32-28-generic
 107.1GB: initrd.img
 107.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  f2 08 51 fb df 8c fa 02  32 d0 5d 76 a0 d1 38 71  |..Q.....2.]v..8q|
00000010  0e ce ae ca e3 fe 2a 2d  3d 48 31 a9 65 eb 51 77  |......*-=H1.e.Qw|
00000020  9f 71 4f 31 c1 94 d0 0e  0d e5 d6 7e e7 f7 77 01  |.qO1.......~..w.|
00000030  ab 64 8c f1 82 4c 59 93  6a 6c 29 4e 65 fd 3c 47  |.d...LY.jl)Ne.<G|
00000040  7a 38 bc c8 c9 6c 8f 25  25 19 91 f3 33 05 65 91  |z8...l.%%...3.e.|
00000050  1d 6d e2 23 44 b3 01 ac  b6 c9 c0 cf d3 88 b2 94  |.m.#D...........|
00000060  c7 02 25 b2 4d 45 26 6a  b3 9a af 78 4d e1 11 49  |..%.ME&j...xM..I|
00000070  18 64 d1 ee c6 3b 27 1a  6a 78 52 e8 47 67 10 a3  |.d...;'.jxR.Gg..|
00000080  da 0b 38 76 93 14 77 3c  45 84 2c f8 91 88 57 6c  |..8v..w<E.,...Wl|
00000090  14 48 52 e5 5c d2 02 50  7b 09 72 85 34 67 6a fd  |.HR.\..P{.r.4gj.|
000000a0  2a b1 3a 30 f3 74 7b f8  e2 4f 91 cb dc c6 5f 41  |*.:0.t{..O...._A|
000000b0  6c 66 0e 11 4a f1 ea 00  ee 2d 01 8e 7e 3c f8 0a  |lf..J....-..~<..|
000000c0  03 0c 47 17 e7 29 ff 71  6c 0f 3c a1 66 0b 6a 21  |..G..).ql.<.f.j!|
000000d0  c4 d0 2b d8 d1 b7 7b 58  36 39 e0 0d 74 69 10 f3  |..+...{X69..ti..|
000000e0  a6 5a 3a d6 9b 1b 10 e2  5a 2d 5f 1a 17 2a 04 02  |.Z:.....Z-_..*..|
000000f0  69 ca 82 5c bc 7f 20 de  ed cd 56 36 19 b1 b5 70  |i..\.. ...V6...p|
00000100  88 7c 98 62 b1 1e 20 a3  81 5e b1 23 08 68 a4 01  |.|.b.. ..^.#.h..|
00000110  b0 c9 77 38 38 e4 c1 f6  f3 52 63 9f 56 3a 6d 3a  |..w88....Rc.V:m:|
00000120  30 f2 ff 62 e5 08 ee 98  8b 84 05 e2 60 de db bc  |0..b........`...|
00000130  0f 21 73 25 02 1f fe db  e7 36 93 f2 6f d2 fc 4e  |.!s%.....6..o..N|
00000140  4d cc fc 5c 38 4c 65 b1  84 94 d1 be 18 be 31 4e  |M..\8Le.......1N|
00000150  3a 48 ae 24 b3 20 9b 19  97 65 ab 63 66 4a b2 71  |:H.$. ...e.cfJ.q|
00000160  fd 14 f9 a2 6f 72 23 56  fc 18 85 f2 9d f9 dd 6f  |....or#V.......o|
00000170  5e 2c 9d 2b cb b9 af ec  db 9c 94 5b 32 86 83 62  |^,.+.......[2..b|
00000180  93 0a 59 07 49 b5 56 7e  5a 3e 63 b1 fa 98 a2 86  |..Y.I.V~Z>c.....|
00000190  27 4a b1 68 94 52 47 8e  1d 20 18 56 c0 15 92 68  |'J.h.RG.. .V...h|
000001a0  d4 e4 b0 ed 01 6d 13 a0  d7 a4 19 ab e4 f0 17 41  |.....m.........A|
000001b0  b6 6a 10 65 88 aa 44 01  f8 36 45 be 3e a7 00 fe  |.j.e..D..6E.>...|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 56 dc c3 09 00 fe  |......?...V.....|
000001d0  ff ff 05 fe ff ff 95 dc  c3 09 73 4e 8a 00 1f ba  |..........sN....|
000001e0  75 72 d6 c2 1f e9 18 a4  7c fc f0 d2 2d ad 67 6b  |ur......|...-.gk|
000001f0  04 97 79 1a 27 88 62 bc  8f bf f9 c8 85 9e 55 aa  |..y.'.b.......U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by seawolf167 on 2011-02-25
As far as I know the "Error: File not found" is telling you that upon boot the system cannot find /boot/grub which is interesting since the bootscript is telling you

```
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for /boot/grub
```

which is correct. Maybe someone else can see something I missed.

The solution for Grub not being found is to reinstall GRUB2

[Here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")are the reinstall instructions

Where your Ubuntu partition is located at 

```
/dev/sda5
```

Once you get your system booted into Ubuntu, you'll want to update grub to detect your other operating systems (i.e. Windows)

```
sudo update-grub
```

---

