---
title: "Problems with booting Ubuntu 10.10"
date: 2011-02-09
forum: General Help
---

### Post by Jukselapp on 2011-02-09
Hi,

After upgrading from 10.04 to 10.10 I have had some problems booting my Ubuntu.

It all started when restarting after the upgrade, and I got the error;
```

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.13.3 (Ubuntu 1:1.13.3.1ubuntu11) built-in shell (ash)

(initramfs)
```

After searching the Internet, I found a "solution". I just had to boot with a USB stick with the Ubuntu Rescue Remix (the normal Ubuntu USB won't boot either), and i wrote;
```
sudo fsck /dev/sdb5
```

Now I could start my Ubuntu again. So whats the problem? If I turn off my computer the normal way, there is no problem, but if I log off, put it into sleep mode, if something happens and I have to turn it off with the button it goes back to the first problem, and I have to reboot it with the USB stick and fix it all over again! If I don't have the USB stick with me, I probably wont be able to use my laptop!

Do anybody know how to fix it? I'm a really Linux newbie ;)

---

### Post by dino99 on 2011-02-09
boot from usb stick, then:

unplug the stick

sudo gedit /etc/fstab

you should only have 2 lines: the ubuntu partition to boot on, and the swap partition. Comment the other lines with # at their very beginning, or remove them.

then:

sudo update-grub

then reboot (without stick)

---

### Post by Jukselapp on 2011-02-09
I tried to boot from the USB and then unplug it, but then I can't do anything.

Anyways, I tried to run gedit in Ubuntu and got this;

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ace801a3-c893-44da-a234-61d83ccae381 none            swap    sw              0       0
```

---

### Post by dino99 on 2011-02-09
seems to be ok

---

### Post by Rubi1200 on 2011-02-09
Hi and welcome to the forums Jukselapp :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jukselapp on 2011-02-10
Hi and thanks!

When my computer crashes, I'm not able to run the Ubuntu Live from a USB, only the Ubuntu Rescue Remix. But after running the command
```
sudo fsck /dev/sdb5
``` I'm able to run Ubuntu from my computer again. At least until the next time i "log off" or something like that.

But I tried to run the boot info script on my Ubuntu installation.

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
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,595,200   210,178,394   197,583,195   7 HPFS/NTFS
/dev/sda3         210,178,456   312,580,095   102,401,640   f W95 Ext d (LBA)
/dev/sda5         210,178,458   214,965,146     4,786,689   7 HPFS/NTFS
/dev/sda6         214,966,272   308,494,335    93,528,064  83 Linux
/dev/sda7         308,496,384   312,580,095     4,083,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80DC2799DC27890C                       ntfs       PQSERVICE                     
/dev/sda2        2CF646C7F646914E                       ntfs       JUKSELAPP                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01CBB74AF5A97EE0                       ntfs       Medier                        
/dev/sda6        dc8dc6ca-2086-4bbb-9caf-79ab7016cd25   ext4                                     
/dev/sda7        ace801a3-c893-44da-a234-61d83ccae381   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
set locale_dir=($root)/boot/grub/locale
set lang=nb
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dc8dc6ca-2086-4bbb-9caf-79ab7016cd25
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 80dc2799dc27890c
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2cf646c7f646914e
	drivemap -s (hd0) ${root}
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
UUID=dc8dc6ca-2086-4bbb-9caf-79ab7016cd25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ace801a3-c893-44da-a234-61d83ccae381 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 144.6GB: boot/grub/core.img
 137.2GB: boot/grub/grub.cfg
 144.7GB: boot/initrd.img-2.6.32-24-generic
 144.7GB: boot/initrd.img-2.6.32-27-generic
 143.6GB: boot/initrd.img-2.6.32-28-generic
 140.0GB: boot/initrd.img-2.6.35-25-generic
 144.6GB: boot/vmlinuz-2.6.32-24-generic
 144.6GB: boot/vmlinuz-2.6.32-27-generic
 144.7GB: boot/vmlinuz-2.6.32-28-generic
 144.8GB: boot/vmlinuz-2.6.35-25-generic
 140.0GB: initrd.img
 143.6GB: initrd.img.old
 144.8GB: vmlinuz
 144.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  9e 6b 14 e8 22 b1 cc 43  79 a7 c4 99 14 60 3b 03  |.k.."..Cy....`;.|
00000010  e5 c0 79 a1 c8 f5 4b 4c  71 65 68 fd 6f 3a a1 6e  |..y...KLqeh.o:.n|
00000020  fd 48 32 40 18 3c dc 07  41 42 10 c1 c4 b4 fe 1f  |.H2@.<..AB......|
00000030  34 3a 03 40 78 0d cd 97  a0 eb ab 9e 02 3d 88 90  |4:.@x........=..|
00000040  ec 88 a1 08 98 3f 07 1f  04 30 52 97 b1 f4 ac 96  |.....?...0R.....|
00000050  46 bf 36 b1 43 a5 5e e7  af 18 f2 05 12 c9 ad d2  |F.6.C.^.........|
00000060  bf fd 64 4e 07 9a 5e 40  e0 3b 00 78 21 31 b3 f0  |..dN..^@.;.x!1..|
00000070  1c 3d fb 57 ec ff f7 b6  e0 88 c3 58 83 bc 5d d2  |.=.W.......X..].|
00000080  63 21 b4 ba e3 54 a4 a8  f8 1e 42 f1 e7 d2 34 3e  |c!...T....B...4>|
00000090  cf 02 22 4f b7 fd 6a e8  39 5e ce 92 c2 da bc 10  |.."O..j.9^......|
000000a0  30 6d d4 7d 3c 0f 05 30  38 20 00 7e b4 d0 f6 81  |0m.}<..08 .~....|
000000b0  c5 60 c0 61 c9 7d 3a 95  8b 75 9f b0 d4 49 d9 aa  |.`.a.}:..u...I..|
000000c0  ca ad d2 d4 19 99 d5 de  2f c2 56 01 a8 9e b0 b9  |......../.V.....|
000000d0  6c f3 12 2d 2f ba a0 af  90 aa 8c c9 cc bb 53 a6  |l..-/.........S.|
000000e0  f3 5e d6 18 6d 8f a8 f3  4d 65 b2 4f f4 ab a6 f8  |.^..m...Me.O....|
000000f0  15 e8 14 ef 1c fd 05 fa  cb fb 0b f9 70 30 28 32  |............p0(2|
00000100  98 50 01 14 00 ae a4 c9  12 b0 24 a3 28 e6 83 f8  |.P........$.(...|
00000110  1c 7e 25 82 af fe 12 be  91 33 6c 31 e5 69 38 3c  |.~%......3l1.i8<|
00000120  f7 9b 2c 4f 3f 95 54 1c  e7 37 d2 42 d2 df c9 bc  |..,O?.T..7.B....|
00000130  51 6d 23 3a c1 c1 00 1c  b8 20 b1 a3 df 82 8e 60  |Qm#:..... .....`|
00000140  3a 36 3e c4 6d 52 6f 6b  25 8a 60 38 14 dd 07 59  |:6>.mRok%.`8...Y|
00000150  a4 53 03 c5 2a 7b c8 16  2c 3f 1f fe 7e 28 49 22  |.S..*{..,?..~(I"|
00000160  6a 0e be ea 92 ce a3 99  03 23 fd 81 2d 5a 5e c2  |j........#..-Z^.|
00000170  ec 54 d1 67 81 5a db 3c  51 de d1 b7 10 0a dc 2b  |.T.g.Z.<Q......+|
00000180  78 41 3e 0a 26 e4 1a 44  47 c0 b6 1e 04 e6 28 4c  |xA>.&..DG.....(L|
00000190  16 21 4f a2 8c a0 86 0e  01 c2 30 ff 68 96 c0 e9  |.!O.......0.h...|
000001a0  ac 1d e5 bd 51 cc fa b6  b6 72 95 c1 b5 44 bc 43  |....Q....r...D.C|
000001b0  05 62 41 2c 10 18 a3 cd  4c 01 a0 a2 54 af 00 fe  |.bA,....L...T...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 01 0a 49 00 00 fe  |............I...|
000001d0  ff ff 05 fe ff ff 6d 0c  49 00 fb 21 93 05 00 00  |......m.I..!....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2011-02-10
Not sure why you would be running fsck on sdb5; there is no such partition according to the results.

Your Ubuntu install is on sda6 and as far as booting is concerned the results seem normal.

If you can get into the Ubuntu install I would try a couple of things:

```
sudo apt-get autoclean

