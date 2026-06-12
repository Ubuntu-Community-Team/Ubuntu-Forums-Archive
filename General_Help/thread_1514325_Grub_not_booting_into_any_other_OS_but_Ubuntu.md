---
title: "Grub not booting into any other OS but Ubuntu"
date: 2010-06-20
forum: General Help
---

### Post by Brii on 2010-06-20
I just installed Ubuntu 10.4

And when I click on Windows 7 in Grub, it just goes to a black screen with a blinking cursor...


Anyone know what's wrong?

---

### Post by wojox on 2010-06-20
Open a terminal and run

```
sudo update-grub
```

Have you looked here [https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows)

---

### Post by Brii on 2010-06-20
> **wojox said:**
> Open a terminal and run

```
sudo update-grub
```

Have you looked here [https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows)

The terminal command didn't work. I'm looking at that link you posted.

---

### Post by confused57 on 2010-06-20
Someone should be able to help you if you can post the output of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If grub2 is installed to the boot sector of your Windows 7 partition(which may be the case), here's a possible fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Brii on 2010-06-20
> **confused57 said:**
> Someone should be able to help you if you can post the output of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If grub2 is installed to the boot sector of your Windows 7 partition(which may be the case), here's a possible fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Here are the results, thanks.

---

### Post by confused57 on 2010-06-21
I see you're using a GUID partition table, which I have no experience with, however, I'll post your bootinfo script in code tags, if someone else wants to take a look:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 268775424 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   178,183,079   177,773,440 HFS+
/dev/sda3     178,446,336   268,774,218    90,327,883 Linux or Data
/dev/sda4     268,775,424   268,777,471         2,048 Bios Boot Partition
/dev/sda5     268,777,472   310,667,263    41,889,792 Linux or Data
/dev/sda6     310,669,312   312,580,095     1,910,784 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        6eddcc66-6510-38bb-8932-231ce760923c   hfsplus    MAC                           
/dev/sda3        1E422035422013D5                       ntfs                                     
/dev/sda5        7105162d-1f90-48f2-89c2-932815f34a83   ext4                                     
/dev/sda6        d4735586-c449-4368-91ef-705d8b55e8ed   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
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
search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7105162d-1f90-48f2-89c2-932815f34a83 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7105162d-1f90-48f2-89c2-932815f34a83 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f5616aaf638973f6
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid f5616aaf638973f6 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f5616aaf638973f6
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid f5616aaf638973f6 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 1e422035422013d5
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
UUID=7105162d-1f90-48f2-89c2-932815f34a83 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d4735586-c449-4368-91ef-705d8b55e8ed none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 139.9GB: boot/grub/core.img
 137.8GB: boot/grub/grub.cfg
 139.9GB: boot/initrd.img-2.6.32-21-generic
 139.8GB: boot/vmlinuz-2.6.32-21-generic
 139.9GB: initrd.img
 139.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 97  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 52 b0 04 8d  |...=HXt.=H+uR...|
