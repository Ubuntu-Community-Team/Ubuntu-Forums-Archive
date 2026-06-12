---
title: "Alert! /dev/sdh1 does not exist. Dropping to a shell."
date: 2010-06-17
forum: General Help
---

### Post by The_Hanged_Man on 2010-06-17
I have a 64 bit ubuntu 9.10 / 64 bit windows 7 dual boot setup, each installed on different drives. Everything worked fine for weeks, but after booting into windows for maybe the third time, when I tried to boot back into ubuntu, the splash screen and xwindows failed to start, dropping me to a terminal to log in.

After rebooting a few more times to see if i could wish the problem away, some kind of fix/recovery screen came up and gave me the chance to try to update/repair installed packages, which I took.

Now, when I boot, I get:

ata_id[428]:HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:80'
ata_id[427]:HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:64'
usplash: Settomg ,pde 1152x864 failed
usplash: Using mode 1024x768

Begin: Waiting for root file system
Done.
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdh1 does not exist. Dropping to a shell.

and it drops me to something called BusyBox

from that prompt, running :
cat /proc/cmdline/

gives:

BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=/dev/sdh1 ro single

When I try to choose Windows 7 from the grub bootlist, it gives: 
Error: Invalid Signature

and returns to the grub menu.

If I boot from the ubuntu cd, I can browse around both hard drives so the hard drives haven't totally failed, which is nice.

Anyway... Help! I'm an ubuntu noob in way over my head.

---

### Post by arrange on 2010-06-17
Could you paste the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/"). You can run it from a LiveCD.)

I'd also check the filesystem (f.e. via GParted) and the HDD (SMART data).

---

### Post by The_Hanged_Man on 2010-06-17
> **boot_info_script]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks for 
    (UUID=f3136190-7604-424b-8afe-6499d2a174a2)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sde3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63       160,649       160,587  de Dell Utility
/dev/sde2    *        161,792    23,078,911    22,917,120   7 HPFS/NTFS
/dev/sde3          23,078,912   976,771,071   953,692,160   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00097b94

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   119,844,899   119,844,837  83 Linux
/dev/sdf2         119,844,900   125,033,894     5,188,995   5 Extended
/dev/sdf5         119,844,963   125,033,894     5,188,932  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        07DA-0414                              vfat       DellUtility                   
/dev/sde2        160E342C0E340771                       ntfs       RECOVERY                      
/dev/sde3        7E9A373F9A36F2EF                       ntfs       OS                            
/dev/sdf1        f3136190-7604-424b-8afe-6499d2a174a2   ext4                                     
/dev/sdf5        edf39853-8ba0-44f7-8a11-15681310424d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdf1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ] said:**
> ; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdh1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdh1 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdh1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdh1 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdh1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdh1 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdh1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdh1 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdg2)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdf1 during installation
UUID=f3136190-7604-424b-8afe-6499d2a174a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=edf39853-8ba0-44f7-8a11-15681310424d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdf1: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/core.img
    .3GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.31-20-generic
   1.3GB: boot/initrd.img-2.6.31-21-generic
   1.7GB: boot/initrd.img-2.6.31-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.0GB: boot/vmlinuz-2.6.31-20-generic
   1.3GB: boot/vmlinuz-2.6.31-21-generic
   1.3GB: boot/vmlinuz-2.6.31-22-generic
   1.7GB: initrd.img
   1.3GB: initrd.img.old
   1.3GB: vmlinuz
   1.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 


There are the results of the boot info script. Finding GParted now.

---

### Post by arrange on 2010-06-17
OK, first things first (Ubuntu).
When you see the Grub menu, press **e** (edit) and change the line
```
linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sdh1 ro quiet splash
```to```
linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f3136190-7604-424b-8afe-6499d2a174a2 ro
```Then Ctrl+x to boot. Are you able to boot into Ubuntu now?

---

### Post by The_Hanged_Man on 2010-06-17
Yes, I was able to boot and log in.

Thanks :)

Now where to?

---

### Post by arrange on 2010-06-17
Could you post the contents of **/etc/default/grub** now?

---

### Post by The_Hanged_Man on 2010-06-17
> **arrange said:**
> Could you post the contents of **/etc/default/grub** now?

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by arrange on 2010-06-17
Strange. Could you please run ```
sudo update-grub
```and then post the output of the command + the contents of **/boot/grub/grub.cfg** (use the CODE tag please).

---

### Post by The_Hanged_Man on 2010-06-17
> **arrange said:**
> Strange. Could you please run ```
sudo update-grub
```and then post the output of the command + the contents of **/boot/grub/grub.cfg** (use the CODE tag please).

```
~$ sudo update-grub 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sde2
done

``````

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f3136190-7604-424b-8afe-6499d2a174a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f3136190-7604-424b-8af
e-6499d2a174a2 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 160e342c0e340771
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by arrange on 2010-06-17
Now hold your breath and restart. :)
If you're unable to boot, edit the Grub menu again, deleting all lines and only leaving these two```
linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f3136190-7604-424b-8afe-6499d2a174a2 ro
initrd /boot/initrd.img-2.6.31-22-generic
```

---

### Post by The_Hanged_Man on 2010-06-17
It works now. Thanks for your help.

Can you tell me what you were looking for or at in what you asked me to post so I can hopefully learn a little?

---

### Post by arrange on 2010-06-17
Study Grub
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
and UUID
[http://en.wikipedia.org/wiki/Uuid](http://en.wikipedia.org/wiki/Uuid)

One thing I don't understand is why your Grub was not using UUID from the start. (and was using */dev/sdxx* instead)

---

### Post by The_Hanged_Man on 2010-06-17
Will do. Thanks again.

---

