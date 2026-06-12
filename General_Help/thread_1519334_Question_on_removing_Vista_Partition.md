---
title: "Question on removing Vista Partition"
date: 2010-06-28
forum: General Help
---

### Post by sports fan Matt on 2010-06-28
Since I have Gparted installed and it turns out I do not need my vista partition at all, I am giving it to Ubuntu.  Is there an easy way to achieve this without messing with my files on the ubuntu side?

---

### Post by Rubi1200 on 2010-06-28
Hi,
first and foremost, you should make a backup of any important files BEFORE playing around with partitions because there is always a chance that something might go wrong.

Second, the recommended method of deleting/moving/resizing partitions is to use the LiveCD and run GParted from there. The reason being that the partitions need to be unmounted for GParted to do its work. You will also need to unmount the swap partition.

I also recommend that you post either a screenshot of your partitions from GParted or run this script from the LiveCD so people here can let you know if there might be any potential problems before you move ahead.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I hope this helps answer your question.

---

### Post by gadolinio on 2010-06-28
> **rubi1200 said:**
> hi,
first and foremost, you should make a backup of any important files before playing around with partitions because there is always a chance that something might go wrong.

Second, the recommended method of deleting/moving/resizing partitions is to use the livecd and run gparted from there. The reason being that the partitions need to be unmounted for gparted to do its work. You will also need to unmount the swap partition.

I also recommend that you post either a screenshot of your partitions from gparted or run this script from the livecd so people here can let you know if there might be any potential problems before you move ahead.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

i hope this helps answer your question.

+1

---

### Post by dino99 on 2010-06-28
do not use gparted (or any formatting tool) on an active hdd or partition: boot on partedmagic for better security

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by kiddykoff on 2010-06-28
> **dino99 said:**
> do not use gparted (or any formatting tool) on an active hdd or partition: boot on partedmagic for better security

[http://partedmagic.com/](http://partedmagic.com/)

Rubi was saying to use the live cd so the hdd would not be mounted. I've used a gparted live cd which worked well for removing my windows 7 demo.

as for backing up your file: burn them to disk, put them in a cloud, or write them to an external hdd. you can also put them on an ipod which is what i did.

---

### Post by sports fan Matt on 2010-06-28
I will post a screenshot of the partitions.

---

### Post by Elfy on 2010-06-28
as you can see - partitions are mounted - the padlock symbols.

Run from a livecd - make sure nothing is mounted - possibly need to right click on the swap partition - and swapoff

Personally I would be inclined to just create a new partition and then mount it in /mnt using fstab.

---

### Post by sports fan Matt on 2010-06-28
Sounds Good.  I think this is what I did before as well.

---

### Post by sports fan Matt on 2010-06-28
I got rid of vista (which was a good thing)  but it seems like I created an extra ubuntu partition.  How can I delete the brand new partition I just created and use this space for the formatted partition?

Is there a way to tell where my data is & then remove that other new partition?

---

### Post by Elfy on 2010-06-28
sda1 is the new partition 

if you want to resize the existing linux partition then you need to resize the extended (sda2) first - then you can you resize the linux install on sda5

If you're going to be moving partitions about make sure you have backups. At least I assume that is what you are trying to do.

Not quite sure why you made a new partition if you just want to resize the existing ;)

---

### Post by sports fan Matt on 2010-06-28
Because I wasn't exactly sure what I was doing:)

At least I haven't screwed this install up.  Here is my boot script as well which describes what you have said.                 Boot Info Script 0.55    dated February 15th, 2010                    
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

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

