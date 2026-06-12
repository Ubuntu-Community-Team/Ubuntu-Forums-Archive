---
title: "Deleted WIndows Can't boot"
date: 2010-08-23
forum: General Help
---

### Post by mamamia88 on 2010-08-23
I had 2 separate harddrives in my laptop.  HD1 contained winodws 7 and HD2 contained ubuntu 10.04.  I formatted the windows 7 harddrive and removed it.  I then moved the ubuntu harddrive to HD1.  I want to use the old windows drive as an external harddrive.  The problem is I just get a black screen with blinking cursor and no grub menu whatsoever upon boot.  can some please help me fix this?

---

### Post by wilee-nilee on 2010-08-23
> **mamamia88 said:**
> I had 2 separate harddrives in my laptop.  HD1 contained windows 7 and HD2 contained ubuntu 10.04.  I formatted the windows 7 harddrive and removed it.  I then moved the ubuntu harddrive to HD1.  I want to use the old windows drive as an external harddrive.  The problem is I just get a black screen with blinking cursor and no grub menu whatsoever upon boot.  can some please help me fix this?

Post the boot script in my sig in code tags.

---

### Post by mamamia88 on 2010-08-23
how do i do that if i can't boot? to begin with?  using another computer right now.

---

### Post by Rubi1200 on 2010-08-23
If you have an Ubuntu CD use it to boot the computer (actually any live distro would do).

Make sure BIOS is set to boot from the CD/DVD drive.

Then, as posted above by wilee-nilee.

---

### Post by mamamia88 on 2010-08-23
allright will give it ago but where do i save the file to if i am running off live cd?  home folder on harddrive?

---

### Post by Rubi1200 on 2010-08-23
> **mamamia88 said:**
> allright will give it ago but where do i save the file to if i am running off live cd?  home folder on harddrive?
There are clear instructions in the link posted by wilee-nilee. The easiest place is simply on the Desktop of the LiveCD.

When you have the results, post it back here and please wrap the text with the # tag

 Paste the results in between the tags and then submit.

---

### Post by mamamia88 on 2010-08-23
I can't view the file properly on xp notepad so i will have to attach the text file

---

### Post by Rubi1200 on 2010-08-23
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     7,999,487     7,997,440  82 Linux swap / Solaris
/dev/sda2           8,001,534   234,440,703   226,439,170   5 Extended
/dev/sda5           8,001,536    47,998,975    39,997,440  83 Linux
/dev/sda6          48,001,024   234,440,703   186,439,680  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 504 MB, 504364544 bytes
4 heads, 8 sectors/track, 30783 cylinders, total 985087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              8       985,086       985,079   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e7a858a1-9f4e-49aa-b40a-88dca0a9de5c   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        85d30cbb-ffcf-4159-ba6c-82716657351f   ext4                                     
/dev/sda6        0e1342f8-d28d-4c64-934b-151ec7b70d55   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F8CF-8327                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/F8CF-8327         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/0e1342f8-d28d-4c64-934b-151ec7b70d55 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=85d30cbb-ffcf-4159-ba6c-82716657351f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=85d30cbb-ffcf-4159-ba6c-82716657351f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=85d30cbb-ffcf-4159-ba6c-82716657351f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=85d30cbb-ffcf-4159-ba6c-82716657351f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 85d30cbb-ffcf-4159-ba6c-82716657351f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 62c45f0fc45ee4b7
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
# / was on /dev/sdb5 during installation
UUID=85d30cbb-ffcf-4159-ba6c-82716657351f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=0e1342f8-d28d-4c64-934b-151ec7b70d55 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=e7a858a1-9f4e-49aa-b40a-88dca0a9de5c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  21.4GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  21.5GB: boot/initrd.img-2.6.32-21-generic
  21.7GB: boot/initrd.img-2.6.32-24-generic
  21.4GB: boot/vmlinuz-2.6.32-21-generic
  21.5GB: boot/vmlinuz-2.6.32-24-generic
  21.7GB: initrd.img
  21.5GB: initrd.img.old
  21.5GB: vmlinuz
  21.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c0 36 af f7 a2 35 c0 2e  a1 47 00 9a ce 98 19 05  |.6...5...G......|
