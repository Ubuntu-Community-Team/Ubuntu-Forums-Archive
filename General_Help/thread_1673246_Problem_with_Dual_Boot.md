---
title: "Problem with Dual Boot"
date: 2011-01-22
forum: General Help
---

### Post by jveron on 2011-01-22
Hi everybody. How are you? I was looking this problem but I didn't find any solution. Perhaps some of you have any idea.
In my Dell 1320 I have installed two operating systems: Windows 7 and Ubuntu 10.10. Windows 7 and Ubuntu work perfectly. I use GRUB2
If I start Ubuntu, I won't have any problem restarting in Windows.
If I start Windows, I will have a problem restarting in any case.
If I use Windows suppose for more than half hour and I want to restart in Ubuntu, often my laptop loads the bios and then restarts itself, then load the Bios and restart itself and again and again. I have fixed this problem reinstalling grub2 but I did it so many times that I won't do it again.
Any ideas? Is a Windows' problem?  Does the Grub2 have any bug? 
In my opinion, Windows &#8220;break&#8221;my MRB. I want to know your points of view.

Thank you for any advice.

PD: I'm sorry if I didn't explain very well.

---

### Post by ajgreeny on 2011-01-22
From your ubuntu OS, download and run the Boot-info-script shown in my signature, then copy the RESULTS.txt file back here in code tags, ie click on the # in the reply toolbar and paste the RESULTS.txt file between the two [CODE][/CODE tags that appear.

---

### Post by oldfred on 2011-01-22
Are you running some windows software that writes into the MBR area used by grub? Known problem with Dell & HP software and some others.

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by jveron on 2011-01-26
I'm not running any program that writes into the MBR area used by grub. In fact, I have just only installed Windows 7 with minimal programs and I have the same problem.

There is the file RESULTS.txt:

