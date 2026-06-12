---
title: "Windows 7 partition no longer recognised"
date: 2010-04-10
forum: General Help
---

### Post by Fudgey on 2010-04-10
After having some issues with GRUB2 not showing my operating system list, I accidently screwed up my Windows 7 partition by selecting the 'Bootable' checkbox in the Palimpsest(?) Disk Utility.

After finding [this thread](http://ubuntuforums.org/showthread.php?t=1358670) (and the links provided in responses), the problem appears to be the same but, unlike the user in that thread, I was unable the uncheck the Bootable flag after checking it - the partition became totally unrecognised, and the Disk Usage Analyser shows only ~5gb of HDD space in use.

I have no other Windows installation on my hard drive, apart from the Recovery Partition which existed when the PC was bought. The thread I linked to suggested that the bootmgr file may be on the partition of another bootable Windows partition (although I'm not able to get to the PC in question right now, so I'm not 100% sure if the Recovery Partition was flagged as bootable or not)

What I need to know is:
(1) Is it possible to solve this problem without having to re-install Windows? I don't really have many tools (or much knowledge about all these things) at my disposal, and have no idea how to access the Recovery Partition files in order to see if the required Boot folder and bootmgr file are there. Also, in the file explorer, my Windows 7 partition is no longer visible.

(2) If this is possible, do I require internet access on the PC itself? Ever since I installed Ubuntu, it has been unable to detect proprietary drivers for my network card (whereas the demo from the USB stick I installed Ubuntu with was capable of detecting proprietary drivers)

---

### Post by oldfred on 2010-04-10
IF you can boot with a CD or the USB run this script which will document you system for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Fudgey on 2010-04-10
I think /dev/sda2 is my Recovery Partition, and /dev/sda3 is the Windows 7 partition

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847  de Dell Utility
/dev/sda2    *        225,280    18,284,543    18,059,264   7 HPFS/NTFS
/dev/sda3          18,298,035 1,145,418,434 1,127,120,400   7 HPFS/NTFS
/dev/sda4       1,145,418,435 1,250,258,624   104,840,190   5 Extended
/dev/sda5       1,145,418,498 1,250,258,624   104,840,127  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0201                              vfat       DellUtility                   
/dev/sda2        781CA8281CA7DEFE                       ntfs       RECOVERY                      
/dev/sda5        bd6888c9-b71e-4284-acf8-2030694d1c9c   ext4                                     
/dev/sdb1        3016-A0A8                              vfat       MAIN FD                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/MAIN FD           vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom1            udf        (ro,nosuid,nodev,utf8,user=james)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set bd6888c9-b71e-4284-acf8-2030694d1c9c
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bd6888c9-b71e-4284-acf8-2030694d1c9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bd6888c9-b71e-4284-acf8-2030694d1c9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bd6888c9-b71e-4284-acf8-2030694d1c9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bd6888c9-b71e-4284-acf8-2030694d1c9c ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=bd6888c9-b71e-4284-acf8-2030694d1c9c /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 589.8GB: boot/grub/core.img
 589.8GB: boot/grub/grub.cfg
 587.0GB: boot/initrd.img-2.6.31-14-generic
 587.0GB: boot/vmlinuz-2.6.31-14-generic
 587.0GB: initrd.img
 587.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4a 75 73 74 59 00 00 00  00 00 00 00 00 00 00 00  |JustY...........|
00000010  05 00 00 00 0f 00 00 00  00 00 00 00 43 45 4e 54  |............CENT|
00000020  45 52 00 00 00 00 00 00  00 00 00 00 06 00 00 00  |ER..............|
00000030  0f 00 00 00 01 00 00 00  b9 22 95 7b 00 00 00 88  |.........".{....|
00000040  00 15 c3 04 f0 15 c3 04  00 15 c3 04 00 00 00 00  |................|
00000050  4e 61 6d 65 00 00 00 00  00 00 00 00 00 00 00 00  |Name............|
00000060  04 00 00 00 0f 00 00 00  00 00 00 00 78 ce bc 04  |............x...|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 12 00 00 00  |................|
00000080  1f 00 00 00 00 00 00 00  af 22 95 7b 00 00 00 88  |.........".{....|
00000090  e0 16 c3 04 30 17 c3 04  20 18 c3 04 00 00 00 00  |....0... .......|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000d0  00 00 00 00 01 01 00 00  a5 22 95 7b 00 00 00 88  |.........".{....|
000000e0  90 16 c3 04 30 17 c3 04  90 16 c3 04 00 00 00 00  |....0...........|
000000f0  42 69 6e 64 58 00 00 00  00 00 00 00 00 00 00 00  |BindX...........|
00000100  05 00 00 00 0f 00 00 00  00 00 00 00 66 61 6c 73  |............fals|
00000110  65 00 00 00 00 00 00 00  00 00 00 00 05 00 00 00  |e...............|
00000120  0f 00 00 00 01 00 00 00  9b 22 95 7b 00 00 00 88  |.........".{....|
00000130  e0 16 c3 04 90 16 c3 04  d0 17 c3 04 00 00 00 00  |................|
00000140  43 6f 6d 70 6f 6e 65 6e  74 00 00 00 00 00 00 00  |Component.......|
00000150  09 00 00 00 0f 00 00 00  00 00 00 00 68 b7 c4 04  |............h...|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 24 00 00 00  |............$...|
00000170  2f 00 00 00 01 00 00 00  91 22 95 7b 00 00 00 88  |/........".{....|
00000180  90 16 c3 04 d0 17 c3 04  90 16 c3 04 00 00 00 00  |................|
00000190  4a 75 73 74 59 00 00 00  00 00 00 00 00 00 00 00  |JustY...........|
000001a0  05 00 00 00 0f 00 00 00  00 00 00 00 42 4f 54 54  |............BOTT|
000001b0  4f 4d 00 00 00 00 00 00  00 00 00 00 06 00 00 00  |OM..............|
000001c0  0f 00 00 00 00 00 00 00  87 22 95 7b 00 00 00 88  |.........".{....|
000001d0  80 17 c3 04 30 17 c3 04  20 18 c3 04 00 00 00 00  |....0... .......|
000001e0  4e 61 6d 65 00 00 00 00  00 00 00 00 00 00 00 00  |Name............|
000001f0  04 00 00 00 0f 00 00 00  00 00 00 00 a0 b7 c4 04  |................|
00000200



```

---

### Post by oldfred on 2010-04-10
You have several issues and I do not know if windows repair will fix them, it  may be partition issues not just install.

You have /boot/grub/core.img in you windows boot partition sda2 and maybe all the other files in /boot. You should delete these first.

Your sda3 is not shown in the script. It does not see the rest of the windows boot that has to be in the boot sector (PBR) and /Windows/System32/winload.exe that should be there. It does not see it as a NTFS partition. Can you see the partition and if the files are in the partition?

These are the standard windows instructions:
Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

IF windows does not see the sda3 partition I might try using gparted to change it to NTFS or right click and see if it can do any repairs.

---

### Post by Fudgey on 2010-04-10
Ah, thanks for the response. Unfortunately, given my general track record with computers, I won't be able to do anything tonight (or, rather, shouldn't for fear that something else breaks :P) - hopefully, when my brother comes out to help, he will heed your advice.

> You will need to boot with your Vista/Windows 7 installation disk
Well, from what I can recall, Dell never shipped an installation disc with my computer, just a recovery partition. I downloaded a recovery disc ISO from [NeoSmart](http://neosmart.net/blog/2009/windows-7-system-repair-discs/). When I booted the PC using the image, I did get a screen with the various repair options (incl. Command Prompt) - is this sufficient, or will I need a disc with the Windows install files?

---

### Post by oldfred on 2010-04-10
If you said you did not have a disk I would have suggested the site you went to for a repair only CD. That should work. Can you see your NTFS partition. Sometime Ubuntu or gparted will not mount windows partitions that need to run checkdisk to then it does not see that drive.

---

### Post by Fudgey on 2010-04-10
> **oldfred said:**
> If you said you did not have a disk I would have suggested the site you went to for a repair only CD. That should work. Can you see your NTFS partition. Sometime Ubuntu or gparted will not mount windows partitions that need to run checkdisk to then it does not see that drive.

Well, I can see what *should* be labelled as 'OS' in the Palimpsest Disk Utility, but it is now labelled as Unrecognized (or something to that effect), if that's what you mean.

As regards Gparted, I don't have that set up - I can't download it on the desktop because of a lack of internet access, and I'm not sure how to set it up on a memory stick/CD, through this laptop, so that it would work for the desktop. Perhaps I overlooked an instructions manual that came in the zip archive :P

---

### Post by oldfred on 2010-04-10
I would try running the windows chkdsk and repairs.

---

