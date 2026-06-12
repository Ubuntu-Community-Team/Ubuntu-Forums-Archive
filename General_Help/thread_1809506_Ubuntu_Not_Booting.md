---
title: "Ubuntu Not Booting"
date: 2011-07-21
forum: General Help
---

### Post by Skid420 on 2011-07-21
So I just got a new custom build and my problem is I can't get Ubuntu to boot at all.
I'm using two identical WD Caviar Blue 500gb drives.
I can boot windows off one, but cannot boot ubuntu from the other.
It just hangs after the bios screen saying loading os.

Any idea how to fix this?

Edit: I can get onto ubuntu using a boot disc, boot to disc then use the disc to boot the hdd. But i cannot boot the hdd directly

---

### Post by MG&amp;TL on 2011-07-21
Have you installed ubuntu, or can't you get your live cd to boot?

If ubuntu installed OK, then you've got a more serious problem, but live cds are temperamental, and often need multiple attempts.

---

### Post by Skid420 on 2011-07-21
> **MG&TL said:**
> Have you installed ubuntu, or can't you get your live cd to boot?

If ubuntu installed OK, then you've got a more serious problem, but live cds are temperamental, and often need multiple attempts.

yes i have ubuntu installed on the drive.

---

### Post by MG&amp;TL on 2011-07-21
Hmm. Try reinstalling ubuntu. Sorry, but that's the best offer I've got for you. :(

Feel free to hang around until someone more experienced turns up.

---

### Post by Skid420 on 2011-07-21
> **MG&TL said:**
> Hmm. Try reinstalling ubuntu. Sorry, but that's the best offer I've got for you. :(

Feel free to hang around until someone more experienced turns up.

Done it. was the first thing i did, assumed the install went wrong and re installed. still doesn't boot.

Although im on ubuntu now, i can get to it using a boot disc then using the disc to boot the hdd

---

### Post by MG&amp;TL on 2011-07-21
Have you done anything special with the BIOS, and did the installer run normally?

Running normally defined here: with pictures!

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Skid420 on 2011-07-21
> **MG&TL said:**
> Have you done anything special with the BIOS, and did the installer run normally?

Running normally defined here: with pictures!

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

no did nothing special with the bios, even tried resetting it, still no look.

And ive installed ubuntu a good few times, i know what the installer looks like, but thanks :)

---

### Post by westie457 on 2011-07-21
> **Skid420 said:**
> So I just got a new custom build and my problem is I can't get Ubuntu to boot at all.
I'm using two identical WD Caviar Blue 500gb drives.
I can boot windows off one, but cannot boot ubuntu from the other.
It just hangs after the bios screen saying loading os.

Any idea how to fix this?

Edit: I can get onto ubuntu using a boot disc, boot to disc then use the disc to boot the hdd. But i cannot boot the hdd directly

Could you post the output of bootinfoscript please.

Download and usage instructions are available here. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by MG&amp;TL on 2011-07-21
Sorry, I have to ask. :)

---

### Post by MG&amp;TL on 2011-07-21
I'll get back to you in the morning (8 hours time here). My brain's starting to fizzle.

---

### Post by Skid420 on 2011-07-21
> **MG&TL said:**
> I'll get back to you in the morning (8 hours time here). My brain's starting to fizzle.

thanks


> **westie457 said:**
> Could you post the output of bootinfoscript please.

Download and usage instructions are available here. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

ive attached the results file to this post

Edit: i also have another 250gb hdd with XP and ubuntu installed, please ignore this as its not being used. Its the ubuntu on the 500gb hdd that im having problems with

---

### Post by westie457 on 2011-07-21
>  => No boot loader is installed in the MBR of /dev/sdc

Unless I am mistaken the above is the cause of the problem.

Personally I am not 100% sure of the commands to get grub to boot from sdc. Do not panic as I am sure someone will be along soon who knows the answer.

When you did the installation did you allow grub to do a default installation or did you do something different?

---

### Post by Skid420 on 2011-07-21
> **westie457 said:**
> Unless I am mistaken the above is the cause of the problem.

