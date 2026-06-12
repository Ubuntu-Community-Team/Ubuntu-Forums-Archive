---
title: "Adding Windows to Grub"
date: 2011-05-11
forum: General Help
---

### Post by bikerbub on 2011-05-11
Hello Ubuntu-ians. 

I have been running 11.04 for what i'd say is about a month now. In the very beginning, i shredded through a few installs, because i couldn't get windows and 10.04 to play nice. With the new update, and some renewed motivation (Portal 2), i'd like to try to get both up and running again.

First, the details. I installed both OS's in a jumbled order, realized that i basically effed everything, and wiped both drives clean. I then installed windows, then Ubuntu 10.04. I think my main point of error was the way i set up the boot sectors on my final Ubuntu install, but i can't remember how i did it. all i know is that linux is sda, and windows is sdb. what is strange, however, is when i do an Fdisk of my mounted drives, i see 3 partitions under sda1, labeled sda1, sda2, and sda5

On to the previously tried methods: 
I've tried a simple mount of the windows drive, followed by a "sudo update-grub." all this gets me is a list consisting of 11.01, 11.01 backup, 10.04, 10.04 backup, and memtest86+. not even a hint of windows.

I've tried "sudo grub-install" on both sda and sdb, but still no dice. 

That's about all i've tried. I've searched for the past week with limited results, and i'd really like to avoid reinstalling ubuntu if at all possible. Any other information, like an fdisk results list or anything like that can be provided if need be. 

Thanks in advance,
Josh

---

### Post by oldfred on 2011-05-11
Welcome to the forum.

This will tell us where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by bikerbub on 2011-05-11
Thanks for responding.
Here's the Results.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for cah.
 => No boot loader? is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,417,142,271 1,417,140,224  83 Linux
/dev/sda2       1,417,144,318 1,465,147,391    48,003,074   5 Extended
/dev/sda5       1,417,144,320 1,465,147,391    48,003,072  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16022241280 bytes
82 heads, 18 sectors/track, 21201 cylinders, total 31293440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,064    31,293,439    31,285,376   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e8e0d53f-6cf0-4440-a844-8904b438f314   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        258541f2-54aa-410b-8c12-13b2d0e6bd22   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D6B6A909B6A8EB67                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        2FC3-A821                              vfat       PATRIOT                       
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/D6B6A909B6A8EB67  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/PATRIOT           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e8e0d53f-6cf0-4440-a844-8904b438f314 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e8e0d53f-6cf0-4440-a844-8904b438f314 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e8e0d53f-6cf0-4440-a844-8904b438f314 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e8e0d53f-6cf0-4440-a844-8904b438f314 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e8e0d53f-6cf0-4440-a844-8904b438f314
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

=============================== sda1/etc/fstab: ===============================

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
UUID=258541f2-54aa-410b-8c12-13b2d0e6bd22 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 195.5GB: boot/grub/core.img
 476.9GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.35-28-generic
   4.3GB: boot/initrd.img-2.6.38-8-generic
    .8GB: boot/vmlinuz-2.6.35-28-generic
   4.4GB: boot/vmlinuz-2.6.38-8-generic
   4.3GB: initrd.img
   2.1GB: initrd.img.old
   4.4GB: vmlinuz
    .8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

NOTE: sdd is my flash drive, that can be basically ignored. i think. maybe that's a problem?

---

### Post by oldfred on 2011-05-11
You installed windows to sdb. but windows likes sda and you were probably in BIOS booting from sda. Windows creates a 100MB boot/recovery partition that is normally sda1 and then the main install is sda2. But since you installed to sdb, it still put the hidden 100MB boot/recovery partition on sda. When you install Ubuntu you overwrote that boot partition.

You can repair the main install as win7 works from one partition. It has the boot partition so you can encrypt the main partition and perhaps repair the main as you are booting the recovery partition.

Do you  have a win7 repair CD? Windows only repairs (installs/sees) NTFS partitions with the boot flag (active partition in windows), so you need to add the boot flag to sdb1. You can do it with gparted, click on partition and right click manage flags. 

Or from terminal:
set boot flag on for sdb1 (off on others)
```
sudo sfdisk -A1 /dev/sdb
```Before running repairs set BIOS to boot from sdb. That way windows should put its boot loader in the MBR of sdb, and leave grub in sda. It is best to have each boot loader in the same drive as the system partition, in  case the other drive fails.

I have posted instructions on repair win7 & getting repair CD in this thread and links to windows sites with further instructions:

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

If windows then boots from the MBR of sdb, change BIOS to sda and boot Ubuntu. Run this to find windows.

```
sudo update-grub
```

---

### Post by bikerbub on 2011-05-11
thank you so much for your help.

i know exactly what you're talking about now, as i've had this problem before, with windows on 2 hard drives. I didn't even think that ubuntu was overwriting that partition. 

i don't have the disk right now, but i can probably get it tomorrow. I won't set it as solved until i'm for certain and windows is booting again. 

one last question; should i disconnect the secondary drive (ubuntu drive) before repairing windows in order to prevent it from screwing up GRUB?

---

### Post by oldfred on 2011-05-12
If it is easy to disconnect that would make sure, but I have seen windows not be happy as drive 0 then being reset to drive 1. That may have been more with XP as I am not sure about win7, it may be more forgiving.

Ubuntu uses UUIDs, so moving drive around does not prevent it from booting from correct drive/partition & rerunning sudo update-grub resets everything.

---

