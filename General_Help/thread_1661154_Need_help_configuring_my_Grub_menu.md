---
title: "Need help configuring my Grub menu"
date: 2011-01-06
forum: General Help
---

### Post by F1lthym0nk3y on 2011-01-06
Hello fellow ubuntu users,

I need some help configuring my Grub setup, currently my PC will just book straight into ubuntu, Id like it so I can choose between this and my windows 7 installation..

Ive tried to follow some internet tutorials on this matter but they all point me in the direction of "sudo gedit /boot/grub/menu.lst" which is, when opened completely empty.

Id like it so ubuntu is the default OS followed by windows 7, but waits 15 seconds before booting into the default.

Thanks guys..

---

### Post by carandraug on 2011-01-06
Hey

those instructions you had been following apply only to the "old" GRUB. Ubuntu now ships with GRUB2 which is slightly different.

If you're not confortable with editing the text file and command line, install and use Startup-manager (see how on the [Ubuntu documentation]("https://help.ubuntu.com/community/StartUpManager")).

If you're ok with changing it yourself, see how on the [ubuntu documentation too]("https://help.ubuntu.com/community/Grub2"). Don't forget to run```
sudo update-grub
``` in the end. You should only need to edit the file [FONT="Courier New"]/etc/default/grub[/FONT]

---

### Post by F1lthym0nk3y on 2011-01-06
> **carandraug said:**
> Hey

those instructions you had been following apply only to the "old" GRUB. Ubuntu now ships with GRUB2 which is slightly different.

If you're not confortable with editing the text file and command line, install and use Startup-manager (see how on the [Ubuntu documentation]("https://help.ubuntu.com/community/StartUpManager")).

If you're ok with changing it yourself, see how on the [ubuntu documentation too]("https://help.ubuntu.com/community/Grub2"). Don't forget to run```
sudo update-grub
``` in the end. You should only need to edit the file [FONT="Courier New"]/etc/default/grub[/FONT]

Okay, so I have got the latest version of grub2 installed..

But cannot find an option to add another OS in startup manager. My original MBR was located within a vista partition I have recently formated over, so this could be tricky.. :/

---

### Post by leeper69 on 2011-01-06
what program did you use to format your old vista partition?

---

### Post by lrgmmc on 2011-01-06
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager) might be what you are looking for. it lets you set default and wait time for grub.

---

### Post by F1lthym0nk3y on 2011-01-06
I used my vista installation disk to format the Vista partition which had the MBR which by default booted into Windows 7...

My startup manager looks abit different from the one shown in the diagram, it only displays 2 tabs.

I know what partition the windows 7 OS is located but somehow think I will have to manually create a new MBR for it?

---

### Post by leeper69 on 2011-01-06
did you create a backup disk in window$ vista?  
going off-line will check u later today  but at this point it look like you may need to reinstall vista and then Ubuntu. but then there is always another answer.

---

### Post by gadolinio on 2011-01-06
> **lrgmmc said:**
> [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager) might be what you are looking for. it lets you set default and wait time for grub.

+1. It might be useful.

---

### Post by oldfred on 2011-01-06
Run the boot script so we can tell what is where. If you have two windows installs it moves the boot files from the second install to the "active" partition or the one with the boot flag. If your second install is in a primary it may be able to repair it, by adding all the boot files back.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by F1lthym0nk3y on 2011-01-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,827,872,247 2,827,870,200   7 HPFS/NTFS
/dev/sda2       2,827,872,256 2,930,272,255   102,400,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,922,801,663 1,922,799,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   890,882,047   890,880,000   6 FAT16
/dev/sdc2         890,884,094   976,771,071    85,886,978   5 Extended
/dev/sdc5         890,884,096   894,787,583     3,903,488  82 Linux swap / Solaris
/dev/sdc6         894,789,632   976,771,071    81,981,440  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    31,326,207    31,326,145   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DA9C94729C944AC1                       ntfs       Downloads                     
/dev/sda2        3A0897110896CB71                       ntfs       Windows 7                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BCEE1DEBEE1D9EA8                       ntfs       Arch Linux                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        feb07c3b-c405-4fd5-b1c6-3debc3183e92   swap                                     
/dev/sdc6        105b93d4-e13a-483d-a5dd-0cc01da32180   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4CD4-3323                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/Arch Linux        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=feb07c3b-c405-4fd5-b1c6-3debc3183e92 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


 495.9GB: boot/grub/core.img
 462.8GB: boot/grub/grub.cfg
 459.7GB: boot/initrd.img-2.6.35-24-generic-pae
 496.0GB: boot/vmlinuz-2.6.35-24-generic-pae
 459.7GB: initrd.img
 496.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  22 23 bc 7e bc 3f dc 6b  bd 07 79 09 5d bc d0 85  |"#.~.?.k..y.]...|
