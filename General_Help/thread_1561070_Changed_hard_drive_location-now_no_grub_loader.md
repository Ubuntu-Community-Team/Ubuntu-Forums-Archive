---
title: "Changed hard drive location-now no grub loader"
date: 2010-08-25
forum: General Help
---

### Post by datashuttle on 2010-08-25
I moved a hard drive with an installed Ubuntu 10.04 installation from an external box and installed it in the PC box.  Now, no grub.  Windows loads without grub options.

Have tried the many grub reinstall directions in the Ubuntu documentation to no avail.

Any ideas how I can get the boot loader to offer grub.

I know this has got to be simple, but I'm not finding the correct instructions.

Regards,

Daryl

---

### Post by oldfred on 2010-08-25
Welcome to the forum.

We can give the general instructions but it is much better to see exactly where everything is at. From a liveCD run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by datashuttle on 2010-08-26
OldFred,

Attached are the results of the boot script.

Regards,

Daryl

---

### Post by Rubi1200 on 2010-08-26
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,247,163,383 1,247,161,336   7 HPFS/NTFS
/dev/sdb2       1,247,164,414 1,953,523,711   706,359,298   5 Extended
/dev/sdb5       1,247,164,416 1,932,355,583   685,191,168  83 Linux
/dev/sdb6       1,932,357,632 1,953,523,711    21,166,080  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        144AB0DB4AB0BB36                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7EF89397F8934BF1                       ntfs       Backup                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        954eee9e-1e2b-4220-95ec-f03ffe86082b   ext4                                     
/dev/sdb6        2775379b-4e1b-47e2-8f11-4afbd69172c9   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        747C650A7C64C886                       ntfs       Netserver                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
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
search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=954eee9e-1e2b-4220-95ec-f03ffe86082b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=954eee9e-1e2b-4220-95ec-f03ffe86082b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 954eee9e-1e2b-4220-95ec-f03ffe86082b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 144ab0db4ab0bb36
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 747c650a7c64c886
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=954eee9e-1e2b-4220-95ec-f03ffe86082b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2775379b-4e1b-47e2-8f11-4afbd69172c9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 754.6GB: boot/grub/core.img
 935.5GB: boot/grub/grub.cfg
 754.7GB: boot/initrd.img-2.6.32-24-generic-pae
 754.7GB: boot/vmlinuz-2.6.32-24-generic-pae
 754.7GB: initrd.img
 754.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  a5 4c a5 76 55 34 ef 73  9b d1 fc 2f e2 ad 1f c6  |.L.vU4.s.../....|
00000010  51 dc c4 a4 bb 0c 36 de  af f8 57 73 a1 5b f8 82  |Q.....6...Ws.[..|
00000020  ce e4 5d bd 84 85 38 57  56 3c 64 d4 39 69 63 59  |..]...8WV<d.9icY|
00000030  b6 d9 ff d3 eb 7f b0 b5  7b 9d 45 ae 1b ec f6 d0  |........{.E.....|
00000040  a2 6e c7 4c 93 ef 55 d9  fc 37 a7 69 f1 be b3 af  |.n.L..U..7.i....|
00000050  5b 45 97 3c b4 c3 d6 be  b3 96 fb 9f 3b 43 0d 29  |[E.<........;C.)|
00000060  a3 17 c4 5f 19 7e 0b 78  5f 5b 54 b8 f1 35 bd d1  |..._.~.x_[T..5..|
00000070  5f 98 c5 13 76 f4 cf 6a  e2 3c 53 fb 67 78 3f 4a  |_...v..j.<S.gx?J|
00000080  96 e2 cf c2 fa 14 73 3c  b9 48 0b a1 2f 9f 50 6a  |......s<.H../.Pj|
00000090  67 89 a5 49 6a 7a 54 72  c7 d4 f3 dd 6b e2 c7 c6  |g..IjzTr....k...|
000000a0  df 18 ea 8b 2d c3 de 69  3a 5c df 2a 82 a4 6f 1f  |....-..i:\.*..o.|
000000b0  5a bd a5 7c 3e d2 ee 2d  21 bb d5 1a 5b a9 e5 c3  |Z..|>..-!...[...|
000000c0  3c 8e c7 79 3f 9f 4a f2  31 59 c2 e6 f7 4e ef aa  |<..y?.J.1Y...N..|
000000d0  46 3a 1b b6 1e 04 d0 a5  90 25 c5 96 f8 f0 01 05  |F:.......%......|
000000e0  8e 3e b5 d1 da 78 1f 45  47 2b 35 80 70 40 01 71  |.>...x.EG+5.p@.q|
000000f0  d5 6b cc ad 9d 4f 98 d6  18 58 3e 87 ff d4 ad 6b  |.k...O...X>....k|
00000100  e0 ad 16 d9 09 b5 d2 ad  a3 18 e4 f9 60 1c d5 d3  |............`...|
00000110  04 69 a6 88 5e 2c 2a 83  b5 80 ef 5c 35 f3 1a b5  |.i..^,*....\5...|
00000120  77 67 5d 3a 0a 3a 22 3f  ec d0 88 7c b4 08 c3 1e  |wg]:.:"?...|....|
00000130  d9 a8 db 4e 91 d2 56 97  01 97 d3 a8 3e d5 c1 29  |...N..V.....>..)|
00000140  b6 f5 36 50 48 8e 4d 2c  45 6e 67 58 f7 94 1b b2  |..6PH.M,EngX....|
00000150  c7 15 6e da d1 45 aa c8  c0 92 79 18 19 15 32 99  |..n..E....y...2.|
00000160  71 42 c7 68 ca d2 a6 18  23 75 c0 a5 5b 01 35 bb  |qB.h....#u..[.5.|
00000170  43 c6 f0 46 d1 8e 2b 19  3f 78 b4 8f ff d5 b3 69  |C..F..+.?x.....i|
00000180  63 72 6e 5e 19 e2 2e d1  9e 98 e8 2a f4 36 48 d0  |crn^.......*.6H.|
00000190  11 1b 34 64 f4 e3 a5 7c  d4 a7 63 d7 6a cc d1 b5  |..4d...|..c.j...|
000001a0  4f 2a f9 39 ca b0 c6 08  c7 35 a0 60 67 11 88 df  |O*.9.....5.`g...|
000001b0  92 7e 60 46 38 a9 e6 6c  bb 0c b9 b3 86 79 00 fe  |.~`F8..l.....y..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 d7 28 00 fe  |...........0.(..|
000001d0  ff ff 05 fe ff ff 02 30  d7 28 00 00 43 01 00 00  |.......0.(..C...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-08-26
I only see one or two minor things.

Have you tried booting from sdb, the 1000GB drive. It shows grub installed and it should boot the install in sdb5. Change BIOS or use one time boot key (f12 or other per BIOS) to boot the 1TB drive.

After booting run
```
sudo update-grub
```

It looks like you reversed or installed Ubuntu as the first drive as it shows hd0,5, but it also will search on the UUID and should boot with that.
If booting windows from the grub menu does not work, it may be because of /grldr in your root of windows. This often confuses grub for some reason.

---

