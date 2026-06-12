---
title: "Reverting back to Vista factory settings after full installation"
date: 2010-10-04
forum: General Help
---

### Post by Pulpish on 2010-10-04
Hello, I fully installed Ubuntu and whenever I hit Restore factory settings or whatever its called on the options booting up, it simply starts up Ubuntu, as if the setting is gone. Is it possible to get Windows back so I can dual boot again? Or do I have to buy it all over again? I have a HP Pavillion dv5 on 32bit.

---

### Post by tabasko on 2010-10-04
That recovery option more likely only tries to use recovery partition from hardrive. This sounds like you have swiped all partitions from hd and replaced it with Ubuntu? Im assuming that you dont have Windows installation discs either, because nowadays PC vendors are trusting to only recovery partitions?
You might try to ask or search HP sites if you can get installation disc from there, because you still got te license for the Windows.

When waiting for Windows disc, try to make yourself comfortable with Ubuntu, maybe you notice that you dont need dual-boot :)
Too bad your journey with Ubuntu started like this, thought this is pretty normal start :P In future, remember backups. Whatever youre doing.

---

### Post by nothingspecial on 2010-10-04
If the computer came with a recovery partition rather than a windows cd, and you have used the entire disk to install Ubuntu, then you have no windows at the moment.

Things like this vary from country to country, but either microsoft or the manufacturer should be required to send you a windows disk for the price of the cd and the postage. Try contacting them before you fork out a load of money.

---

### Post by Mark Phelps on 2010-10-04
While the EULA does vary from country to country, in general, ALL the OEMs are required to do is provide you the means to restore your machine to its original state.  They nearly always do that by putting a customized-OEM version of Windows Image on the hard drive and then providing either a function key to invoke that or a CD to invoke that.

If you carelessly wiped out their image (usually by formatting the drive and removing its parent partition), they are not REQUIRED to do anything for you.

In some cases, if you claim that you had a virus and accidentally wiped out the whole drive, they will send you restore CDs/DVDs --but they are likely to charge you something for that service.

---

### Post by Pulpish on 2010-10-04
Oh alright thanks guys.. I guess I'll just cope :P.. Its not that anythings wrong as ubuntu its just that the graphics and images aren't very sharp and graphics don't render as fast etc..the rest is all good. I even got my Nvidia driver updated and everything and apparently this is the best it gets :P Well thanks haha, I'll find a solution :P
edit: -- hold on, I had never formatted my HP recovery partition :S! I can't find it though :S is there a possibility that it is still there?

---

### Post by philinux on 2010-10-04
> **Pulpish said:**
> Oh alright thanks guys.. I guess I'll just cope :P.. Its not that anythings wrong as ubuntu its just that the graphics and images aren't very sharp and graphics don't render as fast etc..the rest is all good. I even got my Nvidia driver updated and everything and apparently this is the best it gets :P Well thanks haha, I'll find a solution :P
edit: -- hold on, I had never formatted my HP recovery partition :S! I can't find it though :S is there a possibility that it is still there?

From your ubuntu download and run this and post back the results.txt file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

How to run it.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2010-10-04
There will be a key or key combination to press whilst booting (it may be "del" F2, F11 etc) for your particular machine to access the recovery partition. Your manual will tell you which key it is. If you try that a couple of times and it does not start the Windows Recovery Environment, then it is likely that the recovery partition is gone.
I don't suppose you made the Recovery Discs did you? It is usually an option on a new system to create them.

---

### Post by Pulpish on 2010-10-04
> **philinux said:**
> From your ubuntu download and run this and post back the results.txt file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

How to run it.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   470,444,031   470,441,984  83 Linux
/dev/sda2         470,446,078   488,396,799    17,950,722   5 Extended
/dev/sda5         470,446,080   488,396,799    17,950,720  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1591eada-afc0-4f97-8798-c25e77096a66   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d0e8b67d-23eb-4dcf-8f1d-f6bd9aa87eef   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-386' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    linux    /boot/vmlinuz-2.6.32-25-386 root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-386
}
menuentry 'Ubuntu, with Linux 2.6.32-25-386 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    echo    'Loading Linux 2.6.32-25-386 ...'
    linux    /boot/vmlinuz-2.6.32-25-386 root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-386
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1591eada-afc0-4f97-8798-c25e77096a66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1591eada-afc0-4f97-8798-c25e77096a66
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1591eada-afc0-4f97-8798-c25e77096a66 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d0e8b67d-23eb-4dcf-8f1d-f6bd9aa87eef none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 219.1GB: boot/grub/core.img
  37.3GB: boot/grub/grub.cfg
 219.2GB: boot/initrd.img-2.6.32-24-generic
  26.2GB: boot/initrd.img-2.6.32-25-386
 219.2GB: boot/initrd.img-2.6.32-25-generic
 219.1GB: boot/vmlinuz-2.6.32-24-generic
 219.3GB: boot/vmlinuz-2.6.32-25-386
 219.1GB: boot/vmlinuz-2.6.32-25-generic
  26.2GB: initrd.img
 219.2GB: initrd.img.old
 219.3GB: vmlinuz
 219.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  74 f3 fc 2c 46 f3 14 e2  5f 09 b9 54 75 58 ea 5d  |t..,F..._..TuX.]|
