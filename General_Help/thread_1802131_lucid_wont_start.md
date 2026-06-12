---
title: "lucid wont start"
date: 2011-07-11
forum: General Help
---

### Post by bouncingwilf on 2011-07-11
Sorry to post this one butI need a bit of help geting lucid started. It was running ok earlier today , I shut i down normally but all attempts to restart have failed. It's obviously very early in the process where it fails- grub?-  but just hangs with a cursor at the top right of the screen.  A look through the logs on the hard drive using a live cd show nothing after the shutdown Any Ideas on how to get it past grub much appreciated


Bouncingwilf

---

### Post by pqwoerituytrueiwoq on 2011-07-11
can you boot any other options in grub eg recovery?

---

### Post by bouncingwilf on 2011-07-11
No Nothing  - no text appears at all = straight from BIOS splash to black screen - if I could get in I might be able to track the error but nothing!


Bouncingwilf

---

### Post by tasaif09 on 2011-07-11
wait for a minute, then press
ctrl + alt + backspace
or
ctrl + alt + F6

I'm no pro, but that might get you to a terminal at the very least...

Possibly relevant links:
[http://stackoverflow.com/questions/120296/used-ctrl-alt-f6-in-linux-and-cant-get-my-screen-back](http://stackoverflow.com/questions/120296/used-ctrl-alt-f6-in-linux-and-cant-get-my-screen-back)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by bouncingwilf on 2011-07-11
No not even getting that far. Think the problem lies with grub

Can't get anything started.

Bouncingwilf

---

### Post by bouncingwilf on 2011-07-11
Run a check on the hard drive from the Live CD and it says "file system is NOT clean"  - any ideas where I go from here? 

Bouncingwilf

---

### Post by bouncingwilf on 2011-07-11
Nope not that, ran Gparted and got the disc ok but still no boot!

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-11
> **bouncingwilf said:**
> Nope not that, ran Gparted and got the disc ok but still no boot!

BouncingwilfHi, it sounds like a corrupt file system possibly caused by a drive problem, with the live cd open disk utility and run a drive check, then run another file check from disk utility. If the problems persists post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
It is possible that you will have to run testdisk to try and recover the file system, the boot script information will show us a lot more information so we can help you.

---

### Post by bouncingwilf on 2011-07-12
Many thanks for the reply, the file check reported "clean" but  here are the results of the boot_info script

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   112,351,231   112,349,184  83 Linux
/dev/sda2         112,353,278   117,229,567     4,876,290   5 Extended
/dev/sda5         112,353,280   117,229,567     4,876,288  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2b9919b1-a204-4a0e-9366-321dd2571691   ext4       
/dev/sda5        037c0fba-3e06-4ab3-b83f-35784f8603f0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/2b9919b1-a204-4a0e-9366-321dd2571691 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
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
search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=2b9919b1-a204-4a0e-9366-321dd2571691 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=2b9919b1-a204-4a0e-9366-321dd2571691 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2b9919b1-a204-4a0e-9366-321dd2571691 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2b9919b1-a204-4a0e-9366-321dd2571691 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2b9919b1-a204-4a0e-9366-321dd2571691
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  34.144130707 = 36.661981184   boot/grub/core.img                             1
  20.327781677 = 21.826789376   boot/grub/grub.cfg                             2
  34.151580811 = 36.669980672   boot/initrd.img-2.6.32-28-generic              1
  34.258396149 = 36.784672768   boot/initrd.img-2.6.32-32-generic              1
  34.142761230 = 36.660510720   boot/vmlinuz-2.6.32-28-generic                 1
  34.192237854 = 36.713635840   boot/vmlinuz-2.6.32-32-generic                 1
  34.258396149 = 36.784672768   initrd.img                                     1
  34.151580811 = 36.669980672   initrd.img.old                                 1
  34.192237854 = 36.713635840   vmlinuz                                        1
  34.142761230 = 36.660510720   vmlinuz.old                                    1


```     

Bouncingwilf

---

### Post by bouncingwilf on 2011-07-12
Slowly getting there! I've managed to get a text boot in recovery mode  and it's hanging after installing the usb devices after running scripts  init-bottom. It fails at the same place with both the .32 and -28  kernels


Any ideas what's nexr? 

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-12
Hi, I am researching your problem but if you have usb devices plugged in try unplugging them and then boot sometimes usb devices hang up the boot process, but I think it is because of the information in your boot script that is what I am researching.

---

### Post by wildmanne39 on 2011-07-12
Hi. also try what this link says while I research your issue because you may have update some packages that caused this.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bouncingwilf on 2011-07-12
The machine boots fine from the live cd and has previously worked OK with its current configuration. If I knew what it was trying to do when it hangs, we may get somewhere so  where do I find the sequence of events that occur during boot? i.e. at what stage is it hanging?

nomodeset may be relevant but why would it need it now ( and on a different monitor to the one it originally failed on?) 

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-12
> **bouncingwilf said:**
> The machine boots fine from the live cd and has previously worked OK with its current configuration. If I knew what it was trying to do when it hangs, we may get somewhere so  where do I find the sequence of events that occur during boot? i.e. at what stage is it hanging?

nomodeset may be relevant but why would it need it now ( and on a different monitor to the one it originally failed on?) 

BouncingwilfHi, it has nothing to do with the monitor, it has to do with the fact that the video card driver may have been upgraded and that has caused a lot of issues for many people on here, please go through the nomodeset page and try each one and see if it works so we can eliminate it.

---

### Post by bouncingwilf on 2011-07-13
Well I've tried just about every possible combination of boot flags but it still hangs at the same point. Root filesystem is loaded, and USB ports are detected. no keyboard input is accepted but it is possible to add or remove USB devices and they are correctly identified and displayed on screen i.e. adding or removing a USB device gives a sensible screen message.  I've flashed the BIOS to the latest and tried alternative keyboards/mice etc. but it just doesn't want to play!

I suspect I will re-install with Xubuntu to try a different DM but I would really like to know the cause of the problem first.

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-13
Hi, I think this happen because you had a corrupt file system, you can use the instructions from this link to purge and reinstall grub.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by bouncingwilf on 2011-07-14
Well I went through the chrooting procedure but could not get an internet connection and the reconfigure grub command came up with a blank for the  Linux command line. Selecting OK's came up with this error

bash-4.1# dpkg-reconfigure grub-pc
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 22.
/usr/bin/ucf: line 520: awk: command not found
bash-4.1# 

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-14
Hi, when you did not have a internet connection did you go furhter down the page and follow the directions for Reconfiguring Grub 2 without an Internet Connection?

---

### Post by bouncingwilf on 2011-07-14
Yes, that's when I got the error. I did eventually manage to get an internet connection but still no go. In the end I took the easy way out and installed 10.10 ( but with a separate home directory) 

I did notice one strange thing though - the booting behaviour of this motherboard (Intel D510MO) seemed to be affected by what was attached to USB ports. I've now found it difficult to get the board to boot from CD or stick unless the wireless connection is removed ( tries to boot direct from hard disc) As noted yesterday, I flashed the motherboard with the latest BIOS - probably just coincidence or a dodgy wireless!

Many thanks for your help.

Bouncingwilf

---

### Post by wildmanne39 on 2011-07-14
> **bouncingwilf said:**
> Yes, that's when I got the error. I did eventually manage to get an internet connection but still no go. In the end I took the easy way out and installed 10.10 ( but with a separate home directory) 

I did notice one strange thing though - the booting behaviour of this motherboard (Intel D510MO) seemed to be affected by what was attached to USB ports. I've now found it difficult to get the board to boot from CD or stick unless the wireless connection is removed ( tries to boot direct from hard disc) As noted yesterday, I flashed the motherboard with the latest BIOS - probably just coincidence or a dodgy wireless!

Many thanks for your help.

BouncingwilfHi,it is hard to say sometimes flashing a bios can cause more problems then it solves. I am glad you have a working system now, I am sorry that attempts to fix your install failed.

---

