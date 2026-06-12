---
title: "Ubuntu fails to boot randomly."
date: 2011-04-05
forum: General Help
---

### Post by Jerfo on 2011-04-05
Well, this problem began some time ago and I can't quite remember how or why. This computer is somewhat new as my former HDD died and I bought some other stuff along the new HDD and it wasn't until some time later that I noticed the problems which never happened before, I had been using Ubuntu 10.10 both before and after I got the new HDD.

For some reason, Ubuntu began giving error messages when I tried to run it, most often it would give them over and over unless I decided to give up and try again several minutes later. The error message was always a lot of weird things from which the only thing I could make out was

"Kernel panich - Not Synching: VF:S unable to mount root fs on unknown-block 0,0" (or something like that)

I tried using other kernels but it'd give the same error message, I sometimes even used WinXP, sometimes it'd boot correctly, others it'd reboot.

This became really annoying and tried with a clean install, the first few times I logged in seemed to be working fine but this morning I'm having a problem that seems even worse.

When I try the now only kernel I have available it just remains unmoving from a blinking cursor screen. If I try the recovery mode I get the "Kernel panic..." errror message and when I try with Memory Test, computer just reboots.

---

### Post by searchfgold6789 on 2011-04-05
Sounds like a failing hard disk to me.
You will probably be able from a CD just fine, and any other media you care to choose. I would backup as soon as possible if I were you.

---

### Post by Jerfo on 2011-04-05
Failing?! Dammit, it's nearly new! T_T

Oh yeah. I forgot to mention: WinXP now seems to be working fine, it doesn't fail to boot at all. (hurray! ¬¬)

---

### Post by Rubi1200 on 2011-04-05
I don't agree that a failing hard-drive is necessarily the reason for these error messages.

Rather, it is more likely a sign of a damaged file-system.

Can you please post the results of the boot info script so we can get a better idea of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by searchfgold6789 on 2011-04-05
Damaged filesystem then. Much more likely, especially now that Windows is working.
Run fsck from a Ubuntu Live Media, this will check the filesystem for errors. The format for the command should be:```
fsck /dev/sdXX
```Replace "/dev/sdXX" with the filesystem you want to check.
You might have to "umount" (unmount) the partition first.

---

### Post by coffeecat on 2011-04-05
Indeed. Hold on the new HD order - at least until we've done some investigating. :)

Unfortunately, some HDs do fail very early in their life, but there are many other explanations for what you are seeing.

Agreed with what Rubi1200 suggests, and try this as well:

Boot up with the Ubuntu live CD and go to System > Administration > Disk Utility. Highlight your HD in the left pane and then see what it has to say about SMART. Run a couple of self-tests. Hopefully, that will confirm that the HD is OK.

Also - this could be bad memory. How long have you had it? The way Linux uses memory makes it  more likely than Windows to come across bad memory in the upper registers.

---

### Post by Jerfo on 2011-04-05
Ok, here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Be.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046     1,953,791     1,951,746   5 Extended
/dev/sda5               2,048     1,953,791     1,951,744  82 Linux swap / Solaris
/dev/sda2           1,953,792 1,758,212,095 1,756,258,304  83 Linux
/dev/sda3    *  1,758,217,860 1,953,503,999   195,286,140   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        636fa324-87fa-4e7c-9664-2e2f2e636b3c   ext4                                     
/dev/sda3        DEB08FB8B08F95A5                       ntfs                                     
/dev/sda5        b4415840-4da3-4906-83f0-6373dfac20ae   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E652-CC74                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
set locale_dir=($root)/boot/grub/locale
set lang=fr_FR
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if hwmatch ${prefix}/gfxblacklist.txt 3; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.38-7-generic ...'
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-7-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 636fa324-87fa-4e7c-9664-2e2f2e636b3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root DEB08FB8B08F95A5
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=636fa324-87fa-4e7c-9664-2e2f2e636b3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b4415840-4da3-4906-83f0-6373dfac20ae none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 314.6GB: boot/grub/core.img
 484.4GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.35-22-generic
 495.4GB: boot/initrd.img-2.6.35-24-generic
 365.1GB: boot/initrd.img-2.6.35-25-generic
 524.7GB: boot/initrd.img-2.6.35-27-generic
 365.4GB: boot/initrd.img-2.6.35-28-generic
   1.3GB: boot/initrd.img-2.6.38-7-generic
 314.6GB: boot/vmlinuz-2.6.35-22-generic
 314.6GB: boot/vmlinuz-2.6.35-24-generic
 314.8GB: boot/vmlinuz-2.6.35-25-generic
 314.8GB: boot/vmlinuz-2.6.35-27-generic
 314.8GB: boot/vmlinuz-2.6.35-28-generic
 314.8GB: boot/vmlinuz-2.6.38-7-generic
   1.3GB: initrd.img
 314.8GB: vmlinuz

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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

Unknown BootLoader  on sda1

