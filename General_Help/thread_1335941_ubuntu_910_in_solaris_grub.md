---
title: "ubuntu 910 in solaris grub"
date: 2009-11-24
forum: General Help
---

### Post by evelin on 2009-11-24
hello, how do i add ubuntu 910 to solaris grub i have tried this but it doesnt work

in solaris in a terminal 

```
su

password

[B]gedit /rpool/boot/grub/menu.lst

title Ubuntu 9.10, kernel 2.6.31-14-generic
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
root (hd0,6)
search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda6 ro   quiet splash
initrd    /boot/initrd.img-2.6.31-14-generic
[/B]
```but it doesnt boot it says error 15

and i even tried this in solaris livecd

press c

```

rootnoverify (hd0,0)  
and  rootnoverify (hd0,1)  but with this 0,1 it gives me an error later
makeactive
chainloader +1
boot

```then restart but nothing, please help i miss ubuntu

---

### Post by namok on 2009-11-24
If the configuration file for solaris grub is 'menu.lst' it probably use Grub Legacy(the old one)(I do not know nothing about Solaris is only conjecture[IMG]http://www.google.pl/images/cleardot.gif[/IMG]). So code for Ubuntu should be (if yuo can use uuid):
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e82a2105-5d7c-44e4-ad0b-265a7d47aecb
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

```or without uuid:
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

```You can use```
chainloader +1
```command if grub is installed in PBR of partition.

---

### Post by evelin on 2009-11-24
> **namok said:**
> If the configuration file for solaris grub is 'menu.lst' it probably use Grub Legacy(the old one)(I do not know nothing about Solaris is only conjecture[IMG]http://www.google.pl/images/cleardot.gif[/IMG]). So code for Ubuntu should be (if yuo can use uuid):
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e82a2105-5d7c-44e4-ad0b-265a7d47aecb
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

```or without uuid:
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

```You can use```
chainloader +1
```command if grub is installed in PBR of partition.


it doesnt work i try all but i cant make ubuntu boot in solaris, is there a form to make it the otherway to add the grub of solaris to ubuntu, if there it is, how do i restore the grub of ubuntu and add the solaris grub to it

---

### Post by namok on 2009-11-24
[Follow this link]("http://ubuntuforums.org/showthread.php?t=1291280") and attach file RESULT.txt to the next post.

---

### Post by evelin on 2009-11-24
> **namok said:**
> [Follow this link]("http://ubuntuforums.org/showthread.php?t=1291280") and attach file RESULT.txt to the next post.
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 369864545 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: tipo de sistema de ficheros '' desconocido

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros, 390721968 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xa2bf227e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    31,262,489    31,262,427   7 HPFS/NTFS
/dev/sda2          31,262,490   369,864,494   338,602,005   f W95 Ext d (LBA)
/dev/sda5          31,262,553    35,616,104     4,353,552  82 Linux swap / Solaris
/dev/sda6          35,616,168   120,134,069    84,517,902  83 Linux
/dev/sda7         120,134,133   369,864,494   249,730,362  83 Linux
/dev/sda3    *    369,864,495   390,716,864    20,852,370  bf Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 2017 MB, 2017984000 bytes
63 cabezas, 62 sectores/pista, 1009 cilindros, 3941375 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x0004aaf0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,941,153     3,941,092   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="69511edc-5ba4-4531-b520-a8c8b57bf019" TYPE="ext3" 
/dev/sda1: UUID="1C388F2B388F02CE" TYPE="ntfs" 
/dev/sda5: UUID="5027146e-eac9-4baf-9982-fec0d93b7044" TYPE="swap" 
/dev/sda6: UUID="e82a2105-5d7c-44e4-ad0b-265a7d47aecb" TYPE="ext4" 
/dev/sda7: UUID="03a62293-547e-4b8c-ab30-76b1b880cb30" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="" UUID="6459-911E" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\windows="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e82a2105-5d7c-44e4-ad0b-265a7d47aecb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1c388f2b388f02ce
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e82a2105-5d7c-44e4-ad0b-265a7d47aecb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5027146e-eac9-4baf-9982-fec0d93b7044 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  18.2GB: boot/grub/grub.cfg
  18.2GB: boot/initrd.img-2.6.31-14-generic
  18.2GB: boot/initrd.img-2.6.31-15-generic
  18.2GB: boot/vmlinuz-2.6.31-14-generic
  18.2GB: boot/vmlinuz-2.6.31-15-generic
  18.2GB: initrd.img
  18.2GB: initrd.img.old
  18.2GB: vmlinuz
  18.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 04 4d 33 2e 30 fa fc  be 00 7c bf 00 06 8c c8  |..M3.0....|.....|
00000010  8e d0 89 f4 8e c0 8e d8  51 b9 00 01 f3 a5 59 e9  |........Q.....Y.|
00000020  00 8a fb b4 02 cd 16 24  03 3c 03 75 05 c6 06 61  |.......$.<.u...a|
00000030  07 01 bb be 07 b9 04 00  80 3f 80 74 0e 83 c3 10  |.........?.t....|
00000040  e2 f6 bd 75 07 b9 13 00  e9 e6 00 b4 00 cd 13 53  |...u...........S|
00000050  b4 41 bb aa 55 b9 00 00  cd 13 72 3f 81 fb 55 aa  |.A..U.....r?..U.|
00000060  75 39 f7 c1 01 00 74 33  bd a4 07 b9 03 00 e8 c8  |u9....t3........|
00000070  00 5b 53 b9 05 00 66 6a  00 66 ff 77 08 66 ff 36  |.[S...fj.f.w.f.6|
00000080  5c 07 6a 01 6a 10 b4 42  89 e6 cd 13 9f 83 c4 10  |\.j.j..B........|
00000090  9e 73 7b b4 00 cd 13 e2  dd eb 6b bd a7 07 b9 03  |.s{.......k.....|
000000a0  00 e8 95 00 5b 53 8a 16  60 07 b4 08 cd 13 73 08  |....[S..`.....s.|
000000b0  bd 62 07 b9 13 00 eb 79  88 c8 24 3f a2 59 07 fe  |.b.....y..$?.Y..|
000000c0  c6 f6 e6 a3 5a 07 8b 47  08 8b 57 0a f7 36 5a 07  |....Z..G..W..6Z.|
000000d0  89 c3 89 d0 f6 36 59 07  fe c4 30 c9 88 fd c1 e9  |.....6Y...0.....|
000000e0  02 80 e1 c0 08 e1 88 dd  88 c6 8a 16 60 07 c4 1e  |............`...|
000000f0  5c 07 be 05 00 b8 01 02  cd 13 73 12 b4 00 cd 13  |\.........s.....|
00000100  4e 83 fe 00 75 ef bd 88  07 b9 0e 00 eb 23 bb 00  |N...u........#..|
00000110  7c 81 bf fe 01 55 aa 74  08 bd 96 07 b9 0b 00 eb  ||....U.t........|
00000120  10 8a 16 60 07 5e 66 ff  16 5c 07 bd a1 07 b9 03  |...`.^f..\......|
00000130  00 bb 4f 00 e8 0c 00 cd  18 80 3e 61 07 00 74 18  |..O.......>a..t.|
00000140  bb 1f 00 60 b8 01 13 ba  00 17 cd 10 b0 07 b9 01  |...`............|
00000150  00 cd 10 b4 00 cd 16 61  c3 00 00 00 00 7c 00 00  |.......a.....|..|
00000160  80 00 43 61 6e 27 74 20  72 65 61 64 20 67 65 6f  |..Can't read geo|
00000170  6d 65 74 72 79 4e 6f 20  61 63 74 69 76 65 20 70  |metryNo active p|
00000180  61 72 74 69 74 69 6f 6e  43 61 6e 27 74 20 72 65  |artitionCan't re|
00000190  61 64 20 50 42 52 42 61  64 20 50 42 52 20 73 69  |ad PBRBad PBR si|
000001a0  67 21 21 21 4c 42 41 43  48 53 00 00 00 00 00 00  |g!!!LBACHS......|
000001b0  00 00 00 00 00 00 00 00  7e 22 bf a2 00 00 00 01  |........~"......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 db 06 dd 01 00 fe  |......?.........|
000001d0  ff ff 0f fe ff ff 1a 07  dd 01 15 a8 2e 14 80 fe  |................|
000001e0  ff ff bf fe ff ff 2f af  0b 16 92 2e 3e 01 00 00  |....../.....>...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by namok on 2009-11-24
Sorry but I do not understand your system. Perhaps it is because I do not know on Solaris.
What happens when you start the computer from the hard drive without the cd?
Do you know the startup program that runs your system? Can you include the configuration file?
Can you run windows XP? If so, in the same way it is possible to start Ubuntu.

---

### Post by evelin on 2009-11-24
> **namok said:**
> Sorry but I do not understand your system. Perhaps it is because I do not know on Solaris.
What happens when you start the computer from the hard drive without the cd?
Do you know the startup program that runs your system? Can you include the configuration file?
Can you run windows XP? If so, in the same way it is possible to start Ubuntu.

1.it shows me the grub of solaris
2.no, maybe its menu.lst
the grub shows me solaris and windows xp, but no ubuntu i followed a tutorial where i add in the solaris menu.lst ubuntu, but the tutorial was for 8.04 and below, anyway i tried it with ubuntu 910, but nothing

---

### Post by namok on 2009-11-26
You can start Ubuntu from solaris menu, but only then Ubuntu partition **is not ext4**.
```
title Ubuntu menu
root (hd0,5)
kernel /boot/grub/core.img
```In your situation it is possible to run ubuntu but starting with Solaris, you must create a separate partition (not ext4). From this partition you can[IMG]http://www.google.pl/images/cleardot.gif[/IMG] start Ubuntu.
I think that the easiest to start with Ubuntu and then start solaris. You can start solaris then same way as you start windows XP.

---

