---
title: "Grub Didn't Install"
date: 2010-05-31
forum: General Help
---

### Post by yamfox on 2010-05-31
Right after a fresh installation, grub did not appear to install. It cannot find stage1. I've tried the commands update, setup, grub-install etc. but they could not find stage1. Does anyone know how to fix this??

---

### Post by yamfox on 2010-05-31
Sorry about the short bump but this is urgent!

---

### Post by drs305 on 2010-05-31
Your profile says you are using Gutsy Gibbon. What release did you install and what do you need to do? If you installed Karmic or Lucid from a clean install you are now using Grub2. You can check with this command (or look at the top of the Grub menu the next time you boot):
```
grub-install -v
```

You can read up on Grub2, if that is what you are using, by visiting the links in my signature line.

---

### Post by yamfox on 2010-05-31
It says I have 1.98

---

### Post by drs305 on 2010-05-31
That is Grub2. The file structure has changed a lot in Grub2. 

This thread contains a review near the top, as well as explanations of how to use the new Grub:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

This thread is shorter and concentrates on the most common tasks:
[http://ubuntuforums.org/showthread.php?t=1302743]("http://ubuntuforums.org/showthread.php?t=1302743")

And here is the community documentation:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

You still haven't said what you want to do, so if the documentation doesn't help just ask.

---

### Post by yamfox on 2010-05-31
I need to install it.

---

### Post by drs305 on 2010-05-31
Well, you were able to tell us which version of Grub you have, so it must have at least attempted to install. 

Are you having problems when you boot? Is it stopping at a grub> or grub rescue> prompt? Is this a dual boot system?

This link describes how to reinstall Grub2 from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

To give us an idea of your setup and boot situation, it would probably be best to post the results of this boot info script. When you post, click on the # icon in the menu to generate "code" tags, and then paste the results within the tags. Here is the boot info link:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by yamfox on 2010-05-31
Here you go

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   115,107,839   115,105,792  83 Linux
/dev/sda2         115,109,886   120,102,911     4,993,026   5 Extended
/dev/sda5         115,109,888   120,102,911     4,993,024  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   946,799,279   946,799,217   7 HPFS/NTFS
/dev/sdb2         946,799,280   976,767,119    29,967,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d54aa7ba-6d9c-4534-91ae-5e9426269f1c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        95fb02df-455b-4e32-8389-a058d48352de   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5EB028CEB028AF09                       ntfs       HP                            
/dev/sdb2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/d54aa7ba-6d9c-4534-91ae-5e9426269f1c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/HP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/apt               iso9660    (ro)


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
search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
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
search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=d54aa7ba-6d9c-4534-91ae-5e9426269f1c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=d54aa7ba-6d9c-4534-91ae-5e9426269f1c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d54aa7ba-6d9c-4534-91ae-5e9426269f1c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5eb028ceb028af09
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 949ca48c9ca46a86
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95fb02df-455b-4e32-8389-a058d48352de none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  56.0GB: boot/grub/grub.cfg
  34.6GB: boot/initrd.img-2.6.32-22-generic-pae
  34.5GB: boot/vmlinuz-2.6.32-22-generic-pae
  34.6GB: initrd.img
  34.5GB: vmlinuz

============================== sdb1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



find --set-root --ignore-floppies \ubuntu\winboot\menu.lst

configfile \ubuntu\winboot\menu.lst



# All your boot are belong to NeoSmart!=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2f 8a ea b6 33 c9 ae 8b  81 04 2a 5f e5 56 2b fe  |/...3.....*_.V+.|
00000010  48 af 53 fa c1 88 95 82  4e ec 12 fd 12 17 6a 3d  |H.S.....N.....j=|
00000020  af cf 89 3a a6 8f e5 a0  50 f2 18 5a 2c 04 3c df  |...:....P..Z,.<.|
00000030  c9 6e e5 55 72 5a c9 b9  d5 9c 5d 3d f6 55 be 4d  |.n.UrZ....]=.U.M|
00000040  80 97 38 46 05 37 a3 9f  b4 4d e8 ae ab df e4 ed  |..8F.7...M......|
00000050  31 2d f9 85 5d b6 eb ab  64 90 6a 08 3f cf 43 54  |1-..]...d.j.?.CT|
00000060  24 93 b0 44 a8 63 a2 2a  32 b1 2b 81 13 b4 96 e4  |$..D.c.*2.+.....|
00000070  c3 73 84 f7 1e c6 79 87  38 84 ae cb 18 3c fb e5  |.s....y.8....<..|
00000080  f4 f4 bd 39 cf b9 45 c9  cf 25 94 e2 8f 0e b9 6a  |...9..E..%.....j|
00000090  71 27 ea fd 70 d3 4d d9  db d6 70 5b 41 dd 44 65  |q'..p.M...p[A.De|
000000a0  cd 7c 27 6f f1 e1 6e e7  57 57 2b 5f 09 5b e1 e6  |.|'o..n.WW+_.[..|
000000b0  f6 a3 98 5d 8e 5f 94 fc  1a 8a 95 c4 ad ab 9d 50  |...]._.........P|
000000c0  95 ce 61 5c 3c ae 47 c3  ee 71 41 c9 36 9c 1a 95  |..a\<.G..qA.6...|
000000d0  ea aa 74 6e 5e b9 ce 74  dd 27 d9 78 86 10 fb 13  |..tn^..t.'.x....|
000000e0  bd 9f d3 cd f7 f5 18 b2  62 a2 31 04 93 d1 7e a4  |........b.1...~.|
000000f0  bd 98 4c e0 42 53 df 05  d2 c5 ef e2 4f d7 64 ac  |..L.BS......O.d.|
00000100  00 fb b4 9c 12 5d d4 ae  9a 43 c8 f1 11 fc 3d a0  |.....]...C....=.|
00000110  62 84 6a b5 7f 52 c1 6c  9e 14 b4 4c 09 37 75 51  |b.j..R.l...L.7uQ|
00000120  4f 9d 14 ca 65 c2 1a 73  63 15 dc 48 ef 70 9a 10  |O...e..sc..H.p..|
00000130  81 4d 36 d2 73 aa af e1  3c 23 3f 3a cd 19 1d 49  |.M6.s...<#?:...I|
00000140  1f b5 3b a2 98 bb a6 26  70 25 da 7f 37 a8 8f b6  |..;....&p%..7...|
00000150  98 b4 5a cb 6a 88 27 5e  22 74 82 ec 03 11 1e bd  |..Z.j.'^"t......|
00000160  ca 80 f7 93 81 17 82 4e  36 da fe 58 ca a9 51 d8  |.......N6..X..Q.|
00000170  e9 35 9c 20 f1 00 a4 f9  73 ed 35 59 c3 d7 4d b5  |.5. ....s.5Y..M.|
00000180  61 a0 43 f4 ab b2 32 e8  a6 31 4d 8e fe bb fb 57  |a.C...2..1M....W|
00000190  78 8c 9d 03 81 07 f8 e0  2d 50 1e 54 c7 a7 80 a0  |x.......-P.T....|
000001a0  e8 61 e5 0d 45 ae ee fc  63 53 6a 1f 0a c4 8f 3a  |.a..E...cSj....:|
000001b0  06 7e 8d f1 a6 6d 23 97  17 70 22 7a 44 9a 00 fe  |.~...m#..p"zD...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 4c 00 00 00  |...........0L...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by yamfox on 2010-05-31
it gives me a grub terminal when I boot.

