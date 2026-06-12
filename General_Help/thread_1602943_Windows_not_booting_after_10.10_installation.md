---
title: "Windows not booting after 10.10 installation"
date: 2010-10-22
forum: General Help
---

### Post by bash_me on 2010-10-22
Hi Gurus,

I have installed Ubuntu 10.10 in Dell Inspiron 1525 which was having Windows 7.Now when i select Windows entry in GRUB menu for booting the OS is not getting loaded instead it goes to the GRUB menu again. The same happened in my Home PC with Windows XP.
Please tell what i have to do for fixing the error.

Previously i was using 9.10 without any issues.

---

### Post by Rubi1200 on 2010-10-22
Did you install Ubuntu using Wubi?

From a LiveCD, post the results of the boot-script linked at the bottom of my post please.

Thanks.

---

### Post by bash_me on 2010-10-22
I didnt use Wubi.I did install from the CD itself.

---

### Post by Rubi1200 on 2010-10-22
Thanks; please post the results from the boot-script I mentioned in my previous post.

The information will hopefully allow us to see where the problem is and then suggest a solution.

---

### Post by Mark Phelps on 2010-10-22
When you installed Ubuntu, did you choose the side-by-side option and let the installer shrink your Windows partitions to make room for Ubuntu? If so, you most likely corrupted your Win7 OS boot loader -- a common result of choosing to install that way.

If that's what you did, you will need to repair the Win7 boot loader before you can get back into Win7 again.

---

### Post by davidvandoren on 2010-10-22
> **Mark Phelps said:**
> When you installed Ubuntu, did you choose the side-by-side option and let the installer shrink your Windows partitions to make room for Ubuntu? If so, you most likely corrupted your Win7 OS boot loader -- a common result of choosing to install that way.


At this point it should be mentioned to always de-fragment your windows first before installing Ubuntu or resizing  your partition.

---

### Post by bash_me on 2010-10-25
I selected side by side installation only.
Grub shows Windows 7 entry...

I didnt make any change in Windows partition. I was already having Ubuntu installed on the Laptop.So i used  the same partition for installing the new release.

Can anyone tell from where i can get the boot script output file?

---