00000000  bb a8 eb 86 73 34 83 79  f7 37 69 69 25 26 05 5f  |....s4.y.7ii%&._|
00000010  87 3b 15 46 f7 f3 71 1a  d5 b1 29 59 25 cb 3d 8e  |.;.F..q...)Y%.=.|
00000020  0d 44 1b 25 19 7e 17 6b  d3 ee f9 58 e5 67 fd 99  |.D.%.~.k...X.g..|
00000030  83 7e 3b c4 39 0f dd 2f  e1 96 23 b0 df 00 9d 02  |.~;.9../..#.....|
00000040  59 7e 89 76 ad d9 c5 77  ad 64 45 ae 03 f8 89 a4  |Y~.v...w.dE.....|
00000050  37 5d f3 c4 c1 cc 6b 57  9b c4 59 5e bd 43 4b 23  |7]....kW..Y^.CK#|
00000060  ff 49 3b 51 bd 3b 01 04  c5 53 b1 99 ed 85 7d b4  |.I;Q.;...S....}.|
00000070  c5 f7 01 19 dd 64 53 4e  01 3f f5 7a ed 02 db 4a  |.....dSN.?.z...J|
00000080  dd ec b7 18 57 d8 c5 7d  d9 81 25 31 91 78 31 21  |....W..}..%1.x1!|
00000090  cb b1 ab 4e 59 bf 4d 8b  91 05 99 32 21 d5 65 a5  |...NY.M....2!.e.|
000000a0  51 e0 01 1e 09 03 81 bc  25 a0 05 d0 5d ce 79 c3  |Q.......%...].y.|
000000b0  65 12 b7 11 85 53 8b 9e  4b f3 6f 27 81 58 7f 90  |e....S..K.o'.X..|
000000c0  37 b1 a1 ff e3 0e 2f 61  69 2b 39 77 3f fd ab 55  |7...../ai+9w?..U|
000000d0  31 a4 6b 8b 2f 08 c7 91  a9 9e 19 d1 bf 12 3f fb  |1.k./.........?.|
000000e0  f1 df 9d 09 71 2e 45 36  e3 4b 25 2d a5 d2 9d d3  |....q.E6.K%-....|
000000f0  4f d5 8f c2 a3 13 35 48  ab 39 c1 dc 09 51 3b c6  |O.....5H.9...Q;.|
00000100  59 c0 79 95 c1 53 b7 8f  4f b5 af 5d 7d 53 a7 da  |Y.y..S..O..]}S..|
00000110  59 d7 67 fb b3 db 89 de  d1 71 09 8d 0b 08 87 23  |Y.g......q.....#|
00000120  cf 59 3d 6a 61 10 fd aa  ed 86 3f 3a 35 9c 9b 09  |.Y=ja.....?:5...|
00000130  73 7f b9 17 a9 d5 fd 0a  17 50 19 1a f5 b3 bb f6  |s........P......|
00000140  31 47 6d 1c 5f 75 0b 0f  79 2b b9 19 bb c0 d5 60  |1Gm._u..y+.....`|
00000150  35 26 cb f6 55 66 45 7d  fb 18 97 11 73 38 ed 34  |5&..UfE}....s8.4|
00000160  dd 96 13 6e 4b f3 59 ec  33 39 85 d8 7d ac 25 a2  |...nK.Y.39..}.%.|
00000170  c1 87 63 d5 03 c2 95 3e  79 2c a9 b6 b3 c0 b3 44  |..c....>y,.....D|
00000180  b1 aa b1 ae 31 3a dd 7c  d9 51 87 38 69 02 e5 b0  |....1:.|.Q.8i...|
00000190  b5 a3 c7 ad 83 cc a7 11  13 e6 f5 61 65 9f 21 5e  |...........ae.!^|
000001a0  0b 18 4d 1b a1 19 0b 64  a7 02 25 41 ed fc e9 f1  |..M....d..%A....|
000001b0  2b 9d bf 97 23 f9 af d2  c7 7c a1 e1 b7 2e 00 20  |+...#....|..... |
000001c0  21 00 82 9d 24 79 02 00  00 00 00 c8 1d 00 00 00  |!...$y..........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 30 00  |.X.SYSLINUX.. 0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 60 77 00 78 07 00 00  00 00 00 00 02 00 00 00  |.`w.x...........|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 74 cc 52 e6 4b  49 4e 47 53 54 4f 4e 20  |..)t.R.KINGSTON |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 c0  e6 06 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by coffeecat on 2011-04-05
Just a quick comment.

```
 => Grub 2 is installed in the MBR of /dev/sda and looks for [COLOR=Red]Be.[/COLOR]
```Were you using the Natty/11.04 live CD? The bit I've highlighted in red is the sort of things you get when you use that version of the boot script with Natty. It's a known bug. If you were using Natty, you need to use the Maverick or Lucid live CD. Or I'll see if I can find a link for the newer test version of boot script that's compatible with Natty.

---

### Post by coffeecat on 2011-04-05
Another comment. :wink:

I see you have the Natty 2.6.38 kernel listed in you grub.cfg. So, what are you running, Maverick or Maverick upgraded to Natty?

