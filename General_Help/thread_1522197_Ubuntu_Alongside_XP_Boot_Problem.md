---
title: "Ubuntu Alongside XP Boot Problem"
date: 2010-07-01
forum: General Help
---

### Post by ExpL0it0R on 2010-07-01
Hi all ubuntu fans.. x)

I've installed ubuntu alongside my XP. It worked fine, as it had done previously..

But i had problems with my XP, as it does sometimes...

And reinstalled it..

But although i expect to see Ubuntu in the boot screen, no boot screens open, and i automatically logon to XP. How can i solve this?

---

### Post by wilee-nilee on 2010-07-01
Welcome to the forums.;)

Post the bootscript in my signature in code tags as described, and we can look at the master boot record and more parts of the system to see if it is just a reload of grub into the mbr and loading of the Ubuntu partition, that is needed.

---

### Post by Don1500 on 2010-07-01
> **ExpL0it0R said:**
> [B]Hi all ubuntu fans.. x)

I've installed ubuntu alongside my XP. It worked fine, as it had done previously..

But i had problems with my XP, as it does sometimes...

And reinstalled it..

But as i expect to see Ubuntu in the boot screen, no boot screens open, and i automatically logon to XP. How can i solve this?
[/B]

If you load Windows AFTER you load UBUNTU it overwrites the MBR and grub is gone.
Open UBUNTU using the LIVE CD and go here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by ExpL0it0R on 2010-07-02
> **wilee-nilee said:**
> Welcome to the forums.;)

Post the bootscript in my signature in code tags as described, and we can look at the master boot record and more parts of the system to see if it is just a reload of grub into the mbr and loading of the Ubuntu partition, that is needed.


Thx for your advice, here is the result of the info script;

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
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

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,466,810   143,347,994   122,881,185   7 HPFS/NTFS
/dev/sda3         143,348,056   308,576,519   165,228,464   f W95 Ext d (LBA)
/dev/sda5         143,348,058   266,229,179   122,881,122   7 HPFS/NTFS
/dev/sda6         266,229,243   308,576,519    42,347,277  83 Linux
/dev/sda4         308,576,520   312,560,639     3,984,120  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 990 MB, 990904320 bytes
252 heads, 60 sectors/track, 32 cylinders, total 483840 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             60       483,839       483,780   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86649FEAE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        6C28B38C28B353B4                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        bc21ee94-334c-4aba-906a-cad975aae0ba   swap                                     
/dev/sda5        FC70390E7038D15E                       ntfs                                     
/dev/sda6        0df58908-4478-4b8f-9448-b0ccf9d75980   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4CC4-CFE1                              vfat       3012                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/3012              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
set locale_dir=($root)/boot/grub/locale
set lang=tr
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
menuentry 'Ubuntu, Linux 2.6.32-22-generic ile' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0df58908-4478-4b8f-9448-b0ccf9d75980 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, Linux 2.6.32-22-generic ile (kurtarma kipi)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    echo    'Linux Yükleniyor 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0df58908-4478-4b8f-9448-b0ccf9d75980 ro single 
    echo    'Ba&#351;lang&#305;ç ramdiski yükleniyor...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, Linux 2.6.32-21-generic ile' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0df58908-4478-4b8f-9448-b0ccf9d75980 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, Linux 2.6.32-21-generic ile (kurtarma kipi)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    echo    'Linux Yükleniyor 2.6.32-21-generic...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0df58908-4478-4b8f-9448-b0ccf9d75980 ro single 
    echo    'Ba&#351;lang&#305;ç ramdiski yükleniyor...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0df58908-4478-4b8f-9448-b0ccf9d75980
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 86649feae49bed2a
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set ae44d79344d75d21
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=bc21ee94-334c-4aba-906a-cad975aae0ba none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 147.3GB: boot/grub/core.img
 147.4GB: boot/grub/grub.cfg
 147.3GB: boot/initrd.img-2.6.32-21-generic
 147.4GB: boot/initrd.img-2.6.32-22-generic
 147.3GB: boot/vmlinuz-2.6.32-21-generic
 147.3GB: boot/vmlinuz-2.6.32-22-generic
 147.4GB: initrd.img
 147.3GB: initrd.img.old
 147.3GB: vmlinuz
 147.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4f 32 f2 6d 18 07 e1 3c  2d 79 a2 1f f2 2a 43 d9  |O2.m...<-y...*C.|