```


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   121,636,863   121,430,016   7 HPFS/NTFS
/dev/sda3         257,222,656   488,392,703   231,170,048   7 HPFS/NTFS
/dev/sda4         121,638,910   257,222,655   135,583,746   5 Extended
/dev/sda5         121,638,912   133,636,095    11,997,184  82 Linux swap / Solaris
/dev/sda6         133,638,144   257,222,655   123,584,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        668A00418A000FEB                       ntfs       Reservado para el sistema     
/dev/sda2        E6800DC9800DA0E3                       ntfs       Windows 7                     
/dev/sda3        6652C21752C1EBBD                       ntfs       Datos                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f72de7e4-a996-47a5-91d0-cd9a09dacb82   swap                                     
/dev/sda6        283f5098-7f22-48bb-b8ec-71d6ac3dc71d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/Datos             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
insmod tga
if background_image /boot/grub/Plasma-lamp.tga ; then
  set color_normal=white/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=283f5098-7f22-48bb-b8ec-71d6ac3dc71d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=283f5098-7f22-48bb-b8ec-71d6ac3dc71d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 283f5098-7f22-48bb-b8ec-71d6ac3dc71d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 668a00418a000feb
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=283f5098-7f22-48bb-b8ec-71d6ac3dc71d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f72de7e4-a996-47a5-91d0-cd9a09dacb82 none            swap    sw              0       0
/dev/sda3 /media/Datos ntfs defaults,rw,users,auto,iocharset=utf8,umask=000 0 0

=================== sda6: Location of files loaded by Grub: ===================


  90.0GB: boot/grub/core.img
  70.9GB: boot/grub/grub.cfg
  75.2GB: boot/initrd.img-2.6.35-24-generic
  90.1GB: boot/vmlinuz-2.6.35-24-generic
  75.2GB: initrd.img
  90.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  3e cd 35 02 60 d8 a3 dc  3b cf 17 02 60 d8 a4 dc  |>.5.`...;...`...|
00000010  13 d0 95 02 60 d8 a5 dc  19 cf 17 02 60 d8 a6 dc  |....`.......`...|
00000020  19 cf 4d 02 60 d8 a7 dc  18 cf 59 02 60 d8 a8 dc  |..M.`.....Y.`...|
00000030  18 cf 98 02 60 d8 a9 dc  19 cf 44 02 60 d8 aa dc  |....`.....D.`...|
00000040  19 cf 02 02 60 d8 ab dc  18 cf fb 02 60 d8 ac dc  |....`.......`...|
00000050  0e cf 86 02 60 d8 ad dc  18 cf 50 02 60 d8 ae dc  |....`.....P.`...|
00000060  27 cf 6b 02 60 d8 af dc  18 cf c8 02 60 d8 b0 dc  |'.k.`.......`...|
00000070  18 cf 47 02 60 d8 b1 dc  19 cf 1a 02 60 d8 b2 dc  |..G.`.......`...|
00000080  19 cf 2f 02 60 d8 b3 dc  19 cf 32 02 60 d8 b4 dc  |../.`.....2.`...|
00000090  18 cf ef 02 60 d8 b5 dc  18 cf bc 02 60 d8 b6 dc  |....`.......`...|
000000a0  18 cf 9e 02 60 d8 b7 dc  18 cf 8f 02 60 d8 b8 dc  |....`.......`...|
000000b0  18 cf d1 02 60 d8 b9 dc  19 cf 3b 02 60 d8 ba dc  |....`.....;.`...|
000000c0  18 cf f5 02 60 d8 bb dc  18 cf e0 02 60 d8 bc dc  |....`.......`...|
000000d0  18 cf e3 02 60 d8 bd dc  18 cf 92 02 60 d8 be dc  |....`.......`...|
000000e0  18 cf 77 02 60 d8 bf dc  18 cf 89 02 60 d8 c0 dc  |..w.`.......`...|
000000f0  18 cf 80 02 60 d8 c1 dc  18 cf 5c 02 60 d8 c2 dc  |....`.....\.`...|
00000100  18 cf 86 02 60 d8 c3 dc  18 cf ad 02 60 d8 c4 dc  |....`.......`...|
00000110  18 cf b0 02 60 d8 c5 dc  18 cf b9 02 60 d8 c6 dc  |....`.......`...|
00000120  18 cf e6 02 60 d8 c7 dc  19 cf 0b 02 60 d8 c8 dc  |....`.......`...|
00000130  18 cf 68 02 60 d8 c9 dc  18 cf da 02 60 d8 ca dc  |..h.`.......`...|
00000140  18 cf 9b 02 60 d8 cb dc  1a ce 98 02 60 d8 cc dc  |....`.......`...|
00000150  18 cf 53 02 60 d8 cd dc  19 cf 14 02 60 d8 ce dc  |..S.`.......`...|
00000160  18 cf a1 02 60 d8 cf dc  18 cf cb 02 60 d8 d0 dc  |....`.......`...|
00000170  1a ce 9e 02 60 d8 d1 dc  18 cf 56 02 60 d8 d2 dc  |....`.....V.`...|
00000180  19 cf 38 02 60 d8 d3 dc  18 cf 6e 02 60 d8 d4 dc  |..8.`.....n.`...|
00000190  13 d0 b0 02 60 d8 d5 dc  13 d0 f2 02 60 d8 d6 dc  |....`.......`...|
000001a0  18 cf 65 02 60 d8 d7 dc  23 d0 2f 02 60 d8 d8 dc  |..e.`...#./.`...|
000001b0  13 d0 da 02 60 d8 d9 dc  13 d0 83 02 60 d8 00 fe  |....`.......`...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 b7 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  b7 00 00 c8 5d 07 00 00  |............]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-01-26
Do you have Dell data safe installed?

---

### Post by jveron on 2011-01-26
> **Quackers said:**
> Do you have Dell data safe installed?

No, I don't.
I can't understand why my laptop have a random behaviour.
Sometimes when I use Windows for 30 minutes and I have to restart, my laptop can't reboot but sometimes when I use Windows for 30 minutes and I have to restart, my laptop reboot normally. I mean, my laptop doesn't behave in the same way all the time.

---

### Post by oldfred on 2011-01-26
From what I gather the Dell utilities are installed by default. There are other windows programs that also install DRM software that writes into the MBR area. It is only updated periodically so that is why you cna use it for a while and then it has problems.

HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

---

