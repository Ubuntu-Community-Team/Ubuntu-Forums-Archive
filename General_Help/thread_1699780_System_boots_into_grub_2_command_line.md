---
title: "System boots into grub 2 command line"
date: 2011-03-04
forum: General Help
---

### Post by tranceluv on 2011-03-04
Hi guys

New to ubuntu here! After installing the 10.10 Maverick Meerkat, I decided to have a new partition and install Windows 7 on it for development purposes. So this is the method I worked with:

[LIST]
[*]Partitioned the hard disk with gparted
[*]Formatted the drive in NTFS
[*]Installed Windows
[*]Booted into Ubuntu 10.10 Live CD and re-installed grub on the MBR 
[/LIST]

Now after restarting the system a grub command line boots up. I was able to boot into ubuntu with the following commands:

```

find /vmlinuz
kernel /vmlinuz root=/dev/hda1 (or its equivalent)
initrd /initrd
boot

```

Now my question is this... Is there any way how to load up the grub GUI with the options to boot up Ubuntu or Windows 7 respectively?

I hope this is a simple issue... any help is greatly appreciated!

Thank you

---

### Post by YesWeCan on 2011-03-04
Yes. Boot into Ubuntu and run 'sudo update-grub'

---

### Post by tranceluv on 2011-03-04
Tried that - unfortunately didn't work! The system still gets into a grub> command line interface to boot. Any other ideas please?

---

### Post by tranceluv on 2011-03-10
any help guys? :D

---

### Post by Rubi1200 on 2011-03-10
Please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by tranceluv on 2011-03-10
> **Rubi1200 said:**
> Please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

Hi Rubi1200,

Here is my text:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 788816352 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   643,686,399   643,684,352  83 Linux
/dev/sda2         643,686,400   952,197,119   308,510,720   7 HPFS/NTFS
/dev/sda3         952,199,166   976,771,071    24,571,906   5 Extended
/dev/sda5         952,199,168   976,771,071    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6fe02090-92af-4445-bad6-2ddc5f1a3941   ext4                                     
/dev/sda2        65AC36B70AE228AA                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4a32e9c1-d320-4eac-80c4-547a77c0293a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sr0         /media/FIFA 11           udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sr1         /media/Photoshop         udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=6fe02090-92af-4445-bad6-2ddc5f1a3941 ro  vga=775  quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=6fe02090-92af-4445-bad6-2ddc5f1a3941 ro single  vga=775
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=6fe02090-92af-4445-bad6-2ddc5f1a3941 ro  vga=775  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=6fe02090-92af-4445-bad6-2ddc5f1a3941 ro single  vga=775
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6fe02090-92af-4445-bad6-2ddc5f1a3941
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 65ac36b70ae228aa
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 / ext4 errors=remount-ro,user_xattr 0 1

=================== sda1: Location of files loaded by Grub: ===================


  13.8GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
  13.8GB: boot/grub/stage2
  43.6GB: boot/initrd.img-2.6.35-25-generic-pae
 149.5GB: boot/initrd.img-2.6.35-27-generic-pae
  13.8GB: boot/vmlinuz-2.6.35-25-generic-pae
  13.9GB: boot/vmlinuz-2.6.35-27-generic-pae
 149.5GB: initrd.img
  43.6GB: initrd.img.old
  13.9GB: vmlinuz
  13.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  75 00 4d 00 61 00 6e 00  69 00 66 00 65 00 73 00  |u.M.a.n.i.f.e.s.|