---

### Post by drs305 on 2010-05-31
The results indicate you have syslinux installed in the MBR of sda. Since your Ubuntu install is located in sda1, to install Grub2 to the MBR of sda and place the Grub2 configuration files in sda1, use the LiveCD and from the LiveCD desktop run these commands:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note in the second command you are installing to the *drive* (sda), not the Linux partition (sda1).

Once it's installed reboot and then run the following to ensure your Windows install is located by Grub2:
```
sudo update-grub
```

---

### Post by yamfox on 2010-05-31
I'm getting error 15

---

### Post by drs305 on 2010-05-31
> **yamfox said:**
> I'm getting error 15

Are you using the Karmic or Lucid LiveCD? Error numbers are associated with Grub legacy and not Grub2.

---

### Post by yamfox on 2010-05-31
I  think it's because I was using the old super grub disc to get into linux (when I boot, I get the windows bootloader still.) I'll try the new one based on grub 2. It was a lucid cd, by the way.

---

### Post by drs305 on 2010-05-31
Also you can check to make sure your BIOS is booting sda first. It's possible it is trying to access the syslinux files in the MBR of sdb if the BIOS is looking there first.

---

### Post by yamfox on 2010-05-31
I'm so confused right now. I just cannot boot! I tried the disc, and it says  file not found and other such things.

---

### Post by drs305 on 2010-05-31
> **yamfox said:**
> I'm so confused right now. I just cannot boot! I tried the disc, and it says  file not found and other such things.

I think you just need to slow down a bit and provide a bit more information when things don't go as expected. 

When did you get the "file not found" message?  Did the LiveCD boot to the Desktop? If not, make sure the BIOS is set to boot a CD/DVD first.

Were you able to open a terminal? Did you enter each command? If so, what was the exact error message, if there was one?

If you were able to boot the CD, run the commands without error, and got the error message upon rebooting, rerun the boot info script and post the results again please.


ADDED: I'm off for the night. If you are still having problems and don't get anyone to respond you could try the Ubuntu IRC support channel on Freenode at #ubuntu.

---

