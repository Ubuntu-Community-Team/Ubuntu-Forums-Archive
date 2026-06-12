---
title: "grub error"
date: 2011-03-12
forum: General Help
---

### Post by khoraski on 2011-03-12
I got this darn error! And whenever I boot up my computer, I get this:
 
[quote=Error]error: unkown filesystem.
grub rescue>[/quote]
 
It started happening ever since I installed Ubuntu onto Windows 7.
 
SOMEONE, PLEASE HELP! I'm begging you, just tell me what to do. I don't even have any recovery CD's.

---

### Post by Diametric on 2011-03-12
Do you have the Ubuntu live cd?

Do you need any data from the MS 7 install?

What were you doing that lead up to this?

Give us some more info, and we'll be glad to help.

---

### Post by khoraski on 2011-03-12
> **Diametric said:**
> Do you have the Ubuntu live cd?
 
Do you need any data from the MS 7 install?
 
What were you doing that lead up to this?
 
Give us some more info, and we'll be glad to help.
 
I think I have the live cd. I used a CD to install Linux.
 
And when this happened was when I was looking at my boot menu, for some reason Windows 7 was on there. I clicked it and it brought me to some recovery manager so I clicked away and it said "please wait" and it was taking so long I thought it had locked up so I shut the PC down, booted it back up and I got this. 
 
I do have a repair CD though, which only really just let's me open the command prompt.
 
Oh, and I don't know anything about MS 7 install, or if I need it or not. But I don't have any CDs to install Windows 7. Or recovery the system.

---

### Post by wilee-nilee on 2011-03-12
Sounds like a wubi install, can you confirm this, and if you were booting with the W7 bootloader to get to Ubuntu.

You can also click on bootscript in my signature and run that and post the text from the generated file in code tags. To get code tags click on the **(#)** in the reply window and put the text between them

---

### Post by khoraski on 2011-03-12
> **wilee-nilee said:**
> Sounds like a wubi install, can you confirm this, and if you were booting with the W7 bootloader to get to Ubuntu.
 
You can also click on bootscript in my signature and run that and post the text from the generated file in code tags. To get code tags click on the **(#)** in the reply window and put the text between them
 
I think it was Wubi...
 
All I know is I went to the Ubuntu site, download the CD for 10.04 LTS 64-bit, ran it, and clicked "Install" on that purple page.
 
I will try your signature thing now.

---

### Post by wilee-nilee on 2011-03-12
> **khoraski said:**
> I think it was Wubi...
 
All I know is I went to the Ubuntu site, download the CD for 10.04 LTS 64-bit, ran it, and clicked "Install" on that purple page.
 
I will try your signature thing now.

If it is a wubi there is a thread just on this,  just want to confirm we are on the same page.:)

If you have problems with the script in the live Ubuntu terminal just run fdisk -lu and post the output. This command will confirm for us as well.

---

### Post by khoraski on 2011-03-12
> **wilee-nilee said:**
> If it is a wubi there is a thread just on this, just want to confirm we are on the same page.:)
 
If you have problems with the script in the live Ubuntu terminal just run fdisk -lu and post the output. This command will confirm for us as well.
 
Hold on

---

### Post by khoraski on 2011-03-13
Okay, so I loaded the CD I used to install and then clicked the try Ubuntu 10.04 LTS and opened the prompt and typed in fdisk -lu but there was no output at all.
 
Oh, same with bootinfo.
 
SOMEONE, PLEASE REPLY ALREADY.

---

### Post by wilee-nilee on 2011-03-13
> **khoraski said:**
> Okay, so I loaded the CD I used to install and then clicked the try Ubuntu 10.04 LTS and opened the prompt and typed in fdisk -lu but there was no output at all.

You didn't get something like this.

:~$ fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3113a989

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83888127    41943040    7  HPFS/NTFS
/dev/sda2        83894270   312580095   114342913    5  Extended
/dev/sda5       254951613   308369407    26708897+  83  Linux
/dev/sda6       308371456   312580095     2104320   82  Linux swap / Solaris
/dev/sda7        83894272   213891071    64998400   83  Linux



Okay then go to menu-system-admin-gparted take a screen shot of gparted.

---

### Post by khoraski on 2011-03-13
> **khoraski said:**
> Okay, so I loaded the CD I used to install and then clicked the try Ubuntu 10.04 LTS and opened the prompt and typed in fdisk -lu but there was no output at all.
 