### Post by Hippytaff on 2010-10-25
could try [http://ubuntuforums.org/showthread.php?t=1604123](http://ubuntuforums.org/showthread.php?t=1604123) #2

---

### Post by Quackers on 2010-10-25
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bash_me on 2010-10-28
RESULTS.TXT file is attached along with the post.Please have a look at it.

---

### Post by bash_me on 2010-10-28
One screenshot too....dont know whether it will help u guys....

---

### Post by Rubi1200 on 2010-10-28
I don't know how it got there, but first thing to do is delete the [COLOR=Red]grldr[/COLOR] file on sda1. You can do this from within Ubuntu. Then run > sudo update-grub and see if it fixes the issue of getting into Windows. If not, we will try some other stuff.  ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 126617720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /[COLOR=Red]grldr[/COLOR]

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    83,202,047    82,995,200   7 HPFS/NTFS
/dev/sda3          83,204,094   312,580,095   229,376,002   5 Extended
/dev/sda5          83,204,096   133,201,919    49,997,824  83 Linux
/dev/sda6         304,582,656   312,580,095     7,997,440  82 Linux swap / Solaris
/dev/sda7         133,203,968   304,574,463   171,370,496  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9498409898407B2E                       ntfs       System Reserved               
/dev/sda2        4E8284C88284B64D                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        74f5d8f2-0c96-441c-a4ea-c05972f5ef79   ext4                                     
/dev/sda6        18e7f9be-997d-4ba6-afe5-b9d9d457e938   swap                                     
/dev/sda7        e0464d65-81e6-4b2b-b9f1-a084417d991d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 ro single 
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
    search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9498409898407b2e
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
UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e0464d65-81e6-4b2b-b9f1-a084417d991d /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=18e7f9be-997d-4ba6-afe5-b9d9d457e938 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  55.6GB: boot/grub/core.img
  64.3GB: boot/grub/grub.cfg
  43.8GB: boot/initrd.img-2.6.35-22-generic
  55.6GB: boot/vmlinuz-2.6.35-22-generic
  43.8GB: initrd.img
  55.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ca 9c e1 f9 5e f2 1d 83  0c 70 da 76 06 43 25 8d  |....^....p.v.C%.|
00000010  a2 3f b6 b4 f5 d7 d6 bb  fc 0f ae cd 10 8d 12 53  |.?.............S|
00000020  f0 a9 8d ea 0a cf ec bd  42 88 6c 57 cf fa 9c 84  |........B.lW....|
00000030  be de 41 a9 c0 33 e3 a7  5e 8a 71 42 83 f1 a5 18  |..A..3..^.qB....|
00000040  34 d2 3b b0 32 0b 79 db  1a 06 cc 36 da 86 51 38  |4.;.2.y....6..Q8|
00000050  e9 3d 11 95 8d a0 71 f4  6e 7a 41 90 77 4f df f2  |.=....q.nzA.wO..|
00000060  24 c2 fa 11 72 d1 67 35  2e 52 74 69 8f 52 74 69  |$...r.g5.Rti.Rti|
00000070  d1 74 2b bb a8 c5 9f 1d  dc 9d dc d9 30 82 2d bd  |.t+.........0.-.|
00000080  7a 46 15 1b 48 b1 e8 a8  39 1e 3f 0b b6 a7 af 4a  |zF..H...9.?....J|
00000090  d5 de f9 81 b8 a1 b7 f3  04 2b 18 dc 2b 43 b1 bc  |.........+..+C..|
000000a0  52 b7 bc fd da 46 d7 11  9e bc aa 3c 74 3d 03 18  |R....F.....<t=..|
000000b0  35 f8 91 40 dd 5b 6d c6  b3 41 5d 61 81 d1 a8 30  |5..@.[m..A]a...0|
000000c0  3a a0 02 a8 ce 50 5f fc  a8 10 2a b8 51 ee 73 51  |:....P_...*.Q.sQ|
000000d0  2e a4 a4 37 f0 82 07 10  b6 bc d1 f3 a7 5f 39 e9  |...7........._9.|
000000e0  85 fc 3e 7a 73 41 1a 15  23 58 fa 86 60 aa 98 02  |..>zsA..#X..`...|
000000f0  64 e1 ba fd 7b 26 34 cf  fd 7f 17 87 39 a8 00 6e  |d...{&4.....9..n|
00000100  79 9d 9b 75 bc 80 cb 73  2d 1d aa 73 65 76 8c 5c  |y..u...s-..sev.\|
00000110  75 f5 92 5d f8 ec 8c 03  d6 09 71 0f 7d 30 fb e7  |u..]......q.}0..|
00000120  1a 31 e2 65 9a ca ca 34  25 bd e2 a0 ba b3 e5 18  |.1.e...4%.......|
00000130  ba d5 35 59 f0 6d ac 06  bb d6 b9 ad 77 10 55 db  |..5Y.m......w.U.|
00000140  e2 e3 28 c9 07 f5 87 bd  d8 74 97 cf 5a 0b 3e 2c  |..(......t..Z.>,|
00000150  06 d1 3f 23 d8 45 25 7c  2f d4 5a b0 67 31 eb 4e  |..?#.E%|/.Z.g1.N|
00000160  c5 9b 4e 82 1f 3a 77 6a  91 fd eb ce 28 f0 3b 5a  |..N..:wj....(.;Z|
00000170  23 ca 49 9d 50 e2 d7 05  47 df 7f a1 54 31 84 d8  |#.I.P...G...T1..|
00000180  15 45 c4 48 f8 bf 4c a9  c8 bf 52 ba 9d 2d 01 44  |.E.H..L...R..-.D|
00000190  dc 3a fb b0 b4 2d c1 2d  02 13 67 3f ad f8 8b e3  |.:...-.-..g?....|
000001a0  69 9f 32 77 71 6c 97 bb  f8 9a c9 6e 9e 8a 1e 63  |i.2wql.....n...c|
000001b0  a1 a9 82 b7 36 df c4 3e  ba f6 8b b5 f5 14 00 fe  |....6..>........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 fa 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 51 df  31 0d b1 20 7a 00 00 00  |......Q.1.. z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by bcbc on 2010-10-28
You have grub installed in your windows boot sector. You need to restore it using testdisk or repair it using a windows repair cd.
see this link for instructions (testdisk works great on this)[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by oldfred on 2010-10-28
I see two issues from the boot script and you gparted is showing that you need to run chkdsk from windows.

sda1: _________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 126617720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grldr[/COLOR]

Rubi1200 already mentioned the grub4dos folder.

But you have installed grub to the windows boot partition and it has to have windows in it.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD. From meierfra who is the main author of the bootinfo script.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You will need a windows CD to run chkdsk on sda2 if it will not boot and run it as it boots.

---

### Post by bash_me on 2010-10-30
Hi [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746"),bcbc,[oldfred]("http://ubuntuforums.org/member.php?u=852711"),

I removed the file [COLOR=Red]**grldr** [/COLOR]ran and **testdisk** also. Now when i select the Windows menu item it doesn't come to the initial GRUB menu but shows a blank screen.

---

### Post by wilee-nilee on 2010-10-30
and here is the latest script.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    83,202,047    82,995,200   7 HPFS/NTFS
/dev/sda3          83,204,094   312,580,095   229,376,002   5 Extended
/dev/sda5          83,204,096   133,201,919    49,997,824  83 Linux
/dev/sda6         304,582,656   312,580,095     7,997,440  82 Linux swap / Solaris
/dev/sda7         133,203,968   304,574,463   171,370,496  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9498409898407B2E                       ntfs       System Reserved               
/dev/sda2        4E8284C88284B64D                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        74f5d8f2-0c96-441c-a4ea-c05972f5ef79   ext4                                     
/dev/sda6        18e7f9be-997d-4ba6-afe5-b9d9d457e938   swap                                     
/dev/sda7        e0464d65-81e6-4b2b-b9f1-a084417d991d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 74f5d8f2-0c96-441c-a4ea-c05972f5ef79
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 9498409898407b2e
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
UUID=74f5d8f2-0c96-441c-a4ea-c05972f5ef79 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e0464d65-81e6-4b2b-b9f1-a084417d991d /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=18e7f9be-997d-4ba6-afe5-b9d9d457e938 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  55.6GB: boot/grub/core.img
  64.3GB: boot/grub/grub.cfg
  43.8GB: boot/initrd.img-2.6.35-22-generic
  55.6GB: boot/vmlinuz-2.6.35-22-generic
  43.8GB: initrd.img
  55.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ca 9c e1 f9 5e f2 1d 83  0c 70 da 76 06 43 25 8d  |....^....p.v.C%.|
00000010  a2 3f b6 b4 f5 d7 d6 bb  fc 0f ae cd 10 8d 12 53  |.?.............S|
00000020  f0 a9 8d ea 0a cf ec bd  42 88 6c 57 cf fa 9c 84  |........B.lW....|
00000030  be de 41 a9 c0 33 e3 a7  5e 8a 71 42 83 f1 a5 18  |..A..3..^.qB....|
00000040  34 d2 3b b0 32 0b 79 db  1a 06 cc 36 da 86 51 38  |4.;.2.y....6..Q8|
00000050  e9 3d 11 95 8d a0 71 f4  6e 7a 41 90 77 4f df f2  |.=....q.nzA.wO..|
00000060  24 c2 fa 11 72 d1 67 35  2e 52 74 69 8f 52 74 69  |$...r.g5.Rti.Rti|
00000070  d1 74 2b bb a8 c5 9f 1d  dc 9d dc d9 30 82 2d bd  |.t+.........0.-.|
00000080  7a 46 15 1b 48 b1 e8 a8  39 1e 3f 0b b6 a7 af 4a  |zF..H...9.?....J|
00000090  d5 de f9 81 b8 a1 b7 f3  04 2b 18 dc 2b 43 b1 bc  |.........+..+C..|
000000a0  52 b7 bc fd da 46 d7 11  9e bc aa 3c 74 3d 03 18  |R....F.....<t=..|
000000b0  35 f8 91 40 dd 5b 6d c6  b3 41 5d 61 81 d1 a8 30  |5..@.[m..A]a...0|
000000c0  3a a0 02 a8 ce 50 5f fc  a8 10 2a b8 51 ee 73 51  |:....P_...*.Q.sQ|
000000d0  2e a4 a4 37 f0 82 07 10  b6 bc d1 f3 a7 5f 39 e9  |...7........._9.|
000000e0  85 fc 3e 7a 73 41 1a 15  23 58 fa 86 60 aa 98 02  |..>zsA..#X..`...|
000000f0  64 e1 ba fd 7b 26 34 cf  fd 7f 17 87 39 a8 00 6e  |d...{&4.....9..n|
00000100  79 9d 9b 75 bc 80 cb 73  2d 1d aa 73 65 76 8c 5c  |y..u...s-..sev.\|
00000110  75 f5 92 5d f8 ec 8c 03  d6 09 71 0f 7d 30 fb e7  |u..]......q.}0..|
00000120  1a 31 e2 65 9a ca ca 34  25 bd e2 a0 ba b3 e5 18  |.1.e...4%.......|
00000130  ba d5 35 59 f0 6d ac 06  bb d6 b9 ad 77 10 55 db  |..5Y.m......w.U.|
00000140  e2 e3 28 c9 07 f5 87 bd  d8 74 97 cf 5a 0b 3e 2c  |..(......t..Z.>,|
00000150  06 d1 3f 23 d8 45 25 7c  2f d4 5a b0 67 31 eb 4e  |..?#.E%|/.Z.g1.N|
00000160  c5 9b 4e 82 1f 3a 77 6a  91 fd eb ce 28 f0 3b 5a  |..N..:wj....(.;Z|
00000170  23 ca 49 9d 50 e2 d7 05  47 df 7f a1 54 31 84 d8  |#.I.P...G...T1..|
00000180  15 45 c4 48 f8 bf 4c a9  c8 bf 52 ba 9d 2d 01 44  |.E.H..L...R..-.D|
00000190  dc 3a fb b0 b4 2d c1 2d  02 13 67 3f ad f8 8b e3  |.:...-.-..g?....|
000001a0  69 9f 32 77 71 6c 97 bb  f8 9a c9 6e 9e 8a 1e 63  |i.2wql.....n...c|
000001b0  a1 a9 82 b7 36 df c4 3e  ba f6 8b b5 f5 14 00 fe  |....6..>........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 fa 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 51 df  31 0d b1 20 7a 00 00 00  |......Q.1.. z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-10-30
I can't see anything wrong with sda1, which carries the boot flag. 
The only thing I can think of is that a boot file was damaged when grub2 was mistakenly installed to that partition. If that is the case you will need to repair the Windows mbr with a repair disc. Then test to see if Windows boots. Once you are in Windows you can queue a chkdsk for the next boot.
Unfortunately all this may well mean that grub2 will need to be reinstalled to the mbr of sda in order for Ubuntu to boot.

---

### Post by Rubi1200 on 2010-10-30
Are you able to boot into Ubuntu?

If yes, run ```
sudo update-grub
``` and see if that allows you to boot into Windows.

---

### Post by bash_me on 2010-11-01
Still having the same problem,may be windows boot files got corrupted. Currently im not having my W7 installation disk with me.

@Rubi: Im able to boot into Ubuntu.

Once again thank u all for the guidance.

---

### Post by bcbc on 2010-11-01
You can download a win7 repair cd from here [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

