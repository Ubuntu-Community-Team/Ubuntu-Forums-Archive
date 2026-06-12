---
title: "No boot device found"
date: 2010-10-13
forum: General Help
---

### Post by Alycan on 2010-10-13
Ever since I updated to Ubuntu 10.10 I'm encountering problems which forced me to do a completely fresh install with 10.10.

So the problem is as following after installation the bios tells me to "Insert a Proper Boot device." which bug's me since I just had it working for 2 day's again. 

All the partitions on the hard drive are correct, my computer can see the HDD's in the bios which is configured correctly. But yet the machine won't start Ubuntu from the HDD.

At this point I can only see 2 options:

1. Format and re-install and lose all my data.
2. Switch back to windows which is something I definably do not want to do.

Problem with option 1 is the fact that all the data on the hard disk is restricted to the account that I have on that HDD. So I am not able to access my data. Can anyone point me to any solution? 

E.g. Get my data back or ability to repair the other installation? Sadly enough I need this to be awnsered quick because I really need the Data on it for my job.

---

### Post by pmlxuser on 2010-10-13
i would try using a live CD or pen Drive. See if I can access the files first before trying other things. 
However i thing its the grub that is messed up: too bad am not great with grub commands.

---

### Post by Alycan on 2010-10-13
> **pmlxuser said:**
> i would try using a live CD or pen Drive. See if I can access the files first before trying other things. 
However i thing its the grub that is messed up: too bad am not great with grub commands.

Thanks for the quick response, I am on the affected machine with a pen drive at the moment. I cannot acces any of the files that are stored under "Documents" or any other folder like "Music" or "Pictures".

---

