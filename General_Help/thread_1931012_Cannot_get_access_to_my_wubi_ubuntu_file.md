---
title: "Cannot get access to my wubi ubuntu file"
date: 2012-02-24
forum: General Help
---

### Post by tekkisan on 2012-02-24
I installed unbuntu 10.04 with wubi on my Windows 7 machine and later upgraded to 11.04. I did not use my ubuntu for a while and when I tried to boot into ubuntu it said the file was not found. I had a couple of saved files and after changing the names (from ie ubuntu-save to ubuntu) I still could not access my file.
I re-installed ubuntu 11.04 and got a new install. However I still cannot get access to my other installed files.
How can I get access to my ubuntu installed file
Please help

---

### Post by Rubi1200 on 2012-02-25
Hi,

Do you mean you changed the file-name from within Windows?

If you did a fresh install it is likely that things were overwritten.

It would really help us if you can get hold of a LiveCD/USB and then post the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by tekkisan on 2012-02-25
Yes I changed the file name from within windows. Last month when I was configuring my ubuntu  (ie the cube), I was making copies of the ubuntu directory ( virtual partition) within windows. This seemed like a good way to back everything up and I could easily use all thevirtual partition just by renaming to "ubuntu". So I have 3 or 4 ubuntu directories (virtual partitions). Now none of the virtual partions work and I get the error message "file not found" while booting into unbuntu.  I have yesterday done a new install and that works fine, except of course I do not have anything programs etc. This new install will still not access my old virtual partitions
Are you saying a live CD will be able to access my old virtual partition

---

### Post by tekkisan on 2012-02-26
here is the result.txt from the boot_info_script

---

### Post by Rubi1200 on 2012-02-26
Here are the results; I will ask someone to take a look and offer advice.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe /wubildr 
                       /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     26,626,048    26,830,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          26,830,848   165,083,939   138,253,092   7 NTFS / exFAT / HPFS
/dev/sda4         165,083,940   976,768,064   811,684,125   f W95 Extended (LBA)
/dev/sda5         165,084,003   976,768,064   811,684,062   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       84ef529f-4f11-48da-bc0b-2c6f91c88956   ext4       
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        AE36925036921983                       ntfs       SYSTEM RESERVED
/dev/sda3        01CCC729AE377B80                       ntfs       ACER
/dev/sda5        01CCC7297AAA9D10                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 01CCC7297AAA9D10
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 01CCC7297AAA9D10
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=01CCC7297AAA9D10 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 01CCC7297AAA9D10
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=01CCC7297AAA9D10 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root DAA41C49A41C2B11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AE36925036921983
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
--------------------------------------------------------------------------------

============================= sda5/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda5/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.267662048 = 11.024818176   boot/grub/grub.cfg                             1
   0.421875000 = 0.452984832    boot/initrd.img-2.6.38-8-generic               2
  10.267642975 = 11.024797696   boot/vmlinuz-2.6.38-8-generic                  1
   0.421875000 = 0.452984832    initrd.img                                     2
  10.267642975 = 11.024797696   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  00 00 01 ba 44 00 ee bc  14 71 01 89 c3 f8 00 00  |....D....q......|
