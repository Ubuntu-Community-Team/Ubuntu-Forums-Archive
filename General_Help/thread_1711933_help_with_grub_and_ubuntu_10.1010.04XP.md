---
title: "help with grub and ubuntu 10.10/10.04/XP"
date: 2011-03-22
forum: General Help
---

### Post by michaelbr on 2011-03-22
Greetings:
I had a dual boot system (Ubuntu 10.04 and XP) and had a problem with my XP and had to reinstall it. Unfortunately I forgot to backup the boot file. After the re-installation of XP, I can't load Ubuntu 10.04 anymore, so I booted up Ubuntu 10.10 using USB, during the install, it didn't give an option to do a repair, so I did an install along with other OS. After the install, the GRUB showed now 3 OS:
Ubuntu 10.10
Win XP
Ubuntu 10.04
How can I remove the newly installed Ubuntu 10.10 without damaging the other OS? I'd like to keep the 10.04 because it's all customized and have several apps already installed.

---

### Post by wilee-nilee on 2011-03-22
Boot into 10.04 open the terminal and load its grub to the mbr with.
sudo grub-install /dev/sda
this is if the sda is the correct hd
then run 
sudo update-grub

10.10 is now free to be deleted. just run the update grub after deleting to remove the grub menu stanzas.

---

### Post by rockager on 2011-03-22
this MAY work:

1.boot into 10.04
2.run gparted (partition editor), get it from the repositories if you don't have it.
3.delete the 10.10 partition through gparted (this would fail if the 10.10 partition is in a secondary partition with 10.04 having a higher partition number.)
4.update grub (type 'sudo update-grub' in a terminal)
5. restart

I'M NOT SURE IF THIS METHOD WILL WORK SO USE IT AS A LAST RESORT.

the worst: you will have to install 10.10 again to get back grub (so you'll be back to square one)
the best: you will get your old boot config back

---

### Post by michaelbr on 2011-03-25
> **wilee-nilee said:**
> Boot into 10.04 open the terminal and load its grub to the mbr with.
sudo grub-install /dev/sda
this is if the sda is the correct hd
then run 
sudo update-grub

10.10 is now free to be deleted. just run the update grub after deleting to remove the grub menu stanzas.

Sorry for the delay in posting back. I had a huge setback, I made a huge mistake, I didn't run the update-grub after deleting the 10.10, when I tried to boot it, I got the following message:
missing partition
grub rescue>
then I got stuck, neither XP nor Ubuntu will come up, so I have no choice other than re-install the XP again. Right now the XP is up, but how do I get back to my 10.04 without re-installing it? I have a USB drive with 10.10 bootable in it, but I'd like to keep my previous 10.04 (it's all configured). During the 10.04 install, it didn't give me an option to repair existing Ubuntu, could you please give step by step instructions on how to install the grub without damaging my XP and Ubuntu 10.04 already installed.

---

### Post by Quackers on 2011-03-25
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then stay in the live desktop, as that's where the fix can be run from.

---

### Post by michaelbr on 2011-03-27
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then stay in the live desktop, as that's where the fix can be run from.

Thanks Quackers for your help, please find below the result

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

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

/dev/sda1    *             63    24,486,635    24,486,573   7 HPFS/NTFS
/dev/sda2          24,487,934   625,121,279   600,633,346   f W95 Ext d (LBA)
/dev/sda5          40,965,813    45,062,324     4,096,512  82 Linux swap / Solaris
/dev/sda6          45,064,192    75,778,047    30,713,856  83 Linux
/dev/sda7          75,778,668   625,121,279   549,342,612   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        167C30237C2FFC55                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        612fdc45-5144-4842-bebb-53162ba4adce   swap                                     
/dev/sda6        858f60b0-f3c0-4b60-8d35-2252a89b3760   ext4                                     
/dev/sda7        843051B93051B2C2                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb         0C97-2402                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
set default="4"
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=858f60b0-f3c0-4b60-8d35-2252a89b3760 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=858f60b0-f3c0-4b60-8d35-2252a89b3760 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=858f60b0-f3c0-4b60-8d35-2252a89b3760 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=858f60b0-f3c0-4b60-8d35-2252a89b3760 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 858f60b0-f3c0-4b60-8d35-2252a89b3760
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 38c0ee83c0ee46aa
	drivemap -s (hd0) ${root}
	chainloader +1
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
UUID=858f60b0-f3c0-4b60-8d35-2252a89b3760 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=804adbab-927c-439b-9bf1-31b0387d7eae none            swap    sw              0       0
/dev/sda6	/media/sda6	auto	rw,user,auto,exec,utf8	0	0

=================== sda6: Location of files loaded by Grub: ===================


  27.5GB: boot/grub/core.img
  23.6GB: boot/grub/grub.cfg
  28.0GB: boot/initrd.img-2.6.32-29-generic
  25.2GB: boot/initrd.img-2.6.32-30-generic
  28.0GB: boot/vmlinuz-2.6.32-29-generic
  27.9GB: boot/vmlinuz-2.6.32-30-generic
  25.2GB: initrd.img
  28.0GB: initrd.img.old
  27.9GB: vmlinuz
  28.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 02 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 a0 3b 00 80 00 29 02  24 97 0c 4e 4f 20 4e 41  |..;...).$..NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e fa fc 31 c9 8e d1  |.U."..~..N..1...|
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
00000100  7d 00 66 b8 40 16 00 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
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

### Post by Quackers on 2011-03-27
It appears that you have XP installed in sda1 and Ubuntu 10.04.2 installed in sda6 - no 10.10 is shown.
To put grub back in the mbr please boot from the live cd/usb and select "try ubuntu" and when the desktop loads open up a terminal and copy/paste the following commands in, one at a time and pressing enter after each line.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If this reports no errors, you can reboot, taking the disc out and then Ubuntu should boot directly.
If it does, open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to make sure that the Windows Loader for sda1 is found.
If it is, reboot and select Windows from your new grub menu.
You should now be good :-)

---

### Post by michaelbr on 2011-03-28
> **Quackers said:**
> It appears that you have XP installed in sda1 and Ubuntu 10.04.2 installed in sda6 - no 10.10 is shown.
To put grub back in the mbr please boot from the live cd/usb and select "try ubuntu" and when the desktop loads open up a terminal and copy/paste the following commands in, one at a time and pressing enter after each line.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If this reports no errors, you can reboot, taking the disc out and then Ubuntu should boot directly.
If it does, open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to make sure that the Windows Loader for sda1 is found.
If it is, reboot and select Windows from your new grub menu.
You should now be good :-)

Thanks Quackers, your method worked beautifully, I got 10.04 back and grub worked just as you said. Thanks again for your help and detailed step by step explanation.

---

