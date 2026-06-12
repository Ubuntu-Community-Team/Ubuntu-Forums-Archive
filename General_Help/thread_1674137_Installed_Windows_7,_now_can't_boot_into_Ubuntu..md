---
title: "Installed Windows 7, now can't boot into Ubuntu."
date: 2011-01-23
forum: General Help
---

### Post by garrett1415 on 2011-01-23
I have Ubuntu 10.10 64-bit installed on a large partititon, and I installed Windows 7 64 bit on an empty partition. Now, I don't get the GRUB menu that I normally should. Consequently, I can't seem to boot into Ubuntu.

Thanks,
Garrett

---

### Post by Verbeck on 2011-01-23
you'll need to reinstall grub since windows would've overwritten the mbr

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Gordonbp531 on 2011-01-23
See here for how to repair the Grub bootloader:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by garrett1415 on 2011-01-23
Neither method worked correctly. Same problem persists

---

### Post by Quackers on 2011-01-23
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by someusername on 2011-01-23
Verify that the partition that grub is on has the boot flag with "fdisk -l".
Verify that the BIOS has that disk as one that boots before that of the windows disk, or ignore this advice if they are on the same disk.
I did what you did a few days ago. You had to use the advanced install options (aka those that let you create partitions manually) with the Windows installer, if you wanted to save your ubuntu. Otherwise you might have overwritten it. Verify this is not the case by booting with a USB-drive with ubuntu/or cd, and mount your file system: verify the existance of the grub files.

---

### Post by garrett1415 on 2011-01-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 302303792 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   502,818,815   502,816,768  83 Linux
/dev/sda2    *    502,818,816   503,023,615       204,800   7 HPFS/NTFS
/dev/sda3         503,023,616   602,898,431    99,874,816   7 HPFS/NTFS
/dev/sda4         602,900,478   625,141,759    22,241,282   5 Extended
/dev/sda5         602,900,480   625,141,759    22,241,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e628086a-e0b6-4d68-ac29-fbd8bde44ff3   ext4                                     
/dev/sda2        0E06967406965C91                       ntfs       System Reserved               
/dev/sda3        7C2C9E362C9DEC00                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        37a3c586-985c-486e-9e19-6defeb957c67   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e628086a-e0b6-4d68-ac29-fbd8bde44ff3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e628086a-e0b6-4d68-ac29-fbd8bde44ff3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e628086a-e0b6-4d68-ac29-fbd8bde44ff3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e628086a-e0b6-4d68-ac29-fbd8bde44ff3 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e628086a-e0b6-4d68-ac29-fbd8bde44ff3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0e06967406965c91
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=37a3c586-985c-486e-9e19-6defeb957c67 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
 107.5GB: boot/grub/grub.cfg
  52.7GB: boot/initrd.img-2.6.35-22-generic
 120.9GB: boot/initrd.img-2.6.35-24-generic
 154.7GB: boot/vmlinuz-2.6.35-22-generic
 154.7GB: boot/vmlinuz-2.6.35-24-generic
 120.9GB: initrd.img
  52.7GB: initrd.img.old
 154.7GB: vmlinuz
 154.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  70 fb 30 b2 85 10 f1 5e  19 ef 2d 52 68 86 ec a2  |p.0....^..-Rh...|
