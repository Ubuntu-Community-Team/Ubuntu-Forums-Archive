---
title: "Operating System Not Found?"
date: 2011-03-20
forum: General Help
---

### Post by Will F on 2011-03-20
I was running Ubuntu 10.10 on a IBM ThinkPad laptop when I pulled the battery out. It was plugged in, but it still went dead. Now whenever I boot it back up it goes into a GRUB shell. When I exit the GRUB shell (lit. "exit"), it says "Operating System Not Found" and will not boot up. I booted up off of a live cd and backed up all of my data, however I would like to not have to reinstall the entire OS. I have reinstalled the GRUB loader using [these instructions]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/"), however it still gives me the same message. Does anyone know what is going on and how to fix it?

---

### Post by Hedgehog1 on 2011-03-20
Well, now we both know not to yank the battery out even while powered up.  I would think that was OK to do, as well. :confused:

We need to get a look at what shape your partitons are in.

Please boot off the LiveCD/LiveUSB, select try, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Will F on 2011-03-20
So I did as you asked, the output is attached

---

### Post by Hedgehog1 on 2011-03-20
I will post the results from your text file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/hda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sda

hda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000528a0

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *          2,048    74,840,063    74,838,016  83 Linux
/dev/hda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/hda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 3926 MB, 3926949888 bytes
121 heads, 62 sectors/track, 1022 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004eb9b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     7,667,043     7,666,982   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        7d9368ce-fbc0-4892-b594-896276c44651   ext4                                     
/dev/hda5        ca066796-1e04-4538-a323-12ff1a4e896b   swap                                     
/dev/loop0                                              squashfs                                 
/dev/sda1        B1C8-6873                              vfat       KINGSTON DT                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sda1        /media/cdrom0            vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== hda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7d9368ce-fbc0-4892-b594-896276c44651 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7d9368ce-fbc0-4892-b594-896276c44651
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== hda1/etc/fstab: ===============================

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
UUID=ca066796-1e04-4538-a323-12ff1a4e896b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== hda1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  38.0GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   1.0GB: boot/initrd.img-2.6.35-24-generic
   2.8GB: boot/initrd.img-2.6.35-25-generic
   1.5GB: boot/initrd.img-2.6.35-27-generic
   3.1GB: boot/initrd.img-2.6.35-28-generic
  34.7GB: boot/vmlinuz-2.6.35-22-generic
  34.7GB: boot/vmlinuz-2.6.35-24-generic
    .0GB: boot/vmlinuz-2.6.35-25-generic
   1.5GB: boot/vmlinuz-2.6.35-27-generic
   1.7GB: boot/vmlinuz-2.6.35-28-generic
   3.1GB: initrd.img
   1.5GB: initrd.img.old
   1.7GB: vmlinuz
   1.5GB: vmlinuz.old

=========================== sda1/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd800.gz
    .1GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .1GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hda2