sudo apt-get clean

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install -f

sudo dpkg --configure -a
```

Run the commands separately so that if any return errors you can post it back here.

You could try running fsck on sda6 from the live medium (and NOT from within Ubuntu), but I don't see anything in the script that would indicate that as a necessity.

---

### Post by P4man on 2011-02-10
THis is all quite strange. Checking a partition that doesnt exist, wouldnt solve anything. Being unable to boot a livecd, while you can boot the rescue cd is just as weird.

Im going to do some wild guesses here.. First, a possible difference between booting livecd and rescue cd is that the livecd tries to mount /swap partitions on the harddrive, whereas ubuntu rescue might not (not even sure of that, but it seems very plausible).

Secondly, doing "fsck /dev/sdb5", when there is no sdb drive, is pointless. But, you might be doing a warm reboot after that (so not shutting the machine down entirely) and THAT might be what "fixes" the problem.

Putting one and two together, I wonder is there isnt a problem with the drive or drive controller upon a cold boot, or if its a bios problem, something not always initializing properly.  

A long shot, but Id do two things: first check the drive smart status (in system > administration > disk utility). If it says smart is not supported, go in to your bios and enable smart support for your drive.

edit: ignore the below suggestion, seeing your reply.[COLOR="Silver"]
Secondly, you could try increasing the rootdelay for your drive. To do that, add 'rootdelay=90' (without quotes) to your kernel options. My signature has a link that explains how to set kernel options for one boot or permanently.  If rootdelay doesnt help, you might want to experiment with the other parameters I mentioned there, like acpi_osi. That is assuming you always get a grub menu.[/COLOR]

---

### Post by Jukselapp on 2011-02-10
Yeah you are right, i did run the command on /dev/sdb6 !

Anyways, I tried to run these commands in the install, and here are the results:

Command:
```
sudo apt-get autoclean
```
Result:
```
E: dpkg ble avbrutt. Du må kjøre «sudo dpkg --configure -a» manuelt for å rette problemet,
```

*(Translated from Norwegian; E: dpkg was canceled. You have to run «sudo dpkg --configure -a» manually to fix the problem.)*

Command:
```
sudo apt-get clean
```
Nothing "happend", so I guess it maybe works.

Command:
```
sudo apt-get update
```
Result:
It downloads a lot of stuff, but in the end I get the same error as I got running the first command.

Command:
```
sudo apt-get upgrade
```
and
```
sudo apt-get install -f
```
Result:
Same error as in the first command.

Command:
```
sudo dpkg --configure -a
```
Result:
```
E: Cannot open uninstall: /usr/share/cli-common/packages.d//libmono-addins-gui0.2-cil.mono at /usr/share/cli-common/runtimes.d/mono line 91.
E: Installation of libmono-addins-gui0.2-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
E: Cannot open uninstall: /usr/share/cli-common/packages.d//libndesk-dbus1.0-cil.mono at /usr/share/cli-common/runtimes.d/mono line 91.
E: Installation of libndesk-dbus1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
E: Cannot open uninstall: /usr/share/cli-common/packages.d//libndesk-dbus-glib1.0-cil.mono at /usr/share/cli-common/runtimes.d/mono line 91.
E: Installation of libndesk-dbus-glib1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 6 assemblies from libnunit2.4-cil into Mono
E: Cannot open uninstall: /usr/share/cli-common/packages.d//libnunit2.4-cil.mono at /usr/share/cli-common/runtimes.d/mono line 91.
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: Feil ved behandling av mono-gac (--configure):
 underprosessen installerte post-installation skript returnerte feilstatus 9
