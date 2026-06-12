---
title: "Dual boot troubles"
date: 2011-04-06
forum: General Help
---

### Post by dacovale on 2011-04-06
Yes, yet another dual boot thread... I think I've read a few dozen so far while trying to fix my problem.

The situation so far:

Fresh install of both Win7 and Ubuntu 10.10. Installed Windows first, ran through it's updates and generally rebooted it a couple of times while fixing things. Followed up with Ubuntu, install ran without a hitch, updated here as well and then tried to boot back into windows. No dice.
Grub shows, I select Windows and the computer immediately reboots. It does this every time I select the windows option. Ubuntu of course boots without any problems. I just want both available.

So far, I've reset the boot-partition for windows with ```
bootrec.exe /fixboot
``` and when that didn't fix it, I bit the bullet and reset the mbr so I could get in to windows again with ```
bootrec.exe /fixmbr
```

This got me windows back, but of course no linux. As I had understood the various posts here, a re-setup of grub would give me a working dual boot. No dice, I got the original problem back again.

followed [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) with the help of my install CD, and ran ```
sudo update-grub
``` from my ubuntu system afterwards to get grub back as my bootloader.

I've also tried manually editing the grub-menu to load from hd(0,2) instead of hd(0,1) for windows, but with no new result...

Finally, here's my RESULTS.txt from when I ran boot_info_script055.sh:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320,1 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar, totalt 625142448 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   167,774,207   167,567,360   7 HPFS/NTFS
/dev/sda3         167,776,254   625,141,759   457,365,506   5 Extended
/dev/sda5         167,776,256   208,478,207    40,701,952  83 Linux
/dev/sda6         208,480,256   619,128,831   410,648,576   7 HPFS/NTFS
/dev/sda7         619,143,168   625,141,759     5,998,592  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500,1 GB, 500107862016 byte
255 huvuden, 63 sektorer/spår, 60801 cylindrar, totalt 976773168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A8082DB4082D8304                       ntfs       System Reserved               
/dev/sda2        D66456B264569559                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b972226d-749a-43de-82d1-52742637c77f   ext4                                     
/dev/sda6        2C90DA4A90DA1A62                       ntfs       Files                         
/dev/sda7        2da1ed42-1eba-4843-bf1b-0d10434d5156   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0028-64C2                              vfat       TREKSTOR                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/TREKSTOR          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
set locale_dir=($root)/boot/grub/locale
set lang=sv
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro single 
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
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a8082db4082d8304
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
UUID=b972226d-749a-43de-82d1-52742637c77f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2da1ed42-1eba-4843-bf1b-0d10434d5156 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.1GB: boot/grub/core.img
  88.4GB: boot/grub/grub.cfg
  87.3GB: boot/initrd.img-2.6.35-22-generic
  87.4GB: boot/initrd.img-2.6.35-28-generic
 101.6GB: boot/vmlinuz-2.6.35-22-generic
 101.6GB: boot/vmlinuz-2.6.35-28-generic
  87.4GB: initrd.img
  87.3GB: initrd.img.old
 101.6GB: vmlinuz
 101.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e4 b4 f5 62 34 01 dc 2a  12 04 6e 50 27 e0 87 d6  |...b4..*..nP'...|
00000010  3e 8a 9e 87 59 5b 81 f3  70 53 eb 52 bd 32 7b 80  |>...Y[..pS.R.2{.|
00000020  e0 7c eb c4 e6 f9 23 a8  a1 a8 39 72 40 6a 6d 9f  |.|....#...9r@jm.|
00000030  6d 42 8a 13 a6 b4 41 0b  08 4f 86 d1 42 a0 87 c4  |mB....A..O..B...|
00000040  6b 01 a1 ba 33 59 ce 41  3c 2a e3 34 04 a8 23 dc  |k...3Y.A<*.4..#.|
00000050  93 b5 8e 8d b6 4d 0a 1f  38 1c e7 49 fd 59 61 41  |.....M..8..I.YaA|
00000060  f2 7a 8c 27 d9 f7 19 61  09 5e b0 b8 71 02 71 64  |.z.'...a.^..q.qd|
00000070  e3 6b dc 65 10 87 63 08  d7 de 70 20 2a ed 12 62  |.k.e..c...p *..b|
00000080  9c d3 61 75 18 c3 a7 85  f8 05 d1 80 6a e8 46 94  |..au........j.F.|
00000090  26 27 d4 c5 80 fa 0b a3  a8 45 1d 01 a4 6c 6d 32  |&'.......E...lm2|
000000a0  18 44 26 1d 75 53 42 35  29 ac 80 00 00 00 00 00  |.D&.uSB5).......|
000000b0  01 0e 23 91 3d ed 23 94  47 e0 17 00 b2 94 ca d4  |..#.=.#.G.......|
000000c0  4b 4a 3e d5 b6 f4 14 29  a6 30 1d 35 5a 20 f6 65  |KJ>....).0.5Z .e|
000000d0  86 cd 00 ce d1 b2 16 48  38 5d ae 16 d6 cc 98 a6  |.......H8]......|
000000e0  a1 7e ea ee 6c 1f 6e ec  03 e8 da 55 ba 48 c4 8a  |.~..l.n....U.H..|
000000f0  45 4b 29 e7 44 88 61 4d  3a 9e 89 14 82 97 06 13  |EK).D.aM:.......|
00000100  5c 74 3a 2b 55 c4 d9 42  43 c8 91 ae 40 fa 28 d3  |\t:+U..BC...@.(.|
00000110  ad 80 7e 06 8f bb 46 36  68 cf ed 27 b0 1b 68 07  |..~...F6h..'..h.|
00000120  d2 63 6d 10 42 82 28 13  24 05 d2 4e 7e 61 12 d2  |.cm.B.(.$..N~a..|
00000130  7f 50 53 28 9f 74 50 d5  95 9c c5 81 d8 d8 b6 1a  |.PS(.tP.........|
00000140  33 00 0c a4 9a c4 08 db  8c b6 17 e7 80 5f 1d 54  |3............_.T|
00000150  50 f6 79 87 c5 ae ed 4b  3e d9 a4 34 3a b9 81 75  |P.y....K>..4:..u|
00000160  25 1d a4 86 25 a8 a1 92  41 ee 2e 49 49 44 a5 bd  |%...%...A..IID..|
00000170  ca 20 a6 dc ea bb 94 45  73 e7 32 ee 7d 31 b7 13  |. .....Es.2.}1..|
00000180  82 ba 76 f4 48 aa 14 28  48 0d 07 c9 15 2c 68 42  |..v.H..(H....,hB|
00000190  ec 44 bb 46 18 a0 c7 c0  7c 64 59 c7 f0 a9 a4 dc  |.D.F....|dY.....|
000001a0  41 25 7e d0 b9 52 4c e4  0d 19 69 ec 3b 03 db b8  |A%~..RL...i.;...|
000001b0  55 f3 b9 19 e0 19 5a 20  c5 34 06 7b 3a 32 00 fe  |U.....Z .4.{:2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 6d 02 00 ef  |............m...|
000001d0  ff ff 05 ef ff ff 02 10  6d 02 00 08 7a 18 00 00  |........m...z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Pretty please, someone help me? :confused:

---

### Post by wilee-nilee on 2011-04-06
First try 
sudo update-grub 
and see if that lines W7 up.

You left out how you resized W7 if you did one. If you used the Ubuntu partitioning then you may need to run a chkdsk. You know how to get to the command line we want it to run on C run this command to get the run on restart choice.
chkdsk C: /f /r

W7 has a auto repair as well, it supposedly does what the fixmbr, and fixboot, and chkdsk does if run enough times 3 is the general advice.

---

### Post by dacovale on 2011-04-06
> **dacovale said:**
> followed [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) with the help of my install CD ( + ran "sudo update-grub" from my ubuntu system afterwards) to get grub back as my bootloader.


Sorry if I wasn't clear when I formatted my post, but I already tried "*sudo update-grub*". I'll edit it to be even more clear. To be sure, I rechecked ten minutes ago, and it still didn't help.

Since this was a planned side-by-side install, I formatted the 80-gig partition for windows with their own installer. The linux partitions where set up with the ubuntu installer, and the free ntfs partition was setup from within windows with the system tools. All partitions are checked and healthy.

---

### Post by Quackers on 2011-04-06
Altogether odd, this is.
Everything looks fine in the boot script output. All boot files appear to be good and placed well, and everything seems to be pointing in the right direction.
The only dubious thing I see is this (in red)
```
sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info: [COLOR="Red"] According to the info in the boot sector, sda6 starts 
                       at sector 2048.[/COLOR]
    Operating System:  
    Boot files/dirs:   