/dev/sda1    *          2,048   500,283,391   500,281,344  83 Linux
/dev/sda2         500,285,438   976,773,119   476,487,682   5 Extended
/dev/sda5         512,307,200   964,749,311   452,442,112  83 Linux
/dev/sda6         964,751,360   976,773,119    12,021,760  82 Linux swap / Solaris
/dev/sda7         500,285,440   512,307,199    12,021,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        35c9f2df-f02e-4015-b149-a12bc94f805e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6d683e6c-7057-452c-8263-dbcff6f54e18   ext4                                     
/dev/sda6        21a1ab5b-8ba5-4c73-b106-04a862d90f7b   swap                                     
/dev/sda7        ace8e9ce-2f2c-473e-84db-fa02403c7f35   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
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
search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=35c9f2df-f02e-4015-b149-a12bc94f805e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=35c9f2df-f02e-4015-b149-a12bc94f805e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 35c9f2df-f02e-4015-b149-a12bc94f805e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=6d683e6c-7057-452c-8263-dbcff6f54e18 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=6d683e6c-7057-452c-8263-dbcff6f54e18 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
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
# / was on /dev/sda1 during installation
UUID=35c9f2df-f02e-4015-b149-a12bc94f805e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ace8e9ce-2f2c-473e-84db-fa02403c7f35 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 112.5GB: boot/grub/core.img
  64.5GB: boot/grub/grub.cfg
 112.5GB: boot/initrd.img-2.6.32-21-generic
 112.5GB: boot/vmlinuz-2.6.32-21-generic
 112.5GB: initrd.img
 112.5GB: vmlinuz

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6d683e6c-7057-452c-8263-dbcff6f54e18 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6d683e6c-7057-452c-8263-dbcff6f54e18 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6d683e6c-7057-452c-8263-dbcff6f54e18
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 420c137f0c136d63
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=6d683e6c-7057-452c-8263-dbcff6f54e18 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=21a1ab5b-8ba5-4c73-b106-04a862d90f7b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 455.7GB: boot/grub/core.img
 378.4GB: boot/grub/grub.cfg
 455.8GB: boot/initrd.img-2.6.32-23-generic
 455.8GB: boot/vmlinuz-2.6.32-23-generic
 455.8GB: initrd.img
 455.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c0 e9 d4 00 00 00 80 7d  10 00 74 04 83 4b 0c 01  |.......}..t..K..|