00000010  01 e0 07 ec 81 00 00 3f  c8 0d ef d7 98 74 34 30  |.......?.....t40|
00000020  bc e8 c4 a1 c3 3b 61 b8  7e 0a bb 76 94 f6 f4 ff  |.....;a.~..v....|
00000030  4f 63 b7 02 49 c2 77 7d  e2 c9 a5 96 c8 50 68 fd  |Oc..I.w}.....Ph.|
00000040  4e 34 85 d1 d0 9d d9 25  27 8d c8 4f 63 be 19 ed  |N4.....%'..Oc...|
00000050  29 e1 88 74 2d 6f be 7c  70 8b a6 27 9c 30 87 f1  |)..t-o.|p..'.0..|
00000060  48 67 19 9a 29 4a 12 07  bc 42 26 97 b6 ef c6 01  |Hg..)J...B&.....|
00000070  3a 2c 0b 86 b9 c6 20 3a  eb 92 d5 69 02 c8 61 83  |:,.... :...i..a.|
00000080  d8 44 4d 21 92 ce 4f 4b  25 9e 46 e4 a0 cc e4 55  |.DM!..OK%.F....U|
00000090  50 6a 4b 19 dd ce ea c2  3d d1 44 a4 ba 54 b8 a0  |PjK.....=.D..T..|
000000a0  b8 98 4d 0c f8 9a e3 0f  74 77 61 71 5e ee 86 18  |..M.....twaq^...|
000000b0  5a fc fe 4e be 8e c7 74  e5 12 5c c3 23 da cb 46  |Z..N...t..\.#..F|
000000c0  46 3c 5d 13 54 79 2e bb  0b 15 27 e2 99 29 d9 99  |F<].Ty....'..)..|
000000d0  d6 31 3b 27 76 33 d1 30  34 a2 68 15 c3 03 44 38  |.1;'v3.04.h...D8|
000000e0  e5 0e 82 50 e9 50 78 88  31 90 93 0a 33 21 25 8b  |...P.Px.1...3!%.|
000000f0  d1 b7 59 c8 bc 50 14 0c  29 c0 2c 29 9f e3 85 eb  |..Y..P..).,)....|
00000100  41 7b 80 e3 8a fb 89 80  60 8c 42 0d 0d 0d 4a 11  |A{......`.B...J.|
00000110  f6 3b fe 7a e1 89 65 e5  8f 7d ad d3 50 45 74 9c  |.;.z..e..}..PEt.|
00000120  02 d2 dd 3f ec 90 f8 96  9e e6 ed b9 69 e9 2c cd  |...?........i.,.|
00000130  d8 f9 29 25 15 ce 1a 6e  78 0b fe 62 5c d3 6d d0  |..)%...nx..b\.m.|
00000140  53 d9 88 3e 92 d3 ba 71  58 98 56 6c 48 17 e8 98  |S..>...qX.VlH...|
00000150  30 86 57 75 f0 3c 9e 60  b9 29 40 66 18 37 27 ed  |0.Wu.<.`.)@f.7'.|
00000160  d9 0e e7 4c 93 49 84 b0  b2 75 aa f3 99 88 f1 00  |...L.I...u......|
00000170  3a 00 36 e4 d4 06 9e 18  4c 21 f2 61 2b 90 c9 8c  |:.6.....L!.a+...|
00000180  c3 78 6a 4f 61 5a 00 c8  01 d9 48 41 08 b0 14 e0  |.xjOaZ....HA....|
00000190  1b 97 b6 24 bb bb c0 3b  0c 01 31 49 2b f4 24 96  |...$...;..1I+.$.|
000001a0  03 65 ff d8 e1 d0 15 26  96 9e e3 1f a0 33 74 b6  |.e.....&.....3t.|
000001b0  6b b5 38 21 9f 4e 7a 03  40 4c 42 c0 3b cf 00 fe  |k.8!.Nz.@LB.;...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 de 50 61 30 00 00  |......?....Pa0..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by bcbc on 2012-02-26
I guess the question is what happened to break your installs. If you moved them from one 'drive' to another, then that will stop it booting automatically - even renaming the folders won't make a difference. If it was on the same drive, then renaming should make it bootable assuming it's the same release.

What should you do? Not really sure but let's mount one of those backups and check the grub.cfg. 

Boot your new working Ubuntu. Then mount one of the backups. e.g. I'm going to assume for this example you have a backup saved in the \ubuntubackup directory on the root of the same drive as your working \ubuntu install.

So you'd go to a terminal (Ctrl+Alt+T):
```
sudo mount -o loop /host/ubuntubackup/disks/root.disk /mnt
gedit /mnt/boot/grub/grub.cfg

```

Check that it matches your current grub.cfg (partition, etc) and post it here if you're not sure.

You could fsck the disk as well making sure to unmount it first (so exit gedit as well):
```
sudo umount /mnt
sudo fsck /host/ubuntubackup/disks/root.disk

```

---

### Post by tekkisan on 2012-02-27
First, I would like to thank rubi and bcbc for helping me with this problem. I really appreciate it.
I was reading the WUBI megathread and I see there is a problem similar to what I am having. Perhaps I should just partition my harddrive and do a full installation. Then at least I will not have to deal with the WUBI install problem. Is this correct thinking?
I thought the WUBI installation would be a good way to go, but from what I have read, it should only be a temporary trial. I could fix this problem now, but perhaps it will happen again.

---

### Post by bcbc on 2012-02-27
tl;dr Yes, a normal install is better

