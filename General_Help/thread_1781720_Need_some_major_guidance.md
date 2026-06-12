---
title: "Need some major guidance"
date: 2011-06-13
forum: General Help
---

### Post by T&amp;H on 2011-06-13
[FONT="Arial"][/FONT]I'm not sure if I am posting this in the right place but here it goes.
I can not get Lucid Lynx to load. I have been running it on this computer for over a year with no problems but when I started the system it just seems to hang.  It waits for close to a minute looking for IDE drives then without seeming to acknowledge the hard drive it continues on to CD's etc.  Eventually it comes to a black screen with a flashing cursor then I get the following message:

[COLOR="Blue"]Gave up waiting for root device.  Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; Is/dev)
Alert! /dev/disk/by-uuid/4c71cf09-7e94-4fb3-9c4f-1434623820aa does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs) _
[/COLOR][COLOR="Black"][/COLOR]Can anyone tell me what this all means?  How do I get my system back?  I plugged a USB in with Mint Linux and it loads just fine, I can see the contents of my file system.  So again what is going on?
Thanks in advance.
T&H

---

### Post by raja.genupula on 2011-06-13
i cant figure out the problem , but  try this ```
sudo apt-get install ubuntu-desktop
```

---

### Post by wildmanne39 on 2011-06-13
> **T&H said:**
> [FONT="Arial"][/FONT]I'm not sure if I am posting this in the right place but here it goes.
I can not get Lucid Lynx to load. I have been running it on this computer for over a year with no problems but when I started the system it just seems to hang.  It waits for close to a minute looking for IDE drives then without seeming to acknowledge the hard drive it continues on to CD's etc.  Eventually it comes to a black screen with a flashing cursor then I get the following message:

[COLOR="Blue"]Gave up waiting for root device.  Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; Is/dev)
Alert! /dev/disk/by-uuid/4c71cf09-7e94-4fb3-9c4f-1434623820aa does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs) _
[/COLOR][COLOR="Black"][/COLOR]Can anyone tell me what this all means?  How do I get my system back?  I plugged a USB in with Mint Linux and it loads just fine, I can see the contents of my file system.  So again what is going on?
Thanks in advance.
T&HHi, post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by sidzen on 2011-06-13
At terminal --

