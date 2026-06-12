---
title: "Linux wont start"
date: 2011-07-04
forum: General Help
---

### Post by Firaz on 2011-07-04
Hello. Yesterday i was trying to create a partition on my hard drive on Linux using the GParted program. I noticed my hard drive had a key next to its name but could not find information regarding it online. I proceeded to unmount the drive and made 2 partitions. However, it game me an error saying it couldnt make the partitions. I turned my computer off thinking i would get back to trying tomorrow. Today i turn on my laptop and see the usual hp screen. But after that it goes to a black screen with a blinking underscore looking thing. It goes nowhere from there. It usually goes to a black screen after the hp logo, that says GRUB loading. Any ideas on how to fix this problem? Any help would be appreciated.

---

### Post by soumyabratapaul on 2011-07-04
Just press Ctrl + Alt + Del simultaneously, when you get that cursor blinking and see, if there are any messages that are coming, like messages will come. Just do this and let me know.

---

### Post by Firaz on 2011-07-04
ctrl alt del restarts the computer. it goes back to the hp logo and then to the blinking cursor again.

---

### Post by smurphy_it on 2011-07-04
I'd suspect your hosed your partition table.  The "Key" was pointing to your boot partition.  Suggest booting off a LIVE-CD, then follow the HDD link attached to my signature, and post the information back here.

---

### Post by Firaz on 2011-07-06
Hey guys. I started installing from a usb drive. It was going fine, all was installed (10.04 LTS). But then it finished installing and said You must restart computer now. I press that, then this whole slew of errors come up on a black screen. examples of what it said: 


[648.027974 end_request: I/O error, dev sdb, sector 1898680

and it went on for like the whole screen was full and stopped. It then just stays like on those errors. I will restart manually and see if it works 

It goes through some weird stuff, but it let me log in and do what u told me to do. Here are the results.

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 520 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   306,626,559   306,624,512  83 Linux
/dev/sda2         306,628,606   312,580,095     5,951,490   5 Extended
/dev/sda5         306,628,608   312,580,095     5,951,488  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,903,487     3,903,456   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        561d0856-92a5-40f2-9f49-083dd13f22f8   ext4       
/dev/sda5        84f177f3-cb67-4729-a9e3-9a4b5267b871   swap       
/dev/sdb1        CEFC-8B0C                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=561d0856-92a5-40f2-9f49-083dd13f22f8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=561d0856-92a5-40f2-9f49-083dd13f22f8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 561d0856-92a5-40f2-9f49-083dd13f22f8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=84f177f3-cb67-4729-a9e3-9a4b5267b871 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.133739471 = 10.881019904   boot/grub/core.img                             1
   [2.136947632]("tel:2.136947632") = [2.294530048]("tel:2.294530048")    boot/grub/grub.cfg                             1
  10.141170502 = 10.888998912   boot/initrd.img-2.6.32-28-generic              1
   0.264507294 = 0.284012544    boot/vmlinuz-2.6.32-28-generic                 1
  10.141170502 = 10.888998912   initrd.img                                     1
   0.264507294 = 0.284012544    vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

---

### Post by wildmanne39 on 2011-07-06
Hi, am pretty tired tonight but I think this is your problem.
> GiB - GB File Fragment(s)

10.133739471 = 10.881019904 boot/grub/core.img 1
2.136947632 = 2.294530048 boot/grub/grub.cfg 1
10.141170502 = 10.888998912 boot/initrd.img-2.6.32-28-generic 1
0.264507294 = 0.284012544 boot/vmlinuz-2.6.32-28-generic 1
10.141170502 = 10.888998912 initrd.img 1
0.264507294 = 0.284012544 vmlinuz 1
I am not sure how to fix it but I think it will take testdisk,but let someone else take a look that is not so tired.

---

### Post by smurphy_it on 2011-07-06
The IO sector error generally points to a bad sector on your hdd.  You should scan the second (sdb) drive for physical defects.  Any data contained within a bad sector should be automatically moved.

There are a ton of tools around for doing that job.

---

### Post by Firaz on 2011-07-06
Thanks for all your help guys! I really appreciate it. Can you recommend a program to use?

p.s. big fan of rurouni kenshin myself :P

---