### Post by Quackers on 2010-10-13
Please go to the link below and download the file to your desktop. Then in a terminal run the command shown on that site. This will run the script which will produce a results.txt file on your desktop. Please copy the contents of that file and hit "New reply" then click on the # symbol in the top bar then paste the contents in between the code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Alycan on 2010-10-13
Here you go, thanks again for the help and effort!
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34   625,142,414   625,142,381 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   384,579,583   384,577,536  83 Linux
/dev/sdb2         384,581,630   390,721,535     6,139,906   5 Extended
/dev/sdb5         384,581,632   390,721,535     6,139,904  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1046 MB, 1046478848 bytes
16 heads, 63 sectors/track, 2027 cylinders, total 2043904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            512     2,043,902     2,043,391   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        56f77c63-6c5e-43b3-bf9b-e5545571f96c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        61461699-a44d-4b48-8f00-d9148dff6fe2   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EAA6-363B                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/56f77c63-6c5e-43b3-bf9b-e5545571f96c ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56f77c63-6c5e-43b3-bf9b-e5545571f96c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56f77c63-6c5e-43b3-bf9b-e5545571f96c ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 56f77c63-6c5e-43b3-bf9b-e5545571f96c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=56f77c63-6c5e-43b3-bf9b-e5545571f96c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=61461699-a44d-4b48-8f00-d9148dff6fe2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 107.5GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 107.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  3c 87 4e 2f 35 8c f2 40  5e a9 16 06 9b 43 e9 a3  |<.N/5..@^....C..|
00000010  47 64 f3 0f 73 08 2e ff  9c 60 4c 38 e7 7f 14 84  |Gd..s....`L8....|
00000020  a3 4b 34 f9 2a 8f d9 c0  e0 f6 cf 93 82 05 c2 a1  |.K4.*...........|
00000030  08 c8 3a 4f c8 2b e6 d9  41 9e 16 29 d4 d6 1a 19  |..:O.+..A..)....|
00000040  ca 3b 20 74 c7 54 54 b0  6f 35 42 12 73 af da f8  |.; t.TT.o5B.s...|
00000050  a5 ea d3 1b 65 d8 73 58  70 63 9f f0 5f 52 9e d8  |....e.sXpc.._R..|
00000060  a1 cf cb b3 da e3 70 bc  e7 ac 65 d4 25 0f 62 5d  |......p...e.%.b]|
00000070  74 79 8b 27 df e0 d1 23  a0 65 28 c8 71 94 d1 88  |ty.'...#.e(.q...|
00000080  0d 52 d6 7f 94 f9 e2 84  f6 75 67 d4 23 36 e9 2d  |.R.......ug.#6.-|
00000090  78 a8 c2 06 61 ec ca b3  5b 62 47 86 c9 f4 b9 58  |x...a...[bG....X|
000000a0  bb a6 04 15 6e 02 dd 82  2c 0d 29 c9 6c 05 23 2e  |....n...,.).l.#.|
000000b0  15 a3 e0 84 b7 30 fe 85  36 fa 6f 0d 18 d0 91 71  |.....0..6.o....q|
000000c0  24 27 a3 4e b5 8c 52 14  f0 de 02 07 ae db 22 a7  |$'.N..R.......".|
000000d0  9e bd 3c 38 11 4d 0e cc  84 dc 3f 93 77 09 7c e9  |..<8.M....?.w.|.|
000000e0  8e 12 56 5e db 89 eb c5  21 d8 fc 6d 56 80 ca 92  |..V^....!..mV...|
000000f0  ba 46 12 8f 41 de e5 00  31 2e d4 8e 1b c7 4d ff  |.F..A...1.....M.|
00000100  ef d6 38 98 e0 08 f4 9f  c4 a4 9a 05 c0 2b 3d 47  |..8..........+=G|
00000110  86 5d fa 22 dc d9 e9 b4  f3 2e d9 df 1a 2c 09 1b  |.].".........,..|
00000120  b5 ae 48 c1 16 ec 7d b8  20 5e 0e 89 bb 42 3b aa  |..H...}. ^...B;.|
00000130  31 d7 1e c4 7e f9 e5 96  d3 0e fe 67 ab 9f dc 12  |1...~......g....|
00000140  d2 08 d1 cd 65 b3 d7 38  8f 2f b8 64 0b 5d f6 2c  |....e..8./.d.].,|
00000150  52 0e 2d 64 88 8c 80 cc  17 22 52 56 99 cd 2d 33  |R.-d....."RV..-3|
00000160  27 f0 5c e0 03 04 f7 24  d1 62 b2 c7 e4 de e7 d0  |'.\....$.b......|
00000170  db fc b0 4f 6c 59 5c 93  59 bc 4f 48 bb 26 b9 8e  |...OlY\.Y.OH.&..|
00000180  21 c5 b1 52 c2 98 dd 81  08 19 4b 9d 0f 7f 61 db  |!..R......K...a.|
00000190  0b 06 c9 1b 55 55 5f fe  7d 09 b8 3c ae f3 5e e0  |....UU_.}..<..^.|
000001a0  c2 d5 ba 2d 22 50 33 91  20 35 27 49 38 59 05 58  |...-"P3. 5'I8Y.X|
000001b0  2d 58 6a 30 d3 27 57 20  2c 3b 20 7f 9a 62 00 fe  |-Xj0.'W ,; ..b..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 78 10  |.X.SYSLINUX...x.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 02 00 00  |........?.......|
00000020  ff 2d 1f 00 c4 07 00 00  00 00 00 00 02 00 00 00  |.-..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3b 36 a6 ea 4e  4f 20 4e 41 4d 45 20 20  |..);6..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 00 c8 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-10-13
Did you install ubuntu using a usb stick or pendrive? Will ubuntu boot only if your usb stick/pendrive is plugged in?
Grub is not installed in the MBR of any disc. As your ubuntu system is on sdb1 grub should be installed in the MBR of sdb (at least).

---

### Post by Alycan on 2010-10-13
Installed it from USB stick, this worked fine when I first installed Ubuntu 10.04. And the 10.10 (current installation) was working yesterday.

Anyway, as for grub can you point me to a noob proof tutorial about it?

---

### Post by Quackers on 2010-10-13
I suspect grub has been installed to your usb stick and not your hard drive.
Take a look at this guide by drs305. It explains what needs to be done in different sets of circumstances. FYI your ubuntu system is on sdb1 and grub should be installed to sdb, if that is the device set to boot in your bios.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Alycan on 2010-10-13
Great halfway trough and I get the following:

```
WARNING: The following packages cannot be authenticated!
  grub-common grub-pc
Install these packages without verification [y/N]? y
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/main grub-common i386 1.98+20100804-5ubuntu3
  Something wicked happened resolving 'nl.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/main grub-pc i386 1.98+20100804-5ubuntu3
  Something wicked happened resolving 'nl.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3_i386.deb  Something wicked happened resolving 'nl.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3_i386.deb  Something wicked happened resolving 'nl.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Happens when I get at step 4

---

### Post by Quackers on 2010-10-13
Oh dear. Is your internet connection good?
Also are the first four boxes checked under the first tab of the Software Sources page?

---

### Post by Alycan on 2010-10-13
Internet is 100%, all boxes are checked. 

Trying the US server, maybe that will work.

====
Edit: 
No nothing.

Edit2: Software center seems to be able to download the packages so does SPM.

---