00000010  3b 2f 12 e5 f7 bf ec 51  a5 ea 7d ff e8 8d e0 7c  |;/.....Q..}....||
00000020  3f fe c0 9b 5e f3 7e 11  54 7c 18 47 06 4b f0 62  |?...^.~.T|.G.K.b|
00000030  65 3d 8a 07 ea 55 e2 a1  f6 88 a3 c2 f5 20 dd f9  |e=...U....... ..|
00000040  70 3e 6c 00 e3 d5 3e 02  f4 bd 90 52 62 f8 0f 8b  |p>l...>....Rb...|
00000050  ff db 00 c1 50 04 8c f6  54 cd da dd c6 f1 82 08  |....P...T.......|
00000060  9e 7d 20 3c b4 00 e3 35  39 e0 60 57 52 46 8b 1a  |.} <...59.`WRF..|
00000070  e3 7b ca 2e 70 8f 1c c6  d4 60 04 ff 00 fe 2a 53  |.{..p....`....*S|
00000080  6f f6 64 5f f1 2b 0f a0  ab 24 ac c5 94 c6 92 96  |o.d_.+...$......|
00000090  1d 22 4f ec ad 45 e0 14  be e7 c6 8c 82 99 3a 74  |."O..E........:t|
000000a0  40 cb 92 7a 27 6f ff 57  bf 46 07 40 8b 0e 5c 74  |@..z'o.W.F.@..\t|
000000b0  4e 9f 07 81 30 3c 8f ff  78 1d 8c 97 06 16 af c5  |N...0<..x.......|
000000c0  92 05 09 e0 66 a0 e0 31  36 01 bf 2c ab e0 7d 20  |....f..16..,..} |
000000d0  f3 d8 0c 34 4c be e2 ff  4c 2d 5f cb 03 0f 3e 86  |...4L...L-_...>.|
000000e0  17 e7 e8 0f 4f 6c ad 03  22 a9 c5 80 e5 11 53 b5  |....Ol..".....S.|
000000f0  d4 ee a3 91 70 e6 75 c9  ec 79 40 88 23 c0 33 0b  |....p.u..y@.#.3.|
00000100  d6 54 05 80 b1 a0 32 aa  01 9f 8f 2d d0 33 0a 9c  |.T....2....-.3..|
00000110  99 53 62 2c c1 14 1e 3b  ff bf 03 0a 0b 70 14 e8  |.Sb,...;.....p..|
00000120  f8 36 03 06 06 7d da 23  27 49 d4 c0 fa 50 03 a8  |.6...}.#'I...P..|
00000130  f8 eb e0 c9 67 32 2c 3c  40 7e d1 de ab 05 3c 05  |....g2,<@~....<.|
00000140  5a 40 7c 5f fe fd 11 b1  01 e3 a0 07 42 c1 37 02  |Z@|_........B.7.|
00000150  b0 36 b8 33 25 c0 ca 41  0c 0e 36 db 33 65 57 12  |.6.3%..A..6.3eW.|
00000160  0f 26 de 2a 60 7d eb d2  f9 fe 03 01 54 b5 7b 76  |.&.*`}......T.{v|
00000170  2f 50 90 92 4f 98 0c 59  3c ab 7d 4b db fa 49 64  |/P..O..Y<.}K..Id|
00000180  a5 4d 35 f5 6b b7 2c 35  11 a9 52 b0 a8 5c 10 3d  |.M5.k.,5..R..\.=|
00000190  82 4a 7d d1 27 c5 a0 a6  1e 09 63 b5 79 c2 cd 85  |.J}.'.....c.y...|
000001a0  f4 6f 80 c3 24 0b de 10  2d 31 9c 05 13 43 b6 34  |.o..$...-1...C.4|
000001b0  41 10 44 96 92 2b 98 55  8a bc c0 19 c9 3a 00 12  |A.D..+.U.....:..|
000001c0  61 f2 83 fe ff ff 02 00  00 00 00 50 62 02 00 fe  |a..........Pb...|
000001d0  ff ff 05 fe ff ff 02 50  62 02 00 e0 1c 0b 00 00  |.......Pb.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by jocko on 2010-08-23
You had grub in the major boot record of your other hard drive, so when you removed it you also removed the boot loader.
You should be able to fix it by installing grub again. [Try this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

Edit: so just do what wilee-nilee says below...

---

### Post by wilee-nilee on 2010-08-23
**No boot loader is installed in the MBR of /dev/sda**
As of now it looks like you just need to reload grub2 from a live cd karmic or beyond.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Basically from a live cd run
```
sudo mount /dev/sda5 /mnt
```
then,
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
reboot and run 
```
sudo update-grub
```

---

### Post by mamamia88 on 2010-08-23
thanks alot guys works fine now with exception that it seems to take a lot longer too boot.  anyone know how to fix this?

---

### Post by wilee-nilee on 2010-08-24
> **mamamia88 said:**
> thanks alot guys works fine now with exception that it seems to take a lot longer too boot.  anyone know how to fix this?

You say it seems to take longer to boot, could you be more specific=how long.

---

