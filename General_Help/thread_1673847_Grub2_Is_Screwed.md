---
title: "Grub2 Is Screwed"
date: 2011-01-23
forum: General Help
---

### Post by BloodXII on 2011-01-23
Hellos.

Well here is my problem which started from me being a idiot. I had installed ubuntu on a 25gb partiton and wanted to test out kubuntu. So I made a 20Gb partition and installed it to there. Turned out I didn't like it. My bios only lets me choose a harddrive not a partition to boot and since I installed Kubuntu it set it up so it would boot from it's partition. I didn't know that and just reformatted the kubuntu drive from ubuntu. Oh Noes, now when I boot off the drive with ubuntu on it, it gives me this error. 

error: no such device : a3d6c451-5ae0-454d-aed3-cc508f88825d

It does not show me the boot menu, it just says that. I can boot off my other harddrive (Which has windows Xp on it) just fine. I have purged and reinstalled grub to the messed up harddrive following this tutorial [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) to no avail. This is how my partition table looks:

/dev/sda1   ntfs            43.45gb      (win xp)
/dev/sda2   ntfs            68.36gb      (Storage)

/dev/sdb1   ntfs            00.10gb      (System reserved)
/dev/sdb2   ntfs            37.47gb      (Windows 7)
/dev/sdb3   ntfs            144.35gb    (Storage)
/dev/sdb4   extended
/dev/sdb6  linux swap   9.05gb        (swap area)
/dev/sdb7  ext4            18.62gb      (Slackware - used to be the kubuntu drive.)
/dev/sdb5  ext4            23.28gb      (Ubuntu 10.10)

I am guessing the bios is looking to the old kubuntu partition for where to find the grub and since that uuid no longer exists it can't boot grub. I think my course of action would be to either refomat the whole harddrive and restart from scratch which would be bloody annoying as I have been using the ubuntu and windows 7 partition for a while and my settings and applications would take a long time for me to re-set up or I could try to change the uuid of my ubuntu partition to the kubuntu number that pops up, but I have no idea how to do that and I can only find information in changing the uuid to a random number.

If you need any more information just ask.

Thanks in advance,
BloodXII

---

### Post by Quackers on 2011-01-23
When you were trying to purge-re-install grub, which partition did you mount?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by BloodXII on 2011-01-23
Volia!

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 473952960 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 13.1.0
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    91,127,807    91,125,760   7 HPFS/NTFS
/dev/sda2          91,127,808   234,485,759   143,357,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848    78,796,799    78,589,952   7 HPFS/NTFS
/dev/sdb3          78,796,800   381,531,174   302,734,375   7 HPFS/NTFS
/dev/sdb4         381,532,158   488,396,799   106,864,642   5 Extended
/dev/sdb5         439,570,432   488,396,799    48,826,368  83 Linux
/dev/sdb6         381,532,160   400,506,879    18,974,720  82 Linux swap / Solaris
/dev/sdb7         400,508,928   439,568,383    39,059,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DC4853C448539BD8                       ntfs       White Scars                   
/dev/sda2        1ADA924ADA9221D5                       ntfs       Night Lords                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BE2497042496BEB9                       ntfs       System Reserved               
/dev/sdb2        2284B3DC84B3B0A1                       ntfs       Space Wolves                  
/dev/sdb3        7C18E98718E9412E                       ntfs       Iron Warriors                 
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        da954e59-1bf2-4d18-86fe-42360260b769   ext4       Ultramarines                  
/dev/sdb6        a24ed4c1-e6a1-4a0b-bc6c-2fb84e422c6a   swap                                     
/dev/sdb7        45ab3449-2593-443b-9a38-8190783bba94   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=da954e59-1bf2-4d18-86fe-42360260b769 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=da954e59-1bf2-4d18-86fe-42360260b769 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=da954e59-1bf2-4d18-86fe-42360260b769 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=da954e59-1bf2-4d18-86fe-42360260b769 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set da954e59-1bf2-4d18-86fe-42360260b769
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dc4853c448539bd8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set be2497042496beb9
    chainloader +1
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 45ab3449-2593-443b-9a38-8190783bba94
    linux /boot/vmlinuz-generic-2.6.33.4 root=/dev/sdb7
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 45ab3449-2593-443b-9a38-8190783bba94
    linux /boot/vmlinuz-generic-smp-2.6.33.4-smp root=/dev/sdb7
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 45ab3449-2593-443b-9a38-8190783bba94
    linux /boot/vmlinuz-huge-2.6.33.4 root=/dev/sdb7
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 45ab3449-2593-443b-9a38-8190783bba94
    linux /boot/vmlinuz-huge-smp-2.6.33.4-smp root=/dev/sdb7
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb5 :
UUID=da954e59-1bf2-4d18-86fe-42360260b769    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb3 :
UUID=7C18E98718E9412E    /media/Blood\040Angels    ntfs-3g    defaults,nosuid,nodev,locale=en_AU.utf8    0    0
#Entry for /dev/sda2 :
UUID=1ADA924ADA9221D5    /media/Lords    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda1 :
UUID=DC4853C448539BD8    /media/Night    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sdb2 :
UUID=2284B3DC84B3B0A1    /media/Space_Wolves    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb1 :
UUID=BE2497042496BEB9    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
UUID=f14fd1ae-7c41-44ed-955a-a4822023ae44    none    swap    sw    0    0



