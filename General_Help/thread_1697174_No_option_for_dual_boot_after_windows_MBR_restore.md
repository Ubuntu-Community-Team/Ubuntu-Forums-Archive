---
title: "No option for dual boot after windows MBR restore"
date: 2011-02-28
forum: General Help
---

### Post by BudworthTDog on 2011-02-28
Here's the short version of what happened

--Had windows 7 and installed Ubuntu dual boot

--all was well but after some messing around with a failed Backtrack install I had to repartition some things to clean it up

--The partition where Backtrack was installed was corrupt so I deleted it and extended my Ubuntu partition. 

--reload got the no such partition rescue grub

--read threw a bunch of forums and could only seem to find mostly threads on only being able to load Ubuntu and not Windows. Most having to do with post OS install problems and not re partitioning. 

--I decided the best thread to follow was [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

--after that my memory of events is a bit fuzzy, a lot was going on. In short I got a message in the terminal saying "this is a BAD idea" and something about another MBR. (sorry I cant be more specific)

--reading on I decided I would try my windows bootloader restore

--now windows loads up fine but it doesn't even give me an option to boot Ubuntu. I launched a live CD and checked GParted. The partition is still there.

Sorry if this is threaded somewhere already, I know that annoying. I'm just burnt out on combing forums and broke down and decided to ask directly

---

### Post by Quackers on 2011-02-28
It is likely that you need to re-install grub to the mbr again.
Please boot from the Ubuntu live cd and select "try ubuntu" and either post a screenshot of the gparted screen for the drive you are talking about or go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by BudworthTDog on 2011-02-28
Thank you very kindly for the quick reply with clear dirrections!

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,068,414     3,068,352  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   235,003,986   231,929,939   7 HPFS/NTFS
/dev/sda3         235,005,950   625,141,759   390,135,810   5 Extended
/dev/sda5         235,005,952   616,944,194   381,938,243  83 Linux
/dev/sda6         616,944,258   625,137,344     8,193,087  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2812B92412B8F7C0                       ntfs       System                        
/dev/sda2        4C54DEF254DEDE30                       ntfs       TI102618W0G                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        52a8ab85-6af1-4ff9-bba4-c9a469b6832f   ext4                                     
/dev/sda6        64081bab-b2d0-4b20-aaf9-dfe9a1e5d6c3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=52a8ab85-6af1-4ff9-bba4-c9a469b6832f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=52a8ab85-6af1-4ff9-bba4-c9a469b6832f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=52a8ab85-6af1-4ff9-bba4-c9a469b6832f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=52a8ab85-6af1-4ff9-bba4-c9a469b6832f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a8ab85-6af1-4ff9-bba4-c9a469b6832f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2812b92412b8f7c0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 4c54def254dede30
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=52a8ab85-6af1-4ff9-bba4-c9a469b6832f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=64081bab-b2d0-4b20-aaf9-dfe9a1e5d6c3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 122.8GB: boot/grub/core.img
 125.1GB: boot/grub/grub.cfg
 123.7GB: boot/initrd.img-2.6.32-21-generic
 123.9GB: boot/initrd.img-2.6.35-25-generic
 120.4GB: boot/vmlinuz-2.6.32-21-generic
 123.7GB: boot/vmlinuz-2.6.35-25-generic
 123.9GB: initrd.img
 123.7GB: initrd.img.old
 123.7GB: vmlinuz
 120.4GB: vmlinuz.old
```

---

### Post by Quackers on 2011-02-28
Ok, thanks.
From the live cd desktop open up a terminal and please copy/paste these lines in, one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that installs without errors you can reboot the system. If it worked ok, Ubuntu should then boot directly. If it does, open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to see that the Windows Loader is picked up. If it is, you can reboot and choose Windows from the new grub menu. (You may get 2 Windows entries in the grub menu - choose the one for /dev/sda2 as the first one will probably be for the recovery partition).

---

### Post by BudworthTDog on 2011-02-28
Awesome that did it. How do I mark this thread as solved?

---

### Post by Quackers on 2011-02-28
Once you've clicked on the thread look at the top right for Thread Tools. It is one of the options in it.
Glad you've got things back again :-)

---

