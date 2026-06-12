---
title: "Grub2 no longer shows ubuntu only windows"
date: 2010-07-15
forum: General Help
---

### Post by sunshine316 on 2010-07-15
ok so i am dual booting windows 7 and ubuntu 10.4 lucid, i just reinstalled the Grub2 after my windows erased it, and now it boots into grub2 but i can only boot into my windows7 loader, ubuntu is not even listed as an option for me to boot into its just a bow with the win7 loader. How can i get the grub2 to load ubuntu back again? i followed the guide on [this site]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") to reinstall the Grub2 and set up the dual boot. thanks for any help u can offer.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)



edit: i can find plenty of info for getting windows back into grub, but none about getting ubuntu back

---

### Post by oldfred on 2010-07-15
From liveCD post this, so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by sunshine316 on 2010-07-15
```
Ok here it all is, hope it helps



Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 539688 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD /grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 539688 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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

/dev/sda1               2,048   153,597,464   153,595,417  83 Linux
/dev/sda2    *    153,597,952   153,802,751       204,800   7 HPFS/NTFS
/dev/sda3         153,802,752   602,558,463   448,755,712   7 HPFS/NTFS
/dev/sda4         602,560,510   625,141,759    22,581,250   5 Extended
/dev/sda5         602,560,512   625,141,759    22,581,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10ff2eb9-8992-44b1-b9aa-ab9d999b6743   ext4                                     
/dev/sda2        565C65E75C65C27B                       ntfs       System Reserved               
/dev/sda3        783668C0366880CC                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        30e7d3e8-c7a2-45e0-9204-61176273417d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda1        /media/10ff2eb9-8992-44b1-b9aa-ab9d999b6743 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/783668C0366880CC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
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
search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=10ff2eb9-8992-44b1-b9aa-ab9d999b6743 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=10ff2eb9-8992-44b1-b9aa-ab9d999b6743 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10ff2eb9-8992-44b1-b9aa-ab9d999b6743 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10ff2eb9-8992-44b1-b9aa-ab9d999b6743 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 565c65e75c65c27b
    chainloader +1
}
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
UUID=10ff2eb9-8992-44b1-b9aa-ab9d999b6743 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=30e7d3e8-c7a2-45e0-9204-61176273417d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.32-21-generic
   1.4GB: boot/initrd.img-2.6.32-23-generic
   1.3GB: boot/vmlinuz-2.6.32-21-generic
    .8GB: boot/vmlinuz-2.6.32-23-generic
   1.4GB: initrd.img
   1.3GB: initrd.img.old
    .8GB: vmlinuz
   1.3GB: vmlinuz.old

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 10ff2eb9-8992-44b1-b9aa-ab9d999b6743
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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 565c65e75c65c27b
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 565c65e75c65c27b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  c4 30 b1 0a 11 21 2d db  8b bb ac 84 61 38 d9 f2  |.0...!-.....a8..|
00000010  a9 9f 3f e1 e7 7e ee e7  91 ca 30 dc 7b 85 5b 07  |..?..~....0.{.[.|
00000020  47 7c f1 8b 5f e6 f1 37  be 85 ba 6d 78 e7 fb de  |G|.._..7...mx...|
00000030  cb b4 3b c7 54 9a 2f 7e  f9 69 5e 79 f1 65 36 f7  |..;.T./~.i^y.e6.|
00000040  07 1e 7a e8 31 9a 6b d7  08 42 f3 81 0f fc 0e 62  |..z.1.k..B.....b|
00000050  d4 88 ba 43 36 35 d3 d9  39 55 57 c3 b4 83 6b 47  |...C65..9UW...kG|
00000060  b0 bd e0 93 bf f0 0b 9c  9f dd e3 bb be e7 fb 93  |................|
00000070  1a 64 7f fd e7 a1 48 b1  73 91 0b 3f 3a e7 30 a5  |.d....H.s..?:.0.|
00000080  1f 10 73 2a b0 eb 47 74  9d 18 79 b2 78 4c 5a 4f  |..s*..Gt..y.xLZO|
00000090  b0 13 d5 6a 9d eb 46 81  54 2a d7 62 b9 e6 b0 09  |...j..F.T*.b....|
000000a0  ec 71 e3 84 6e 32 a9 a1  ca eb 43 f4 b8 71 a2 3e  |.q..n2....C..q.>|
000000b0  5c 27 1b 04 25 89 08 94  4e c3 3c 69 aa ac 84 52  |\'..%...N.<i...R|
000000c0  29 29 b8 92 89 cd 88 24  ba c4 d8 c3 4f 44 8a 4f  |)).....$....OD.O|
000000d0  ad 42 44 81 ae 1a c2 38  a4 f4 77 b5 60 44 c9 65  |.BD....8..w.`D.e|
000000e0  df 34 65 f2 6f 02 e6 cb  72 17 9c c7 e8 12 08 96  |.4e.o...r.......|
000000f0  d3 68 55 35 a7 fd 86 6c  4d 13 6c be d5 7d 2e 63  |.hU5...lM.l..}.c|
00000100  44 1a 26 f9 c4 78 4d 64  80 b4 5f 09 99 41 42 9f  |D.&..xMd.._..AB.|
00000110  55 03 59 41 1a 6d c8 c7  4a ce 8c 4c 3f 24 fb 86  |U.YA.m..J..L?$..|
00000120  71 07 67 f7 f9 d4 47 7f  99 67 be f0 79 7e cf 0f  |q.g...G..g..y~..|
00000130  7e 98 da 5f 70 1c b7 7c  e9 57 fe 25 4f 6d 3c bf  |~.._p..|.W.%Om<.|
00000140  fa 6b 1f e7 46 33 c2 c5  6d 5e 3a 3b a3 c2 22 82  |.k..F3..m^:;..".|
00000150  a2 ab 1b da ae c2 5b cb  e6 fc 16 4d db a4 d7 ac  |......[....M....|
00000160  0d 21 44 74 95 3c 15 27  1b 10 d1 52 57 9a 71 1c  |.!Dt.<.'...RW.q.|
00000170  59 af 5b a2 1b 01 81 75  2e 8f ba 15 b4 07 58 73  |Y.[....u......Xs|
00000180  c4 c5 e0 b9 b6 ba c1 b7  fc 6f ff 4b 70 5d 1a ba  |.........o.Kp]..|
00000190  4a 01 47 af 4f 4a 32 aa  34 a4 6a d7 b8 61 87 ae  |J.G.OJ2.4.j..a..|
000001a0  04 d1 3a 88 3e 1d 03 6b  93 77 a4 49 81 92 89 25  |..:.>..k.w.I...%|
000001b0  94 fb e1 3d 93 26 2e ac  1b e4 02 e8 2b 75 00 fe  |...=.&......+u..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 58 01 00 00  |............X...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by sunshine316 on 2010-07-15
no one? its killing me to not be able to log my ubuntu :cry:

---

### Post by techunit on 2010-07-15
boot from your live cd and type the following in the Terminal:

```
sudo update-grub
```

---

### Post by sunshine316 on 2010-07-15
i already tried that >.> this is something else. Im not that newbish to ubuntu

---

### Post by wilee-nilee on 2010-07-15
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   **/grub/grub.cfg** /bootmgr /Boot/BCD **/grub/core.img**

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  **Grub 2 is installed in the boot sector of sda3 **and 
                       looks at sector 539688 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

You have grub in these two ntfs partitions use this link to clear this out.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by sunshine316 on 2010-07-16
tried using it but didnt seem to do anything, just told me the boot sectors are the same. What am i supposed to do with this program? cuz following the website data didnt do anything

---

### Post by oldfred on 2010-07-16
Did you remove the /grub folder from sda2. But it may not matter.

You will need to run the windows repairs but when windows has the separate boot partition it often will not repair the boot and the install. You usually have to move the boot flag to sda3 and repair that partition, in effect obsoleting the boot partition in sda2.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

