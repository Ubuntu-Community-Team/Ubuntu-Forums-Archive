---
title: "grub : add OS entry"
date: 2011-05-13
forum: General Help
---

### Post by enimeizoo on 2011-05-13
Hello,
I juste installed freeBSD on my sda3 partition, but grub doesn't detect it, even after update-grub.
What do I do to add a new entry for it in grub?
Thanks in advance.

(edit) some info that might help :
sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc4fa8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       23724   189026006    7  HPFS/NTFS
/dev/sda3           27400       60801   268301565   a5  FreeBSD
/dev/sda4           23725       27399    29519437+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad66528c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1265       48631   380475427+   7  HPFS/NTFS
/dev/sdb2           48632       60801    97755525   83  Linux
/dev/sdb3               1        1264    10153048+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Also, I just notice I don't have the grub package installed... But my system is actually booted by grub...
```

seb@seb-laptop:~$ grub --version
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
seb@seb-laptop:~$ grub2 --version
No command 'grub2' found, did you mean:
 Command 'grub' from package 'grub' (main)
grub2: command not found

```

---

### Post by Quackers on 2011-05-13
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by enimeizoo on 2011-05-13
Here is the info you asked for.
Thanks for your help.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   381,126,059   378,052,012   7 HPFS/NTFS
/dev/sda3         440,164,935   976,768,064   536,603,130  a5 FreeBSD
/dev/sda4         381,126,060   440,164,934    59,038,875  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          20,306,160   781,257,014   760,950,855   7 HPFS/NTFS
/dev/sdb2         781,257,015   976,768,064   195,511,050  83 Linux
/dev/sdb3                  63    20,306,159    20,306,097  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B8026ED9026E9C5E                       ntfs       WinRE                         
/dev/sda2        444E70A84E709500                       ntfs       Vista                         
/dev/sda3                                               ufs                                      
/dev/sda4        44f8f9c9-9a54-4d42-9b56-d874119d3822   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8CB601CA10D70666                       ntfs                                     
/dev/sdb2        0532184f-11e0-4ca4-b038-4b0c80a45a2b   ext4                                     
/dev/sdb3        547b6da4-67a2-44c5-8a18-b2489f496da0   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /home                    ext4       (rw)
/dev/sda2        /home/seb/Vista          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
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
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.36' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.36 root=/dev/sda4 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.36 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.36 ...'
    linux    /boot/vmlinuz-2.6.36 root=/dev/sda4 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44f8f9c9-9a54-4d42-9b56-d874119d3822
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 444e70a84e709500
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda4 :
UUID=44f8f9c9-9a54-4d42-9b56-d874119d3822    /    ext4    errors=remount-ro    0    1

#Entry for /dev/sdb2 :
UUID=0532184f-11e0-4ca4-b038-4b0c80a45a2b    /home    ext4    defaults    0    2

#Entry for /dev/sda2 :
UUID=444E70A84E709500    /home/seb/Vista    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=8CB601CA10D70666    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda3 :
UUID=f742aa6f-f253-4c26-a700-dd70b3144db2    none    swap    sw    0    0



=================== sda4: Location of files loaded by Grub: ===================


 197.5GB: boot/grub/core.img
 202.0GB: boot/grub/grub.cfg
 197.5GB: boot/initrd.img-2.6.32-21-generic
 198.5GB: boot/initrd.img-2.6.32-24-generic
 198.9GB: boot/initrd.img-2.6.32-25-generic
 200.9GB: boot/initrd.img-2.6.32-29-generic
 198.0GB: boot/initrd.img-2.6.32-30-generic
 199.0GB: boot/initrd.img-2.6.32-31-generic
 197.4GB: boot/vmlinuz-2.6.32-21-generic
 198.3GB: boot/vmlinuz-2.6.32-24-generic
 198.5GB: boot/vmlinuz-2.6.32-25-generic
 198.6GB: boot/vmlinuz-2.6.32-29-generic
 199.0GB: boot/vmlinuz-2.6.32-30-generic
 198.1GB: boot/vmlinuz-2.6.32-31-generic
 198.7GB: boot/vmlinuz-2.6.36
 199.0GB: initrd.img
 198.0GB: initrd.img.old
 198.1GB: vmlinuz
 199.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea f0 ff  00 f0 bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200



```

---

### Post by Quackers on 2011-05-13
There is a problem with the freeBSD partition. It is not mounting
```
sda3: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by enimeizoo on 2011-05-13
Yes, I see that. But I just installed it with the dvd. The md5 sum was ok, and there was another integrity check during install. 
Besides, the install takes a long time, so if there was a solution to try before reinstalling it, it would be nice.

---

### Post by oldfred on 2011-05-13
The partition is probably ok, it is just Ubuntu/Linux does not have native ZFS drivers. You may need a boot partition for FreeBSD that Ubuntu can read, but I have no idea if even that works. Most suggest BSD on a separate drive.

Any current driver is beta so use at your own risk.
[http://www.howtoforge.com/native-zfs-on-ubuntu](http://www.howtoforge.com/native-zfs-on-ubuntu)

I had this old entry for 40_custom:
[http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)
menuentry "freebsd 8.0" {
    set root=(hd0,2,a)
    chainloader +1
}

Not sure if above example is for sda2 but I think so, you would need sda3.

---

### Post by enimeizoo on 2011-05-13
Ok, I added this in 40_custom
```

menuentry "FreeBSD"{
    insmod ufs2
    set root=(hd0,3)
    kfreebsd /boot/loader
    chainloader +1
}

```

I still have a problem, but that is inside BSD, so this one issue is solved, than you guys.

---

