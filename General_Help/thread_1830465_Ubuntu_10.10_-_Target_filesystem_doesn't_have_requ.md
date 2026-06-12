---
title: "Ubuntu 10.10 - Target filesystem doesn't have requested /sbin/init."
date: 2011-08-21
forum: General Help
---

### Post by AdamShumpisxXx on 2011-08-21
Ubuntu has officially jumped the shark. I did an update...restarted and got this:

> mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg 

Which led me here:

[http://ubuntuforums.org/showthread.php?t=1610269]("http://ubuntuforums.org/showthread.php?t=1610269")

Which led me here:

[http://ubuntuforums.org/showpost.php?p=9411005&postcount=2]("http://ubuntuforums.org/showpost.php?p=9411005&postcount=2")

Which wouldn't work unless I booted with Slax. I finally got that command working. I pressed "y" a bunch of times. It said my partition was clean. Then I reboot. Then Ubuntu hit's me with:

> The disc drive for / is not ready yet or not present.

Then I try:

> mount -o remount, rw /

Now I get:

> EXT4-fs error (device sda3): ext4_remount: Abort forced by user
mount: you must specify the filesystem type

Even though it apparently works for EVERYONE ELSE except me. Then I try:

> mount -t ext4 -o remount, rw /

On a whim from reading the mount help and I get:

> EXT4-fs error (device sda3): ext4_remount: Abort forced by user
mount: cannot remount block device rw read-write, is write protected

AND NOW I'M HERE! What the hell is going on? I CAN NOT JUST BACKUP AND RE-INSTALL! Someone just please help me. This is just plain insane and makes no sense. Thank you in advance to anyone who can get me out of this. My hands are in the air.

---

### Post by fdrake on 2011-08-21
are you able to see the grub menu normaly?
boot from a live cd and try to get some info with [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

run the script and post it here.


did you try to check for filesystem errors?
while you upload the results run

```

sudo fdisk -l

sudo fsck -y /dev/<Linuxpartition>
```

where <linupartition> is the partition that is mouted in your / folder is

---

### Post by AdamShumpisxXx on 2011-08-21
THANK YOU! I am sweating death right now over this. I will do as you say as fast as possible!

---

### Post by AdamShumpisxXx on 2011-08-21
>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004a711

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       999,423       997,376  83 Linux
/dev/sda2             999,424     4,999,167     3,999,744  82 Linux swap / Solaris
/dev/sda3           4,999,168 1,250,263,039 1,245,263,872  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d8160884-b953-4656-b2d1-857b7ecf805e   ext2       
/dev/sda2        e7a64c62-2d17-46f9-a3f9-a553a6ebff0e   swap       
/dev/sda3        32613837-1122-44b9-8f04-0257fdf374a1   ext4       
/dev/sdb         E447-E2EF                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/sda1                ext2       (rw,noatime)
/dev/sdb         /mnt/sdb                 vfat       (rw)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 32613837-1122-44b9-8f04-0257fdf374a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
set locale_dir=($root)/grub/locale
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
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-25-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-24-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-23-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img
            ?? = ??             grub/grub.cfg
            ?? = ??             initrd.img-2.6.35-22-generic
            ?? = ??             initrd.img-2.6.35-23-generic
            ?? = ??             initrd.img-2.6.35-24-generic
            ?? = ??             initrd.img-2.6.35-25-generic
            ?? = ??             initrd.img-2.6.35-28-generic
            ?? = ??             vmlinuz-2.6.35-22-generic
            ?? = ??             vmlinuz-2.6.35-23-generic
            ?? = ??             vmlinuz-2.6.35-24-generic
            ?? = ??             vmlinuz-2.6.35-25-generic
            ?? = ??             vmlinuz-2.6.35-28-generic

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 e0 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  8e 7e 7a 00 90 1e 00 00  00 00 00 00 02 00 00 00  |.~z.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ef e2 47 e4 4e  4f 20 4e 41 4d 45 20 20  |..)..G.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file



> root@slax:~# fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a711

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      498688   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              63         312     1999872   82  Linux swap
Partition 2 does not end on cylinder boundary.
/dev/sda3             312       77826   622631936   83  Linux

Disk /dev/sdb: 4110 MB, 4110228480 bytes
127 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       98824      243796   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(98823, 58, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(243795, 59, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       21424      267300   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21423, 77, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(267299, 87, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      237476      483352   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(237475, 53, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(483351, 62, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      366483      366490       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(366482, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(366489, 36, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


> root@slax:~# fsck -y /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3: recovering journal
/dev/sda3 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -24154030 -24154034 -24154036 -24154040 -24154066 -24154073 -24154081 -(24154084--24154085) -24154092 -24154095 -24154105 -24154108
Fix? yes


/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda3: 232582/38920192 files (0.6% non-contiguous), 15533018/155657984 blocks
 


There you go! Thanks again!

---

### Post by fdrake on 2011-08-21
did you try to reboot after the fsck? any progress or just the same?

---

### Post by AdamShumpisxXx on 2011-08-21
As per your instructions I rebooted. I am now faced with the Ubuntu Logo and a loading bar underneath...Progress! It checked my HDD for errors. Nothing seemed wrong. Now it says:

> The disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recover

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> As per your instructions I rebooted. I am now faced with the Ubuntu Logo and a loading bar underneath...Progress! It checked my HDD for errors. Nothing seemed wrong. Now it says:

what happens when you press "S"? does it directs you somewhere?

---

### Post by AdamShumpisxXx on 2011-08-21
I pressed "S" once and I got:

> The disk drive for /boot is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recover 

If I press "S" again there is absolutely no response. The loading bar just pretends to make progress.

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> I pressed "S" once and I got:



If I press "S" again there is absolutely no response. The loading bar just pretends to make progress.

it looks like it cannod find the / , somehow. probably the UIDD has changed somehow. that's why you have all those ???? symbols under the "sda1: Location of files loaded by Grub" in your results.

boot again from the live cd.
and try:
```

sudo mount -a
gksudo /mnt/ (or /media/  depending on where it is being mounted)

```
search for you sda3 filesystem look for a file in /etc/fstab
open the file with gedit (copy and paste here) keep gedit open, you may need to change the id later one.

then run from the terminal this:
```
sudo blkid /dev/sd??
```
post here.

---

### Post by AdamShumpisxXx on 2011-08-21
I'm not sure what you're instructions are. Here is what I have:

> root@slax:~# mount -a
mount: devpts already mounted or /dev/pts busy
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Also, how am I supposed to get you something from my SDA3 filesystem if I am not able to access it because I am not able to mount it? Should I perhaps try a different LiveCD? I am using SLAX v6.1.2 at the moment. Thank you.

[COLOR="Red"]!EDIT![/COLOR]

I can gain access to SDA3 if I run the fsck command you mentioned above through SLAX, boot into Ubuntu, and click M when I am confronted with:

> The disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recover 

This gains me access to the root command prompt. I am not sure I can extract a file for you but I am able to open /etc/fstab with nano under those circumstances. Let me know! Thanks again!

---

### Post by fdrake on 2011-08-21
i am not sure if slax live cd has an install for grub2 since it states that it cannot find /boot too. can you get an install-live cd for ubuntu 11.04. Boot from it and do
(hopefully it will be able to mount the /boot partition.)
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
----------------------------
edit:

can you just check if in nano /etc/fstab the uidd of the sda3 partiotion is the same as in the one shown in sudo blkid /dev/sd??

---

### Post by fdrake on 2011-08-21
```

nano /etc/fstab

```
is the output same as this?
```

/dev/sda1 d8160884-b953-4656-b2d1-857b7ecf805e ext2
/dev/sda2 e7a64c62-2d17-46f9-a3f9-a553a6ebff0e swap
/dev/sda3 32613837-1122-44b9-8f04-0257fdf374a1 ext4
```
from your source file

---

### Post by AdamShumpisxXx on 2011-08-21
Yes, SDA3's UUID in /etc/fstab is the exact same as the display of blkid /dev/sda3. Should I now try your other suggestion about reinstalling GRUB?

---

### Post by fdrake on 2011-08-21
yes can you try to install the grub  since the uiid wasn't the issue... hopefully this solve the mount problem of both /boot and /

---

### Post by AdamShumpisxXx on 2011-08-21
Do you have exact instructions I could follow, please? I see above you want me to mount SDA5 which I do not have. I just want to make sure I do these things the exact way you want me to so there is no confusion. Thank you!

---

### Post by fdrake on 2011-08-21
from ubuntu 11.04 live-cd

if it does not mount sd3, run few times fsck until it does!
```

sudo mount /dev/sda3 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev/
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
sudo umount /mnt/dev
sudo umount /mnt/

```

reboot and good luck!!

---

### Post by AdamShumpisxXx on 2011-08-21
I'm still booted into the LiveCD environment. The installation is finished and no error is reported. Should I reboot and test or is there something I should do first? Thanks.

[COLOR="Red"]!EDIT![/COLOR]

Wait...I did what your instructions told me to do that you edited and did not see your newest post. This post I made was referring to that. I will reboot now and let you know what's going on. If there is no change I will follow your CURRENT instructions unless otherwise instructed. Thanks you!

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> I'm still booted into the LiveCD environment. The installation is finished and no error is reported. Should I reboot and test or is there something I should do first? Thanks.

[COLOR="Red"]!EDIT![/COLOR]

Wait...I did what your instructions told me to do that you edited and did not see your newest post. This post I made was referring to that. I will reboot now and let you know what's going on. If there is no change I will follow your CURRENT instructions unless otherwise instructed. Thanks you!

nothing else left to be done. just check and cross fingers!

edit:
it's ok with the new installation the old one will be omitted. so no damage done.

---

### Post by AdamShumpisxXx on 2011-08-21
All I have now is an instant boot to a GRUB bash. I will now follow your CURRENT instructions to see if this remedies that problem. Sorry for the crossed wires.

---

### Post by AdamShumpisxXx on 2011-08-21
All went perfectly on the first try up until I get to:

> sudo umount /mnt/dev

From that I get:

> sudo:unable to resolve host ubuntu
umount: /mnt/dev: not found

When I enter:

> umount /mnt/dev

I get:

> umount: /mnt/dev: not found

I just figure I'd try that since I'm already in root since I entered:

> sudo chroot /mnt

When I enter:

> umount /mnt

I get:

> umount: /mnt: not mounted

Is it OK to reboot or is there something else I should do first? Thanks.

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> All went perfectly on the first try up until I get to:



From that I get:



When I enter:



I get:



I just figure I'd try that since I'm already in root since I entered:



When I enter:



I get:



Is it OK to reboot or is there something else I should do first? Thanks.

probably was already unmounted?  just reboot and see what happens.

did it give you anyt error message when you mounted /dev/sda3 ?

---

### Post by AdamShumpisxXx on 2011-08-21
No errors at all other than what was outlined in my last post. I will reboot now and let you know the results! I'm excited!

---

### Post by AdamShumpisxXx on 2011-08-21
It got to the Ubuntu Logo with the progress bar underneath and was checking my disks for errors in 2 passes. When it was done I didn't notice any errors as I was turned away when it actually happened and it rebooted back to GRUB (Which is oddly enough not GRUB2. It's GRUB 1.98 for some reason.) and then...Same thing:

> An error occurred while mounting /
Press S to skip mounting or M for manual recovery

:confused:

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> It got to the Ubuntu Logo with the progress bar underneath and was checking my disks for errors in 2 passes. When it was done I didn't notice any errors as I was turned away when it actually happened and it rebooted back to GRUB (Which is oddly enough not GRUB2. It's GRUB 1.98 for some reason.) and then...Same thing:
:confused:

u used a live cd from ubuntu 11.04 live-cd?

---

### Post by AdamShumpisxXx on 2011-08-21
I used this exact torrent from [http://www.ubuntu.com/]("http://www.ubuntu.com/") :

[http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent")

Should I have used the DVD version?

---

### Post by fdrake on 2011-08-21
the commands i gave you i checked on different sites , like this one.
[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

grub-install is for grub2

grub is for grub(1)

that's weird.:confused:

ps your booting scripts says you had:Grub2 (v1.97-1.9)
you can always double check with that.

---

### Post by AdamShumpisxXx on 2011-08-21
There is one command we didn't use from that site's instructions...What about the command "update-grub"? Does that apply to me and if so what step would that be between?

---

### Post by fdrake on 2011-08-21
also the message has changed:
it used to be:

> The disc drive for / is not ready yet or not present

now it says:

> An error occurred while mounting /
Press S to skip mounting or M for manual recovery 

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> There is one command we didn't use from that site's instructions...What about the command "update-grub"? Does that apply to me and if so what step would that be between?

i did not change the grub source file, that's why there was no reason to update grub.

---

### Post by AdamShumpisxXx on 2011-08-21
Well, it used to say that every other time I would boot into SLAX and fsck SDA3. Oh and when I rebooted I'm directly back into BusyBox initramfs. No ground gained...

What is going on here?! There has to be something small we're missing. This is frying me!!!

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> Well, it used to say that every other time I would boot into SLAX and fsck SDA3. Oh and when I rebooted I'm directly back into BusyBox initramfs. No ground gained...

What is going on here?! There has to be something small we're missing. This is frying me!!!

can you run again that boot script i post at the begging and post the result here?

also if you are able to mount sd3 open /etc/fstab and post it here.
i noticed that in you mount point "/" in not present in the script.

---

### Post by AdamShumpisxXx on 2011-08-21
I made some progress. I realized you have to hit CTRL+D between steps 7 and 8. Now the only error I get is when I try and unmount /mnt which results in:

> ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt:device is busy.


I'm still in the Ubuntu 11.04 LiveCD environment. What do I do now? Thanks!

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> I made some progress. I realized you have to hit CTRL+D between steps 7 and 8. Now the only error I get is when I try and unmount /mnt which results in:



I'm still in the Ubuntu 11.04 LiveCD environment. What do I do now? Thanks!

do you have any window that is browsing in /dev/sda3? if just reboot. 
just repeat again the steps. But before that open with gedit /etc/fstab and post you results here, please. untill then is like walking in the dark.

---

### Post by AdamShumpisxXx on 2011-08-21
I repeated the steps:

> An error occurred while mounting /
Press S to skip mounting or M for manual recovery 

I will reboot back into the LiveCD and post you the results of my /etc/fstab ASAP. Thanks for sticking with me...

---

### Post by fdrake on 2011-08-21
> **AdamShumpisxXx said:**
> I repeated the steps:



I will reboot back into the LiveCD and post you the results of my /etc/fstab ASAP. Thanks for sticking with me...

and while you're there post here the results of the booting script I told you at the beginning.

---

### Post by AdamShumpisxXx on 2011-08-21
I don't know if I did this right but here goes...

/etc/fstab:
> aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0


> ubuntu@ubuntu:~/Desktop$ sudo bash boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sdb for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".



>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       999,423       997,376  83 Linux
/dev/sda2             999,424     4,999,167     3,999,744  82 Linux swap / Solaris
/dev/sda3           4,999,168 1,250,263,039 1,245,263,872  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d8160884-b953-4656-b2d1-857b7ecf805e   ext2       
/dev/sda2        e7a64c62-2d17-46f9-a3f9-a553a6ebff0e   swap       
/dev/sda3        32613837-1122-44b9-8f04-0257fdf374a1   ext4       
/dev/sdb         E447-E2EF                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /media/E447-E2EF         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 32613837-1122-44b9-8f04-0257fdf374a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
set locale_dir=($root)/grub/locale
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
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-25-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-24-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-23-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32613837-1122-44b9-8f04-0257fdf374a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8160884-b953-4656-b2d1-857b7ecf805e
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.404406548 = 0.434228224    boot/grub/core.img                             2
   0.353612900 = 0.379688960    grub/core.img                                  2
   0.358997345 = 0.385470464    grub/grub.cfg                                  1
   0.031311035 = 0.033619968    initrd.img-2.6.35-22-generic                  44
   0.051081657 = 0.054848512    initrd.img-2.6.35-23-generic                  48
   0.066492081 = 0.071395328    initrd.img-2.6.35-24-generic                  47
   0.093375206 = 0.100260864    initrd.img-2.6.35-25-generic                  45
   0.272281647 = 0.292360192    initrd.img-2.6.35-28-generic                  45
   0.013771057 = 0.014786560    vmlinuz-2.6.35-22-generic                     19
   0.037656784 = 0.040433664    vmlinuz-2.6.35-23-generic                     18
   0.042383194 = 0.045508608    vmlinuz-2.6.35-24-generic                     20
   0.045322418 = 0.048664576    vmlinuz-2.6.35-25-generic                     21
   0.081173897 = 0.087159808    vmlinuz-2.6.35-28-generic                     21

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=32613837-1122-44b9-8f04-0257fdf374a1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d8160884-b953-4656-b2d1-857b7ecf805e /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=e7a64c62-2d17-46f9-a3f9-a553a6ebff0e none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 e0 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  8e 7e 7a 00 90 1e 00 00  00 00 00 00 02 00 00 00  |.~z.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ef e2 47 e4 4e  4f 20 4e 41 4d 45 20 20  |..)..G.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200





---

### Post by fdrake on 2011-08-21
while in live cd do :
sudo cp /etc/fstab /etc/fstab_bk
gksudo gedit /etc/fstab
delete all,copy and paste the text below
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#/dev/sda1  
UUID=d8160884-b953-4656-b2d1-857b7ecf805e    /boot        ext2        defaults,noatime     1      2
#/dev/sda3       
UUID=32613837-1122-44b9-8f04-0257fdf374a1        /        ext4    errors=remount-ro,rw     0      1
/dev/sda2    
UUID=e7a64c62-2d17-46f9-a3f9-a553a6ebff0e     swap        swap                defaults     0      0
#    aufs                                        /        aufs                      rw     0      0
tmpfs                                            /tmp     tmpfs           nosuid,nodev     0      0



```

reboot



ps. if you check your boot script results yu do have installed GRUB2(v 1.97). so the grub installation is fine. the only thing missing is in the fstab an entry for the / and /boot partitions. we should have checked that for first. also compare this booting script with the first one, all the inode numbers are present while in the first you had just a bunch of ????????? symbols because of filesystem errors.

---

### Post by AdamShumpisxXx on 2011-08-22
OK. Done. Also, I'd like to add that I don't think I'm actually editing my real /etc/fstab by the way it looked when I initially gave you the read-out of sudo gedit /etc/fstab but I obviously could be wrong. Anyways...what's next? Save and reboot or...?

---

### Post by Miljet on 2011-08-22
Shouldn't "gksudo /etc/fstab" read "gksudo gedit /etc/fstab"?

---

### Post by fdrake on 2011-08-22
> **AdamShumpisxXx said:**
> OK. Done. Also, I'd like to add that I don't think I'm actually editing my real /etc/fstab by the way it looked when I initially gave you the read-out of sudo gedit /etc/fstab but I obviously could be wrong. Anyways...what's next? Save and reboot or...?

replace your fstab with the one i posted. Make a backup first!always.
reboot.


make sure you are actually changing the fstab. use sudo or gksudo to be sure.

---

### Post by AdamShumpisxXx on 2011-08-22
Yes and I did such when I actually went to input that into the terminal. Thanks!

Also...no change.

---

### Post by fdrake on 2011-08-22
> **Miljet said:**
> Shouldn't "gksudo /etc/fstab" read "gksudo gedit /etc/fstab"?

thanks for the heads up!!:D:D i am fused:D

---

### Post by Miljet on 2011-08-22
Don't mean to intrude, but I am following this with great interest. I have had the same problem with wife's computer twice in the last month. Wound up re-installing both times. Best I could ever figure, the partition was somehow corrupted.

---

### Post by AdamShumpisxXx on 2011-08-22
Nothing happened. When you had me overwrite /etc/fstab with what you had we only overwrote the temporary /etc/fstab from the LiveCD environment. I don't know how to mount and edit the real one. Do you? Thanks!

---

### Post by fdrake on 2011-08-22
> **AdamShumpisxXx said:**
> Nothing happened. When you had me overwrite /etc/fstab with what you had we only overwrote the temporary /etc/fstab from the LiveCD environment. I don't know how to mount and edit the real one. Do you? Thanks!
```

sudo mount /dev/sda3 /mnt
gksudo /mnt/etc/fstab
``` 

my bad my fault!. i am on too many threads.

edit can you also post the post of the file here. since the one you gave me is from the cd!!! :D:D

---

### Post by AdamShumpisxXx on 2011-08-22
Here is my REAL /etc/fstab file:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=32613837-1122-44b9-8f04-0257fdf374a1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d8160884-b953-4656-b2d1-857b7ecf805e /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=e7a64c62-2d17-46f9-a3f9-a553a6ebff0e none            swap    sw              0       0


Let me know what I have to change! Thanks!

---

### Post by fdrake on 2011-08-22
the fstab is fine. the grub installation is fine too . In the /boot/grub/grub.cfg some urls are wrong. That's all i could notice. My last shot after that i am going to take a nap  :DD

post here please
```
mount /dev/sda1 /mnt
less /mnt/grub/grub.cfg
```

btw:where r u from and what time is over there?

---

### Post by AdamShumpisxXx on 2011-08-22
Since I believe I am alone in this now I have tried a few things. I tried editing my /etc/fstab file using certain suggestions left but no matter what I do my changes NEVER stick! I boot up the Ubuntu 11.04 LiveCD environment, I mount /dev/sda3 to /mnt, I mount /dev/sda1 to /mnt/boot, and now all of the files are visible and useable on my HDD. I edit my /etc/fstab file with gedit by doing:

> sudo gedit /mnt/etc/fstab

After I'm done with the changes I'd like to make I save the file, unmount the partitions, and reboot the laptop. This gets me nowhere. When I press "M" for manual recover I go in to check my etc/fstab file. NO CHANGES STUCK!!! I've done this 3 times already.

I've been on this problem for over 15 hours straight (dead serious) and I've gained no ground WHAT-SO-EVER. I've only lost it. To me...Ubuntu is broken. An OS is not worth this struggle in any way shape or form. You know what caused it? An update! A RECOMMENDED update! This laptop had 4 things installed on it beyond it's vanilla setup. Sun Java, Adobe Flash, Shotwell Photo manager, and a printer driver PPD file. Ubuntu 10 (both .04 and .10) are the Windows ME OSes of the Linux world. I'm done! I tap out! My advice?! Steer clear of this landmine! If it hasn't happened to you yet it will and when it does...Get ready to reformat and reinstall! That's what I'm going to do. Guess what, though? It's not going to be Ubuntu 10!

Thanks for all your help, fdrake! You're a really good person for hanging in there as long as you did. Too all those reading on...TAKE MY ADVICE! Have a good one!

---