Oh, same with bootinfo.
 
SOMEONE, PLEASE REPLY ALREADY.
[img]http://oi55.tinypic.com/2z80lqp.jpg[/img]
 
Sorry if I'm a little impatient. It's midnight and I have to wake up early tommorow for church. 
Also, sorry it took so long. My internet is SUPER slow.

---

### Post by khoraski on 2011-03-13
It's been 15 minutes, I really need some help and I only have a couple hours.

---

### Post by wilee-nilee on 2011-03-13
So you are getting help this is not a forum where we follow my forum name we make sure we know what is up.

Boot the live cd and get the bootscript on the desktop again and run this command and post the text in code tags. copy and paste it to the terminal if you get nothing take a screen shot of it. There is no reason the terminal should not work.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This command is on the links page, anybody else that will help you is going to ask for the script as well it's standard procedure to some extent.

You have not really given enough information to risk much, we don't really know what led to this situation, but the script will give us a what is where, and it's not called bootscript for chuckles.:)

Your flustered man chill and follow the help.

---

### Post by khoraski on 2011-03-13
> **wilee-nilee said:**
> So you are getting help this is not a forum where we follow my forum name we make sure we know what is up.
 
Boot the live cd and get the bootscript on the desktop again and run this command and post the text in code tags. copy and paste it to the terminal if you get nothing take a screen shot of it. There is no reason the terminal should not work.
```
sudo bash ~/Desktop/boot_info_script*.sh
```
 
This command is on the links page, anybody else that will help you is going to ask for the script as well it's standard procedure to some extent.
 
You have not really given enough information to risk much, we don't really know what led to this situation, but the script will give us a what is where, and it's not called bootscript for chuckles.:)
 
Your flustered man chill and follow the help.
 
The results were 348 lines long, so I just uploaded the text file.
Here ya go:
 
[http://www.mediafire.com/?wznzznnkyza37v3](http://www.mediafire.com/?wznzznnkyza37v3)
 
Sorry I used mediafire. File-holder and dropbox won't work on Ubuntu.

---

### Post by wilee-nilee on 2011-03-13
Cool let me post it I sent another member a PM so we can take a look hold a minute.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    28,313,599    28,311,552  27 Hidden HPFS/NTFS
/dev/sda2    *     28,313,600    28,518,399       204,800   7 HPFS/NTFS
/dev/sda3          28,518,400   281,394,335   252,875,936   7 HPFS/NTFS
/dev/sda4         281,395,198   488,396,799   207,001,602   5 Extended
/dev/sda5         281,395,200   289,003,495     7,608,296  83 Linux
/dev/sda6         289,003,520   472,023,039   183,019,520  83 Linux
/dev/sda7         472,025,088   479,877,119     7,852,032  82 Linux swap / Solaris
/dev/sda8         479,891,456   488,396,799     8,505,344  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,911,039     3,910,977   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F65053B550537AF7                       ntfs       PQSERVICE                     
/dev/sda2        28B65419B653E63A                       ntfs       SYSTEM RESERVED               
/dev/sda3        C842553A42552E86                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        50b24836-3e20-47a8-9207-fe425c50ad9d   ext4                                     
/dev/sda6        942214b2-ad4a-4faf-a247-522416f12668   ext4                                     
/dev/sda7        c5009c46-5dca-4715-8b59-27fae8422035   swap                                     
/dev/sda8        be73db06-c44c-4a40-9ce6-3830ccc0bdfe   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1884-3BE2                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=50b24836-3e20-47a8-9207-fe425c50ad9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=be73db06-c44c-4a40-9ce6-3830ccc0bdfe none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 144.9GB: boot/vmlinuz-2.6.35-22-generic
 144.9GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=942214b2-ad4a-4faf-a247-522416f12668 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=942214b2-ad4a-4faf-a247-522416f12668 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 942214b2-ad4a-4faf-a247-522416f12668
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f65053b550537af7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 28b65419b653e63a
	chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 50b24836-3e20-47a8-9207-fe425c50ad9d
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=942214b2-ad4a-4faf-a247-522416f12668 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c5009c46-5dca-4715-8b59-27fae8422035 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 221.1GB: boot/grub/core.img
 169.7GB: boot/grub/grub.cfg
 221.1GB: boot/initrd.img-2.6.32-28-generic
 221.1GB: boot/vmlinuz-2.6.32-28-generic
 221.1GB: initrd.img
 221.1GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  41 ad 3b 00 00 00 29 e2  3b 84 18 20 20 20 20 20  |A.;...).;..     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 cd 18  |      FAT16   ..|