00000010  7c ab 4c a7 da 01 be 4e  8a 8d db f1 3c bc 7c 83  ||.L....N....<.|.|
00000020  83 3c 8c b3 44 5a c9 35  a7 e2 5e c2 be 2f 30 a1  |.<..DZ.5..^../0.|
00000030  3b c8 2f e6 6f 1f 83 fe  92 30 6f 3c d5 01 8f a5  |;./.o....0o<....|
00000040  76 81 1b 79 c3 6f 16 17  e2 d0 0b 75 d1 81 d7 69  |v..y.o.....u...i|
00000050  7f 4c f2 77 c2 29 e9 6b  92 a4 7b cb 4b a0 7b eb  |.L.w.).k..{.K.{.|
00000060  e3 39 d4 a1 c4 16 cb 18  0b 7c c4 97 a2 0e e0 e7  |.9.......|......|
00000070  c9 57 7e 23 e8 19 39 20  a1 79 88 6e 55 59 18 76  |.W~#..9 .y.nUY.v|
00000080  24 bb 68 b3 1b 7e 5e a7  68 a3 0b 7e 84 b2 36 35  |$.h..~^.h..~..65|
00000090  8a 7d 1f 69 57 07 20 a7  7c bb 63 02 f2 d9 13 3b  |.}.iW. .|.c....;|
000000a0  7b 1a eb a5 64 03 22 c8  bf ab 54 f4 3c e8 f0 bd  |{...d."...T.<...|
000000b0  ab b2 e0 00 89 8b 53 e1  81 08 e4 eb ad c0 e6 22  |......S........"|
000000c0  e0 fb ab 7b 59 a3 80 fb  41 dc 10 06 bc 6b ec 0f  |...{Y...A....k..|
000000d0  3f 84 1f 75 2f 9e 4a 03  1e 98 8f 9e 13 02 be ba  |?..u/.J.........|
000000e0  48 55 15 f4 99 36 46 f4  3f a1 97 45 58 d0 8f 79  |HU...6F.?..EX..y|
000000f0  63 6a 9d 08 cf 67 4f 6f  be 8c d1 fa 5a 43 0b e6  |cj...gOo....ZC..|
00000100  6b 89 e7 5a 10 b7 1f cb  2d f5 a0 9e b4 9f e5 e1  |k..Z....-.......|
00000110  3d e9 ec f7 f2 bd f0 af  83 b6 e0 ab 90 db 22 bf  |=.............".|
00000120  f7 f5 2f b4 7a 89 4a d7  20 46 9d ee 03 9f ab 12  |../.z.J. F......|
00000130  74 ba 7e fb 41 3e ed 67  fb c9 95 59 f0 b9 6c 5f  |t.~.A>.g...Y..l_|
00000140  95 1e 7a 83 61 4e 9c 38  d8 1a 50 84 5e 6b 25 fe  |..z.aN.8..P.^k%.|
00000150  f9 94 f4 52 e0 50 64 1b  ea 52 ac 3e 89 71 2f c7  |...R.Pd..R.>.q/.|
00000160  da 60 8f 74 f6 36 05 f8  83 dd 58 45 fb aa 52 31  |.`.t.6....XE..R1|
00000170  4d 1d f4 d3 be d3 2c 8f  f6 07 94 39 67 a0 f7 34  |M.....,....9g..4|
00000180  1a 96 0f bd 58 14 32 6d  21 78 97 a4 82 88 b3 0b  |....X.2m!x......|
00000190  c4 8f 1b 86 8d b8 6f 1f  36 a1 9e 22 71 b0 86 53  |......o.6.."q..S|
000001a0  f0 9b 79 ec e0 69 e0 f9  aa 8f eb a3 fd 12 9a 24  |..y..i.........$|
000001b0  5d 77 3c c9 19 e0 7f bf  c6 3e ab 07 fd 6a 00 fe  |]w<......>...j..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 14 93  3b 00 ee f4 e2 04 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Hope this can help :/?

I don't want to reinstall vista at all, deleting it was why I switched over to ubuntu (Ultimate edition 2.8, not that theres much difference).

Just really want ubuntu as my default and windows 7 for my games :D

---

### Post by oldfred on 2011-01-06
You are missing two files from your windows, so it will not boot. These files are normally in the hidden separate boot/recovery partition that win7 creates or are moved to other windows installs. You can run repairs and add them to sda2.

[COLOR=Red]/bootmgr /Boot/BCD[/COLOR]   /Windows/System32/winload.exe

First you need to move boot flag (active partition in windows) to sda2. You can use gparted or a command to move it.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

Use a windows 7 repair CD and run the repairs:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by F1lthym0nk3y on 2011-01-06
> **oldfred said:**
> You are missing two files from your windows, so it will not boot. These files are normally in the hidden separate boot/recovery partition that win7 creates or are moved to other windows installs. You can run repairs and add them to sda2.

[COLOR=Red]/bootmgr /Boot/BCD[/COLOR]   /Windows/System32/winload.exe

First you need to move boot flag (active partition in windows) to sda2. You can use gparted or a command to move it.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

Use a windows 7 repair CD and run the repairs:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Hello, many thanks for such a detailed and explained solution, I remember running the exact same commands for something like this before, but just to clear it up, will I still be able to boot into ubuntu if I do this, or choose it at a menu?

---

### Post by Quackers on 2011-01-06
No, oldfed's instructions will get Windows booting again (as currently you have boot files missing). It will then be necessary to re-install grub, which will then offer you a choice of OS at the grub menu.

---

### Post by oldfred on 2011-01-06
If you do not run the fixMBR or the automatic repairs grub should remain. But since you have several hard drives I would boot Ubuntu first and install grub2 to sdc. Then totally fix windows including MBR to know it works. Then in BIOS change to boot sdc, the 500GB drive and run sudo update-grub to find windows.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
If that returns any errors run:
sudo grub-install --recheck /dev/sdc
Then after rebooting:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by leeper69 on 2011-01-06
I see you got some professional help going on hope it works out for you 
sorry I had to leave but if you follow there directions you will get your duel boot to work.

---

### Post by QLee on 2011-01-07
[QUOTE=F1lthym0nk3y]...
I don't want to reinstall vista at all, deleting it was why I switched over to ubuntu (Ultimate edition 2.8, not that theres much difference).
...[/QUOTE]

oldfred is giving you good help with booting, I just want to clarify one point. Ultimate edition 2.8 is not an official Ubuntu, that's why they can't use the name Ubuntu in their name. It's based on Ubuntu but, when you ask questions here, it would always be best for you to identify the OS that you are using as from time-to-time there might be differences which might affect the answer you need.

---

### Post by F1lthym0nk3y on 2011-01-07
Hello again guys, ive succesfully entered the commands in a windows command line with success and have tried booting from each hard drive.. But all of them drop straight into ubuntu with no grub menu to choose from. I ran the command sudo update-grub to try and find the windows installation but nothing.. Hmm a tricky one, maybe if I uninstalled grub completely from each hard drive, to see if it will boot into windows then, then use a live cd to setup my grub menu, would this work?

---

### Post by oldfred on 2011-01-07
If you ran fixMBR command on the windows drive it should boot windows (or crash, until fully fixed), there would be no way to get to Ubuntu from a standard windows boot.

If not running standard Ubuntu you may not have the osprober that does all the good work of finding other operating systems. You can add a manual boot stanza to 40_custom if necessary, but lets see if windows works first.

---

### Post by hansolo4949 on 2011-01-07
You should open up a Terminal and type sudo update-grub2 wait for that to finish, then close it out. The other command probably didn't work because it was for the OLD version of grub.


That should work.

hansolo4949

---

### Post by F1lthym0nk3y on 2011-01-07
> **QLee said:**
> oldfred is giving you good help with booting, I just want to clarify one point. Ultimate edition 2.8 is not an official Ubuntu, that's why they can't use the name Ubuntu in their name. It's based on Ubuntu but, when you ask questions here, it would always be best for you to identify the OS that you are using as from time-to-time there might be differences which might affect the answer you need.

Okay thank you for the input, though Ive used Ultimate Edition for a while now and have had no problems following Ubuntu tutorials etc, I thought it was ubuntu with pre installed software and other extras? However I will mention it in future threads.

The BootRec.exe /FixMBR command ran fine with no problems, but when I tried the BootRec.exe /FixBoot, I was confronted with a "Element not found" message. I have managed to get the grub menu to be displayed upon boot, is there a way I could type a command to add a option to the boot menu, as I know where my windows installation is mounted.. Currently having a flick through this [http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html)..

---

### Post by F1lthym0nk3y on 2011-01-07
> **hansolo4949 said:**
> You should open up a Terminal and type sudo update-grub2 wait for that to finish, then close it out. The other command probably didn't work because it was for the OLD version of grub.


That should work.

hansolo4949

Hello, Ive entered this and had the same output as the "sudo update-grub" command:

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done"

Will it find a windows installation if there is one actually written to a MBR? :/

---

### Post by hansolo4949 on 2011-01-07
Yes, it should. I think you (might) have the cmd lines wrong when you run the recovery CD. I use bootrec/fixmbr and bootrec/fixboot.  Maybe that's the problem?

---

### Post by oldfred on 2011-01-07
You need the boot flag (active partition) on the windows partition you are repairing. Which should be sda2 as that has winload.exe.

But your windows looks backwards. Normally the large partition has /Windows/System32/winload.exe and  a small boot partition has /bootmgr /Boot/BCD  or all three are in a large partition and you do not have a separate boot partition. But you have the winload.exe in a small partition - sda2. Is that how your system was configured?

---

### Post by F1lthym0nk3y on 2011-01-09
Well originally I had vista as my main OS but then started using ubuntu and windows 7.. I installed windoze 7 onto a 40gb partition not knowing you couldnt choose partitions instead of just disks in my BIOS..

Ive now used both vista and windows 7 rescue disks and entered the command line codes with no luck, grub2 is now installed onto all 3 drives..

Where to from here? :confused:

---

### Post by oldfred on 2011-01-09
If you have tried repairing windows in both sda1 & sda2 and neither boot I think you may have to reinstall windows. Do you have all your data backed up. Does Ubuntu see those partitions and let you browse them. Do either have the full windows install structure /windows/system and /windows/system32 etc.

If you have to reinstall windows let it set up everything and boot sda. Then in BIOS set your Ubuntu drive as the boot drive and run sudo update-grub to find windows.

---

### Post by F1lthym0nk3y on 2011-01-10
> **oldfred said:**
> If you have tried repairing windows in both sda1 & sda2 and neither boot I think you may have to reinstall windows. Do you have all your data backed up. Does Ubuntu see those partitions and let you browse them. Do either have the full windows install structure /windows/system and /windows/system32 etc.

If you have to reinstall windows let it set up everything and boot sda. Then in BIOS set your Ubuntu drive as the boot drive and run sudo update-grub to find windows.

I think ill try one more time, but when I run "bootrec /fixboot" I still get "Element not found", I once did it, and received a BOOTMNGR is missing message, so I really hope I dont have to reinstall windows, Ive put a lot of work into getting that the way I wanted and only want to do that as a last resort.

I can browse and mount all the drives under ubuntu, and yes the windows install does have the correct structure e.g. /windows/system32..

---

### Post by oldfred on 2011-01-10
The fixboot is to repair the boot sector which also has to do with the partition starts and ends. Have you run chkdsk on your windows partitions? Then try fixboot again.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by F1lthym0nk3y on 2011-01-11
> **oldfred said:**
> The fixboot is to repair the boot sector which also has to do with the partition starts and ends. Have you run chkdsk on your windows partitions? Then try fixboot again.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Ive ran the chkdsk now with no problems, I can run the fixmbr command with no problems. When I run the Fixboot command I still receive a Element not found message, ScanOs returns saying that its found my windows 7 installation on the F: partition but when I run /rebuildBCD it says

"Successfully scanned windows installations.
Total idetidied windows instllations:1
[1] F:\Windows
Add installation to boot list Yes/No/All:Y
Element not found"

So when I choose yes it comes up with a element not found message, argggggh! :confused:

I can get a BOOTMNGR is missing message on the disk on which windows is installed?

I cant boot into any OS now two of my drives will return a "select proper boot device" message upon booting, and my other drive says BOOTMNGR is missing, this is on the drive windows is installed..

---

### Post by oldfred on 2011-01-11
I recommend that you have the boot loader for a system in the MBR of the same drive as the system is installed. When you repaired windows, it overwrote the grub in sda, which is ok as you have windows in sda but Ubuntu in sdc. 

So install grub2 to sdc, and in BIOS set sdc as the boot drive. Then you can still try fixing windows in sda without changing the boot from sdc.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdc6 and want grub2 in drive sdc's MBR:
#Find linux partition, change sdc6 if not correct:
sudo fdisk -l
#confirm that linux is sdc6
sudo mount /dev/sdc6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc
# After rebooting into working system
sudo update-grub

---

### Post by F1lthym0nk3y on 2011-01-12
> **oldfred said:**
> I recommend that you have the boot loader for a system in the MBR of the same drive as the system is installed. When you repaired windows, it overwrote the grub in sda, which is ok as you have windows in sda but Ubuntu in sdc. 

So install grub2 to sdc, and in BIOS set sdc as the boot drive. Then you can still try fixing windows in sda without changing the boot from sdc.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdc6 and want grub2 in drive sdc's MBR:
#Find linux partition, change sdc6 if not correct:
sudo fdisk -l
#confirm that linux is sdc6
sudo mount /dev/sdc6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc
# After rebooting into working system
sudo update-grub

Everythings okay, except sudo updategrub2 doesnt find my windows installation..

What if I installed vista to another disk, that would probably allow me to boot into windows 7? Or is it possible to just copy and paste my windows partition to another drive... I think the reason its not finding the windows 7 partition is because its not located at the front part of the disk :(

Ive installed the testdisk utility program, Ive found that my windows 7 partition doesn't start at block 0.. but there is an option to change sector geometry, is there a way to swap the windows 7 partition to block 0?

---

### Post by Quackers on 2011-01-12
duplicate post

---

### Post by Quackers on 2011-01-12
Can you please re-run the boot script and post the new results?
Also, the command is ```
sudo update-grub
```

---

### Post by Quackers on 2011-01-12
duplicate

---

### Post by Quackers on 2011-01-12
just another duplicate - this is fun!

---

### Post by oldfred on 2011-01-12
Windows will work from any primary NTFS partition with the boot flag. It does not have to be first, it just usually is as most computers come with windows. Some even have the vendor partition as sda1 and windows as sda2. Win7's standard install is now a boot/recovery partition that is hidden (usually sda1 but not always) and then the main install.

---

### Post by F1lthym0nk3y on 2011-01-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,827,872,247 2,827,870,200   7 HPFS/NTFS
/dev/sda2       2,827,872,256 2,930,272,255   102,400,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,922,801,663 1,922,799,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   890,882,047   890,880,000   7 HPFS/NTFS
/dev/sdc2         890,884,094   976,771,071    85,886,978   5 Extended
/dev/sdc5         890,884,096   894,787,583     3,903,488  82 Linux swap / Solaris
/dev/sdc6         894,789,632   976,771,071    81,981,440  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    31,326,207    31,326,145   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DA9C94729C944AC1                       ntfs       Downloads 2010                
/dev/sda2        3A0897110896CB71                       ntfs       Windows 7                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BCEE1DEBEE1D9EA8                       ntfs       Arch Linux                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7B75476C23DA0CEB                       ntfs       Downloads 2011                
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        feb07c3b-c405-4fd5-b1c6-3debc3183e92   swap                                     
/dev/sdc6        105b93d4-e13a-483d-a5dd-0cc01da32180   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4CD4-3323                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/UDF Volume        udf        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdc1        /media/Downloads 2011    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/Arch Linux        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro  quiet  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro single  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=feb07c3b-c405-4fd5-b1c6-3debc3183e92 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


 495.5GB: boot/grub/core.img
 462.9GB: boot/grub/grub.cfg
 493.1GB: boot/initrd.img-2.6.35-24-generic-pae
 496.0GB: boot/vmlinuz-2.6.35-24-generic-pae
 493.1GB: initrd.img
 496.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  22 23 bc 7e bc 3f dc 6b  bd 07 79 09 5d bc d0 85  |"#.~.?.k..y.]...|
00000010  7c ab 4c a7 da 01 be 4e  8a 8d db f1 3c bc 7c 83  ||.L....N....<.|.|
00000020  83 3c 8c b3 44 5a c9 35  a7 e2 5e c2 be 2f 30 a1  |.<..DZ.5..^../0.|
00000030  3b c8 2f e6 6f 1f 83 fe  92 30 6f 3c d5 01 8f a5  |;./.o....0o<....|
00000040  76 81 1b 79 c3 6f 16 17  e2 d0 0b 75 d1 81 d7 69  |v..y.o.....u...i|
00000050  7f 4c f2 77 c2 29 e9 6b  92 a4 7b cb 4b a0 7b eb  |.L.w.).k..{.K.{.|
00000060  e3 39 d4 a1 c4 16 cb 18  0b 7c c4 97 a2 0e e0 e7  |.9.......|......|
00000070  c9 57 7e 23 e8 19 39 20  a1 79 88 6e 55 59 18 76  |.W~#..9 .y.nUY.v|
00000080  24 bb 68 b3 1b 7e 5e a7  68 a3 0b 7e 84 b2 36 35  |$.h..~^.h..~..65|
00000090  8a 7d 1f 69 57 07 20 a7  7c bb 63 02 f2 d9 13 3b  |.}.iW. .|.c....;|
000000a0  7b 1a eb a5 64 03 22 c8  bf ab 54 f4 3c e8 f0 bd  |{...d."...T.<...|
000000b0  ab b2 e0 00 89 8b 53 e1  81 08 e4 eb ad c0 e6 22  |......S........"|
000000c0  e0 fb ab 7b 59 a3 80 fb  41 dc 10 06 bc 6b ec 0f  |...{Y...A....k..|
000000d0  3f 84 1f 75 2f 9e 4a 03  1e 98 8f 9e 13 02 be ba  |?..u/.J.........|
000000e0  48 55 15 f4 99 36 46 f4  3f a1 97 45 58 d0 8f 79  |HU...6F.?..EX..y|
000000f0  63 6a 9d 08 cf 67 4f 6f  be 8c d1 fa 5a 43 0b e6  |cj...gOo....ZC..|
00000100  6b 89 e7 5a 10 b7 1f cb  2d f5 a0 9e b4 9f e5 e1  |k..Z....-.......|
00000110  3d e9 ec f7 f2 bd f0 af  83 b6 e0 ab 90 db 22 bf  |=.............".|
00000120  f7 f5 2f b4 7a 89 4a d7  20 46 9d ee 03 9f ab 12  |../.z.J. F......|
00000130  74 ba 7e fb 41 3e ed 67  fb c9 95 59 f0 b9 6c 5f  |t.~.A>.g...Y..l_|
00000140  95 1e 7a 83 61 4e 9c 38  d8 1a 50 84 5e 6b 25 fe  |..z.aN.8..P.^k%.|
00000150  f9 94 f4 52 e0 50 64 1b  ea 52 ac 3e 89 71 2f c7  |...R.Pd..R.>.q/.|
00000160  da 60 8f 74 f6 36 05 f8  83 dd 58 45 fb aa 52 31  |.`.t.6....XE..R1|
00000170  4d 1d f4 d3 be d3 2c 8f  f6 07 94 39 67 a0 f7 34  |M.....,....9g..4|
00000180  1a 96 0f bd 58 14 32 6d  21 78 97 a4 82 88 b3 0b  |....X.2m!x......|
00000190  c4 8f 1b 86 8d b8 6f 1f  36 a1 9e 22 71 b0 86 53  |......o.6.."q..S|
000001a0  f0 9b 79 ec e0 69 e0 f9  aa 8f eb a3 fd 12 9a 24  |..y..i.........$|
000001b0  5d 77 3c c9 19 e0 7f bf  c6 3e ab 07 fd 6a 00 fe  |]w<......>...j..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 14 93  3b 00 ee f4 e2 04 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Why is the sudo update-grub / sudo update-grub2 command not picking up the windows 7 installation :(?

---

### Post by Quackers on 2011-01-12
It would seem that the reason is sda is not mounting at all.

---

### Post by F1lthym0nk3y on 2011-01-12
> **Quackers said:**
> It would seem that the reason is sda is not mounting at all.

sda does mount, I am able to mount both the Downloads 2010 partition along with the windows 7 partition on it  within ubuntu.

---

### Post by Quackers on 2011-01-12
Hmm, but not in the boot script. Maybe oldfred will understand what's happening _ I don't :-(

---

### Post by oldfred on 2011-01-12
I would try removeing all the spaces in your labels. Either just remove space or replace it with underscore. You can use gparted, or system, administration, disk utility, click on drive, then partition, then edit label. Sometime I cannot get it to open window to change, not sure why, But gparted will work from liveCD. It may have to do with mounted partitions.

example:
Downloads 2010
Downloads2010
or 
Downloads_2010

These also have spaces:
Windows 7 , Arch Linux, Downloads 2011

---

### Post by F1lthym0nk3y on 2011-01-12
Many thanks anyway Quackers, any help is appreciated, this is driving me mad! I need to get into my windows install asap really so I can use Visual studio for work..


> **oldfred said:**
> I would try removeing all the spaces in your labels. Either just remove space or replace it with underscore. You can use gparted, or system, administration, disk utility, click on drive, then partition, then edit label. Sometime I cannot get it to open window to change, not sure why, But gparted will work from liveCD. It may have to do with mounted partitions.

example:
Downloads 2010
Downloads2010
or 
Downloads_2010

These also have spaces:
Windows 7 , Arch Linux, Downloads 2011

Right, Ive read what you suggested and whilst I was in gparted I saw that the Downloads 2010 partition was selected as the bootable/boot flagged partition on the disk so Ive changed that now so the Windows 7 partition is bootable/boot flagged. Ive also changed the names of each drive/partition so there are no space, at this stage Im really ready to try anything. I re ran the update grub command, but it is still not turning up :( argggh

---

### Post by oldfred on 2011-01-12
Did you put boot flag on the windows boot partition, which I thought was the boot partition. Boot flag will not help grub but is required for windows to repair that partition.

If you rerun script does it now show sda1 & sda2?

Have you tried running the windows repairs on both sda1 & sda2?

---

### Post by F1lthym0nk3y on 2011-01-13
> **oldfred said:**
> Did you put boot flag on the windows boot partition, which I thought was the boot partition. Boot flag will not help grub but is required for windows to repair that partition.

If you rerun script does it now show sda1 & sda2?

Have you tried running the windows repairs on both sda1 & sda2?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 2,827,872,247 2,827,870,200   7 HPFS/NTFS
/dev/sda2    *  2,827,872,256 2,930,272,255   102,400,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,922,801,663 1,922,799,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   890,882,047   890,880,000   7 HPFS/NTFS
/dev/sdc2         890,884,094   976,771,071    85,886,978   5 Extended
/dev/sdc5         890,884,096   894,787,583     3,903,488  82 Linux swap / Solaris
/dev/sdc6         894,789,632   976,771,071    81,981,440  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DA9C94729C944AC1                       ntfs       Downloads2010                 
/dev/sda2        3A0897110896CB71                       ntfs       Windows7                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BCEE1DEBEE1D9EA8                       ntfs       ArchLinux                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7B75476C23DA0CEB                       ntfs       Downloads2011                 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        feb07c3b-c405-4fd5-b1c6-3debc3183e92   swap                                     
/dev/sdc6        105b93d4-e13a-483d-a5dd-0cc01da32180   ext4                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1        /media/ArchLinux         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Downloads2011     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 105b93d4-e13a-483d-a5dd-0cc01da32180
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=105b93d4-e13a-483d-a5dd-0cc01da32180 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=feb07c3b-c405-4fd5-b1c6-3debc3183e92 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


 495.5GB: boot/grub/core.img
 462.9GB: boot/grub/grub.cfg
 493.1GB: boot/initrd.img-2.6.35-24-generic-pae
 496.0GB: boot/vmlinuz-2.6.35-24-generic-pae
 493.1GB: initrd.img
 496.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  22 23 bc 7e bc 3f dc 6b  bd 07 79 09 5d bc d0 85  |"#.~.?.k..y.]...|
00000010  7c ab 4c a7 da 01 be 4e  8a 8d db f1 3c bc 7c 83  ||.L....N....<.|.|
00000020  83 3c 8c b3 44 5a c9 35  a7 e2 5e c2 be 2f 30 a1  |.<..DZ.5..^../0.|
00000030  3b c8 2f e6 6f 1f 83 fe  92 30 6f 3c d5 01 8f a5  |;./.o....0o<....|
00000040  76 81 1b 79 c3 6f 16 17  e2 d0 0b 75 d1 81 d7 69  |v..y.o.....u...i|
00000050  7f 4c f2 77 c2 29 e9 6b  92 a4 7b cb 4b a0 7b eb  |.L.w.).k..{.K.{.|
00000060  e3 39 d4 a1 c4 16 cb 18  0b 7c c4 97 a2 0e e0 e7  |.9.......|......|
00000070  c9 57 7e 23 e8 19 39 20  a1 79 88 6e 55 59 18 76  |.W~#..9 .y.nUY.v|
00000080  24 bb 68 b3 1b 7e 5e a7  68 a3 0b 7e 84 b2 36 35  |$.h..~^.h..~..65|
00000090  8a 7d 1f 69 57 07 20 a7  7c bb 63 02 f2 d9 13 3b  |.}.iW. .|.c....;|
000000a0  7b 1a eb a5 64 03 22 c8  bf ab 54 f4 3c e8 f0 bd  |{...d."...T.<...|
000000b0  ab b2 e0 00 89 8b 53 e1  81 08 e4 eb ad c0 e6 22  |......S........"|
000000c0  e0 fb ab 7b 59 a3 80 fb  41 dc 10 06 bc 6b ec 0f  |...{Y...A....k..|
000000d0  3f 84 1f 75 2f 9e 4a 03  1e 98 8f 9e 13 02 be ba  |?..u/.J.........|
000000e0  48 55 15 f4 99 36 46 f4  3f a1 97 45 58 d0 8f 79  |HU...6F.?..EX..y|
000000f0  63 6a 9d 08 cf 67 4f 6f  be 8c d1 fa 5a 43 0b e6  |cj...gOo....ZC..|
00000100  6b 89 e7 5a 10 b7 1f cb  2d f5 a0 9e b4 9f e5 e1  |k..Z....-.......|
00000110  3d e9 ec f7 f2 bd f0 af  83 b6 e0 ab 90 db 22 bf  |=.............".|
00000120  f7 f5 2f b4 7a 89 4a d7  20 46 9d ee 03 9f ab 12  |../.z.J. F......|
00000130  74 ba 7e fb 41 3e ed 67  fb c9 95 59 f0 b9 6c 5f  |t.~.A>.g...Y..l_|
00000140  95 1e 7a 83 61 4e 9c 38  d8 1a 50 84 5e 6b 25 fe  |..z.aN.8..P.^k%.|
00000150  f9 94 f4 52 e0 50 64 1b  ea 52 ac 3e 89 71 2f c7  |...R.Pd..R.>.q/.|
00000160  da 60 8f 74 f6 36 05 f8  83 dd 58 45 fb aa 52 31  |.`.t.6....XE..R1|
00000170  4d 1d f4 d3 be d3 2c 8f  f6 07 94 39 67 a0 f7 34  |M.....,....9g..4|
00000180  1a 96 0f bd 58 14 32 6d  21 78 97 a4 82 88 b3 0b  |....X.2m!x......|
00000190  c4 8f 1b 86 8d b8 6f 1f  36 a1 9e 22 71 b0 86 53  |......o.6.."q..S|
000001a0  f0 9b 79 ec e0 69 e0 f9  aa 8f eb a3 fd 12 9a 24  |..y..i.........$|
000001b0  5d 77 3c c9 19 e0 7f bf  c6 3e ab 07 fd 6a 00 fe  |]w<......>...j..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 14 93  3b 00 ee f4 e2 04 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```


Yes Ive used the windows 7 repair disk, when it comes up with the list of operating systems it says Windows 7 (recovered). Then when I try get into the command prompt it says the installation disk you are using is not compatible with the version of windows you are trying to repair.

---

### Post by oldfred on 2011-01-13
Some progress, boot script is now able to parse the sda1 & sda2 partitions. but they still look reversed.

Normally windows has a sda1 100MB boot/recovery partition with:
/bootmgr /Boot/BCD

then it has the large main partition in sda2 with:
/Windows/System32/winload.exe

Or all three boot files are in one partition. But your sda2 is tiny and sda1 is the large partition.

From Ubuntu does the file structure look correct for a full install in sda2? If not that may be why windows will not repair it.

---

### Post by F1lthym0nk3y on 2011-01-13
I installed windows 7 after vista was pre installed and choose to use only 40 GB for that partition. Everything in that partition is structured correctly. I was originally using that drive to store games/music etc but shrunk it down in the disk management utility so I could install windows 7 on a separate partition.

---

### Post by Quackers on 2011-01-13
oldfred is right (as usual :-) ) when he says that the Windows partitions look swapped around.
You now have the boot flag on sda2 but the first Windows boot file is in sda1. The second Windows boot file (bootmgr) is missing!
I would leave the boot flag where it is and run bootrec.exe /fixmbr from the command prompt on the Windows repair disc - or move the boot flag to sda1 and then run bootrec.exe /fixmbr.
That should hopefully get Windows booting. 
See what oldfred thinks.

---

### Post by oldfred on 2011-01-13
Thanks for the confidence Quackers, but oldfred is not always right, that is why he likes others to review things.:)

If you have both Vista and 7, then that is why you may be getting an error on wrong version. Script may show both as win7 since you installed that last and windows does some combining. (not sure of that)

You need to set boot flag on Vista partition and run repairs from a windows Vista repair CD. And set the boot flag on the Win7 partition and run repairs from a win7 repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by F1lthym0nk3y on 2011-01-14
> **oldfred said:**
> Thanks for the confidence Quackers, but oldfred is not always right, that is why he likes others to review things.:)
 
If you have both Vista and 7, then that is why you may be getting an error on wrong version. Script may show both as win7 since you installed that last and windows does some combining. (not sure of that)
 
You need to set boot flag on Vista partition and run repairs from a windows Vista repair CD. And set the boot flag on the Win7 partition and run repairs from a win7 repair CD.
 
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
No, you misunderstood me, I the reason why windows isnt booting (I think) is because I had vista installed, and choose that as the the boot partition, then when I deleted that because I had no use for it, it wouldnt boot into seven, because the bootmnger was obviously installed onto the vista partition.

I cant use the windows 7 repair/install disk either becase it comes up with a "Yes Ive used the windows 7 repair disk, when it comes up with the list of operating systems it says Windows 7 (recovered). Then when I try get into the command prompt it says the installation disk you are using is not compatible with the version of windows you are trying to repair. "

Before when I had the boot flag on sda1 and I tried to boot from it it would says "please choose a proper boot device", but now its on sda2 it says BOOTMNGR is missing..

---

### Post by Quackers on 2011-01-14
Are you using a 32 bit Win 7 disk for a 64 bit installation, by any chance? Or vice versa.

---

### Post by F1lthym0nk3y on 2011-01-14
> **Quackers said:**
> Are you using a 32 bit Win 7 disk for a 64 bit installation, by any chance? Or vice versa.
 

Ahh thats the ticket, didnt think it would make a difference, but ill try that, thanks!

---

### Post by Quackers on 2011-01-14
Lol, somebody else did the same thing within the last day or two. It happens :-)

---

### Post by Eddie R. Runner on 2011-01-14
> **gadolinio said:**
> +1. It might be useful.

gadolinio i am agree with you. it is useful.

---

### Post by F1lthym0nk3y on 2011-01-14
> **Eddie R. Runner said:**
> gadolinio i am agree with you. it is useful.
 
 
Would be useful but my startup manager only has two tabs for some reason and hardly any of the features mentioned in this article.

---

### Post by F1lthym0nk3y on 2011-01-14
Didn't do much unfortunately, still get a "element not found" message after entering bootrec.exe /fixboot and /rebuildbcd + y. Then had to reinstall grub again from a livecd for it to boot

---

### Post by oldfred on 2011-01-14
Grub is in sdc and windows should not even be anywhere near that??

We are not a windows repair. You do have windows on a separte drive. If necessary you might try unplugging all the other drives.

Google found these suggestions:
[http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/7791044e-db7f-4144-a96c-945299811f58](http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/7791044e-db7f-4144-a96c-945299811f58)

---

### Post by Quackers on 2011-01-14
In my experience, bootrec.exe /fixmbr seems to have the best effect on missing boot files.

---

### Post by F1lthym0nk3y on 2011-01-14
> **oldfred said:**
> Grub is in sdc and windows should not even be anywhere near that??

We are not a windows repair. You do have windows on a separte drive. If necessary you might try unplugging all the other drives.

Google found these suggestions:
[http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/7791044e-db7f-4144-a96c-945299811f58](http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/7791044e-db7f-4144-a96c-945299811f58)


Exactly, I know, many thanks for the link, I'm going to try some of their suggestions and report back!

---

### Post by F1lthym0nk3y on 2011-01-15
Right so Ive tried some of the suggestions on the provided link such as ```
Diskpart

LIST DISK

SELECT DISK (followed by the number of the disk . most likely 0)

LIST PARTITION

SELECT PARTITION (followed by your partition number. most likely 0)

ACTIVE

EXIT
```

Also tried the commands over at [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

But only got so far when it said the system device could not be found

So now I'm left with 3 drives that boot into a grub recovery console, can only access the PC through the windows 7 CD or a live cd...  :(:(:(

---

### Post by Quackers on 2011-01-15
Disks start from 0, partitions start from 1. There is no partition called 0. All this does is move the boot flag.

---

### Post by F1lthym0nk3y on 2011-01-15
Okay after many hours of torture, I have finally been able to boot into windows, and am typing this within it, now back to my original question.

As it stands I can boot into windows, but just get the grub recovery console when I select the drive its installed on, How do I get it so I can choose between OS's upon boot, and how do I fix the grub problems with not being able to boot into ubuntu..

Many thanks guys

---

### Post by F1lthym0nk3y on 2011-01-16
Bump

---

### Post by oldfred on 2011-01-16
Reinstall grub2 to the same drive Ubuntu is installed on and set BIOS to boot that drive.  After you boot Ubuntu if you run this it will find you windows install.

sudo update-grub

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

