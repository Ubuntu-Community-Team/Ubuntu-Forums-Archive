---
title: "Lost dual boot  and can't restore - GRUB2"
date: 2010-06-18
forum: General Help
---

### Post by von Stalhein on 2010-06-18
Hello all,
I'm back where I was in Karmic (it's a long story), and even though it was fantastic (no issues whatsoever) with Lucid, somehow I've borked it again.

I have 3 drives - sda is a windows data drive, sdb has the XP Home on it, and sdc contains Lucid. When the above happened, I tried what I'd done on a clean install to no avail - installing grub to the sdb drive and putting it first in BIOS order, which worked.

Perhaps the following 2 items will help the gurus - by the FSM I hope so!!!: -

fdisk - ```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3f79c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1309    10514511   83  Linux
/dev/sdc2            1310       18705   139733370   83  Linux
/dev/sdc3           18706       19458     6042960+   f  W95 Ext'd (LBA)
/dev/sdc5           18706       19458     6042959+  82  Linux swap / Solaris

```

---

### Post by wilee-nilee on 2010-06-18
I'm posting the script so all can see.
              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065   234,436,544   234,420,480   f W95 Ext d (LBA)
/dev/sda5              16,128   234,436,544   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    21,029,084    21,029,022  83 Linux
/dev/sdc2          21,029,085   300,495,824   279,466,740  83 Linux
/dev/sdc3         300,495,886   312,581,806    12,085,921   f W95 Ext d (LBA)
/dev/sdc5         300,495,888   312,581,806    12,085,919  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda5        A83CB1173CB0E18C                       ntfs       Disk 2                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01C3D871F965AC80                       ntfs       DSK1_VOL1                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b362ac08-3495-40da-8589-20eb502bca5d   ext4                                     
/dev/sdc2        45d7a870-5993-4a9d-8380-5bffe691aa1c   ext4       home                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        27179ee5-e990-4dcb-9fc8-a5857a0f1b37   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /home                    ext4       (rw)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b362ac08-3495-40da-8589-20eb502bca5d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=45d7a870-5993-4a9d-8380-5bffe691aa1c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=27179ee5-e990-4dcb-9fc8-a5857a0f1b37 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   6.6GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.32-21-generic
   5.3GB: boot/initrd.img-2.6.32-22-generic
   2.5GB: boot/vmlinuz-2.6.32-21-generic
   5.1GB: boot/vmlinuz-2.6.32-22-generic
   5.3GB: initrd.img
   4.3GB: initrd.img.old
   5.1GB: vmlinuz
   2.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  de 00 5c 00 4d 00 6d 00  da 00 dc 00 dd 00 0e 00  |..\.M.m.........|