```
This appears to wrong, in that sda1 starts at sector 2048. I'm wondering if the Windows loader is somehow confused by this.
As a test, you could delete the sda6 partition, temporarily, then run sudo update-grub and try to boot Windows again from grub.
It would certainly clear that item up.

---

### Post by techunit on 2011-04-06
you likely need to install grub again. I wish the Ubuntu website would arn Dualbooters more clearly that partitioning windows can cause damage if done incorrectly. you can find more information on grub here. I would make sure that you install grub to the mbr of the hard drive. If you have two disks set the bios to boot your Ubuntu one first and them install grub to that disk. installing to the partition is possible as well but not recommended as it creats a chain load that will cause problems in the end.
[URL="http://ubuntuforums.org/showthread.php?t=1195275"]
http://ubuntuforums.org/showthread.php?t=1195275[/URL]

---

### Post by dacovale on 2011-04-06
Sitting in the liveCD environment right now to re-install grub after another trip into windows via mbr reset. I didn't notice (or didn't get, don't know which) this message last time, but I got this:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f233f22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10444    83783680    7  HPFS/NTFS
/dev/sda3           10444       38914   228682753    5  Extended
/dev/sda5           10444       12978    20350976   83  Linux
/dev/sda6           38540       38914     2999296   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
[COLOR="Red"]/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.[/COLOR]
```