00000010  44 69 48 00 1a 07 3f 2e  79 e2 83 45 74 60 c2 34  |DiH...?.y..Et`.4|
00000020  18 51 3b bb 26 21 e5 6e  33 5b 6f 1f 65 04 83 aa  |.Q;.&!.n3[o.e...|
00000030  9b a7 29 79 c5 8f ea 01  dd 2d 6c 3b 24 27 a0 2c  |..)y.....-l;$'.,|
00000040  a3 7b 7b f9 86 a2 6f bf  2c 4c 0e 58 2c ef 1f 3a  |.{{...o.,L.X,..:|
00000050  f4 37 0a 0b 38 8a a2 85  98 0f 83 78 03 85 0f 8e  |.7..8......x....|
00000060  30 f9 01 d4 9e b6 02 1c  33 fb df e9 e5 ef 57 fa  |0.......3.....W.|
00000070  0f 76 34 13 3b 5a d1 2b  c5 85 e6 05 a3 ae ea 2d  |.v4.;Z.+.......-|
00000080  d4 d0 ff df 81 70 c4 c4  14 5e a9 a0 38 9e b9 a3  |.....p...^..8...|
00000090  3d 07 c3 42 cf e3 7f 03  7c 34 14 f7 34 e3 74 b5  |=..B....|4..4.t.|
000000a0  37 00 0f e0 15 10 d9 5d  05 33 b9 f4 c5 49 20 c2  |7......].3...I .|
000000b0  a8 c0 9a a5 41 ef d9 e4  2b ea c2 b1 6c f7 e3 86  |....A...+...l...|
000000c0  27 1e 5d 4a 78 2e ee 27  1c 29 c7 d9 66 17 ed 15  |'.]Jx..'.)..f...|
000000d0  6e 64 37 5e 5d ea d5 7c  b2 15 92 69 46 cb 50 1c  |nd7^]..|...iF.P.|
000000e0  da b8 ad 75 9a c7 9b 60  92 56 ce a3 a2 57 b2 67  |...u...`.V...W.g|
000000f0  80 1b a9 c1 26 10 e0 74  78 2e f5 54 98 96 79 b4  |....&..tx..T..y.|
00000100  bd 63 76 d7 db c3 fd 4e  a5 93 ed 2e 03 82 61 8e  |.cv....N......a.|
00000110  3a 35 9d 81 09 cd 57 7e  6c 35 ec f2 4f 00 5a 4d  |:5....W~l5..O.ZM|
00000120  89 40 94 c5 47 b6 c4 dd  c1 b9 f4 04 4b d9 76 a9  |.@..G.......K.v.|
00000130  38 71 03 be 59 82 1f 1f  5a f5 bf 12 99 8b 29 1a  |8q..Y...Z.....).|
00000140  07 b8 f2 40 1e 05 6f 68  54 fc a5 c9 a8 4f 81 19  |...@..ohT....O..|
00000150  47 1e 28 1a 61 e6 24 2a  69 96 60 d9 24 bb 85 a6  |G.(.a.$*i.`.$...|
00000160  ba b5 7f 1f 1b 99 28 ed  c7 d3 66 fb a6 1e 63 4b  |......(...f...cK|
00000170  80 d2 98 26 4e 56 b1 51  76 38 99 ed 94 52 ce d9  |...&NV.Qv8...R..|
00000180  ac 5d 18 74 8f 7a 9e c2  76 7a d9 6a 25 21 47 85  |.].t.z..vz.j%!G.|
00000190  8f 61 90 34 c2 a8 ce 56  fc 56 56 fa 09 50 8f e5  |.a.4...V.VV..P..|
000001a0  b2 20 70 04 6b 7e 04 2c  03 93 f5 39 9a c9 6e 61  |. p.k~.,...9..na|
000001b0  a4 e1 3f 96 c1 ac fc 56  a7 88 55 6a 65 1a 00 fe  |..?....V..Uje...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 11 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


And Quackers, when I try that it boots up Ubuntu

---

### Post by Mark Phelps on 2010-10-04
From the script, it looks like the whole drive is being used.

Thus, it appears that, if there ever WAS a Recovery partition there containing an MS Win image, it is gone now.

The only way you're going to get it back now is to contact the PC supplier and see if you can get them to send you full-restore CDs (or DVD).  And, as I said earlier, they're most probably going to charge you for that service.

---

