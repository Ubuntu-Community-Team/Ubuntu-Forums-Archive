---
title: "After reinstalling Ubunutu 10.10 win7 not booting"
date: 2011-04-07
forum: General Help
---

### Post by argisti on 2011-04-07
Hi to all.
I had reinstalled ubuntu 10.10.
When opening computer grub menu load and i can boot ubuntu and windows 7 listed on grub but when i tried to boot show me a black screen and showing grub menu again. I can't open Windows.
Can anyone help me?

---

### Post by coffeecat on 2011-04-07
Hi, and welcome to the forum.

Boot up into Ubuntu and the go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags. You can use the # icon in the message toolbar for this.

The contents of RESULTS.txt will provide information about your system and hopefully from that we'll be able to see what's wrong and what's needed to fix it.

---

### Post by argisti on 2011-04-07
it's here. Thanks for help.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 301893603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   266,236,261   266,236,199   7 HPFS/NTFS
/dev/sda2         266,239,998   267,239,423       999,426   5 Extended
/dev/sda5         266,240,000   267,239,423       999,424  82 Linux swap / Solaris
/dev/sda3         267,241,275   312,576,704    45,335,430  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,766,975   976,764,928   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A8E75178E74FD0F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        cd217cf8-02d6-4358-be65-483302246696   ext3                                     
/dev/sda5        43c6093d-3639-4874-8089-b56ba7a3efe3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8EF2EAA6F2EA91AF                       ntfs       Yeni Birim                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Repair disc Windows 7 32-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
set locale_dir=($root)/boot/grub/locale
set lang=ku
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=cd217cf8-02d6-4358-be65-483302246696 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=cd217cf8-02d6-4358-be65-483302246696 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set cd217cf8-02d6-4358-be65-483302246696
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0a8e75178e74fd0f
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=43c6093d-3639-4874-8089-b56ba7a3efe3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 154.5GB: boot/grub/core.img
 154.6GB: boot/grub/grub.cfg
 154.6GB: boot/initrd.img-2.6.35-28-generic
 154.5GB: boot/vmlinuz-2.6.35-28-generic
 154.6GB: initrd.img
 154.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  35 b2 3f 76 68 eb ce f2  e9 bf 3b 12 3f f9 aa 0a  |5.?vh.....;.?...|
00000010  d3 8e 73 ba 6d b4 6a b8  f7 26 98 bf 51 73 b7 c3  |..s.m.j..&..Qs..|
00000020  bd ed f1 41 a8 cc ce a8  8f a7 07 92 e6 61 6a 95  |...A.........aj.|
00000030  cf 9a 59 cf 94 46 72 b3  67 ec dc a6 9e bd 7a e8  |..Y..Fr.g.....z.|
00000040  78 19 31 42 f3 d6 88 1b  6c d2 35 cd da 29 d2 0d  |x.1B....l.5..)..|
00000050  f3 64 6b 15 6b 05 a0 59  f9 45 a1 90 c8 21 62 c3  |.dk.k..Y.E...!b.|
00000060  db 02 b7 44 b3 07 8e fb  a7 aa 82 75 cf 50 23 40  |...D.......u.P#@|
00000070  ba 6b 4f 36 34 0e b9 00  0a d0 76 8d ed 1c 77 54  |.kO64.....v...wT|
00000080  b1 cb 08 31 26 82 4b 21  e2 57 23 b5 c5 04 86 59  |...1&.K!.W#....Y|
00000090  af 68 e5 0c f8 a6 f9 13  ed 87 d9 d1 13 33 a2 e6  |.h...........3..|
000000a0  bc d0 b2 01 5f 09 62 3f  60 10 90 20 dd 38 1e 65  |...._.b?`.. .8.e|
000000b0  8d 3e 9f c4 02 80 32 81  2c f5 a8 9b c8 b2 f2 9f  |.>....2.,.......|
000000c0  db 2c 01 09 98 1b 88 ae  ae 47 69 f5 a4 d2 01 f7  |.,.......Gi.....|
000000d0  4f 4a 30 a0 c7 30 c5 29  31 1c aa ed 08 4c 19 fd  |OJ0..0.)1....L..|
000000e0  f3 f9 17 e8 57 cf 6e b9  da a8 f0 bf 6d 54 4a 59  |....W.n.....mTJY|
000000f0  b5 9c 43 e8 e7 b0 ae 99  14 cc 6d 31 4d 47 ff 2b  |..C.......m1MG.+|
00000100  6a 0c 30 dc c9 5f 2e 91  f0 5f 9c cc 6d d6 f2 b9  |j.0.._..._..m...|
00000110  b0 34 a1 12 f1 7a cb 78  f2 d3 95 94 4c 5f 71 95  |.4...z.x....L_q.|
00000120  88 12 a8 a8 35 d2 54 15  87 78 a3 91 1b f0 38 e6  |....5.T..x....8.|
00000130  0a 9c d3 fc 28 56 d9 57  80 9c 0f 76 81 53 78 8f  |....(V.W...v.Sx.|
00000140  df 53 83 10 0f b7 69 b2  55 71 ab 0b 58 dd 20 bc  |.S....i.Uq..X. .|
00000150  9c 47 b2 7f 9c a9 aa ef  17 6e 96 7b 52 a9 72 64  |.G.......n.{R.rd|
00000160  46 f0 a3 96 bf 86 27 5c  b8 87 e4 02 a5 30 4f 93  |F.....'\.....0O.|
00000170  cf 4e 7a c5 5b 7f d7 5b  b7 a4 e3 ed ac 35 47 09  |.Nz.[..[.....5G.|
00000180  f0 0d d4 cd 75 fc 8a 5a  9e e7 ce e6 39 fe f8 af  |....u..Z....9...|
00000190  0c f1 c9 fd ac f3 89 ca  5c ae a2 56 58 68 c1 50  |........\..VXh.P|
000001a0  06 1e 2b 86 69 84 7b 60  cb c0 f2 0b f6 15 c0 36  |..+.i.{`.......6|
000001b0  dc 18 6c df 03 38 da 79  1f 39 a6 37 1d b9 00 fe  |..l..8.y.9.7....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 0f 00 00 00  |...........@....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by coffeecat on 2011-04-07
Hi

Here's the problem:

> **argisti said:**
> 
```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 301893603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe


```

Partition sda1 is your Windows C: partition, but some grub files have been written to its boot sector and they are interfering with the Windows boot files. Grub code should only appear in the mbr and the Ubuntu/Linux root partition.

Two alternative fixes. If you have a Windows 7 install DVD or Windows 7 repair CD, you can boot with this and go to a command prompt. Then run 'bootrec /FixBoot'. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

On no account run 'bootrec/ FixMbr'. That will only make things worse. If you do not have either of those discs you can download the ISO for the Windows 7 repair disc here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

The alternative is by using testdisk in Ubuntu. See here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Interesting comment in that link:

> or "bootrect /fixboot" from a Windows Vista/7 CD.  But in my experience testdisk works best in this situation.If the author of that wiki page is running "bootrect /fixboot" I'm not surprised testdisk works better. The command is "bootrec /fixboot". :wink:

Good luck!

---

### Post by argisti on 2011-04-07
Thanks!!
i have this cd but i don't have windows cd. I will try this and writing answer to here.

---

### Post by argisti on 2011-04-07
Yes it's work. I able to open windows. But i need to reinstall grub :):)
Thanks.

---

### Post by coffeecat on 2011-04-07
> **argisti said:**
> Yes it's work. I able to open windows. But i need to reinstall grub 

Grub was correctly installed, so I don't understand why you need to reinstall it. Do you need help with that?

---