***sudo ls -l /dev/disk/by-uuid/* ***

What is "4c71cf09-7e94-4fb3-9c4f-1434623820aa?"

Should output something along the lines 
lrwxrwxrwx 1 root root 10 Jun 13 18:37 /dev/disk/by-uuid/4c71cf09-7e94-xxxxxx -> ../../sda1

---

### Post by T&amp;H on 2011-06-14
Neat idea raja.genupula but looks really scary when I entered code, chose to abort for now as I was afraid of losing my saved files.

---

### Post by T&amp;H on 2011-06-14
> **wildmanne39 said:**
> Hi, post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

[FONT="Arial"][/FONT]Alright wildmanne here we go, though this seems a mile long and makes absolutely no sense to me.
[COLOR="Blue"]#                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98 ) is installed in the MBR of /dev/sda and looks at sector 
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
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 7770 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   960,159,743   960,157,696  83 Linux
/dev/sda2         960,161,790   976,773,119    16,611,330   5 Extended
/dev/sda5         960,161,792   976,773,119    16,611,328  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,964,589     3,964,528   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4c71cf09-7e94-4fb3-9c4f-1434623820aa   ext4       
/dev/sda5        eb73589b-0d53-4225-adc0-49288c353880   swap       
/dev/sdb1        1976-C708                              vfat       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
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
search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-32-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-31-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-29-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4c71cf09-7e94-4fb3-9c4f-1434623820aa
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
# / was on /dev/sda1 during installation
UUID=4c71cf09-7e94-4fb3-9c4f-1434623820aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb73589b-0d53-4225-adc0-49288c353880 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 332.126033783 = 356.617613312  boot/grub/core.img                             1
  54.533103943 = 58.554474496   boot/grub/grub.cfg                             2
 332.269615173 = 356.771782656  boot/initrd.img-2.6.32-24-generic-pae          1
 332.328231812 = 356.834721792  boot/initrd.img-2.6.32-25-generic-pae          1
  52.273979187 = 56.128757760   boot/initrd.img-2.6.32-26-generic-pae          1
 332.406497955 = 356.918759424  boot/initrd.img-2.6.32-27-generic-pae          1
 332.457126617 = 356.973121536  boot/initrd.img-2.6.32-28-generic-pae          1
 332.464508057 = 356.981047296  boot/initrd.img-2.6.32-29-generic-pae          1
  52.065929413 = 55.905366016   boot/initrd.img-2.6.32-30-generic-pae          2
  14.529815674 = 15.601270784   boot/initrd.img-2.6.32-31-generic-pae          2
  16.535697937 = 17.755070464   boot/initrd.img-2.6.32-32-generic-pae          2
 332.262237549 = 356.763860992  boot/vmlinuz-2.6.32-24-generic-pae             1
 332.273498535 = 356.775952384  boot/vmlinuz-2.6.32-25-generic-pae             1
 332.379913330 = 356.890214400  boot/vmlinuz-2.6.32-26-generic-pae             1
 332.399120331 = 356.910837760  boot/vmlinuz-2.6.32-27-generic-pae             1
 332.442363739 = 356.957270016  boot/vmlinuz-2.6.32-28-generic-pae             1
 332.446250916 = 356.961443840  boot/vmlinuz-2.6.32-29-generic-pae             1
 332.469383240 = 356.986281984  boot/vmlinuz-2.6.32-30-generic-pae             1
 332.504867554 = 357.024382976  boot/vmlinuz-2.6.32-31-generic-pae             1
 332.510368347 = 357.030289408  boot/vmlinuz-2.6.32-32-generic-pae             1
  16.535697937 = 17.755070464   initrd.img                                     2
  14.529815674 = 15.601270784   initrd.img.old                                 2
 332.510368347 = 357.030289408  vmlinuz                                        1
 332.504867554 = 357.024382976  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------

default vesamenu.c32
timeout 100

menu background splash.jpg
menu title Welcome to Linux Mint 10 32-bit
menu color border 0 #00eeeeee #00000000
menu color sel 7 #ffffffff #33eeeeee
menu color title 0 #ffeeeeee #00000000
menu color tabmsg 0 #ffeeeeee #00000000
menu color unsel 0 #ffeeeeee #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000
menu hidden
menu hiddenrow 6
label live
menu label Start Linux Mint
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash --
menu default
label xforcevesa
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/mint.seed boot=casper xforcevesa initrd=/casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
label check
menu label Check the integrity of the DVD
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Memory Test
kernel memtest
label local
menu label Boot from local drive
localboot 0x80
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

[/COLOR]I sure hope someone can make sense out of all this.
I did notice that it mentions Linux Mint in the list so just a refresher that is what I am running the system on in trial mode from a USB drive and so far all seems fine.  Except it won't load Ubuntu.:(
Again thanks for all the help.
T&H

---

### Post by ventrical on 2011-06-14
I had just updated yesterday to the linux kernel 32-32 on one of my pendrives and it crashed . I rebooted and chose 32-31 from the GRUB MENU and it re-booted fine.

I see also that you have the 32-32 Kernel.

---

### Post by T&amp;H on 2011-06-14
> **ventrical said:**
> I had just updated yesterday to the linux kernel 32-32 on one of my pendrives and it crashed . I rebooted and chose 32-31 from the GRUB MENU and it re-booted fine.

I see also that you have the 32-32 Kernel.

[FONT="Arial"]Grub Menu? Where do I find that?[/FONT]

---

### Post by wildmanne39 on 2011-06-15
> **T&H said:**
> [FONT="Arial"]Grub Menu? Where do I find that?[/FONT]
Hi, do you still have mint linux installed? are you using it?
I think you should try this
```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
``` Boot from the livecd and click try then open up a terminal and copy/paste the following commands in, one line at a time, pressing enter after each line. If no errors are reported, please reboot and see if Ubuntu boots up,it does open a terminal and run this command.
sudo update-grub

---

### Post by T&amp;H on 2011-06-15
> **wildmanne39 said:**
> Hi, do you still have mint linux installed? are you using it?
I think you should try this
```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
``` Boot from the livecd and click try then open up a terminal and copy/paste the following commands in, one line at a time, pressing enter after each line. If no errors are reported, please reboot and see if Ubuntu boots up.

[FONT="Arial"]Still using Mint off the flash drive as I am afraid of over writing Lucid. Tried the line commands and this is exactly what transpired from that:
[COLOR="Blue"]#mint@mint ~ $ sudo mount /dev/sda1 /mnt
mint@mint ~ $ sudo grub-install --root-directory=/mnt /dev/sda
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
Installation finished. No error reported.
mint@mint ~ $
[COLOR="Black"]Now I get a Grub menu with many back up points to choose from and have tried several, all give very long lists of code and end up like this:[COLOR="Blue"]
#[    1.888052] usb 4-1: new low speed USB device using ohci_hcd and address2
[    2.056877] usb 4-1: configuration #1 chosen from 1 choice
[    6.156031] ata1: link is slow to respond, please be patient (ready=0)[    6.1896691] scsi 8:0:0:0: Direct-access    Generic STORAGE DEVICE  0119 PQ
: 0 AMSI: 0
[    6.193656] sd 8:0:0:0: [sda] Attached SCSI removable disk
[    10.972030] ata1: SRST failed (errno=-16)
[    16.168030] ata1: link is slow to respond, please be patient (ready=0)
[    20.984030] ata1:SRST failed (errno=-16)
[    26.180030] ata1: link is slow to respond, please be patient (ready=0)
Gave up waiting for root device.  Common problems:
-Boot args (cat /proc cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4c71cf09-7e94-4fb3-9c4f-1434623820aa does not exist. Dr
opping to a shell

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-n shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   56.028030] ata1: SRST failed (errno=-16)[COLOR="Black"]
So at this time this is where I am.  Out of curiosity what kind of problem am I looking at?  Would it be easier to use Mint to retreve all that is retreveable and reboot?
For refrence I do remember the system doing an update during its last operational session but don't ask what it updated as I can't remember.
Again thanks for all the help.
T&H[/COLOR][/COLOR][/COLOR][/COLOR][/FONT]

---

### Post by wildmanne39 on 2011-06-15
Hi, I just realized you are using mint, sorry I did not catch it earlier, you have to boot from the same version of ubuntu as you are trying to repair, it can not be any other version or distro. of linux.

---

### Post by T&amp;H on 2011-06-16
[FONT="Arial"]Well leave it to me to add a new wrench to the gears.  I'll set up a lucid flash and retry the aforementioned attempts again and then let you know what I get.
Thanks again.
T&H[/FONT]

---

### Post by T&amp;H on 2011-06-23
Sorry about the long delay, my grandfather passed away late last week and this is the first time I have been on line since.

This morning I intended to transfer some files from a flash drive to my Droid intending to use Mint, however I had inadvertently left the live CD in the drawer at last attempt to repair the system.  To my surprise it found the live CD and loaded to a point, then quit.  I removed all flash drives and the CD then restarted.  At the Grub menu I chose the newest entry, and the repair option screen came up, I chose repair.  28 packages later we appear to be up and running! :)
I am still not sure exactly what happened but I thank you for all your help. Although I have been using Ubuntu for a while (unlike windoze) I haven't had any major trouble so when something does go wrong EEEK!:confused:

Thanks again,
T&H

---

