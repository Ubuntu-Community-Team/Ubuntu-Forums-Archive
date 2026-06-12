---
title: "GRUB : Booting Windows Vista from Ubuntu 11.04"
date: 2011-06-08
forum: General Help
---

### Post by nikhilt on 2011-06-08
Hi Grub gurus,

I have to test Ubuntu 11.04 across multiple systems in my company and enable dual booting with Windows Vista PE x86. On selecting the Windows GRUB entry, the Grub menu just loads again without loading Vista and thus enters into an infinite loop.

Fdisk -l gives me:

```
/dev/sda1 : W95 FAT32 (LBA) {Note: Vista PE}
/dev/sda2 : Extended
/dev/sda5 : Linux
/dev/sda6 : Linux swap / Solaris
```

When I did a update-grub, the output shows that it detected and added a Windows Vista OS. Also, I went ahead and added "MyWindows" as an option as well which has (worked for all other versions)

```
root=(hd0,1)
chainloader +1
```

Selecting either of the GRUB Windows entries just loads GRUB menu again. I'm very confused and this deployment is critical for my company. Please help.

thanks
Nikhil

---

### Post by drs305 on 2011-06-08
> **nikhilt said:**
> 
Selecting either of the GRUB Windows entries just loads GRUB menu again. I'm very confused and this deployment is critical for my company. Please help.


I'm not a Windows expert and I'm not sure how often those who are frequent this thread any longer, but we can give it a shot. One thing is to make sure the Grub chainload points to the original boot folder of Windows (which may then transfer control to another Windows partition - if you have one).

Please click on the "BIS" link in my signature line and download/extract and run the boot info script. Post the contents of RESULTS.txt and we can take a look at your Grub files. 

If I can't see anything I can break these posts off on a new thread so others are more likely to see it and give you prompt help.

---

### Post by nikhilt on 2011-06-08
Hi drs305,

Please have a look at the results file:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 394532344 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /grldr /ntldr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04 Desktop 32bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    499,124,224   625,139,711   126,015,488   c W95 FAT32 (LBA)
/dev/sda2               2,046   499,124,223   499,122,178   5 Extended
/dev/sda5               2,048   490,735,615   490,733,568  83 Linux
/dev/sda6         490,737,664   499,124,223     8,386,560  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8CDD-2A24                              vfat       TACCBOOT
/dev/sda5        67b09dde-8620-42d2-9afb-a68c6eb6604b   ext4       
/dev/sda6        2e4866fe-b307-450c-b4e1-830028cf2d79   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /cdrv                    vfat       (rw,iocharset=utf8,umask=000)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
default 0
timeout 1
fallback 1
--------------------------------------------------------------------------------

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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=67b09dde-8620-42d2-9afb-a68c6eb6604b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=67b09dde-8620-42d2-9afb-a68c6eb6604b ro single 
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
	search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 67b09dde-8620-42d2-9afb-a68c6eb6604b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8cdd-2a24
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows_TACCBOOT"{
root=(hd0,1)
chainloader +1
}
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
UUID=67b09dde-8620-42d2-9afb-a68c6eb6604b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2e4866fe-b307-450c-b4e1-830028cf2d79 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 188.127708435 = 202.000588800  boot/grub/core.img                             1
 118.143642426 = 126.855770112  boot/grub/grub.cfg                             1
   1.505092621 = 1.616080896    boot/initrd.img-2.6.38-8-generic               2
   0.204406738 = 0.219480064    boot/vmlinuz-2.6.38-8-generic                  1
   1.505092621 = 1.616080896    initrd.img                                     2
   0.204406738 = 0.219480064    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by drs305 on 2011-06-08
You don't have the normal files for booting Windows in sda1. /grldr I believe it Grub4Dos. I don't have much experience with this type of issue, so I'm going to fork this to a new thread with an applicable title.

From what I can tell, when you are chainloading it is taking you to the Windows partition, but you have installed Grub into the PBR. I think you are going to have to repair the Windows boot files/PBR. Here is a link that might help:

[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by nikhilt on 2011-06-08
> You don't have the normal files for booting Windows in sda1. /grldr I believe it Grub4Dos. I don't have much experience with this type of issue, so I'm going to fork this to a new thread with an applicable title.


Ignore that grub4dos grldr. That is from some other test I was doing. bootmgr is present. Can you rename the thread "GRUB : Booting Windows Vista from Ubuntu 11.04 "?

Nikhil

---

### Post by oldfred on 2011-06-09
You have one boot file from XP and one from Vista. Normal files are:
XP:
/boot.ini /ntldr /NTDETECT.COM
Vista or 7:
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

And you have to run the fixboot (XP) or BootRec.exe /FixBoot (Vista/7).

If you have only updated the windows boot sector once, there is a backup boot sector that you can recover with testdisk.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

