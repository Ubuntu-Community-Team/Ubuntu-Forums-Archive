---
title: "Windows 7 Is not showing in boot menu even after editing 40_custom file"
date: 2010-10-09
forum: General Help
---

### Post by dhyan on 2010-10-09
Dear all,

I am very new user to ubuntu and new to this community,first of all if i make anything wrong in this post please forgive and guide me,

My friend have a laptop which was running in windows 7.Last week he installed Ubuntu 10.04 Lucid Lynx.But after that boot menu is not showing and it is automatically booting to ubuntu.

So i pressed Shift key during boot and checked boot menu list,which is showing only linux OS ,Linux OS recovery mode and memtest86,No windows 7 option.

So I did following things.

Step1: Tried to find out the partitions using fdisk -l

das@das:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       15371   123459494+   f  W95 Ext'd (LBA)
/dev/sda2           15372       16118     5999616   82  Linux swap / Solaris
/dev/sda3   *       16118       30402   114729984   83  Linux
/dev/sda5               2        3825    30716248+   7  HPFS/NTFS
/dev/sda6            3826       15371    92743213+   7  HPFS/NTFS

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders
Units = cylinders of 342 * 512 = 175104 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92362ec

2.So i tried to add a manual entry by editing the /etc/grub.d/40_custom file like below ,and changed the permission using chmod +x update-grub command 

#!/bin/sh
exec tail -n +3 $0
echo "Adding Windows 7" 
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7"	{
	set root=(hd0,6)
	chainloader +1
}

3.Run the update-grub command 

das@das:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

But it is not updating the manual entry,The above update-grub command output showing the update-grub command  not even entering into the /etc/grub.d/40_custom file because i put echo in that file in that ,and that also not coming.

So somebody please help me on resolving this issue?attaching the 40_custom file 

Thanks In Advance
Abhilash V R

---

### Post by Quackers on 2010-10-09
Welcome to UbuntuForums.
Go to the link below and download the boot_info_script and run it. Then please post the contents of the results.txt file in your next post inside code tags (click on New Reply then on the menu bar click on # then paste the contents in between the code tags).
This will give people a better idea of what's going on with your system.

---

### Post by oldfred on 2010-10-09
Please run boot info script, but I think I see one of the issues. 

You must have had an older install of windows in sda1 or sda2. Windows only boots from a primary partition. If you install a second windows it can be in a logical partition but moves all its boot files to the first install and can only boot thru the primary partition.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by dhyan on 2010-10-09
Hi
please find the boot info script results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   246,935,114   246,918,989   f W95 Ext d (LBA)
/dev/sda5              16,128    61,448,624    61,432,497   7 HPFS/NTFS
/dev/sda6          61,448,688   246,935,114   185,486,427   7 HPFS/NTFS
/dev/sda2         246,935,552   258,934,783    11,999,232  82 Linux swap / Solaris
/dev/sda3    *    258,934,784   488,394,751   229,459,968  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     3,944,447     3,936,256   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        035df22c-8406-4373-aa51-80db8d3886b3   swap                                     
/dev/sda3        ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836   ext4                                     
/dev/sda5        E21287111286EA3D                       ntfs                                     
/dev/sda6        46A0B51EA0B51601                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BC7A-3720                              vfat       ABIS                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/ABIS              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
echo "Adding Windows 7" 
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7"	{
	set root=(hd0,6)
	chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=ba4d1a6a-f916-4f98-9ec3-9fbd1fb32836 /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 188.5GB: boot/grub/core.img
 188.5GB: boot/grub/grub.cfg
 188.5GB: boot/initrd.img-2.6.32-21-generic
 132.7GB: boot/vmlinuz-2.6.32-21-generic
 188.5GB: initrd.img
 132.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  a3 6f b9 0f 99 09 49 36  2e 84 48 ea d2 18 a6 38  |.o....I6..H....8|
00000010  54 c9 61 d4 aa 34 14 7e  58 66 30 9f fa f1 af 40  |T.a..4.~Xf0....@|
00000020  93 3e 0b 9c 0e 93 0f ae  20 18 32 de f9 da 20 98  |.>...... .2... .|
00000030  6c cd 94 71 98 fe da 8f  6b aa 04 22 d5 68 cd d6  |l..q....k..".h..|
00000040  e5 90 4d 57 6b 34 61 d5  99 61 2e 69 4b 29 de 4c  |..MWk4a..a.iK).L|
00000050  49 7a a5 b5 da 91 66 b8  b7 d8 f5 cc 32 72 96 43  |Iz....f.....2r.C|
00000060  0e 4b 34 6a 63 77 11 93  d0 7a 99 37 1c e4 07 3d  |.K4jcw...z.7...=|
00000070  28 51 a0 1d 8a 18 bd 88  42 8a 5c 09 5a 8f 0f 1b  |(Q......B.\.Z...|
00000080  a3 e4 36 f3 ad 3f ea 9f  f7 2a 25 c3 be 82 07 3f  |..6..?...*%....?|
00000090  d7 ac f4 29 09 1c 93 79  f1 b5 5a a7 3b f5 0d be  |...)...y..Z.;...|
000000a0  ff 2a 59 39 f5 e2 5f a7  ac fe a3 00 98 32 8a 9b  |.*Y9.._......2..|
000000b0  b3 17 16 be 79 06 44 de  cc 3c 0b bd 1a 91 bc ec  |....y.D..<......|
000000c0  16 bc 32 0e 8b 6f 32 fd  c9 fa 86 5f d2 85 28 f7  |..2..o2...._..(.|
000000d0  d7 48 8e b6 f7 ae 46 a2  c5 a1 a4 d2 a6 a6 2b 4f  |.H....F.......+O|
000000e0  ea 01 c9 9d 57 5f e8 7f  89 2e 30 46 28 ca 27 b8  |....W_....0F(.'.|
000000f0  b0 c0 78 87 22 c9 03 51  53 6f 7d d3 98 7c 63 df  |..x."..QSo}..|c.|
00000100  fb b7 5e 8c 5f 76 37 23  c9 95 be df 80 e0 c0 10  |..^._v7#........|
00000110  29 cc 3c aa 1c ce 39 e4  f9 c8 86 1f 87 7f 14 1a  |).<...9.........|
00000120  e8 b9 af be 29 d5 c8 70  ee 0d de 46 5d e3 31 c6  |....)..p...F].1.|
00000130  da 37 30 23 b0 4c d6 8b  c9 e8 2f 65 f3 49 f1 10  |.70#.L..../e.I..|
00000140  95 33 08 23 94 59 86 7e  c3 ea b0 4c 26 2a dc 3b  |.3.#.Y.~...L&*.;|
00000150  d3 6a 9e 12 41 dd ba 70  6d 12 54 31 2b 1f 93 e8  |.j..A..pm.T1+...|
00000160  6b 55 b5 3e 9e 3c 1f 5e  1a 6e 3d 90 fd 84 0c ee  |kU.>.<.^.n=.....|
00000170  85 66 94 ca 10 f3 fd 1c  84 1f 92 5c 4c 77 1a 7c  |.f.........\Lw.||
00000180  58 7d 14 de 70 8e 6c 0a  1f 77 e7 ba 77 b7 f8 5f  |X}..p.l..w..w.._|
00000190  dc b7 22 f6 be 44 65 fa  06 27 00 52 f3 1f 19 37  |.."..De..'.R...7|
000001a0  41 cb dd db 71 e5 2d 1e  74 16 ab d3 e3 81 09 01  |A...q.-.t.......|
000001b0  d2 3e c3 27 88 17 ed 6a  9f 47 d4 71 0c ea 00 01  |.>.'...j.G.q....|
000001c0  01 01 07 fe ff ff 02 00  00 00 b1 62 a9 03 00 fe  |...........b....|
000001d0  ff ff 05 fe ff ff b3 62  a9 03 9a 4c 0e 0b 00 00  |.......b...L....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2010-10-09
Your NTFS windows partition is missing:
/bootmgr /Boot/BCD 