Behandler utløsere for python-support ...
dpkg: ugjenopprettelig kritisk feil, avbryter:
 klarte ikke tømme oppdatert status for «python-support»: Filsystem med kun lesetilgang
```
*(Translated; dpkg: unfixable critical fault, cancel: couldn't emtpy updated status for "python-support": File system only readable.)*

I tried to run the command a second time, then i just get;
```
sudo: Can't open /var/lib/sudo/jukselapp/0: Filsystem med kun lesetilgang
dpkg: får ikke tilgang til dpkg-statusområdet: Filsystem med kun lesetilgang

```
[I](Translated; sudo: Can't open /var/lib/sudo/jukselapp/0: File system only readable.
dpkg: doesn't get permission to dpkg-status area: File system only readable.)[/I]

---

### Post by Jukselapp on 2011-02-10
It says:

SMART status: Disk is healthy.

---

### Post by P4man on 2011-02-10
Hang on a second. If you boot from the rescue remix, I take it sda is your USB stick and sdb becomes your harddrive? in that case, "fsck /dev/sdb6" would be correct indeed.

Your filesystem is mounted a readonly though. Something bad is going on, but frankly I have no idea what else to do. Perhaps you can post the output of

```
mount
```

Also, try this:

```
sudo touch /forcefsck 
```

then reboot. It should force a filesystem check, not that it would be very different from doing so from the rescue cd I imagine, but at least im sure it will run on the correct partition. After that, try the commands you just tried again to fix your dpkg.

---

### Post by Jukselapp on 2011-02-10
"mount" gives this
```
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jukselapp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jukselapp)

```

I will try to do the filesystem check!

---

### Post by P4man on 2011-02-10
Your filesystem is not mounted as read only, judging by that output.  Im at a loss :confused:

Unless someone comes up with a better idea, Id start considering doing a full reinstall.

---

### Post by Jukselapp on 2011-02-10
The filesystem check found this error:
```
The disk drive for /tmp is not ready yet or present
```

After doing the check Ubuntu started in something that reminds "about safe" mode in windows. I had to restart twice to get back to "normal" mode.

---

### Post by P4man on 2011-02-10
Is your  ubuntu root partition full perhaps?

---

### Post by Jukselapp on 2011-02-10
I don't know how to check if root is full, but sdb6 isn't..

---