00000010  e9 00 e0 00 12 00 e5 00  c0 00 71 00 2c 00 db 00  |..........q.,...|
00000020  12 00 15 00 07 00 ba 00  4d 00 a2 00 78 01 72 00  |........M...x.r.|
00000030  df 00 3e 00 df 00 4d 00  af 00 48 00 27 00 ee 00  |..>...M...H.'...|
00000040  7d 00 63 00 69 00 21 20  1a 00 08 00 22 20 25 00  |}.c.i.! ...." %.|
00000050  a4 00 11 00 78 00 10 00  2c 00 d7 00 24 00 92 01  |....x...,...$...|
00000060  a5 00 e4 00 af 00 13 00  7b 00 1e 00 01 00 0a 00  |........{.......|
00000070  15 00 35 00 bb 00 13 00  0f 00 1d 00 33 00 ab 00  |..5.........3...|
00000080  4a 00 42 00 3f 00 20 00  cf 00 76 00 eb 00 e1 00  |J.B.?. ...v.....|
00000090  76 00 75 00 ca 00 b2 00  64 00 f5 00 2d 00 58 00  |v.u.....d...-.X.|
000000a0  2b 00 a5 00 dc 00 aa 00  71 00 f6 00 f2 00 d3 00  |+.......q.......|
000000b0  10 00 1a 00 fd 00 c1 00  6a 00 70 00 7e 01 02 00  |........j.p.~...|
000000c0  b4 00 ef 00 ab 00 a0 00  2b 00 1b 00 76 00 f1 00  |........+...v...|
000000d0  c5 00 f9 00 df 00 75 00  3a 20 8d 00 50 00 4b 00  |......u.: ..P.K.|
000000e0  d3 00 f9 00 78 00 5a 00  1c 00 ca 00 8f 00 2e 00  |....x.Z.........|
000000f0  22 00 c4 00 17 00 59 00  7f 00 17 00 a2 00 bf 00  |".....Y.........|
00000100  6a 00 57 00 c9 00 bf 00  e1 00 a7 00 d9 00 c2 00  |j.W.............|
00000110  dc 02 22 20 c4 00 53 01  34 00 52 01 ee 00 76 00  |.." ..S.4.R...v.|
00000120  6a 00 20 20 d4 00 f7 00  06 00 7f 00 c1 00 59 00  |j.  ..........Y.|
00000130  bf 00 b1 00 59 00 d1 00  1e 20 ac 00 51 00 0a 00  |....Y.... ..Q...|
00000140  52 01 c6 02 f9 00 27 00  29 00 23 00 68 00 c5 00  |R.....'.).#.h...|
00000150  a1 00 60 01 de 00 ea 00  ac 00 75 00 ac 00 ed 00  |..`.......u.....|
00000160  a3 00 7f 00 40 00 d4 00  61 00 ec 00 b1 00 a2 00  |....@...a.......|
00000170  31 00 be 00 c8 00 e7 00  27 00 46 00 b1 00 fb 00  |1.......'.F.....|
00000180  cd 00 18 00 e6 00 78 01  1a 00 54 00 49 00 d1 00  |......x...T.I...|
00000190  2b 00 ee 00 f7 00 6b 00  1e 20 ba 00 b3 00 f6 00  |+.....k.. ......|
000001a0  b8 00 cb 00 ac 00 bd 00  76 00 29 00 53 00 ea 00  |........v.).S...|
000001b0  26 00 c5 00 f6 00 51 00  2c 00 a3 00 7d 00 00 fe  |&.....Q.,...}...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 9f 6a b8 00 00 00  |...........j....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-06-18
Have you tried putting sdc as the first HD to be read, it has grub2 there.

---

### Post by von Stalhein on 2010-06-18
> **wilee-nilee said:**
> Have you tried putting sdc as the first HD to be read, it has grub2 there.

Yes, it's the first HDD in the BIOS - sorry, I should have stated that.

If I place the XP one first, it loads XP, any other combo goes to the grub menu, and the only OS that boots is Lucid.

I have run ```
sudo update-grub
``` many times without any change. I think the OS prober is designed to sort this, but unfortunately my setup seems to have beaten it :(

I thought I'd fixed this on Lucid install back in May by installing grub2 on dev/sdb (the XP drive) but when I tried to replicate this last night everything faded to black.

Racking my brain, the only change I can remember trying was to make XP the default (wife & kids) in grub, but following the instructions I found didn't work. 
I had no reason to use XP so I think it was a couple of weeks before I found that I couldn't boot into it from grub. Sorry for the dissertation, but I include it in the interests of completeness.

---

### Post by wilee-nilee on 2010-06-18
You have ms bootloaders in sda and sdb and sda1 has a bootflag on it and is a extended partition.

I'm not really sure of the fix here but I think the boot order should be sdc sdb then sda. sda should probably have the boot flag removed since you not trying to boot sda. I haven't looked at the uuid to make sure if they read correctly. I am at the end of being able to stay awake and probably just need to crash and leave this to more experienced helpers.

---

### Post by von Stalhein on 2010-06-18
> **wilee-nilee said:**
> You have ms bootloaders in sda and sdb and sda1 has a bootflag on it and is a extended partition.

I'm not really sure of the fix here but I think the boot order should be sdc sdb then sda. sda should probably have the boot flag removed since you not trying to boot sda. I haven't looked at the uuid to make sure if they read correctly. I am at the end of being able to stay awake and probably just need to crash and leave this to more experienced helpers.
Me too on the eyes thing!!! After this post I'm hitting the sack

blkid
```
/dev/sda5: LABEL="Disk 2" UUID="A83CB1173CB0E18C" TYPE="ntfs" 
/dev/sdb1: LABEL="DSK1_VOL1" UUID="01C3D871F965AC80" TYPE="ntfs" 
/dev/sdc1: UUID="b362ac08-3495-40da-8589-20eb502bca5d" TYPE="ext4" 
/dev/sdc2: LABEL="home" UUID="45d7a870-5993-4a9d-8380-5bffe691aa1c" TYPE="ext4" 
/dev/sdc5: UUID="27179ee5-e990-4dcb-9fc8-a5857a0f1b37" TYPE="swap
```

In the above, Disk 2 is an NTFS data drive (sda), DSK1_VOL1 is XP (sdb), and sdc has Lucid.

How do I take the flag off dev/sda?
Maybe it's worth doing that in isolation to unconfuse grub when trying the update-grub sequence?

---

### Post by wilee-nilee on 2010-06-18
> **von Stalhein said:**
> Me too on the eyes thing!!! After this post I'm hitting the sack

blkid
```
/dev/sda5: LABEL="Disk 2" UUID="A83CB1173CB0E18C" TYPE="ntfs" 
/dev/sdb1: LABEL="DSK1_VOL1" UUID="01C3D871F965AC80" TYPE="ntfs" 
/dev/sdc1: UUID="b362ac08-3495-40da-8589-20eb502bca5d" TYPE="ext4" 
/dev/sdc2: LABEL="home" UUID="45d7a870-5993-4a9d-8380-5bffe691aa1c" TYPE="ext4" 
/dev/sdc5: UUID="27179ee5-e990-4dcb-9fc8-a5857a0f1b37" TYPE="swap
```

In the above, Disk 2 is an NTFS data drive (sda), DSK1_VOL1 is XP (sdb), and sdc has Lucid.

How do I take the flag off dev/sda?
Maybe it's worth doing that in isolation to unconfuse grub when trying the update-grub sequence?

Gparted from the lucid or a live cd will allow the bootflag to be removed. I will look closer at the script a little  today I just got up and need some coffee.

---

### Post by oldfred on 2010-06-18
Some BIOS require a boot flag on a primary partition. Windows needs a boot flag for its boot loader, but Ubuntu/grub does not use a boot flag.

in sda1 you tried installing grub.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

That may be confusing windows or the osprober in correctly finding windows. Just delete that. In Vista/7 is a /Boot folder that the above greatly confuses but not sure in XP.

I found in my system when I boot from sdc my sda drive is not hd0 but hd1. You might try experimenting with editing the chainboot entry for windows from the grub menu. Hit e for edit and scroll down to the windows entry, try all the alternative but it may be hd2,1.

---

### Post by wilee-nilee on 2010-06-18
> **oldfred said:**
> Some BIOS require a boot flag on a primary partition. Windows needs a boot flag for its boot loader, but Ubuntu/grub does not use a boot flag.

in sda1 you tried installing grub.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

That may be confusing windows or the osprober in correctly finding windows. Just delete that. In Vista/7 is a /Boot folder that the above greatly confuses but not sure in XP.

I found in my system when I boot from sdc my sda drive is not hd0 but hd1. You might try experimenting with editing the chainboot entry for windows from the grub menu. Hit e for edit and scroll down to the windows entry, try all the alternative but it may be hd2,1.

Good call I missed that grub entry Doh.;) I'm going to have to start paying closer attention. I realized this as I had saved the bootscript to post it. And came back to the thread to see what was up and you had posted.;)

---

### Post by von Stalhein on 2010-06-19
Thanks all - I'm very appreciative of your input - I don't have time to troubleshoot the whole thing today or tomorrow, but rest assured I'll give your suggestions a crack and let you know the outcome :-)

It's annoying when RL intervenes!!!

edit: other than the quick thing of removing the boot flag, which I did under gparted - thx.

However, no cigar :-)

Where do I change the ```
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img
```?

---

### Post by oldfred on 2010-06-19
That should be in your c: or windows root. You can delete any way you can. LiveCD or whatever does work.

---

### Post by von Stalhein on 2010-06-20
> **oldfred said:**
> That should be in your c: or windows root. You can delete any way you can. LiveCD or whatever does work.

Sorry, I'm looking in the root of c: and the only thing I can find is the boot.ini

This is the boot.ini on Xp
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

As well, if the Lucid (dev/sdc) drive doesn't need a boot flag, should I remove it as I did for the dev/sda?

---

### Post by oldfred on 2010-06-20
The script showed this;

   Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

So is the script not correct?

You should leave a boot flag on a primary partition on every drive. Only windows and a few others need it but some BIOS will not let you boot unless is sees a boot flag (active partition).

---

### Post by von Stalhein on 2010-06-21
> **oldfred said:**
> The script showed this;

   Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

So is the script not correct?

You should leave a boot flag on a primary partition on every drive. Only windows and a few others need it but some BIOS will not let you boot unless is sees a boot flag (active partition).

No it was right, I was stupid :confused: but I found it eventually.

I've deleted it and updated grub, same thing. The XP disk spins up and I can hear it being accessed but then nothing.

Here is the latest script: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   234,436,544   234,420,480   f W95 Ext d (LBA)
/dev/sda5              16,128   234,436,544   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    21,029,084    21,029,022  83 Linux
/dev/sdc2          21,029,085   300,495,824   279,466,740  83 Linux
/dev/sdc3         300,495,886   312,581,806    12,085,921   f W95 Ext d (LBA)
/dev/sdc5         300,495,888   312,581,806    12,085,919  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda5        A83CB1173CB0E18C                       ntfs       Disk 2                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01C3D871F965AC80                       ntfs       DSK1_VOL1                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b362ac08-3495-40da-8589-20eb502bca5d   ext4                                     
/dev/sdc2        45d7a870-5993-4a9d-8380-5bffe691aa1c   ext4       home                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        27179ee5-e990-4dcb-9fc8-a5857a0f1b37   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /home                    ext4       (rw)
/dev/sda5        /media/Disk 2            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b362ac08-3495-40da-8589-20eb502bca5d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=45d7a870-5993-4a9d-8380-5bffe691aa1c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=27179ee5-e990-4dcb-9fc8-a5857a0f1b37 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.32-21-generic
   5.3GB: boot/initrd.img-2.6.32-22-generic
   2.5GB: boot/vmlinuz-2.6.32-21-generic
   5.1GB: boot/vmlinuz-2.6.32-22-generic
   5.3GB: initrd.img
   4.3GB: initrd.img.old
   5.1GB: vmlinuz
   2.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  de 00 5c 00 4d 00 6d 00  da 00 dc 00 dd 00 0e 00  |..\.M.m.........|
00000010  e9 00 e0 00 12 00 e5 00  c0 00 71 00 2c 00 db 00  |..........q.,...|
00000020  12 00 15 00 07 00 ba 00  4d 00 a2 00 78 01 72 00  |........M...x.r.|
00000030  df 00 3e 00 df 00 4d 00  af 00 48 00 27 00 ee 00  |..>...M...H.'...|
00000040  7d 00 63 00 69 00 21 20  1a 00 08 00 22 20 25 00  |}.c.i.! ...." %.|
00000050  a4 00 11 00 78 00 10 00  2c 00 d7 00 24 00 92 01  |....x...,...$...|
00000060  a5 00 e4 00 af 00 13 00  7b 00 1e 00 01 00 0a 00  |........{.......|
00000070  15 00 35 00 bb 00 13 00  0f 00 1d 00 33 00 ab 00  |..5.........3...|
00000080  4a 00 42 00 3f 00 20 00  cf 00 76 00 eb 00 e1 00  |J.B.?. ...v.....|
00000090  76 00 75 00 ca 00 b2 00  64 00 f5 00 2d 00 58 00  |v.u.....d...-.X.|
000000a0  2b 00 a5 00 dc 00 aa 00  71 00 f6 00 f2 00 d3 00  |+.......q.......|
000000b0  10 00 1a 00 fd 00 c1 00  6a 00 70 00 7e 01 02 00  |........j.p.~...|
000000c0  b4 00 ef 00 ab 00 a0 00  2b 00 1b 00 76 00 f1 00  |........+...v...|
000000d0  c5 00 f9 00 df 00 75 00  3a 20 8d 00 50 00 4b 00  |......u.: ..P.K.|
000000e0  d3 00 f9 00 78 00 5a 00  1c 00 ca 00 8f 00 2e 00  |....x.Z.........|
000000f0  22 00 c4 00 17 00 59 00  7f 00 17 00 a2 00 bf 00  |".....Y.........|
00000100  6a 00 57 00 c9 00 bf 00  e1 00 a7 00 d9 00 c2 00  |j.W.............|
00000110  dc 02 22 20 c4 00 53 01  34 00 52 01 ee 00 76 00  |.." ..S.4.R...v.|
00000120  6a 00 20 20 d4 00 f7 00  06 00 7f 00 c1 00 59 00  |j.  ..........Y.|
00000130  bf 00 b1 00 59 00 d1 00  1e 20 ac 00 51 00 0a 00  |....Y.... ..Q...|
00000140  52 01 c6 02 f9 00 27 00  29 00 23 00 68 00 c5 00  |R.....'.).#.h...|
00000150  a1 00 60 01 de 00 ea 00  ac 00 75 00 ac 00 ed 00  |..`.......u.....|
00000160  a3 00 7f 00 40 00 d4 00  61 00 ec 00 b1 00 a2 00  |....@...a.......|
00000170  31 00 be 00 c8 00 e7 00  27 00 46 00 b1 00 fb 00  |1.......'.F.....|
00000180  cd 00 18 00 e6 00 78 01  1a 00 54 00 49 00 d1 00  |......x...T.I...|
00000190  2b 00 ee 00 f7 00 6b 00  1e 20 ba 00 b3 00 f6 00  |+.....k.. ......|
000001a0  b8 00 cb 00 ac 00 bd 00  76 00 29 00 53 00 ea 00  |........v.).S...|
000001b0  26 00 c5 00 f6 00 51 00  2c 00 a3 00 7d 00 00 fe  |&.....Q.,...}...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 9f 6a b8 00 00 00  |...........j....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I haven't played around in the grub menu yet, I'll try that now.