Somehow, I don't like that message, even though it alleges that the install went fine. Will reboot, update grub and try windows again and post the results. Just wanted to post this while I could copy the message verbatim from the console.

---

### Post by Quackers on 2011-04-06
That's the problem, but I thought grub worked around it now. Some software which can be run in Windows writes data to the mbr - it shouldn,t but it does. This plays havoc with booting - or it used to.
The message is saying that grub is working around it. 
What happens when you try to boot Windows now?

---

### Post by dacovale on 2011-04-06
Still no go.

New RESULTS.txt (since I've pulled a partition and a disk):
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320,1 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar, totalt 625142448 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   167,774,207   167,567,360   7 HPFS/NTFS
/dev/sda3         167,776,254   625,141,759   457,365,506   5 Extended
/dev/sda5         167,776,256   208,478,207    40,701,952  83 Linux
/dev/sda6         619,143,168   625,141,759     5,998,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A8082DB4082D8304                       ntfs       System Reserved               
/dev/sda2        D66456B264569559                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b972226d-749a-43de-82d1-52742637c77f   ext4                                     
/dev/sda6        2da1ed42-1eba-4843-bf1b-0d10434d5156   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
set locale_dir=($root)/boot/grub/locale
set lang=sv
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b972226d-749a-43de-82d1-52742637c77f ro single 
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
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set b972226d-749a-43de-82d1-52742637c77f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a8082db4082d8304
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
UUID=b972226d-749a-43de-82d1-52742637c77f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2da1ed42-1eba-4843-bf1b-0d10434d5156 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.1GB: boot/grub/core.img
  90.9GB: boot/grub/grub.cfg
  87.3GB: boot/initrd.img-2.6.35-22-generic
  87.4GB: boot/initrd.img-2.6.35-28-generic
 101.6GB: boot/vmlinuz-2.6.35-22-generic
 101.6GB: boot/vmlinuz-2.6.35-28-generic
  87.4GB: initrd.img
  87.3GB: initrd.img.old
 101.6GB: vmlinuz
 101.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e4 b4 f5 62 34 01 dc 2a  12 04 6e 50 27 e0 87 d6  |...b4..*..nP'...|
00000010  3e 8a 9e 87 59 5b 81 f3  70 53 eb 52 bd 32 7b 80  |>...Y[..pS.R.2{.|
00000020  e0 7c eb c4 e6 f9 23 a8  a1 a8 39 72 40 6a 6d 9f  |.|....#...9r@jm.|
00000030  6d 42 8a 13 a6 b4 41 0b  08 4f 86 d1 42 a0 87 c4  |mB....A..O..B...|
00000040  6b 01 a1 ba 33 59 ce 41  3c 2a e3 34 04 a8 23 dc  |k...3Y.A<*.4..#.|
00000050  93 b5 8e 8d b6 4d 0a 1f  38 1c e7 49 fd 59 61 41  |.....M..8..I.YaA|
00000060  f2 7a 8c 27 d9 f7 19 61  09 5e b0 b8 71 02 71 64  |.z.'...a.^..q.qd|
00000070  e3 6b dc 65 10 87 63 08  d7 de 70 20 2a ed 12 62  |.k.e..c...p *..b|
00000080  9c d3 61 75 18 c3 a7 85  f8 05 d1 80 6a e8 46 94  |..au........j.F.|
00000090  26 27 d4 c5 80 fa 0b a3  a8 45 1d 01 a4 6c 6d 32  |&'.......E...lm2|
000000a0  18 44 26 1d 75 53 42 35  29 ac 80 00 00 00 00 00  |.D&.uSB5).......|
000000b0  01 0e 23 91 3d ed 23 94  47 e0 17 00 b2 94 ca d4  |..#.=.#.G.......|
000000c0  4b 4a 3e d5 b6 f4 14 29  a6 30 1d 35 5a 20 f6 65  |KJ>....).0.5Z .e|
000000d0  86 cd 00 ce d1 b2 16 48  38 5d ae 16 d6 cc 98 a6  |.......H8]......|
000000e0  a1 7e ea ee 6c 1f 6e ec  03 e8 da 55 ba 48 c4 8a  |.~..l.n....U.H..|
000000f0  45 4b 29 e7 44 88 61 4d  3a 9e 89 14 82 97 06 13  |EK).D.aM:.......|
00000100  5c 74 3a 2b 55 c4 d9 42  43 c8 91 ae 40 fa 28 d3  |\t:+U..BC...@.(.|
00000110  ad 80 7e 06 8f bb 46 36  68 cf ed 27 b0 1b 68 07  |..~...F6h..'..h.|
00000120  d2 63 6d 10 42 82 28 13  24 05 d2 4e 7e 61 12 d2  |.cm.B.(.$..N~a..|
00000130  7f 50 53 28 9f 74 50 d5  95 9c c5 81 d8 d8 b6 1a  |.PS(.tP.........|
00000140  33 00 0c a4 9a c4 08 db  8c b6 17 e7 80 5f 1d 54  |3............_.T|
00000150  50 f6 79 87 c5 ae ed 4b  3e d9 a4 34 3a b9 81 75  |P.y....K>..4:..u|
00000160  25 1d a4 86 25 a8 a1 92  41 ee 2e 49 49 44 a5 bd  |%...%...A..IID..|
00000170  ca 20 a6 dc ea bb 94 45  73 e7 32 ee 7d 31 b7 13  |. .....Es.2.}1..|
00000180  82 ba 76 f4 48 aa 14 28  48 0d 07 c9 15 2c 68 42  |..v.H..(H....,hB|
00000190  ec 44 bb 46 18 a0 c7 c0  7c 64 59 c7 f0 a9 a4 dc  |.D.F....|dY.....|
000001a0  41 25 7e d0 b9 52 4c e4  0d 19 69 ec 3b 03 db b8  |A%~..RL...i.;...|
000001b0  55 f3 b9 19 e0 19 5a 20  c5 34 06 7b 3a 32 00 fe  |U.....Z .4.{:2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 6d 02 00 fe  |............m...|
000001d0  ff ff 05 fe ff ff cd 18  e7 1a 35 bf 5b 00 00 00  |..........5.[...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-04-06
Sorry to hear that. This used to be a bigger problem than it is now, mostly due to grub being adapted to work around that sector.
It may be worthwhile trying to figure out what program in Windows is writing the data.
If it's not a huge list, can you remember what programs are installed? I don't mean the original ones, for the moment. Just ones that you have installed.
I'm sure there is some kind of list giving details of the offending programs. Maybe oldfred had a few put together.

---

### Post by dacovale on 2011-04-06
Since it's a new install, it's a fairly short list.

Avast Internet Security
MS Live Essentials (msn, etc)
MS Office 2010
Mozilla Firefox
Adobe Flash
updated IE

other than that, nothing that didn't come with a windows update/install.


EDIT:

Since I believe none of the above uses FlexNet (although I could of course be  wrong), I'm thinking of using [http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254) to get rid of the offending sector.

Would that be wise? and would the grub2 team still be interested in a copy of the sectors before and after the change?

---

### Post by Quackers on 2011-04-06
I've been googling myself :-)
That worked for the poster, so it may work for you. Just be sure to make backups first!
Also, unless the offending program is uninstalled, it may just write the data back to sector 32 again.
It seems it is often caused by Adobe's DRM. I have just installed Avast and have had no problems with booting either system (and I've booted many times in the lst 24 hours!) so it's probably not that. I did disable the rootkit search though - have you?

---

### Post by techunit on 2011-04-06
It could be a windows program breaking grub. But I have never had the problem before and find it unlikely that it would be that. Is grub still intact? Did you attempt to reinstall grub from the live cd? 

I read through the post and it seams like your trying to run ```
sudo update-grub
``` without first mounting your HD. You need to gain access to your computers HD first.

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
Subject 13 and mount your drive and then run ```
sudo update-grub
```

I apologize if this is redundant.

---

### Post by dacovale on 2011-04-06
I run ```
sudo update-grub
``` from my installed environment. So I do have it mounted :)

As for trying to overwrite the 32nd sector, I still need to convince my girlfriend that this is a worthwhile project (since it's our shared PC). She's beginning to lean towards going 100% windows since "linux obviously doesn't work". So I guess this is where I sign off for the day. Thank you all for your help. If I get my gf to agree with me and I succeed, I'll post here and let you all know.

Cheers

---

### Post by techunit on 2011-04-06
Good luck. hope it all works out.

---

### Post by Quackers on 2011-04-06
Good luck in your decision :-)

---

### Post by dacovale on 2011-04-06
I've got it working!
It's half past two in the morning here and all I can say is "victory is worth it!"
Having a girlfriend who says I'm cute as a puppy for not giving up helps too. :)

Although, I'm almost at the point where I'd rather not tell anyone how it works :p
It's almost at the same level as [XKCD: Workaround]("http://xkcd.com/763/")...

After a clean format, and a ```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1
``` whipe of some of the sectors between the MBR and the first partition, I set up the system again. 

First a Windows partition (without the separate load-partition), then a Ubuntu partition, then the joint file-partition for movies/music/documents/etc and last, the swap. 

After updating the Ubuntu system, I uninstalled Grub2 (both the ***grub-PC*** and ***grub-common*** packages) and instead installed the legacy ***grub***.

I installed grub to the Ubuntu partition instead of the MBR, and didn't bother to list Windows in menu.lst

Next I reinstalled the Windows bootloader to the MBR, and configured the BCD bootloader to load my Ubuntu install with the help of [EasyBCD]("http://neosmart.net/dl.php?id=1").

Fine-tuned it so that Ubuntu is the default OS and shortened the wait to 10 seconds, and voila. I now load Ubuntu via the Windows bootloader :lolflag:

It would probably work with grub2 as well, but by the time I stumbled onto the idea of actually using the windows bootloader, I didn't feel like changing back. Besides, this works (for now).

---

