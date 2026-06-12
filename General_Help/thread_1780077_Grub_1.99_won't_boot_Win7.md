---
title: "Grub 1.99 won't boot Win7"
date: 2011-06-11
forum: General Help
---

### Post by PCNetSpec on 2011-06-11
I've been asked for help with a (supposed) dual-boot Win7/Ubuntu 11.04 PC that won't boot Win7.

History... from what I gather...

Originally a dual boot Win7/Vista setup.
Ubuntu installed to Win7 partition using Wubi
(changed mind)... uninstalled Wubi from Win7
Removed Vista partition, and in its place...
Created an extended partition that contains 2 logical partitions, 1 ext4, and 1 linux swap.
Installed Ubuntu 11.04 to these partitions.

Result - Ubuntu boots fine, but select Win7 and the GRUB menu immediately loops back to the GRUB menu

Now the messed up GRUB bit...

First here's the boot_info_script output -


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 954302920 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   According to the info in the boot sector, sdg1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdg1 starts at sector 10163. According to the info in 
                       the boot sector, sdg1 has 0 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,116,928   836,579,327   815,462,400   7 NTFS / exFAT / HPFS
/dev/sda4         836,581,374   976,771,071   140,189,698   5 Extended
/dev/sda5         836,581,376   968,959,999   132,378,624  83 Linux
/dev/sda6         968,962,048   976,771,071     7,809,024  82 Linux swap / Solaris


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 139 MB, 139829760 bytes
255 heads, 63 sectors/track, 17 cylinders, total 273105 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1              10,163        42,229        32,067   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D9-010C                              vfat       DellUtility
/dev/sda2        228C510A8C50DA3D                       ntfs       RECOVERY
/dev/sda3        601A53461A5317FC                       ntfs       Windows 7
/dev/sda5        fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1   ext4       
/dev/sda6        e80fc741-4044-4b6a-b86b-65a93b926631   swap       
/dev/sdg1        EEF7-BB3D                              vfat       EDMINILOGON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdg1        /media/EDMINILOGON       vfat       (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
  if [ -e ${prefix}/gfxblacklist.txt ]; then
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
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1 ro   quiet splash nodmraids vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 601A53461A5317FC
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fe2215b3-4f86-4f31-a6d7-fe02c6cac8b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e80fc741-4044-4b6a-b86b-65a93b926631 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 455.047119141 = 488.603123712  boot/grub/core.img                             1
 411.202499390 = 441.525321728  boot/grub/grub.cfg                             1
 400.221897125 = 429.734989824  boot/initrd.img-2.6.38-8-generic               1
 455.045391083 = 488.601268224  boot/vmlinuz-2.6.38-8-generic                  1
 400.221897125 = 429.734989824  initrd.img                                     1
 455.045391083 = 488.601268224  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdg

00000000  45 52 02 00 00 00 a4 f6  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 24 4c 61 43  69 65 24 24 00 00 00 fe  |....$LaCie$$....|
000001c0  ff 0f 0c fe ff 0f b3 27  00 00 43 7d 00 00 00 00  |.......'..C}....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Now I can see what's happened... part of GRUB somehow got installed to sda3 (Win7 partition), and *didn't* get installed to sda's MBR, so I can see why it's looping... but I can't think of a way out... any ideas would be much appreciated ?

---

### Post by bcbc on 2011-06-11
Try this link: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This used to be a very common problem. Grub's not supposed to allow itself to install to windows' boot sectors anymore. Maybe this is a regression. Do you know how the user managed to do this?

PS after fixing the boot sector you'll have to install grub to the MBR
Actually you might want to do this before fixing the boot sector... boot Ubuntu, and run:
```
sudo grub-install /dev/sda
```

---

### Post by Rubi1200 on 2011-06-11
I am actually surprised Ubuntu can boot at all!

In any event, having anything other than the Windows files on its boot partition is likely to cause problems sooner or later.

I suggest fixing the Windows boot sector and then installing GRUB properly to the MBR of sda so as to have a true dual-boot.

To fix the Windows bootloader see the relevant section:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To reinstall GRUB from the LiveCD:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

Reboot and back in Ubuntu run this to pick up the Windows install:

```
sudo update-grub
```

Let me know how it goes and if you need any other help.

---

### Post by oldfred on 2011-06-11
It is an old fashioned chainboot. Windows boot loader is not smart and just looks for a boot flag on a primary partition. It jumps to that partition to continue to boot expecting windows code. But since grub is in the partition grub2 will load and boot. Grub2 in a partition is not recommended, but will work. But in a windows partition it breaks windows.

If you follow bcbc's instructions to install grub2's boot loader to the MBR first then you will not have to follow Rubi1200's instructions, but they will also work.

The testdisk procedure the bcbc posted usually works unless the backup boot sector is also overwritten.

---

### Post by PCNetSpec on 2011-06-11
OK, thanks guys... I'll suggest installing grub to sda, then installing/running the testdisk procedure... then move on to bootrec /fixboot and grub reinstall if necessary.

**@bcbc**
> Do you know how the user managed to do this?

The only other info I can provide that *may* be related, is that there were issues with the Ubuntu LiveCD only intermittently seeing the drive due to SATA in the DELL BIOS being set to IDE mode .. see here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

This appeared to be fixed by the nodmraid kernel boot parameter (though god knows why, there was no RAID metadata on the drive)... I probably should have got Win7 to load the AHCI driver then switched the SATA mode in the BIOS *before* installing Ubuntu, but the nodmraid seemed to take care of the issue, so I left it at that.

At first wondered if this was something Wubi had left behind in the Win7 BCD, as like bcbc, I was surprised the system was bootable at all.

If you ask me it's a weird build up of circumstances, and no doubt a little bit of human error thrown in... thanks again for the suggestions, I'm pretty sure I've got a handle on it now.

I'll let you know how we get on.

[EDIT]
Another question if you don't mind... If/when I fix the Win7 boot issue, should I get Win7 to load the AHCI driver, then switch the BIOS to RAID as suggested in the above link... what I'm really after is confirmation this won't break the Ubuntu side of things.

---

### Post by PCNetSpec on 2011-06-27
Just a quick post to say thanks to all that helped, and to let you know that reinstalling GRUB to the MBR (sda), and using testdisk sorted the problem... GRUB now boots both OS's properly.

Again, thanks for the help.

---