Just tried all combinations of 0,1 and 2 with the same result - HDD light, whirr, whirr, whirr, black screen, fade to grey, silence. Not sure if I said, but if I put the XP drive first in BIOS order XP fires up without any issues, so the stopper must be elsewhere.

---

### Post by oldfred on 2010-06-21
If your windows boots ok then it must be the combination of 

menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='[COLOR=Red](hd1,1[/COLOR])'
    search --no-floppy --fs-uuid --set 01c3d871f965ac80
    drivemap -s [COLOR=Red](hd0) ${root}[/COLOR]
    chainloader +1
}

I would think the hd1 in set root should match hd1 in drivemap which is now hd0. I never understood which {root} means so you can also use in the drivemap -s (hd0) (hd1) as an alternative.

Your windows boot.ini says it is:
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
but grub is seeing it as sdb or disk(1). Something is wrong that windows works when it boots as drive 0 but grub will not see it as drive 0.

---

### Post by von Stalhein on 2010-06-22
> **oldfred said:**
> If your windows boots ok then it must be the combination of 

menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='[COLOR=Red](hd1,1[/COLOR])'
    search --no-floppy --fs-uuid --set 01c3d871f965ac80
    drivemap -s [COLOR=Red](hd0) ${root}[/COLOR]
    chainloader +1
}