00000010  74 00 20 00 4e 00 33 00  36 00 30 00 20 00 2f 00  |t. .N.3.6.0. ./.|
00000020  4e 00 4f 00 52 00 45 00  47 00 41 00 50 00 50 00  |N.O.R.E.G.A.P.P.|
00000030  49 00 44 00 20 00 2d 00  63 00 6f 00 6e 00 73 00  |I.D. .-.c.o.n.s.|
00000040  75 00 6d 00 65 00 72 00  20 00 2f 00 55 00 73 00  |u.m.e.r. ./.U.s.|
00000050  65 00 4c 00 75 00 4d 00  61 00 6e 00 69 00 66 00  |e.L.u.M.a.n.i.f.|
00000060  65 00 73 00 74 00 20 00  4e 00 33 00 36 00 30 00  |e.s.t. .N.3.6.0.|
00000070  20 00 2f 00 4e 00 4f 00  52 00 45 00 47 00 41 00  | ./.N.O.R.E.G.A.|
00000080  50 00 50 00 49 00 44 00  20 00 2d 00 63 00 6f 00  |P.P.I.D. .-.c.o.|
00000090  6e 00 73 00 75 00 6d 00  65 00 72 00 20 00 2f 00  |n.s.u.m.e.r. ./.|
000000a0  55 00 73 00 65 00 4c 00  75 00 4d 00 61 00 6e 00  |U.s.e.L.u.M.a.n.|
000000b0  69 00 66 00 65 00 73 00  74 00 20 00 4e 00 33 00  |i.f.e.s.t. .N.3.|
000000c0  36 00 30 00 20 00 2f 00  4e 00 4f 00 52 00 45 00  |6.0. ./.N.O.R.E.|
000000d0  47 00 41 00 50 00 50 00  49 00 44 00 20 00 2d 00  |G.A.P.P.I.D. .-.|
000000e0  63 00 6f 00 6e 00 73 00  75 00 6d 00 65 00 72 00  |c.o.n.s.u.m.e.r.|
000000f0  20 00 2f 00 55 00 73 00  65 00 4c 00 75 00 4d 00  | ./.U.s.e.L.u.M.|
00000100  61 00 6e 00 69 00 66 00  65 00 73 00 74 00 20 00  |a.n.i.f.e.s.t. .|
00000110  4e 00 33 00 36 00 30 00  20 00 2f 00 4e 00 4f 00  |N.3.6.0. ./.N.O.|
00000120  52 00 45 00 47 00 41 00  50 00 50 00 49 00 44 00  |R.E.G.A.P.P.I.D.|
00000130  20 00 2d 00 63 00 6f 00  6e 00 73 00 75 00 6d 00  | .-.c.o.n.s.u.m.|
00000140  65 00 72 00 20 00 2f 00  55 00 73 00 65 00 4c 00  |e.r. ./.U.s.e.L.|
00000150  75 00 4d 00 61 00 6e 00  69 00 66 00 65 00 73 00  |u.M.a.n.i.f.e.s.|
00000160  74 00 20 00 4e 00 33 00  36 00 30 00 20 00 2f 00  |t. .N.3.6.0. ./.|
00000170  4e 00 4f 00 52 00 45 00  47 00 41 00 50 00 50 00  |N.O.R.E.G.A.P.P.|
00000180  49 00 44 00 20 00 2d 00  63 00 6f 00 6e 00 73 00  |I.D. .-.c.o.n.s.|
00000190  75 00 6d 00 65 00 72 00  20 00 2f 00 55 00 73 00  |u.m.e.r. ./.U.s.|
000001a0  65 00 4c 00 75 00 4d 00  61 00 6e 00 69 00 66 00  |e.L.u.M.a.n.i.f.|
000001b0  65 00 73 00 74 00 20 00  4e 00 33 00 36 00 00 fe  |e.s.t. .N.3.6...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by WorMzy on 2011-03-10
You've installed the wrong version of grub to the MBR. Ubuntu uses Grub2, you've installed Grub legacy.

Make sure you're booting from a Karmic, Lucid, Maverick or Narwhal LiveCD, then follow this tutorial:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Rubi1200 on 2011-03-11
As WorMzy mentioned, you need to use GRUB2. 

The other problem is that GRUB is installed to the partition on sda1 rather than the MBR of sda.

Following the guide WorMzy posted should resolve the issue.

---

### Post by tranceluv on 2011-03-11
Followed the tutorial given... (booted from a 10.10 live usb, is that ok?)

The terminal gave the following output:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```

What is FlexNet? And how can I remove it? I don't know what I messed up here :/

---

### Post by WorMzy on 2011-03-11
It's some Windows application/DRM software connected to Adobe products (I think). I don't think it causes a problem though*, grub just needs to work around it.


*I mean, not while you're re-installing grub. It can overwrite grub though, if grub has information written to the sectors in question.

---

### Post by YesWeCan on 2011-03-11
You said in post #1 that you can boot Ubuntu. So do that and then update grub from there. Follow the upgrading to grub2 instructions here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
:)

---

### Post by Rubi1200 on 2011-03-11
Once you can boot back into Ubuntu, just run this:

```
sudo update-grub
```

This should pick up the Windows install and you will be dual-booting again.

---