---

### Post by Rubi1200 on 2011-04-05
I agree with coffeecat; let's first get some more information to help us diagnose the problem.

You might also try installing gawk and then running the boot script again.

---

### Post by Jerfo on 2011-04-05
I'm running a Maverick Live CD, well, actually a live usb but it's about the same, right?

---

### Post by Jerfo on 2011-04-05
> **coffeecat said:**
> Indeed. Hold on the new HD order - at least until we've done some investigating. :)

Unfortunately, some HDs do fail very early in their life, but there are many other explanations for what you are seeing.

Agreed with what Rubi1200 suggests, and try this as well:

Boot up with the Ubuntu live CD and go to System > Administration > Disk Utility. Highlight your HD in the left pane and then see what it has to say about SMART. Run a couple of self-tests. Hopefully, that will confirm that the HD is OK.

Also - this could be bad memory. How long have you had it? The way Linux uses memory makes it  more likely than Windows to come across bad memory in the upper registers.

It says Disk has a few bad sectors in the SMART status, I'll try and run the tests now.

It reads: ID 197, Value: Current Pending Sector Count, Assessment: Warning.

---

### Post by coffeecat on 2011-04-05
> **Jerfo said:**
> It reads: ID 197, Value: Current Pending Sector Count, Assessment: Warning.

Hmm. That doesn't look good after all. The current pending sector count is to do with sectors waiting to be remapped. If you are getting many sectors remapped early in the drive life, then that is ominous. Since you already have bad sectors, then some will already have been mapped, and it may have been remapped sectors that had critical Ubuntu files on them - hence the Ubuntu problems now.

Suggest:

1 - Use the live CD to backup personal data now.

2 - Run the Extended self-test rather than the short or "conveyance". This will give more information. But it will inevitably put some stress on the drive, which is why I suggest you backup your files first.

---

### Post by matt-fender on 2011-04-05
> **Jerfo said:**
> It says Disk has a few bad sectors in the SMART status, I'll try and run the tests now.

It reads: ID 197, Value: Current Pending Sector Count, Assessment: Warning.

this might sound simple and possibly dumb, but you say you've replaced the hard drive and it's giving you problems, have you had a look at the connections on the motherboard/changed the data cable? I recently had a computer to fix, which would play up with 3 different hard drives, changed the SATA cable, problem solved.

---

### Post by Jerfo on 2011-04-05
On value it reads 3 sectors... I really really want to think that is not 'many' sectors, right? Ok, now I feel screwed u_u

Right now it's running the test you mentioned though it seems it will take a veeeery long time.

---

### Post by Jerfo on 2011-04-05
> **matt-fender said:**
> this might sound simple and possibly dumb, but you say you've replaced the hard drive and it's giving you problems, have you had a look at the connections on the motherboard/changed the data cable? I recently had a computer to fix, which would play up with 3 different hard drives, changed the SATA cable, problem solved.

The SATA cable is a new one, I had a *mumbleIDEmumble* HDD before

---

### Post by searchfgold6789 on 2011-04-05
LOL I might've been right to begin with.
Not that that matters. It's good that we investigated the more likely case first.
It seems to me that the few bad sectors on the disk had important system data on it. That is why you are getting the garbled error messages.

---

### Post by Rubi1200 on 2011-04-05
In most cases, it is good to get a second opinion.

So, here is what I suggest; go to the website of the HDD manufacturer and see if they have a diagnostic tool available for downloading and testing the status of the drive.

If it confirms what Disk Utility is telling you, then you really need to save your data before proceeding with anything else.

---

### Post by coffeecat on 2011-04-05
That's a good idea from Rubi1200. If, by chance, the drive is failing in the warranty period, then data from the manufacturer's utility will back you up and help you get the drive replaced for free. They'll likely quibble less than with results from a Linux utility. It'll probably be Windows software so good luck with the Windows side working for at least as long as you need.

I agree 3 sectors is not many. Did the current pending sector count give you a number? You didn't quote one, just the 'warning' assessment. Here's the Wikipedia page on SMART:

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

Near the bottom of the page is the table of attributes. The description for Current Pending Sector Count might be useful for you.

---

### Post by Jay Christnach on 2011-04-05
Just my five cents:

You said you had RANDOM booting problems. I had a similar problem with a new drive (and with the old one :-) ) and it turned out the disk simply got too hot because I was using it inside a sound dampening foam sandwich. Once removed from there everything worked fine again.

Good luck with this!

---

### Post by Jerfo on 2011-04-06
The autotests hasn't moved for the last 3 hours, it seems to be missing 5 or 10% to finish. Should I stop it and use the manufacturer software instead or leave it running?

---

### Post by coffeecat on 2011-04-07
I don't remember the extended self-test taking more than an hour when I tried it - I think that was on a 500GB drive. 3 hours and stuck doesn't seem right. I would try the manufacturer's software.

---

### Post by Jerfo on 2011-04-07
Thanks for your help, I ran the manufacturer tools and got in contact with them, I'll have to wait for a replacement HDD.

---

