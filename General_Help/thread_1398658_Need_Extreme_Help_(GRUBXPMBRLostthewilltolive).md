---
title: "Need Extreme Help (GRUB/XP/MBR/Lostthewilltolive)"
date: 2010-02-04
forum: General Help
---

### Post by sweeper128 on 2010-02-04
Probably be easier to list everything I have done, then ask questions.

It all started when I tried to install BURG. I went ahead, tried to install it, and got it sort of working. But It only showed my XP partition, then chain booted to GRUB, because I idiotically tried to remove BURG from the wrong place and installed GRUB on my XP partition instead of the MBR. So I got a crazy chainboot which put me back to my GRUB when I tried XP. 
```
grub-install "(hd0,1)"
``` or ```
grub-install "/dev/sda1
``` (which was a terrible mistake.)

After looking about for a while, trying to get Super Grub Disk to try to sort it out, I saw a possible solution - download the mbr package and install it to my XP Partition, from my Linux Mint 8 partition.
```
sudo install-mbr dev/sda1
```
 Big mistake. This, after a reboot gave me a black screen with "MBR:1234F" and no possible options. So I decided to reset it all - quickly create a Linux Mint partition, thus fixing GRUB once and for all.

**This was not the case**. XP is now gone. Vanished, as you can see from my terminal code:

```

sweeper128@sweeper128-laptop ~/Desktop $ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 8 Helena - Main Edition (8) on /dev/sda7
done
sweeper128@sweeper128-laptop ~/Desktop $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97be5b6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9585    76991481    7  HPFS/NTFS
/dev/sda2            9586       19457    79296840    5  Extended
/dev/sda5            9586       18691    73143913+  83  Linux
/dev/sda6           19087       19457     2980026   82  Linux swap / Solaris
/dev/sda7           18692       19061     2971993+  83  Linux
/dev/sda8           19062       19086      200781   82  Linux swap / Solaris

Partition table entries are not in disk order
sweeper128@sweeper128-laptop ~/Desktop $ sudo os-prober
/dev/sda7:Linux Mint 8 Helena - Main Edition (8):LinuxMint:linux

```

Now /dev/sda1 is where XP is, and I presumed that's where it boots from. /dev/sda5 is my main Linux partition and /dev/sda7 is my quicky fix-GRUB one.

Long story short - I screwed up royally.

Now I'm wondering if there is a solution to this? Although my files where copied over from XP when I installed Mint for the first time, I have not made any backup of it.
I would prefer someway to remove the changes that install-mbr did to my XP so GRUB can recognise it.

Sorry for rambling. I just don't want to take extreme measures like formatting my whole laptop and starting everything again.

---

### Post by audiomick on 2010-02-04
Hi Sweeper.
I am not going to be able to fix this, it is a bit to convoluted for me, but I am sure it is possible. As a start, I would suggest going here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the instructions and post the result back here. The output is a pretty comprehensive list of the state of your system, and will likely help anyone who can help you.
The file is quite long. Use the # button at the top of the posting window to put code tags around it.

---

### Post by Leppie on 2010-02-04
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by audiomick on 2010-02-04
> **Leppie said:**
> could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?
beat you!

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> beat you!
you stealin my beanses as well now? :P

---

### Post by sweeper128 on 2010-02-04
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97be5b6a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,983,024   153,982,962   7 HPFS/NTFS
/dev/sda2         153,983,025   312,576,704   158,593,680   5 Extended
/dev/sda5         153,983,088   300,270,914   146,287,827  83 Linux
/dev/sda6         306,616,653   312,576,704     5,960,052  82 Linux swap / Solaris
/dev/sda7         300,270,978   306,214,964     5,943,987  83 Linux
/dev/sda8         306,215,028   306,616,589       401,562  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        9812ca0c-1fdf-41e8-89c0-fe2b370b3599   ext4                                     
/dev/sda6        d85a1e6e-8aee-4fde-a9b3-2796d758164a   swap                                     
/dev/sda7        7c922c7b-4db8-40f0-88b0-60049056c6a5   ext4                                     
/dev/sda8        aab20813-0913-4140-8c2c-6079e7ece972   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-17-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-16-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda7) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7c922c7b-4db8-40f0-88b0-60049056c6a5 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7c922c7b-4db8-40f0-88b0-60049056c6a5 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set gfxmode="1280x800"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/grub/themes/sora/theme.txt
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d85a1e6e-8aee-4fde-a9b3-2796d758164a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda7)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7c922c7b-4db8-40f0-88b0-60049056c6a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7c922c7b-4db8-40f0-88b0-60049056c6a5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7c922c7b-4db8-40f0-88b0-60049056c6a5 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-16-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-16-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9812ca0c-1fdf-41e8-89c0-fe2b370b3599
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=9812ca0c-1fdf-41e8-89c0-fe2b370b3599 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7c922c7b-4db8-40f0-88b0-60049056c6a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=aab20813-0913-4140-8c2c-6079e7ece972 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 153.7GB: boot/grub/core.img
 153.7GB: boot/grub/grub.cfg
 153.7GB: boot/initrd.img-2.6.31-14-generic
 153.7GB: boot/vmlinuz-2.6.31-14-generic
 153.7GB: initrd.img
 153.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 63 6f  |..............co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Leppie on 2010-02-04
if you have a windows installation disk, it would be good to check the partition.
otherwise you could try with a vista recovery disk: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
or ultimate boot cd: [http://www.ubcd4win.com/downloads.htm](http://www.ubcd4win.com/downloads.htm)

---

### Post by audiomick on 2010-02-04
As I thought, it is to complicated for me.
You have a complete set of grub files in sda5 and sda7, both of which should boot both of the existing Linux installs. Grub is currently using the files on sda7

As far as sda1 goes, the script recognises that as an NTFS partition, but cant see an operating system there. Also, the hieroglyphics in the very last section of the file is something I have never seen before.

Maybe this
```
=========================== Unknown MBRs/Boot Sectors/etc =======================

[COLOR=Red]**Unknown BootLoader  on sda1**[/COLOR]

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
```is why the XP can't be found. _**Maybe**_ it is still there, but "invisible".
I don't want to suggest anything for fear of making it worse.

edit: Ok, this time Leppie beat me. Do what he says. He knows more about this sort of thing than me... ;)

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> is why the XP can't be found. _**Maybe**_ it is still there, but "invisible".
I don't want to suggest anything for fear of making it worse.

edit: Ok, this time Leppie beat me. Do what he says. He knows more about this sort of thing than me... ;)
i think the installation of grub2 into the boot sector of sda1 has messed up something. normally the boot info script should be able to find both grub2 and the xp boot loader in the partition. i therefore believe it's best to first check the partition with chkdsk or another windows application which can check the partitions integrity properly.

---

### Post by audiomick on 2010-02-04
> **Leppie said:**
> i think the installation of grub2 into the boot sector of sda1 has messed up something. normally the boot info script should be able to find both grub2 and the xp boot loader in the partition. i therefore believe it's best to first check the partition with chkdsk or another windows application which can check the partitions integrity properly.
Sounds good to me.

---

### Post by john newbuntu on 2010-02-04
The boot sector of XP needs to be fixed.  Use the recovery console using Win XP CD and run 
```
fixboot c:
```
presuming c:\ to be the windows boot partition.

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> Sounds good to me.
danke, das freud mich ;)

---

### Post by sweeper128 on 2010-02-09
Will do, as soon as I can find my disk.

Though it is a sort of excuse to get W7... :P

---