Wubi is a mechanism for people to try out Ubuntu risk free. It works very well for what it does. But using a virtualized disk isn't ideal for long term use. The main reason for using Wubi is if you can't (or won't) repartition your computer, and also to try out Ubuntu easily and remove easily.

You did all the right things, backing up your data. That should work (I do it all the time for testing - I have different releases in various places and it's straightforward getting them to boot). But something obviously has gone wrong in your case - what isn't clear. Assuming it's wubi related (e.g. corruption of the root.disk, or moving between partitions) then installing normally will get around it.

Backup and restore is important in a normal install as well, and making sure it works (before needing it too).

---

### Post by tekkisan on 2012-02-27
Yes thanks again. I think I will do an install on a partition. I think a windows update probably changed the boot into ubuntu. But that is just a guess.

---

### Post by bcbc on 2012-02-27
We can try and repair it - usually it's not a big deal and you have a bunch of backups. If you've done a lot of work, you can migrate a wubi install to a normal one so you don't have to start from scratch.

---

### Post by tekkisan on 2012-02-28
Ok, that sounds cool. I'd like to try for the fun of it. When I get a change I will do the next step outlined above

---

### Post by tekkisan on 2012-02-29
Here is the printout from grub.config from one of my backups that does not load
I cannot decifer.

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 01CBE0178973D310
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 01CBE0178973D310
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=01CBE0178973D310 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 01CBE0178973D310
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=01CBE0178973D310 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 01CBE0178973D310
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=01CBE0178973D310 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 01CBE0178973D310
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=01CBE0178973D310 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root DAA41C49A41C2B11
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root AE36925036921983
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

---

### Post by bcbc on 2012-02-29
Your /dev/sda5 has a UUID of:
```
/dev/sda5        01CCC7297AAA9D10                       ntfs       Data
```

But the grub.cfg you showed is trying to boot on:
```
linux /boot/vmlinuz-2.6.38-11-generic root=UUID=**01CBE0178973D310** loop=/ubuntu/disks/root.disk ro quiet splash
```

So, all you should have to do is change that line to:
```
linux /boot/vmlinuz-2.6.38-11-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash
```

in other words, when the grub menu loads, hit 'E' and delete the UUID=xxx bit and make it as above, then hit Ctrl+X to boot.
After booting run:
```
sudo update-grub
```

---

### Post by tekkisan on 2012-02-29
Ok, I am not sure, when the grub menu loads. Is this while it is booting and after the boot process stops?  or do I edit that  in the text file first and then boot.

---

### Post by tekkisan on 2012-02-29
And a further thought. I have 2 partitions on my hard disk, with ubuntu virtual partition on the D drive. I changed the partition sizes about a few weeks ago. Would that have changed the UUID number on the partition? Perhaps this is why the boot gets lost.

---

### Post by bcbc on 2012-02-29
> **tekkisan said:**
> And a further thought. I have 2 partitions on my hard disk, with ubuntu virtual partition on the D drive. I changed the partition sizes about a few weeks ago. Would that have changed the UUID number on the partition? Perhaps this is why the boot gets lost.
Yes modifying the partition can affect the UUID and if that's what Wubi is using (which it is) then it explains the problem.

So, let's say you changed your working root.disk to oldroot.disk and then moved in your backup root.disk (moving is immediate, as opposed to copying which takes a while) into the \ubuntu\disks directory. The when you boot, select Ubuntu, you'll see the grub menu, hit 'E' on the first entry, change as I specified, and then hit ctrl+X to boot.

---

### Post by tekkisan on 2012-03-01
That was very straight forward, but it did not work. I changed the line  but the error message was that is was still looking for 01CBE0178973D310. So the second time I changed the linux /boot  line to /dev/sda5 and changed the set=root /dev/sda5.
The it said not fount /dev/sda5

The grub menu looked something like below ( but this was copied from above for reference)

set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 01CBE0178973D310
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=01CBE0178973D310 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-11-generic

---

### Post by bcbc on 2012-03-01
The line beginning "search --no-floppy ..." is also trying to set root to be the partition with the bad UUID. So likely you'll see that message. However it will fail and root remains as /dev/sda5. You can delete the whole line if you like - it shouldn't make a difference.

The part you need to worry about is the line beginning "linux /vmlinuz..."

Make sure you have it typed in correct as I showed before with " root=/dev/sda5 " (NOT set=root /dev/sda5)

---

### Post by tekkisan on 2012-03-01
Ok, great, that worked and I am in. I changed the line and also deleted the line referring to the  floppy . It looked like is would not work as I still got an error message "no such disk".  In fact I did it twice and the first time I just powered down and back into windows. However the second time I just left the computer and after a few minutes it then continued to boot. In fact it might have worked earlier today without deleting the floppy line. I might even try not deleting the floppy line because I did not yet update the grub

So thank you again for your time and help. I really appreciate it. Perhaps this thread will help someone else.

---

### Post by bcbc on 2012-03-01
Yeah ironically I helped someone else with the same problem today. So I'm sure it will help. Grub boot entries aren't fun, but once you get past the gobbledygook they're not too bad.

PS I mentioned earlier about [migrating]("http://ubuntuforums.org/showthread.php?t=1519354"). You can actually migrate from an old root.disk as well (so keeping backups - even if you find it hard to boot them ;) - is a good idea).

Another trick I use is to 'resize' my root.disk. The [script]("http://ubuntuforums.org/showthread.php?t=1625371") actually duplicates it so you can choose the smallest size possible for your 'new.disk'. E.g. you have a 17GB root.disk but you're only using 8GB, you can 'resize' to a 9GB new.disk and then you have a good backup without wasting space. (I'm working on an update that will use rsync's built-in features to synchronize the backup, keeping it up-to-date by only copying files that have changed).

And if all else fails, normal data backups (e.g. /home) and/or synching data to Ubuntu One works as well.

---