Personally I am not 100% sure of the commands to get grub to boot from sdc. Do not panic as I am sure someone will be along soon who knows the answer.

When you did the installation did you allow grub to do a default installation or did you do something different?

i left it as default, but i did uninstall grub and reinstall it, a few minutes before i ran that script

---

### Post by westie457 on 2011-07-21
Take a look at this recent thread. It may give you a solution.

[http://ubuntuforums.org/showthread.php?p=11062363](http://ubuntuforums.org/showthread.php?p=11062363)

It revolves around a similar problem to yours.

---

### Post by Skid420 on 2011-07-21
> **westie457 said:**
> Take a look at this recent thread. It may give you a solution.

[http://ubuntuforums.org/showthread.php?p=11062363](http://ubuntuforums.org/showthread.php?p=11062363)

It revolves around a similar problem to yours.

not exactly what im looking for. my problem is that the hdd does not boot, it just hangs at the bios screen. that thread is for someone who has xp and ubuntu installed on the same hdd and cannot access the grub menu

---

### Post by westie457 on 2011-07-21
The point I was trying to get across here was about grub and how to get some of it onto sdc so the drive will boot. That thread also had this link in. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

A how-to on purging and reinstalling grub. It has saved my hair (not so much now) and finger nails in the past.

---

### Post by Skid420 on 2011-07-21
> **westie457 said:**
> The point I was trying to get across here was about grub and how to get some of it onto sdc so the drive will boot. That thread also had this link in. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

A how-to on purging and reinstalling grub. It has saved my hair (not so much now) and finger nails in the past.

i will try it soon and get back to.
although i really dont think grub is the problem. i have another hdd (from my laptop) with windows 7 and ubuntu on it and when i put it into my desktop it seems to boot up fine

---

### Post by westie457 on 2011-07-21
Referring back to your bootinfoscript> Device           Mount_Point              Type       Options

/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
[COLOR="Red"]/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)[/COLOR]
/dev/sr1         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

Highlighted is where I think the problem is.

Grub is not seeing the hard drive so it cannot start it.

---

### Post by Skid420 on 2011-07-21
> **westie457 said:**
> Referring back to your bootinfoscript
Highlighted is where I think the problem is.

Grub is not seeing the hard drive so it cannot start it.

and so how would i go about fixing it? 

thats weird consdidering grub is installed on the hdd it can't see :/

---

### Post by Hakunka-Matata on 2011-07-21
I'll try again..

---

### Post by Hakunka-Matata on 2011-07-21
Hope you don't mind, I've reposted your Results.txt file in code tags.  

Grub should be installed to the MBR of the drive that you choose as your boot drive in BIOS.
example: sda, sdb, ........

It appears Grub is not installed on any MBR.  Not sda, sdb, or sdc.

Gateway 'diagnostics likely' are installed on the MBR of sda, 
Windows on the MBR of sdb
and no bootloader on the MBR of sdc.

Grub should not be installed to any partition, ex: sda1, sdb5, etc.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    11,486,474    11,486,412  12 Compaq diagnostics
/dev/sda2    *     11,486,475   206,707,035   195,220,561   7 NTFS / exFAT / HPFS
/dev/sda3         206,708,734   488,396,799   281,688,066   5 Extended
/dev/sda5         206,708,736   476,872,703   270,163,968  83 Linux
/dev/sda6         476,874,752   488,396,799    11,522,048  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   976,771,071   976,564,224   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   943,964,159   943,962,112  83 Linux
/dev/sdc2         943,966,206   976,771,071    32,804,866   5 Extended
/dev/sdc5         943,966,208   976,771,071    32,804,864  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        423B-2BDF                              vfat       
/dev/sda2        9E2470A924708655                       ntfs       Partition_1
/dev/sda5        5a643a69-210f-49f1-94d9-226d43a941b1   ext4       
/dev/sda6        8bc03524-ab34-43bd-89ae-8fe7bc5e874d   swap       
/dev/sdb1        BE02B6D602B692BF                       ntfs       System Reserved
/dev/sdb2        A852BBA052BB7224                       ntfs       
/dev/sdc1        c35ab1c5-a674-4867-993d-4da76b6d4bfb   ext4       
/dev/sdc5        194535ae-b6bf-44e9-9835-5788bbdfe8e3   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINNT="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a643a69-210f-49f1-94d9-226d43a941b1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a643a69-210f-49f1-94d9-226d43a941b1 ro single 
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
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 5a643a69-210f-49f1-94d9-226d43a941b1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c35ab1c5-a674-4867-993d-4da76b6d4bfb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=c35ab1c5-a674-4867-993d-4da76b6d4bfb ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c35ab1c5-a674-4867-993d-4da76b6d4bfb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=c35ab1c5-a674-4867-993d-4da76b6d4bfb ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Windows NT/2000/XP (on /dev/sdg1)" {
    insmod part_msdos
    insmod fat
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdg2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e2470a924708655
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdg5 during installation
UUID=5a643a69-210f-49f1-94d9-226d43a941b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdg6 during installation
UUID=8bc03524-ab34-43bd-89ae-8fe7bc5e874d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 124.700248718 = 133.895872512  boot/grub/core.img                             1
 156.703277588 = 168.258863104  boot/grub/grub.cfg                             1
  98.972549438 = 106.270965760  boot/initrd.img-2.6.35-22-generic              2
 124.698715210 = 133.894225920  boot/vmlinuz-2.6.35-22-generic                 1
  98.972549438 = 106.270965760  initrd.img                                     2
 124.698715210 = 133.894225920  vmlinuz                                        1

========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  cc 44 af 00 bc 2b 00 00  00 00 00 00 02 00 00 00  |.D...+..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 2b 3b 42 20  20 20 20 20 20 20 20 20  |..).+;B         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  cc 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 53 54 4c 44 52 20 20  |.f..f.F..STLDR  |
000001b0  20 20 20 20 0d 0a 49 6e  76 61 6c 69 64 20 53 79  |    ..Invalid Sy|
000001c0  73 74 65 6d 20 44 69 73  6b 20 6f 72 0d 0a 44 69  |stem Disk or..Di|
000001d0  73 6b 20 49 2f 4f 20 65  72 72 6f 72 0d 0a 50 72  |sk I/O error..Pr|
000001e0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 73  |ess a key to res|
000001f0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 55 aa  |tart..........U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