Windows will not repair your install in a logical partition. You have partition logic reversed. Windows has to be in a primary partition to boot. (At least first install of windows). And Ubuntu can be in logical partitions and boot without issue.

You might be able to create a sda4 partition and make it be the boot partition but without a full install of windows I am not sure how. Or delete and move swap into the logical partition but that also requires editing fstab.

The best solution is to back up all important data and reinstall. If you really want to try to make it bootable, I do have some older links from those that really understand systems and may be able to rebuild the partition table to convert a logical to a primary.

---

### Post by dhyan on 2010-10-10
Thanks for the guidance ,i will try to repair one of the way you mentioned.

But Still i have a doubt,After editing the Manual entry /etc/grub.d/40_custom file when i run the update-grub command why update-grub is not entering into the /etc/grub.d/40_custom file (i put an echo command which is not printing after i run the command)?

my 40_custom file 

```
#!/bin/sh
exec tail -n +3 $0
echo "Adding Windows 7" 
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7"	{
	set root=(hd0,6)
	chainloader +1
}

```

output of update-grub command

```

das@das:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by dcstar on 2010-10-10
> **dhyan said:**
> 
.........
output of update-grub command

```

das@das:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

That is the output of the detected boot partition code, a manual entry may not be listed there.

What is in the actual Grub menu?

---

### Post by dcstar on 2010-10-10
> **dhyan said:**
> Thanks for the guidance ,i will try to repair one of the way you mentioned.

But Still i have a doubt,After editing the Manual entry /etc/grub.d/40_custom file when i run the update-grub command why update-grub is not entering into the /etc/grub.d/40_custom file (i put an echo command which is not printing after i run the command)?

my 40_custom file 

```
#!/bin/sh
exec tail -n +3 $0
echo "Adding Windows 7" 
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7"	{
	set root=(hd0,6)
	chainloader +1
}

```


Here is a Windows entry from my BURG system, you may want to try something in this format (the UUID is my own one, substitute yours):

```
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	savedefault
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 61e2897c116b5df4
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

---

### Post by Mark Phelps on 2010-10-10
It's not a matter of the entry -- it's a matter of the boot files being missing!  If the boot loader files are there, the new GRUB 2 WILL create an entry for them.

No entry you try, no matter how you create it, is going to work until you take oldfred's advice and reinstall the Win7 boot loader files.

---

### Post by oldfred on 2010-10-10
More info, if you want. Any partition editing may corrupt system so have good backups.

Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

