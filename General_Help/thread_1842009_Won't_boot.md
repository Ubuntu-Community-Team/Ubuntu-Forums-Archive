---
title: "Won't boot"
date: 2011-09-10
forum: General Help
---

### Post by kemorc on 2011-09-10
I've had a problem for quite some time now on my tower.  Ever since the latest updates, my computer will not boot.  All I get is a flashing underscore or the purple screen.  I can leave it there for as long as I please, and there will not be any progress in loading/booting.

Assuming something was wrong with the update, I downloaded the latest version of 11.04 and tried to start fresh.

System:
ASUS M3A79T Deluxe
AMD Phenom II x6 1090t
4 1GB OCZ DDR2 800 sticks
NVidia GTX 275
Ubuntu 11.04 x86

System works perfectly fine on my windows 7 installation, which is on a separate hard drive.  I know the hard drive is good, because before I completely wiped it, it would allow me to successfully boot older versions of 11.04.

Oddly enough, same exact install works fine on my Thinkpad T61P.

---

### Post by marin123 on 2011-09-10
Can you boot into single user mode?

Choose kernel in GRUB, press e, delete words quiet and splash and put single in their place, ctrl+x and you should be booting :)

There you can fix your problems. Did the update include Xorg updates? If it did, try reinstalling proprietary video drivers (if you have them).

Good luck :)

---

### Post by kemorc on 2011-09-10
replacing quiet splash, with single, did not fix my problem.

Going through the huge faq posted here, does not help or fix my problem.

These are the options I have:

Ubuntu, with Linux 2.6.38-11-generic-pae
Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)
Memory test (memtestx86+)
Memory test (memtestx86+, serial console 115200)
Windows 7 (loader)

---

### Post by Rubi1200 on 2011-09-10
I recommend using a LiveCD/USB to boot the computer and then post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by kemorc on 2011-09-10
@Rubi

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 513 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdd: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......{..:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 30792 of /dev/sdd for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   283,756,543   283,754,496  83 Linux
/dev/sda2         283,758,590   312,576,704    28,818,115   5 Extended
/dev/sda5         300,528,018   312,576,704    12,048,687  82 Linux swap / Solaris
/dev/sda6         292,143,104   300,527,615     8,384,512  82 Linux swap / Solaris
/dev/sda7         283,758,592   292,141,055     8,382,464  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   390,719,487   390,717,440   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            255     3,932,159     3,931,905   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        55af0156-a381-42b8-b34b-fb9427c4b7e6   ext4       
/dev/sda5        05cff0e7-95e1-49f9-867c-99d469335700   swap       
/dev/sda6        23935bf4-2e52-4ba6-87ec-47714fa6dabd   swap       
/dev/sda7        5085d64a-4939-4e1f-97f8-5f3264a87ca9   swap       
/dev/sdb1        E25AAD795AAD4ADD                       ntfs       New Volume
/dev/sdc1        BB68-0E2B                              vfat       PENDRIVE
/dev/sdd         207C-2B6A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd         /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=55af0156-a381-42b8-b34b-fb9427c4b7e6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=55af0156-a381-42b8-b34b-fb9427c4b7e6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 55af0156-a381-42b8-b34b-fb9427c4b7e6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root E25AAD795AAD4ADD
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=55af0156-a381-42b8-b34b-fb9427c4b7e6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5085d64a-4939-4e1f-97f8-5f3264a87ca9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  58.130798340 = 62.417469440   boot/grub/core.img                             1
 118.133014679 = 126.844358656  boot/grub/grub.cfg                             1
  73.930664062 = 79.382446080   boot/initrd.img-2.6.38-11-generic-pae          2
  72.685001373 = 78.044925952   boot/vmlinuz-2.6.38-11-generic-pae             1
  73.930664062 = 79.382446080   initrd.img                                     2
  72.685001373 = 78.044925952   vmlinuz                                        1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected












It finally booted!  Nothing has been changed, but after trying at least 30 times, it finally booted.  I am currently on it now... afraid to let it shut down because I'm confident it won't boot again.

Edit 2 - Tried installing latest NVIDIA drivers manually, and it will NOT allow me to.  I've done everything as per directions, and of course, there has to be yet even more problems.  I don't know what more to do, I've never had such a persisting problem with Ubuntu before.

Edit 3 - Installed proprietary Nvidia driver that Ubuntu pointed me to.  Will no longer boot.  Back to square nothing.

---

### Post by kemorc on 2011-09-11
What else should I try here?  I have a computer that will not work.  Is Ubuntu the problem? Is a driver the problem? 

I started fresh, again.  This time without the Nvidia driver, same problem!  However, I managed to get it to boot once again... of which I am currently typing with said boot session.

---

### Post by Rubi1200 on 2011-09-11
Is this only a problem with 11.04 or also older versions?

The computer specifications look good to me and, in most cases, installing the drivers for your video card should not cause issues.

---

### Post by kemorc on 2011-09-11
This is strictly 11.04.  There was another version I used to have on here, 9.04 I think... the only one that supported my wireless usb stick.  Then for several updates afterwards, it was disabled, so I usually reverted back to 9.04.

I just tried Fedora 15 32 bit, same problem.  Looks like whatever is being changed for linux, is bad for my "newer" computer.

EDIT - I am currently going to try Linux Mint 11 and hope for the best.

---

### Post by kemorc on 2011-09-11
Fedora does not work, Ubuntu does not work, Linux Mint does not work.

I am currently re-downloading 9.04, hopefully I can get something to work.

Edit - I give up, absolutely no variant of Linux will boot on this computer.  No live cd, no usb stick, nothing.  

Not sure what is wrong, but absolutely nothing (except windows) will boot...

---

### Post by kemorc on 2011-09-25
Bingo!  The problem is with ANY 32 bit installation.  32 bit will NOT work on this computer.  Why? I don't know, but I only assume it is the hexacore processor, because I've never had a problem before with my old tricore.

---

