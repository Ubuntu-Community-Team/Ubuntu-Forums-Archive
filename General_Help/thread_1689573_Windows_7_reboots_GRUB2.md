---
title: "Windows 7 reboots GRUB2"
date: 2011-02-17
forum: General Help
---

### Post by Niterios on 2011-02-17
Recently, I installed Ubuntu 10.10 on my computer from a USB. I _did not_ use wubi to install ubuntu. The computer already had Windows 7 installed. According to gparted, Windows 7 is installed in sda1, linux swap space is in sda2. Then sda3 is shown as a drop down menu containing sda5, where linux is installed. A picture to show this is attached :D. sda4 is a recovery partition that came with the computer.

The problem is that Windows 7 sometimes boots, and sometimes it does not boot. Most of the times it does not. Ubuntu boots perfectly. The process to boot is the usual, turning on the computer, wait for grub to load. If I pick Windows, it goes to the splash screen (which is by the way not the usual windows 7 splash screen, it resembles more the vista splash screen, picture attached. I do not know the reason, and I have no idea if it has anything to do with the problem) About 80% of the time, it simply reboots a few seconds after the windows splash screen is shown. The reboot takes me back to the usual HP splash screen, then grub again. The other 20% of the time, it boots normally and works perfectly well.

Right after I installed ubuntu Windows was shown in grub as installed at sdb1. I updated grub and now it is shown as sda1. I already tried some grub custom entries for loading Windows differently, but they all present the same problem. Please do not discard a custom entry as a solution, as the source I used for these custom entries was not entirely trustable.

I also tried popping in the windows installation disk and trying a system repair, but apparently no errors were found.

Reinstalling grub using Ubuntu live cd (booted from a USB) did not work either...

Im a learning user, can handle most of the simple terminal work but mostly noobish, so please keep in mind that I will probably need full instructions for everything D:

Thanks in advance to everyone who posts here as this will help me keep linux and keep learning. I just cant live without windows yet because I need it for school (and starcraft 2 ;))

---

### Post by sikander3786 on 2011-02-17
Welcome to the forums :-)

Please boot Ubuntu and run and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Copy/paste all the text from your Results.txt. While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

You might need to do a startup repair with Windows 7 and then re-install Grub but let us see the output first.

---

### Post by Mark Phelps on 2011-02-17
Looks like you're mounting your Win7 OS partition.  As long as you continue to do that, you're going to continue to experience boot problems with Win7.

It's generally a BAD idea to mount Win7 or Vista OS partitions in Ubuntu.

If you want to share data, a better solution is to create a shared NTFS data partition.  That won't suffer from boot issues.

---

### Post by Niterios on 2011-02-17
So.. here are the contents you asked me for:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   466,040,831   466,038,784   7 HPFS/NTFS
/dev/sda2         568,440,832   584,824,831    16,384,000  82 Linux swap / Solaris
/dev/sda3         584,826,878   602,234,879    17,408,002   f W95 Ext d (LBA)
/dev/sda5         584,826,880   602,234,879    17,408,000  83 Linux
/dev/sda4         602,234,880   625,135,615    22,900,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3377330D045E96CF                       ntfs                                     
/dev/sda2        37553d6e-aff5-4fed-b665-11056e926c0f   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        C8B66794B6678234                       ntfs       RECOVERY                      
/dev/sda5        af885cbd-d36b-4610-9a8d-ff9b57c6a95b   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        F855-A6FB                              vfat       TRAINMAN                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/TRAINMAN          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=af885cbd-d36b-4610-9a8d-ff9b57c6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=af885cbd-d36b-4610-9a8d-ff9b57c6a95b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af885cbd-d36b-4610-9a8d-ff9b57c6a95b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af885cbd-d36b-4610-9a8d-ff9b57c6a95b ro single 
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
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af885cbd-d36b-4610-9a8d-ff9b57c6a95b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3377330d045e96cf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set c8b66794b6678234
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 1.0 (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,0)
      chainloader +1
}
menuentry "Windows 1.1 (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,1)
      chainloader +1
}
menuentry "Windows 1.2 (on /dev/sda1)" {
      insmod ntfs
      set root=(hd1,0)
      chainloader +1
}
menuentry "Windows 1.3 (on /dev/sda1)" {
      insmod ntfs
      set root=(hd1,1)
      chainloader +1
}
menuentry "Windows 2.0 (on /dev/sdb1)" {
      insmod ntfs
      set root=(hd0,0)
      chainloader +1
}
menuentry "Windows 2.1 (on /dev/sdb1)" {
      insmod ntfs
      set root=(hd0,1)
      chainloader +1
}
menuentry "Windows 2.2 (on /dev/sdb1)" {
      insmod ntfs
      set root=(hd1,0)
      chainloader +1
}
menuentry "Windows 2.3 (on /dev/sdb1)" {
      insmod ntfs
      set root=(hd1,1)
      chainloader +1
}
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
# / was on /dev/sdb5 during installation
UUID=af885cbd-d36b-4610-9a8d-ff9b57c6a95b /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=37553d6e-aff5-4fed-b665-11056e926c0f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 305.4GB: boot/grub/core.img
 301.8GB: boot/grub/grub.cfg
 305.4GB: boot/initrd.img-2.6.20
 305.5GB: boot/initrd.img-2.6.35-22-generic
 307.9GB: boot/initrd.img-2.6.35-25-generic
 305.5GB: boot/vmlinuz-2.6.35-22-generic
 305.5GB: boot/vmlinuz-2.6.35-25-generic
 307.9GB: initrd.img
 305.5GB: initrd.img.old
 305.5GB: vmlinuz
 305.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  a2 d8 07 7f 9e db 9a 3a  79 71 78 07 03 6a ae de  |.......:yqx..j..|