/home/andreas/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")


```

---

### Post by Skid420 on 2011-07-21
so your saying grub is not installed??

---

### Post by Hakunka-Matata on 2011-07-21
Yes, that's correct.  Here's an excellent ubuntu help article on how to fix it.  

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Skid420 on 2011-07-21
> **Hakunka-Matata said:**
> Yes, that's correct.  Here's an excellent ubuntu help article on how to fix it.  

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

i have tried boot repair gui, still no luck. 
ill try some other methods in the morning. (its 3am here)

---

### Post by Hakunka-Matata on 2011-07-21
I was thinking it's quite late in Ireland, are you related to Darren Clarke?  Great game he shot

You'll get if fixed,

---

### Post by Skid420 on 2011-07-21
> **Hakunka-Matata said:**
> I was thinking it's quite late in Ireland, are you related to Darren Clarke?  Great game he shot

You'll get if fixed,

thanks for the help :) 

and darren clarke, i had to google him to find out who he was, so um no I'm not related hahah

---

### Post by Hakunka-Matata on 2011-07-21
boot_info_script file output from a working multi-boot Ubuntu - XP machine.  Created while running Ubuntu 10.10 OS.  

Notice the very first section, how it differs from your RESULTS.txt file.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,915,434    81,915,372  83 Linux
/dev/sda2          81,915,902   152,188,927    70,273,026   5 Extended
/dev/sda5         148,066,304   152,188,927     4,122,624  82 Linux swap / Solaris
/dev/sda6          81,915,904   148,066,303    66,150,400  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87   ext3       
/dev/sda5        6709c2c9-a0a2-4108-8a69-0b46fb72b44c   swap       
/dev/sda6        5eda9f40-29d9-4749-bb23-08f936004417   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        13

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
color cyan/red white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Chainload into GRUB 2
root        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=97752ae5-079a-4e22-9d8e-cf246323fde7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.289165020 = 1.384230400    boot/grub/core.img                             2
   1.629607677 = 1.749777920    boot/grub/menu.lst                             1
   1.304835796 = 1.401056768    boot/grub/stage2                               2
   1.272918224 = 1.366785536    boot/initrd.img-2.6.28-14-generic              3
   1.288535595 = 1.383554560    boot/initrd.img-2.6.28-16-generic              3
   1.343852520 = 1.442950656    boot/initrd.img-2.6.31-15-generic              4
   1.377364635 = 1.478934016    boot/initrd.img-2.6.31-20-generic              4
   1.273005962 = 1.366879744    boot/initrd.img-2.6.31-21-generic              7
   1.747390270 = 1.876246016    boot/initrd.img-2.6.31-22-generic             103
   1.354861736 = 1.454771712    boot/vmlinuz-2.6.28-14-generic                 2
   1.323607922 = 1.421213184    boot/vmlinuz-2.6.28-16-generic                 2
   1.300540447 = 1.396444672    boot/vmlinuz-2.6.31-15-generic                 2
   1.255626202 = 1.348218368    boot/vmlinuz-2.6.31-20-generic                 2
   1.308475018 = 1.404964352    boot/vmlinuz-2.6.31-21-generic                 2
  16.515140057 = 17.732996608   boot/vmlinuz-2.6.31-22-generic                 2
   1.747390270 = 1.876246016    initrd.img                                    103
   1.273005962 = 1.366879744    initrd.img.old                                 7
  16.515140057 = 17.732996608   vmlinuz                                        2
   1.308475018 = 1.404964352    vmlinuz.old                                    2

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    echo    'Loading Linux 2.6.35-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5eda9f40-29d9-4749-bb23-08f936004417 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5eda9f40-29d9-4749-bb23-08f936004417
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=77ce9b4c-c692-4aab-ad7f-20fe5ae54c87 ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77ce9b4c-c692-4aab-ad7f-20fe5ae54c87
    linux /boot/memtest86+.bin 
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5eda9f40-29d9-4749-bb23-08f936004417 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6709c2c9-a0a2-4108-8a69-0b46fb72b44c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  61.199192047 = 65.712132096   boot/grub/core.img                             1
  54.469215393 = 58.485874688   boot/grub/grub.cfg                             1
  46.343978882 = 49.761468416   boot/initrd.img-2.6.35-22-generic-pae          1
  46.484611511 = 49.912471552   boot/initrd.img-2.6.35-28-generic-pae          1
  54.630859375 = 58.659438592   boot/initrd.img-2.6.35-30-generic-pae          2
  61.314666748 = 65.836122112   boot/vmlinuz-2.6.35-22-generic-pae             1
  61.318794250 = 65.840553984   boot/vmlinuz-2.6.35-28-generic-pae             1
  61.322925568 = 65.844989952   boot/vmlinuz-2.6.35-30-generic-pae             1
  54.630859375 = 58.659438592   initrd.img                                     2
  46.484611511 = 49.912471552   initrd.img.old                                 1
  61.322925568 = 65.844989952   vmlinuz                                        1
  61.318794250 = 65.840553984   vmlinuz.old                                    1


```

Good Luck

---

### Post by Skid420 on 2011-07-22
i got it fixed, for some reason grub would not install to the hard drive.
dont know why but i have it installed now.
thanks to everyone for the help

---

### Post by Hakunka-Matata on 2011-07-23
That's good, glad you got it going.  Would you mind marking your thread [solved]?  [COLOR=Red]Thread Tools[COLOR=Black], upper right-hand side

Thanks
[/COLOR][/COLOR]

---

### Post by Skid420 on 2011-07-24
> **Hakunka-Matata said:**
> That's good, glad you got it going.  Would you mind marking your thread [solved]?  [COLOR=Red]Thread Tools[COLOR=Black], upper right-hand side

Thanks
[/COLOR][/COLOR]

thanks, was wondering where that option was

---