I would think the hd1 in set root should match hd1 in drivemap which is now hd0. I never understood which {root} means so you can also use in the drivemap -s (hd0) (hd1) as an alternative.

Your windows boot.ini says it is:
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
but grub is seeing it as sdb or disk(1). Something is wrong that windows works when it boots as drive 0 but grub will not see it as drive 0.

Hi oldfred,

I tried matching set root to be the same as drivemap, but no success. Although, as I write this I realise that I only tried with the "1" value. I suppose I should run through some other combinations.

I take your point about sdb. I wonder if it has something to do with the way my hdds are setup on the motherboard?

In the BIOS the disks are seen as:
1. SCSI-0 *(drive #)*(Lucid)
2. Ch0 S S_ATA2*(drive #)* (XP)
3. Ch0 M S_ATA1*(drive #)* (Data)

---

### Post by oldfred on 2010-06-22
I assume S is slave & M is master. It would be better I think to have an operating system as master. These are then IDE drives?

---

### Post by von Stalhein on 2010-06-22
No, 3 x SATA. Your guess on designations makes sense though I would think.

The mobo is a [GigaByte GA-8PENXP]("http://www.pcstats.com/articleview.cfm?articleid=1437&page=1")
I built it  along time ago!!

I wonder how much confusion I would cause swapping them around on the mobo :-)

I'll give it a go after work (7.30am here atm).

Thanks.

New script, but same result - XP is now dev/sda - I've run sudo update-grub
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   234,436,544   234,420,480   f W95 Ext d (LBA)
/dev/sdb5              16,128   234,436,544   234,420,417   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    21,029,084    21,029,022  83 Linux
/dev/sdc2          21,029,085   300,495,824   279,466,740  83 Linux
/dev/sdc3         300,495,886   312,581,806    12,085,921   f W95 Ext d (LBA)
/dev/sdc5         300,495,888   312,581,806    12,085,919  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01C3D871F965AC80                       ntfs       DSK1_VOL1                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        A83CB1173CB0E18C                       ntfs       Disk 2                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b362ac08-3495-40da-8589-20eb502bca5d   ext4                                     
/dev/sdc2        45d7a870-5993-4a9d-8380-5bffe691aa1c   ext4       home                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        27179ee5-e990-4dcb-9fc8-a5857a0f1b37   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b362ac08-3495-40da-8589-20eb502bca5d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=45d7a870-5993-4a9d-8380-5bffe691aa1c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=27179ee5-e990-4dcb-9fc8-a5857a0f1b37 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   6.9GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.32-21-generic
   5.3GB: boot/initrd.img-2.6.32-22-generic
   2.5GB: boot/vmlinuz-2.6.32-21-generic
   5.1GB: boot/vmlinuz-2.6.32-22-generic
   5.3GB: initrd.img
   4.3GB: initrd.img.old
   5.1GB: vmlinuz
   2.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  de 00 5c 00 4d 00 6d 00  da 00 dc 00 dd 00 0e 00  |..\.M.m.........|
00000010  e9 00 e0 00 12 00 e5 00  c0 00 71 00 2c 00 db 00  |..........q.,...|
00000020  12 00 15 00 07 00 ba 00  4d 00 a2 00 78 01 72 00  |........M...x.r.|
00000030  df 00 3e 00 df 00 4d 00  af 00 48 00 27 00 ee 00  |..>...M...H.'...|
00000040  7d 00 63 00 69 00 21 20  1a 00 08 00 22 20 25 00  |}.c.i.! ...." %.|
00000050  a4 00 11 00 78 00 10 00  2c 00 d7 00 24 00 92 01  |....x...,...$...|
00000060  a5 00 e4 00 af 00 13 00  7b 00 1e 00 01 00 0a 00  |........{.......|
00000070  15 00 35 00 bb 00 13 00  0f 00 1d 00 33 00 ab 00  |..5.........3...|
00000080  4a 00 42 00 3f 00 20 00  cf 00 76 00 eb 00 e1 00  |J.B.?. ...v.....|
00000090  76 00 75 00 ca 00 b2 00  64 00 f5 00 2d 00 58 00  |v.u.....d...-.X.|
000000a0  2b 00 a5 00 dc 00 aa 00  71 00 f6 00 f2 00 d3 00  |+.......q.......|
000000b0  10 00 1a 00 fd 00 c1 00  6a 00 70 00 7e 01 02 00  |........j.p.~...|
000000c0  b4 00 ef 00 ab 00 a0 00  2b 00 1b 00 76 00 f1 00  |........+...v...|
000000d0  c5 00 f9 00 df 00 75 00  3a 20 8d 00 50 00 4b 00  |......u.: ..P.K.|
000000e0  d3 00 f9 00 78 00 5a 00  1c 00 ca 00 8f 00 2e 00  |....x.Z.........|
000000f0  22 00 c4 00 17 00 59 00  7f 00 17 00 a2 00 bf 00  |".....Y.........|
00000100  6a 00 57 00 c9 00 bf 00  e1 00 a7 00 d9 00 c2 00  |j.W.............|
00000110  dc 02 22 20 c4 00 53 01  34 00 52 01 ee 00 76 00  |.." ..S.4.R...v.|
00000120  6a 00 20 20 d4 00 f7 00  06 00 7f 00 c1 00 59 00  |j.  ..........Y.|
00000130  bf 00 b1 00 59 00 d1 00  1e 20 ac 00 51 00 0a 00  |....Y.... ..Q...|
00000140  52 01 c6 02 f9 00 27 00  29 00 23 00 68 00 c5 00  |R.....'.).#.h...|
00000150  a1 00 60 01 de 00 ea 00  ac 00 75 00 ac 00 ed 00  |..`.......u.....|
00000160  a3 00 7f 00 40 00 d4 00  61 00 ec 00 b1 00 a2 00  |....@...a.......|
00000170  31 00 be 00 c8 00 e7 00  27 00 46 00 b1 00 fb 00  |1.......'.F.....|
00000180  cd 00 18 00 e6 00 78 01  1a 00 54 00 49 00 d1 00  |......x...T.I...|
00000190  2b 00 ee 00 f7 00 6b 00  1e 20 ba 00 b3 00 f6 00  |+.....k.. ......|
000001a0  b8 00 cb 00 ac 00 bd 00  76 00 29 00 53 00 ea 00  |........v.).S...|
000001b0  26 00 c5 00 f6 00 51 00  2c 00 a3 00 7d 00 00 fe  |&.....Q.,...}...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 9f 6a b8 00 00 00  |...........j....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by von Stalhein on 2010-06-23
OK oldfred - new post as I have fixed it :p

I remembered some stuff from the last time I "lost" the grub functionality.

Basically, I think Windows likes to be the first drive in the disk pecking order.

Therefore grub needs to be in the first disk's mbr.

So I uninstalled grub from dev/sdc (Lucid) and reinstalled it to /dev/sda (XP after I shifted the plug on the mobo).

It worked, booting into XP when that menu choice was selected.

For interest' sake I post the results.txt as it now is:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   234,436,544   234,420,480   f W95 Ext d (LBA)
/dev/sdb5              16,128   234,436,544   234,420,417   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    21,029,084    21,029,022  83 Linux
/dev/sdc2          21,029,085   300,495,824   279,466,740  83 Linux
/dev/sdc3         300,495,886   312,581,806    12,085,921   f W95 Ext d (LBA)
/dev/sdc5         300,495,888   312,581,806    12,085,919  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01C3D871F965AC80                       ntfs       DSK1_VOL1                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        A83CB1173CB0E18C                       ntfs       Disk 2                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b362ac08-3495-40da-8589-20eb502bca5d   ext4                                     
/dev/sdc2        45d7a870-5993-4a9d-8380-5bffe691aa1c   ext4       home                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        27179ee5-e990-4dcb-9fc8-a5857a0f1b37   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b362ac08-3495-40da-8589-20eb502bca5d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=45d7a870-5993-4a9d-8380-5bffe691aa1c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=27179ee5-e990-4dcb-9fc8-a5857a0f1b37 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.32-21-generic
   5.3GB: boot/initrd.img-2.6.32-22-generic
   2.5GB: boot/vmlinuz-2.6.32-21-generic
   5.1GB: boot/vmlinuz-2.6.32-22-generic
   5.3GB: initrd.img
   4.3GB: initrd.img.old
   5.1GB: vmlinuz
   2.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  de 00 5c 00 4d 00 6d 00  da 00 dc 00 dd 00 0e 00  |..\.M.m.........|
00000010  e9 00 e0 00 12 00 e5 00  c0 00 71 00 2c 00 db 00  |..........q.,...|
00000020  12 00 15 00 07 00 ba 00  4d 00 a2 00 78 01 72 00  |........M...x.r.|
00000030  df 00 3e 00 df 00 4d 00  af 00 48 00 27 00 ee 00  |..>...M...H.'...|
00000040  7d 00 63 00 69 00 21 20  1a 00 08 00 22 20 25 00  |}.c.i.! ...." %.|
00000050  a4 00 11 00 78 00 10 00  2c 00 d7 00 24 00 92 01  |....x...,...$...|
00000060  a5 00 e4 00 af 00 13 00  7b 00 1e 00 01 00 0a 00  |........{.......|
00000070  15 00 35 00 bb 00 13 00  0f 00 1d 00 33 00 ab 00  |..5.........3...|
00000080  4a 00 42 00 3f 00 20 00  cf 00 76 00 eb 00 e1 00  |J.B.?. ...v.....|
00000090  76 00 75 00 ca 00 b2 00  64 00 f5 00 2d 00 58 00  |v.u.....d...-.X.|
000000a0  2b 00 a5 00 dc 00 aa 00  71 00 f6 00 f2 00 d3 00  |+.......q.......|
000000b0  10 00 1a 00 fd 00 c1 00  6a 00 70 00 7e 01 02 00  |........j.p.~...|
000000c0  b4 00 ef 00 ab 00 a0 00  2b 00 1b 00 76 00 f1 00  |........+...v...|
000000d0  c5 00 f9 00 df 00 75 00  3a 20 8d 00 50 00 4b 00  |......u.: ..P.K.|
000000e0  d3 00 f9 00 78 00 5a 00  1c 00 ca 00 8f 00 2e 00  |....x.Z.........|
000000f0  22 00 c4 00 17 00 59 00  7f 00 17 00 a2 00 bf 00  |".....Y.........|
00000100  6a 00 57 00 c9 00 bf 00  e1 00 a7 00 d9 00 c2 00  |j.W.............|
00000110  dc 02 22 20 c4 00 53 01  34 00 52 01 ee 00 76 00  |.." ..S.4.R...v.|
00000120  6a 00 20 20 d4 00 f7 00  06 00 7f 00 c1 00 59 00  |j.  ..........Y.|
00000130  bf 00 b1 00 59 00 d1 00  1e 20 ac 00 51 00 0a 00  |....Y.... ..Q...|
00000140  52 01 c6 02 f9 00 27 00  29 00 23 00 68 00 c5 00  |R.....'.).#.h...|
00000150  a1 00 60 01 de 00 ea 00  ac 00 75 00 ac 00 ed 00  |..`.......u.....|
00000160  a3 00 7f 00 40 00 d4 00  61 00 ec 00 b1 00 a2 00  |....@...a.......|
00000170  31 00 be 00 c8 00 e7 00  27 00 46 00 b1 00 fb 00  |1.......'.F.....|
00000180  cd 00 18 00 e6 00 78 01  1a 00 54 00 49 00 d1 00  |......x...T.I...|
00000190  2b 00 ee 00 f7 00 6b 00  1e 20 ba 00 b3 00 f6 00  |+.....k.. ......|
000001a0  b8 00 cb 00 ac 00 bd 00  76 00 29 00 53 00 ea 00  |........v.).S...|
000001b0  26 00 c5 00 f6 00 51 00  2c 00 a3 00 7d 00 00 fe  |&.....Q.,...}...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 9f 6a b8 00 00 00  |...........j....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thanks again for your input - it got me on the right track for sure. I'll mark this as solved!!! :biggrin:

---

### Post by oldfred on 2010-06-23
Glad you got it solved.

There is something about grub2 drive numbering when you do not boot from sda. On my system I boot sdc, but my chainboot entry to sda has to be hd1 not hd0 as I would expect. Then that kind of renumbering must mess with windows renumbering. I thought drivemap was supposed to straighten it out but obviously not.

---