00000010  f7 fd b0 0e 69 8b 65 46  ca f9 87 44 3c f5 3c fd  |....i.eF...D<.<.|
00000020  16 ef 35 75 4a c0 5a 10  ea 2f c4 07 44 ea 81 ce  |..5uJ.Z../..D...|
00000030  ae 6d 0f f1 d4 10 10 ed  f8 92 a4 99 20 64 22 71  |.m.......... d"q|
00000040  ca 73 da 8d bd 71 2f a3  38 43 60 89 04 0d 96 06  |.s...q/.8C`.....|
00000050  84 25 d5 26 03 d2 57 ec  8a c9 aa bb 1d 2d ac 96  |.%.&..W......-..|
00000060  03 a0 54 86 fd 9f 2c b9  76 82 65 95 39 16 d7 7a  |..T...,.v.e.9..z|
00000070  dc e6 bd 4c 83 23 93 3f  0c da 6a 56 71 01 53 a8  |...L.#.?..jVq.S.|
00000080  5b 24 3c de e7 29 ef 45  14 ec c8 ef e5 49 9e 16  |[$<..).E.....I..|
00000090  df aa 63 72 08 dd 66 fc  9e d6 0d 32 f5 fb 4e 48  |..cr..f....2..NH|
000000a0  80 86 70 e7 43 2d 95 5d  ee 3b 6c a3 e5 7c 38 02  |..p.C-.].;l..|8.|
000000b0  dd 64 36 8d 3e fc 1f a3  00 3e bc 97 8d c8 8c ed  |.d6.>....>......|
000000c0  a6 bc 4b e1 1d b4 4c f4  4c 5f 6d 1c fd 78 9e 51  |..K...L.L_m..x.Q|
000000d0  c0 80 67 a2 3f d6 6c a6  c1 c8 76 03 87 2a 9d e2  |..g.?.l...v..*..|
000000e0  1d 56 2d 58 04 4a 08 f4  2e c9 61 07 50 55 33 03  |.V-X.J....a.PU3.|
000000f0  5f d1 27 7e 32 e8 0f 9b  79 4e bd bf 39 6c a1 dd  |_.'~2...yN..9l..|
00000100  63 c3 f8 7a 7c ba 64 fe  f7 bb 7b c3 b9 90 3d ca  |c..z|.d...{...=.|
00000110  69 69 a0 de 2c 3c a0 1b  6a 55 17 27 01 f9 cd 35  |ii..,<..jU.'...5|
00000120  98 ab 6c ab 0c 5d 6b f2  36 b9 7e 1d 3f bd 9f d7  |..l..]k.6.~.?...|
00000130  7d 36 7d d1 d4 97 fa 03  a8 a0 27 d9 5c a0 05 5f  |}6}.......'.\.._|
00000140  76 82 22 a7 0b 0c ff 2a  93 d7 90 c5 39 aa df 73  |v."....*....9..s|
00000150  ad 1d 4e 49 42 c4 80 44  21 f0 df 6a 3c d8 7f be  |..NIB..D!..j<...|
00000160  f5 d2 22 04 07 10 ac 24  93 29 cd b5 2d e3 5d db  |.."....$.)..-.].|
00000170  76 8f 11 30 ee 26 2c ad  24 c8 5b 90 e8 e4 86 5f  |v..0.&,.$.[...._|
00000180  06 0d f2 ac f4 23 79 6a  45 99 ae e9 0d a1 cb f8  |.....#yjE.......|
00000190  6e 9a 5a 86 26 b6 21 e8  26 d5 e8 3c b7 2c d1 f7  |n.Z.&.!.&..<.,..|
000001a0  23 63 40 19 56 f0 12 fa  9b 56 ee 32 3a d7 3f b7  |#c@.V....V.2:.?.|
000001b0  36 dc 31 f6 27 f0 a5 14  f8 d3 3b dd 6f f9 00 fe  |6.1.'.....;.o...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 53 01 00 00  |...........`S...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sandy8925 on 2011-01-23
You need to reinstall GRUB.

Here's the best resource(imo) for GRUB - 

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

See the link about reinstalling GRUB from LiveCD/USB: [http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

This will reinstall GRUB so that you can boot both Ubuntu and Windows 7. An awesome thing about GRUB 2 is that it automatically detects the OS installed, so you don't have to mess around with config files.

---

### Post by Quackers on 2011-01-23
Boot from the live cd and copy/paste these commands into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that reports no errors reboot. You may then see your grub menu with Windows listed. If not, Ubuntu may load directly. If Ubuntu loads please open a terminal and run ```
sudo update-grub
``` and watch to see that the Windows Loader is picked up as grub.cfg is run.

---

### Post by garrett1415 on 2011-01-23
That did the trick! Windows shows up and everything. Thanks so much, Quackers, and others!

---

### Post by Quackers on 2011-01-23
You're welcome :-)
Have fun!

---