00000010  8b 45 0c 8d 50 02 66 8b  08 40 40 66 85 c9 75 f6  |.E..P.f..@@f..u.|
00000020  2b c2 d1 f8 8d 44 00 02  be 57 6d 69 70 56 50 6a  |+....D...WmipVPj|
00000030  01 89 45 10 e8 cc 7d f9  ff 89 43 18 8b 45 14 8d  |..E...}...C..E..|
00000040  48 02 66 8b 10 40 40 66  85 d2 75 f6 2b c1 d1 f8  |H.f..@@f..u.+...|
00000050  56 8d 7c 00 02 57 6a 01  e8 a8 7d f9 ff 8b 4b 18  |V.|..Wj...}...K.|
00000060  85 c9 89 43 1c 74 41 85  c0 74 3d ff 75 0c 8b 45  |...C.tA..t=.u..E|
00000070  10 51 e8 20 92 ed ff ff  75 14 8b c7 ff 73 1c e8  |.Q. ....u....s..|
00000080  13 92 ed ff e8 e2 94 ed  ff a1 6c b2 4f 00 8b 48  |..........l.O..H|
00000090  04 89 03 89 4b 04 89 19  89 58 04 e8 e5 bb f8 ff  |....K....X......|
000000a0  8b 45 18 c6 00 01 eb 0d  be 9a 00 00 c0 eb 1f 8b  |.E..............|
000000b0  45 18 c6 00 00 8b 75 08  85 f6 74 1e e8 aa 94 ed  |E.....u...t.....|
000000c0  ff 53 e8 1f fe ff ff 8b  f0 e8 b7 bb f8 ff 8b c3  |.S..............|
000000d0  bf 1c af 4e 00 e8 4c ac  04 00 5f 8b c6 5e 5b 5d  |...N..L..._..^[]|
000000e0  c2 14 00 90 90 90 90 90  8b ff 55 8b ec 56 57 e8  |..........U..VW.|
000000f0  77 94 ed ff 8b 3d 6c b2  4f 00 8b 0f eb 6c 8b 55  |w....=l.O....l.U|
00000100  08 8b 41 18 66 8b 30 66  3b 32 75 1e 66 85 f6 74  |..A.f.0f;2u.f..t|
00000110  15 66 8b 70 02 66 3b 72  02 75 0f 83 c0 04 83 c2  |.f.p.f;r.u......|
00000120  04 66 85 f6 75 de 33 c0  eb 05 1b c0 83 d8 ff 85  |.f..u.3.........|
00000130  c0 75 35 8b 55 0c 8b 41  1c 66 8b 30 66 3b 32 75  |.u5.U..A.f.0f;2u|
00000140  1e 66 85 f6 74 15 66 8b  70 02 66 3b 72 02 75 0f  |.f..t.f.p.f;r.u.|
00000150  83 c0 04 83 c2 04 66 85  f6 75 de 33 c0 eb 05 1b  |......f..u.3....|
00000160  c0 83 d8 ff 85 c0 74 0a  8b 09 3b cf 75 90 33 f6  |......t...;.u.3.|
00000170  eb 0c 33 d2 8d 41 10 42  f0 0f c1 10 8b f1 e8 02  |..3..A.B........|
00000180  bb f8 ff 5f 8b c6 5e 5d  c2 08 00 90 90 90 90 90  |..._..^]........|
00000190  8b ff 55 8b ec 53 56 57  e8 ce 93 ed ff 8b 45 08  |..U..SVW......E.|
000001a0  83 c0 24 8b 30 3b f0 89  45 08 0f 84 e2 00 00 00  |..$.0;..E.......|
000001b0  8b 46 0c a8 01 0f 84 81  00 00 00 8b 46 34 00 fe  |.F..........F4..|
000001c0  ff ff 83 fe ff ff 02 70  b7 00 00 b8 f7 1a 00 fe  |.......p........|
000001d0  ff ff 05 fe ff ff 02 28  af 1b 00 78 b7 00 00 00  |.......(...x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

My question is: from the live cd (10.04) can you walk me through how this can be done? 

I assume home is on sda 1, am i right?  Then can't i just right click on sda2 and "remove" and it will shrink, gaining the full space of sda1?

---

### Post by Elfy on 2010-06-28
What have you been doing?

Both sda1 and sda5 have installs on them it appears.

You're not just resizing and moving partitions here are you ... might be worth saying what you have done between the screenshot in #6 and #9


Oh - and please use code tags - # in new reply box or [noparse]```
[/noparse]at beginning and[noparse]
```[/noparse] at the end in quick reply box


Edit - but to answer the question here > Then can't i just right click on sda2 and "remove" and it will shrink, gaining the full space of sda1 - no - you can delete the partitions from iside sda2 and then remove sda2, then you can resize sda1

---

### Post by sports fan Matt on 2010-06-28
What have I been doing?

Reinstalling fresh after realizing it's not all lost, and my data has been backed up:).  Even from a reinstall, (backed up everything as a firefox bookmark) it's not that time consuming.

Not the most conveinent method, but it works :)

---

### Post by Elfy on 2010-06-28
> **sox fan Matt said:**
> What have I been doing?

Reinstalling fresh after realizing it's not all lost, and my data has been backed up:).  Even from a reinstall, (backed up everything as a firefox bookmark) it's not that time consuming.

Not the most conveinent method, but it works :)

Indeed - if you are in that position a reinstall can be much quicker than mucking about with partitions.

If you're new install is in sda1 then delete all the other partitions - and then resize the new install, though if you want to keep the exisitng swap it will be a bit more work.

I would just delete the superfluous partitions and make a new swap, then edit fstab's swap line while in the livecd.

---