00000010  3a 25 f0 87 a0 bd d1 88  d7 36 e1 c1 df fd fd 13  |:%.......6......|
00000020  01 e4 ff 3b 77 d1 9d 04  e5 78 5f f7 85 e9 44 72  |...;w....x_...Dr|
00000030  be a0 56 1b 33 47 22 ca  c3 4d 5d 9f 55 b2 84 0b  |..V.3G"..M].U...|
00000040  04 53 7f 4c 8e 69 10 6e  73 7b 96 64 6d 23 1f 10  |.S.L.i.ns{.dm#..|
00000050  b5 b7 36 d2 5d ca 87 f8  74 7a 63 30 1f f9 0f fb  |..6.]...tzc0....|
00000060  22 dc cd 0b 05 cd c4 b3  93 ed e1 70 fc 81 b5 ee  |"..........p....|
00000070  ba 85 79 f7 18 93 96 72  1f 58 7f f3 af 4a af 15  |..y....r.X...J..|
00000080  a2 f5 2d 5b 1b ae 49 c4  f2 18 ff 95 9a 58 5c 4d  |..-[..I......X\M|
00000090  0c 32 79 77 e9 9d a0 fb  6c aa be b0 12 f1 6b fc  |.2yw....l.....k.|
000000a0  f2 8b 51 a5 0c fa 01 9e  db 4d 3b 10 0f d0 57 06  |..Q......M;...W.|
000000b0  98 bd 04 9b b1 b1 ee 8d  13 a0 87 ae 7d 16 1a 31  |............}..1|
000000c0  42 54 e2 9f 5e e0 86 27  23 5c 18 2f 2c 30 43 1c  |BT..^..'#\./,0C.|
000000d0  d0 7e 44 bb 14 fa 1a d6  77 c5 f4 35 23 7f b1 34  |.~D.....w..5#..4|
000000e0  ff a4 1b 1f 7d df 64 ab  30 c1 dc c2 b0 21 99 9d  |....}.d.0....!..|
000000f0  46 36 e2 c1 91 9c e2 76  d1 49 5c 61 3f 78 10 74  |F6.....v.I\a?x.t|
00000100  0e 9b 72 ea 56 82 8e e1  ee 09 6e 8f 81 d8 84 4d  |..r.V.....n....M|
00000110  74 e4 57 82 3f c1 af ac  18 87 78 ec 8b eb 0c 2d  |t.W.?.....x....-|
00000120  6c 8b 3a 84 f5 1a 62 80  5d 9f 52 30 ab af de f6  |l.:...b.].R0....|
00000130  5e 99 69 3b e9 ce e1 f3  a8 ea 76 51 25 ee ec 5b  |^.i;......vQ%..[|
00000140  6e 81 7c dd 99 91 fd 3a  e0 c9 8f f5 85 ce 90 f7  |n.|....:........|
00000150  7f f8 7a 98 06 79 5e 63  ee b2 bf 83 9f eb 51 4e  |..z..y^c......QN|
00000160  f8 f8 2a aa 45 8f fc 37  ec 19 41 eb 30 a5 29 e1  |..*.E..7..A.0.).|
00000170  8d 51 44 15 4c 5f b7 c5  43 9e f2 61 ef c4 0c ac  |.QD.L_..C..a....|
00000180  bf 23 d1 3d 7d 90 a7 9c  90 74 ec 28 42 e7 67 a9  |.#.=}....t.(B.g.|
00000190  f2 94 7f 28 db 41 6a 3f  8b 09 f7 41 bc eb 76 f1  |...(.Aj?...A..v.|
000001a0  60 78 0a e2 fd 8f 3e a9  55 fb a0 e3 8c 63 ef 06  |`x....>.U....c..|
000001b0  bd 15 12 e1 ae d3 55 f6  6b 0d 85 c2 b7 bd 00 fe  |......U.k.......|
000001c0  ff ff 07 fe ff ff 02 00  00 00 62 04 53 07 00 fe  |..........b.S...|
000001d0  ff ff 05 fe ff ff 64 04  53 07 4c 2b 86 02 00 00  |......d.S.L+....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
**Btw; i've installed Ubuntu manually.. Can u check if there is a fault ? e.g Did i have to create a swap disk, if i did, what does it do ?**
> **Don1500 said:**
> If you load Windows AFTER you load UBUNTU it  overwrites the MBR and grub is gone.
Open UBUNTU using the LIVE CD and go here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


**Thx but it didnt work .. :\   I've tried to install Grub 2, but got an error at the first place.. Here it's;**

```
buntu@ubuntu:/$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-pc
E: Package grub2 has no installation candidate

```

---

### Post by ExpL0it0R on 2010-07-02
Thanks all of u to help i ve solved the problem but got another one. Now I cant see XP !!

---

### Post by Don1500 on 2010-07-02
If you have not yet put any data into the Ubuntu home folder (Your data, pictures, songs, stuff you don't want to lose) I suggest you just bite the bullet and reinstall Ubuntu. It will take about 45 minutes but your problems should be solved.

If you want you can reinstall Windows, too, but do that first, then Ubuntu.

---

### Post by wilee-nilee on 2010-07-02
Run the bootscript again it is hard to tell what you have done since the first time you have a attempt at a install after the script with a edit. You still have windows installed in the MBR of sda.
```
Windows is installed in the MBR of /dev/sda
```
And you have lilo install in sdb
```
Lilo is installed in the MBR of /dev/sdb
```

If your able to boot Ubuntu it is because of lilo probably. So as it is if you haven't reinstalled and you start your computer  what happens?

Your swap on the old script is sda4 you have one already.

---