00000060  36 dd e3 8d 3e 20 e5 e8  96 01 75 43 8d b6 1d 01  |6...> ....uC....|
00000070  8b 34 81 3c 00 02 75 37  66 8b 5c 5c 66 0f cb 66  |.4.<..u7f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 1f  |......f.......w.|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 8a 16  04 e6 ea 00 02 00 20 f4  |.|h.N......... .|
000000b0  eb fd 66 60 89 c3 66 31  c0 88 d8 81 fb 40 00 72  |..f`..f1.....@.r|
000000c0  02 b0 40 e8 12 00 29 c3  74 0b 66 01 c1 c1 e0 09  |..@...).t.f.....|
000000d0  66 01 c2 eb e1 66 61 c3  66 60 06 89 e5 52 31 d2  |f....fa.f`...R1.|
000000e0  66 c1 ea 04 8e c2 5b 1e  1e 66 03 0e 00 e6 66 51  |f.....[..f....fQ|
000000f0  06 53 30 e4 50 68 10 00  8a 16 04 e6 89 e6 b4 42  |.S0.Ph.........B|
00000100  cd 13 72 ab 89 ec 07 66  61 c3 66 60 ad 86 e0 ab  |..r....fa.f`....|
00000110  3c 00 74 23 89 c1 ad 86  e0 80 3e 01 e4 58 74 14  |<.t#......>..Xt.|
00000120  09 c0 75 01 48 80 fc 00  77 0a 3c 41 72 06 3c 5a  |..u.H...w.<Ar.<Z|
00000130  77 02 04 20 ab e2 df 66  61 c3 66 60 b2 00 66 8b  |w.. ...fa.f`..f.|
00000140  44 02 66 3b 45 02 75 0f  80 3c 00 75 0a 66 8b 44  |D.f;E.u..<.u.f.D|
00000150  06 66 3b 45 06 74 48 77  44 72 3d 66 60 31 d2 87  |.f;E.tHwDr=f`1..|
00000160  f7 66 ad 66 89 c1 87 f7  66 ad 66 39 c8 77 2e 72  |.f.f....f.f9.w.r|
00000170  27 87 f7 ad 89 c1 87 f7  ad 80 f9 00 74 1f 39 c8  |'...........t.9.|
00000180  74 0b 77 07 fe ce 89 c1  e9 02 00 fe c6 f3 a7 77  |t.w............w|
00000190  0c 72 05 88 f2 e9 07 00  fe ca e9 02 00 fe c2 88  |.r..............|
000001a0  96 14 00 80 fa 00 66 61  c3 50 57 8b 3e 0a e6 57  |......fa.PW.>..W|
000001b0  47 47 49 49 b0 00 f3 aa  89 3e 0a e6 5d 89 2d 5f  |GGII.....>..].-_|
000001c0  58 c3 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |X...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda4

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 30 05 10  00 00 00 00 2f 00 20 08  |.....0....../. .|
00000200

```

---

### Post by oldfred on 2010-06-21
I do not know GPT but plan to convert one drive just to learn so I saved this info:

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
I added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
I can now see all the partitions on my IDE drives and boot from them too!!!!!

grub2 & GPT info
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)
[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos"

---

### Post by Brii on 2010-06-21
> **oldfred said:**
> I do not know GPT but plan to convert one drive just to learn so I saved this info:

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
I added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
I can now see all the partitions on my IDE drives and boot from them too!!!!!

grub2 & GPT info
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)
[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos"

Didn't work. Any other ideas?

---

### Post by wilee-nilee on 2010-06-21
> **Brii said:**
> Didn't work. Any other ideas?

Since you have run some fixes, and can only post didn't work run the script again as things may have changed and without this information it is very difficult to fix.

---

### Post by Brii on 2010-06-21
> **wilee-nilee said:**
> Since you have run some fixes, and can only post didn't work run the script again as things may have changed and without this information it is very difficult to fix.

All right, sorry about being so discrete. 





Here it is; I'll also put it as an attachment:


 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 268775424 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   178,183,079   177,773,440 HFS+
/dev/sda3     178,446,336   268,774,218    90,327,883 Linux or Data
/dev/sda4     268,775,424   268,777,471         2,048 Bios Boot Partition
/dev/sda5     268,777,472   310,667,263    41,889,792 Linux or Data
/dev/sda6     310,669,312   312,580,095     1,910,784 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        6eddcc66-6510-38bb-8932-231ce760923c   hfsplus    MAC                           
/dev/sda3        1E422035422013D5                       ntfs                                     
/dev/sda5        7105162d-1f90-48f2-89c2-932815f34a83   ext4                                     
/dev/sda6        d4735586-c449-4368-91ef-705d8b55e8ed   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
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
search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
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
search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7105162d-1f90-48f2-89c2-932815f34a83 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7105162d-1f90-48f2-89c2-932815f34a83 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7105162d-1f90-48f2-89c2-932815f34a83
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f5616aaf638973f6
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid f5616aaf638973f6 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f5616aaf638973f6
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid f5616aaf638973f6 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 1e422035422013d5
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
UUID=7105162d-1f90-48f2-89c2-932815f34a83 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d4735586-c449-4368-91ef-705d8b55e8ed none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 139.9GB: boot/grub/core.img
 148.5GB: boot/grub/grub.cfg
 139.9GB: boot/initrd.img-2.6.32-21-generic
 139.8GB: boot/vmlinuz-2.6.32-21-generic
 139.9GB: initrd.img
 139.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 97  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 52 b0 04 8d  |...=HXt.=H+uR...|
00000060  36 dd e3 8d 3e 20 e5 e8  96 01 75 43 8d b6 1d 01  |6...> ....uC....|
00000070  8b 34 81 3c 00 02 75 37  66 8b 5c 5c 66 0f cb 66  |.4.<..u7f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 1f  |......f.......w.|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 8a 16  04 e6 ea 00 02 00 20 f4  |.|h.N......... .|
000000b0  eb fd 66 60 89 c3 66 31  c0 88 d8 81 fb 40 00 72  |..f`..f1.....@.r|
000000c0  02 b0 40 e8 12 00 29 c3  74 0b 66 01 c1 c1 e0 09  |..@...).t.f.....|
000000d0  66 01 c2 eb e1 66 61 c3  66 60 06 89 e5 52 31 d2  |f....fa.f`...R1.|
000000e0  66 c1 ea 04 8e c2 5b 1e  1e 66 03 0e 00 e6 66 51  |f.....[..f....fQ|
000000f0  06 53 30 e4 50 68 10 00  8a 16 04 e6 89 e6 b4 42  |.S0.Ph.........B|
00000100  cd 13 72 ab 89 ec 07 66  61 c3 66 60 ad 86 e0 ab  |..r....fa.f`....|
00000110  3c 00 74 23 89 c1 ad 86  e0 80 3e 01 e4 58 74 14  |<.t#......>..Xt.|
00000120  09 c0 75 01 48 80 fc 00  77 0a 3c 41 72 06 3c 5a  |..u.H...w.<Ar.<Z|
00000130  77 02 04 20 ab e2 df 66  61 c3 66 60 b2 00 66 8b  |w.. ...fa.f`..f.|
00000140  44 02 66 3b 45 02 75 0f  80 3c 00 75 0a 66 8b 44  |D.f;E.u..<.u.f.D|
00000150  06 66 3b 45 06 74 48 77  44 72 3d 66 60 31 d2 87  |.f;E.tHwDr=f`1..|
00000160  f7 66 ad 66 89 c1 87 f7  66 ad 66 39 c8 77 2e 72  |.f.f....f.f9.w.r|
00000170  27 87 f7 ad 89 c1 87 f7  ad 80 f9 00 74 1f 39 c8  |'...........t.9.|
00000180  74 0b 77 07 fe ce 89 c1  e9 02 00 fe c6 f3 a7 77  |t.w............w|
00000190  0c 72 05 88 f2 e9 07 00  fe ca e9 02 00 fe c2 88  |.r..............|
000001a0  96 14 00 80 fa 00 66 61  c3 50 57 8b 3e 0a e6 57  |......fa.PW.>..W|
000001b0  47 47 49 49 b0 00 f3 aa  89 3e 0a e6 5d 89 2d 5f  |GGII.....>..].-_|
000001c0  58 c3 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |X...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda4

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 30 05 10  00 00 00 00 2f 00 20 08  |.....0....../. .|
00000200
```

---

### Post by wilee-nilee on 2010-06-21
Since at best the best people at this fix don't really know of a fix it would be helpful if you put the readout in code tags just hit edit reply-advanced highlight the txt then click on the # (code tags) it will really help to read it.

---

### Post by Brii on 2010-06-23
Screw it. I'm just going to reinstall windows then reinstall grub.

---

### Post by oldfred on 2010-06-23
I just converted one of my 160GB drives to GPT. I changed it to GPT from MBR, created a bios boot partition, root partition, & swap. Then I installed like normal from my USB key and I can not see any difference. Install went just like normal. 

But I still have BIOS not efi. EFI required grub-efi to work. But I do not know the details.

---

### Post by Brii on 2010-07-06
> **wilee-nilee said:**
> Since at best the best people at this fix don't really know of a fix it would be helpful if you put the readout in code tags just hit edit reply-advanced highlight the txt then click on the # (code tags) it will really help to read it.

Oh thanks, I didn't see that message last time I visited this thread. Edited, thanks.

---