00000000  14 91 a8 35 02 98 70 c3  35 71 12 08 79 e5 2d f6  |...5..p.5q..y.-.|
00000010  fe 37 0b 40 14 ef 15 4a  20 b8 89 fe f6 2a d0 64  |.7.@...J ....*.d|
00000020  58 dd 9d 80 ad 03 cf f8  a1 0d 00 c6 0e 85 48 60  |X.............H`|
00000030  87 4e 4b dc 72 24 f5 2d  2f c0 61 88 ce af b6 21  |.NK.r$.-/.a....!|
00000040  74 a1 39 a3 67 05 29 6f  7b 34 4e f2 8a 4c 7f 94  |t.9.g.)o{4N..L..|
00000050  59 9e 67 79 3a 32 1c 62  b8 84 25 4a 20 3d d1 59  |Y.gy:2.b..%J =.Y|
00000060  5f 16 07 35 6d 36 ea bc  9a bc 64 ba 8d b8 fe 9d  |_..5m6....d.....|
00000070  ed 22 d7 62 ab 00 d9 9f  4d d6 5e d9 dd e7 c9 1f  |.".b....M.^.....|
00000080  89 e2 d7 d7 d4 bd fa ed  c7 aa 9e a5 27 05 61 9a  |............'.a.|
00000090  a1 6f fc b8 59 b8 cd 24  f6 e3 e4 93 b1 8c 35 59  |.o..Y..$......5Y|
000000a0  68 1b 4d a3 c8 cc 39 a7  4a 6d d2 4b d1 31 27 a7  |h.M...9.Jm.K.1'.|
000000b0  41 a6 4d e1 37 77 05 ed  ef 1a bd a0 1c 61 90 e1  |A.M.7w.......a..|
000000c0  6e 30 56 1c 27 c0 95 01  ed 21 61 39 3c 31 84 ac  |n0V.'....!a9<1..|
000000d0  93 5b ef 62 98 03 a0 1d  17 46 1c e5 61 71 ef 8f  |.[.b.....F..aq..|
000000e0  eb be a3 49 77 c2 d8 5c  7c 93 a3 ba ac 9c 17 a4  |...Iw..\|.......|
000000f0  8b 4f 46 3b b9 ee 55 94  78 1e b6 b8 3f 5c fc 51  |.OF;..U.x...?\.Q|
00000100  3f 2b 3e cd 6e 7c df ee  28 53 7f 37 47 8b eb 7f  |?+>.n|..(S.7G...|
00000110  02 25 94 72 a9 f8 f2 ff  8b 61 39 94 dc a1 a2 90  |.%.r.....a9.....|
00000120  4d 6f 73 c5 e1 1a a9 8a  79 f5 7a b6 21 b8 fd d0  |Mos.....y.z.!...|
00000130  d7 8b ec 14 f5 fc 1e dd  04 cb 55 c9 24 bb b3 66  |..........U.$..f|
00000140  ef ee 40 0e f6 59 09 b3  af cb 5a 05 62 0b 5c 58  |..@..Y....Z.b.\X|
00000150  80 60 81 80 15 02 0e 2b  c8 60 80 57 67 c0 16 d0  |.`.....+.`.Wg...|
00000160  06 85 b0 01 88 43 ba 93  65 56 4f 37 3e bf 02 96  |.....C..eVO7>...|
00000170  76 35 7a 25 cf 64 39 7f  be 04 a7 eb a7 27 8f e8  |v5z%.d9......'..|
00000180  e5 f6 ac b1 cf 89 4e 3d  78 32 d4 a3 ab 3d 18 7d  |......N=x2...=.}|
00000190  e0 17 25 03 61 b3 9b 8a  2a b6 83 ea 7a 2d 9d bf  |..%.a...*...z-..|
000001a0  f6 52 68 0c 16 b9 d5 1f  2e 48 2a f5 6b f1 66 fd  |.Rh......H*.k.f.|
000001b0  82 de a3 33 ed 7e 93 c7  f5 bd 00 28 bf 2c 00 fe  |...3.~.....(.,..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 79 00 00 00 00 00  |........>.y.....|
00000020  26 fd 74 00 38 1d 00 00  00 00 00 00 02 00 00 00  |&.t.8...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 73 68 c8 b1 4b  49 4e 47 53 54 4f 4e 20  |..)sh..KINGSTON |
00000050  44 54 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |DTFAT32   ..1...|
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
00000100  7d 00 66 b8 f8 08 3e 00  66 ba 00 00 00 00 bb 00  |}.f...>.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

hdc 
```

---

### Post by Hedgehog1 on 2011-03-20
OK - I see the issue.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**[COLOR="Red"]/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]**
# swap was on /dev/sda5 during installation
UUID=ca066796-1e04-4538-a323-12ff1a4e896b none  swap    sw  0 
```

Your /etc/fstab (**F**ile **S**ystem **TAB**le) file is referencing the ext4(Linux/Ubuntu) in a way that has changed.

The **/dev/sda1** really needs to point to **/dev/hda1**, however it is much safer to use the UUID of this drive so this will not happen to you again.

The script you ran gave us the UUID for that drive:
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

**/dev/hda1        7d9368ce-fbc0-4892-b594-896276c44651   ext4**                                     
/dev/hda5        ca066796-1e04-4538-a323-12ff1a4e896b   swap                                     
/dev/loop0                                              squashfs                                 
/dev/sda1        B1C8-6873                              vfat       KINGSTON DT 
```


So, you need to update the /etc/fstab file on your hard disk to look like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0[B][COLOR="Red"]
#/dev/sda1                       /             ext4  errors=remount-ro 0  1
UUID=7d9368ce-fbc0-4892-b594-896276c44651  /   ext4  errors=remount-ro 0  1[/COLOR][/B]
# swap was on /dev/sda5 during installation
UUID=ca066796-1e04-4538-a323-12ff1a4e896b none swap  sw          0  0
```

Commenting out the old line ([COLOR="Red"]**#**[/COLOR]) and adding the new line should do the trick.

***The Hedge***

:KS

---