00000010  fa 8f 5c 4a 23 d8 f0 eb  ab 0b c7 63 f6 21 72 37  |..\J#......c.!r7|
00000020  e4 3c cb dc 14 c0 e8 09  06 57 5e 25 80 78 92 07  |.<.......W^%.x..|
00000030  95 44 e7 c2 0f e9 e1 f0  97 3e 01 74 f9 f0 a6 0c  |.D.......>.t....|
00000040  07 d4 0f ad 78 40 12 c0  ea b5 43 e6 75 e0 d5 52  |....x@....C.u..R|
00000050  bf 04 1f 84 32 ef 5e 0f  a7 69 80 61 f0 20 68 96  |....2.^..i.a. h.|
00000060  0c 5e 5f 67 4b 84 8f d5  44 2a 46 38 65 dd ad c9  |.^_gK...D*F8e...|
00000070  7f 9c fd 78 66 ab f4 e4  3a 32 b5 86 ac 34 34 a6  |...xf...:2...44.|
00000080  13 7e 93 a8 a7 57 0c 97  0a 46 4b d6 df 66 70 28  |.~...W...FK..fp(|
00000090  27 ae 49 fb 2f 52 e0 d2  b8 33 0a 76 ac f4 1f d1  |'.I./R...3.v....|
000000a0  d0 12 f8 3e 64 00 e1 9c  56 c2 73 fa 6a 19 4d 91  |...>d...V.s.j.M.|
000000b0  7f f3 e1 a1 c1 28 7f 41  08 b9 5a ea 2c 21 d3 82  |.....(.A..Z.,!..|
000000c0  57 e8 1c f3 2a 64 07 cb  ff ec 29 a6 5d f5 4a fe  |W...*d....).].J.|
000000d0  5d 40 f5 c5 7c 1d ad 19  78 37 84 a0 80 0d 83 f2  |]@..|...x7......|
000000e0  f5 7f aa 55 fc 45 ad e7  0d e0 b8 32 8c b8 f2 b8  |...U.E.....2....|
000000f0  8a 3a 0f 0e f5 b2 24 f9  2d 18 93 fe 94 41 73 d0  |.:....$.-....As.|
00000100  94 f8 66 af 01 8c 03 45  45 e0 a3 12 4b 81 80 c2  |..f....EE...K...|
00000110  80 55 9d 0a 25 1d 74 ea  4f a8 24 fc 3c 78 fa 7f  |.U..%.t.O.$.<x..|
00000120  d4 7b 87 a7 4f 88 84 07  04 6f 99 f6 cd a8 bb 16  |.{..O....o......|
00000130  7c 03 cc c8 ad 4a 6a 73  c0 78 4b d9 6c 3c f1 9f  ||....Jjs.xK.l<..|
00000140  2c 1a f8 96 c2 e2 f8 df  80 2e 66 7f bc 38 48 9e  |,.........f..8H.|
00000150  94 ca b2 e1 1f b8 d1 eb  23 06 c1 49 49 c2 9f 72  |........#..II..r|
00000160  e5 51 91 18 ab b5 53 3e  02 20 c2 ad c4 07 33 86  |.Q....S>. ....3.|
00000170  09 bd b7 4d 05 30 5c 05  ab 12 c1 9d 20 94 7c 03  |...M.0\..... .|.|
00000180  44 b0 60 b8 77 15 37 f5  04 6a bd 4e 97 88 e7 02  |D.`.w.7..j.N....|
00000190  9c 12 07 80 fe c4 1e 02  03 70 61 28 18 b8 03 c1  |.........pa(....|
000001a0  e0 20 3d a1 0c 21 50 60  3b f1 2d 58 32 98 91 e0  |. =..!P`;.-X2...|
000001b0  1e 0c ae 02 81 5f 95 01  73 ca 81 00 1a 89 00 fe  |....._..s.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a0 09 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```In any case, can anybody corroborate what Mark Phelps said? I guess I could handle myself with a storage partition. Would this actually solve the problem as soon as I stop mounting it? Even though I could handle myself without mounting it, its not a very convenient solution :/, would take it as a last resource tho.

---

### Post by oldfred on 2011-02-17
I agree with Mark  Phelps. You could mount the windows partition read only if you want, but writing into it can cause issues.

I created a separate NTFS shared partition with XP & Ubuntu where I keep my Firefox & Thunderbird profiles & pictures. When I first started with Ubuntu my wife would want to check email or Internet with links from Windows version. Rebooting to XP was a hassle as it took 5 minutes. I found just having one install of the profiles worked and has worked now for 4 years. I rarely use XP but still have my profiles in the shared partition.

---

### Post by Niterios on 2011-02-17
Does this happen to all the people that dual boot with Windows 7? Is it a documented bug? It seemd weird that after all the searching I did not find anything related to mounting the partition. :S

---

### Post by oldfred on 2011-02-18
Not all users, all the time. 

Not sure why, but several things we do know. Ubuntu shows all files, even those that windows hides to prevent you from doing something to them. Also if you hibernate in windows you will definitely have issues. Windows just does not like too many changes that it has not seen. Often a chkdsk will resolve it, but sometimes it is more.

Even in Windows I have  accidentally clicked on a folder and moved mouse just enough to drag folder to a new location. That kind of error can then destroy a system, unless you know exactly what you did and can reverse it.

---

### Post by Niterios on 2011-02-18
Okay so I'll stop booting it from now. The issue is just gonna fix itself over time?

---

### Post by Niterios on 2011-02-20
anyone?

---

### Post by oldfred on 2011-02-20
Did the windows chkdsk report any errors?

---

### Post by Niterios on 2011-02-20
I haven't run one lately. Ill run it and post the results. Is there any way to obtain a logfile after running it?

---