00000040  fa 33 c9 8e d1 bc fc 7b  16 07 bd 78 00 c5 76 00  |.3.....{...x..v.|
00000050  1e 56 16 55 bf 22 05 89  7e 00 fa fc 31 c9 8e d1  |.V.U."..~...1...|
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
00000100  7d 00 66 b8 ff 01 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by wilee-nilee on 2011-03-13
Okay from the live cd again in the terminal run these two commands.
```
sudo mount /dev/sda6 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```
reboot to the Ubuntu install and run
```
sudo update-grub
```

I notice you have  wubi remnants as well, no big deal you can clean that up from windows. You also have 2 swaps you just need one. Not sure what is going on with the sda5, just showing fstab, and to small of an amount of data for a full install of Maverick.

---

### Post by khoraski on 2011-03-13
> **wilee-nilee said:**
> Okay from the live cd again in the terminal run these two commands.
```
sudo mount /dev/sda6 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```
reboot to the Ubuntu install and run
```
sudo update-grub
```
 
I notice you have wubi remnants as well, no big deal you can clean that up from windows. You also have 2 swaps you just need one. Not sure what is going on with the sda5, just showing fstab, and to small of an amount of data for a full install of Maverick.
 
I typed in the first two commands, and then when I rebooted I forgot to put the CD back in and it brought me to the boot menu! :D
It fixed it, but I went ahead and reloaded Ubuntu and typed in the command.
 
Thanks so much! :DDDDDDDDDDDDDDDDDDD
:D:D:D:D:D:D
 
I don't know what you did, but I owe you my laptop.

---

### Post by wilee-nilee on 2011-03-13
> **khoraski said:**
> I typed in the first two commands, and then when I rebooted I forgot to put the CD back in and it brought me to the boot menu! :D
It fixed it, but I went ahead and reloaded Ubuntu and typed in the command.
 
Thanks so much! :DDDDDDDDDDDDDDDDDDD
:D:D:D:D:D:D
 
I don't know what you did, but I owe you my laptop.

Here's the clue; I saw this on the script.
```
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **partition #7** for /boot/grub.
```

Your install is on sda6=partition 6 so you just reloaded grub to the mbr and had it now pointing at the correct partition. You boot in after the commands without going through the cd so you did it just right. Here is the link of the commands for future reference.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by khoraski on 2011-03-13
> **wilee-nilee said:**
> Here's the clue; I saw this on the script.
```
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **partition #7** for /boot/grub.
```

Your install is on sda6=partition 6 so you just reloaded grub to the mbr and had it now pointing at the correct partition. You boot in after the commands without going through the cd so you did it just right. Here is the link of the commands for future reference.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Okay. Again, thanks. 
Oh, and could this happen again? And if so, would these same three commands fix it?

---

### Post by wilee-nilee on 2011-03-13
> **khoraski said:**
> Okay. Again, thanks. 
Oh, and could this happen again? And if so, would these same three commands fix it?

Are you using the startup manager, if so when you get a kernel upgrade it doesn't follow the grub lines it just still tries to boot from where it was pointed. 

Kind of a unusual thing to happen, but I don't know what voodoo you were doing beforehand.:)

If you look at the link there is a fdisk -l command to confirm the booting partition so you run that then the other two. There are two other sets of commands below the first set if the ones you did don't work.

---

### Post by khoraski on 2011-03-13
> **wilee-nilee said:**
> Are you using the startup manager, if so when you get a kernel upgrade it doesn't follow the grub lines it just still tries to boot from where it was pointed. 

Kind of a unusual thing to happen, but I don't know what voodoo you were doing beforehand.:)

If you look at the link there is a fdisk -l command to confirm the booting partition so you run that then the other two. There are two other sets of commands below the first set if the ones you did don't work.

Should I upgrade my kernel like this?

[http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/)

---

### Post by wilee-nilee on 2011-03-13
> **khoraski said:**
> Should I upgrade my kernel like this?

[http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/)

I just let the kernel upgrades that come from the repos install, and don't use startup manager, so I never have problems. I am not familiar with the method in the link to be honest. Looks correct though there is a kernel repo that will have various releases including the latest I don't have the the http though. 

Did you remove or add any partitions right before this or at some time before rebooting, that will change the partition numbers.

---