=================== sdb5: Location of files loaded by Grub: ===================


 242.5GB: boot/grub/core.img
 247.4GB: boot/grub/grub.cfg
 242.6GB: boot/grub/stage2
 226.3GB: boot/initrd.img-2.6.35-22-generic
 248.8GB: boot/initrd.img-2.6.35-24-generic
 242.4GB: boot/vmlinuz-2.6.35-22-generic
 242.5GB: boot/vmlinuz-2.6.35-24-generic
 248.8GB: initrd.img
 226.3GB: initrd.img.old
 242.5GB: vmlinuz
 242.4GB: vmlinuz.old

=============================== sdb7/etc/fstab: ===============================

/dev/sdb7        /                ext4        defaults         1   1
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0

=================== sdb7: Location of files loaded by Grub: ===================


 222.3GB: boot/vmlinuz
 222.3GB: boot/vmlinuz-generic-2.6.33.4
 222.3GB: boot/vmlinuz-generic-smp-2.6.33.4-smp
 222.3GB: boot/vmlinuz-huge-2.6.33.4
 222.3GB: boot/vmlinuz-huge-smp-2.6.33.4-smp
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  9e f8 dc e1 d7 fc 5d 77  29 cd 31 42 dc 2c 03 60  |......]w).1B.,.`|
00000010  b8 69 b3 f2 39 a7 d7 8c  fc 4e cb 4f 8e 80 b1 73  |.i..9....N.O...s|
00000020  c3 d2 7b 78 d4 35 02 c4  ff 52 0a 74 3a 32 4a 2f  |..{x.5...R.t:2J/|
00000030  a7 3d 67 4c 17 38 0d a9  29 e6 a4 fd ee 9c 5e 89  |.=gL.8..).....^.|
00000040  39 9f 87 66 1d b4 e0 11  82 ac c4 9c 29 82 d4 e3  |9..f........)...|
00000050  ce 28 e0 0d 16 a5 f0 e7  51 f4 fd 77 01 88 0a 2d  |.(......Q..w...-|
00000060  a4 3f 8c 71 61 85 a3 a2  7c db dc ff 8f de de f1  |.?.qa...|.......|
00000070  ee fe 28 4d cf 17 4f 6d  de db be c5 bc 5a 4e 59  |..(M..Om.....ZNY|
00000080  b7 a2 70 cc 33 78 d1 a9  5e a8 02 5c 23 68 fb fc  |..p.3x..^..\#h..|
00000090  7d ce 4c d8 05 8f cf 90  ab 3e 04 50 2c c5 b5 ff  |}.L......>.P,...|
000000a0  5f c2 d1 b1 77 01 bf 7e  17 7c 6e 58 b0 57 7d ae  |_...w..~.|nX.W}.|
000000b0  f9 bb 56 5b 82 86 3f 0f  86 f3 e3 4f 4d 3d 80 6f  |..V[..?....OM=.o|
000000c0  80 da bb 62 93 e9 fa ce  11 26 a0 90 6b 25 9d 3b  |...b.....&..k%.;|
000000d0  61 1e 33 fd 5c 5c f0 c9  55 75 af 0d 82 fa 7a be  |a.3.\\..Uu....z.|
000000e0  0e b9 1f f3 ef 1b 20 06  d5 ca f4 e1 f9 15 ff 59  |...... ........Y|
000000f0  5d 1d 42 9e 3e 36 0c 19  09 48 13 05 03 e8 cc 1d  |].B.>6...H......|
00000100  35 a5 a1 7a a3 c1 98 1f  51 b3 6b 0c 9e 37 1d fa  |5..z....Q.k..7..|
00000110  a7 6b 72 79 f9 44 6b 1b  6e 28 c3 6c ab 98 c4 50  |.kry.Dk.n(.l...P|
00000120  a4 93 af d5 29 5f 55 53  4a 04 e8 a8 54 cc b8 0a  |....)_USJ...T...|
00000130  75 5d 83 c0 40 86 0c 01  c1 06 84 10 85 ef b3 ea  |u]..@...........|
00000140  36 0b c2 04 a4 e0 f0 10  21 83 02 00 42 03 df 12  |6.......!...B...|
00000150  c7 ca a0 42 54 3c b0 0e  45 60 61 b1 fa b9 fc e1  |...BT<..E`a.....|
00000160  7e 34 34 08 0c 4b 44 5e  e4 de 08 84 60 86 0c 6e  |~44..KD^....`..n|
00000170  0f a9 c1 1e 0c e1 f1 18  30 65 04 34 06 1c c6 19  |........0e.4....|
00000180  06 aa 31 3e 3e 94 be d0  1a db 3d 51 f3 95 f3 ae  |..1>>.....=Q....|
00000190  c3 18 27 f6 c6 a0 0c 1c  ba 76 72 3a 85 ed ef 1b  |..'......vr:....|
000001a0  3b 9e ee f8 fd e1 7d ef  1e 9b c3 18 25 5f 75 47  |;.....}.....%_uG|
000001b0  16 e7 8f 64 f7 51 55 86  4f 68 93 c4 ca f7 00 fe  |...d.QU.Oh......|
000001c0  ff ff 83 fe ff ff 02 98  75 03 00 08 e9 02 00 fe  |........u.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 88 21 01 00 00  |............!...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2011-01-23
I would say that you need to repair the mbr on the Windows XP drive (sda) with a Windows XP repair disc, as, at the moment grub2 is installed there and pointing to a partition that does not exist. There isn't even a Linux file system on that disc.

Then I would suggest that you follow the guide below to purge/re-install grub to the mbr of your second drive (sdb) as, at the moment it seems to have a mixture of grub legacy and grub2 installed. 
The partiton you need to mount is sdb5, and grub(2) needs to be installed to the mbr of sdb (not a partition, like sdb5).
You should use the chroot method from the live cd/usb detailed here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by BloodXII on 2011-01-23
i did that not an hour ago. the chroot method. on the mdr of sdb. it didnt work. It shouldn't matter if there is grub on the sda as i am booting from only the sdb. How can I change a partition uuid?

---

### Post by Quackers on 2011-01-23
If you purged and re-installed grub before you ran the boot script, something didn't work.

---

### Post by BloodXII on 2011-01-23
Gimme a minute.

EDIT: Fixed. Thankyou. I hadn't removed The grub legacy when i first purged. Thankyou.

---

### Post by Quackers on 2011-01-23
Excellent :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

---

