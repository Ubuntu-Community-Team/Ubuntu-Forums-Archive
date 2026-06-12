---
title: "grub 2 is only adding windows, no ubuntu"
date: 2010-05-17
forum: General Help
---

### Post by foolfoolz on 2010-05-17
so i decided to shrink my linux partition and make my windows one bigger
this worked out fine for linux, ended up screwing the windows one up bad
so i reinstalled windows

i ended up getting everything back to normal almost. the only difference was when i would pick windows in the grub menu the windows boot manager would go and find 2 windows installations. so i decided to install windows 7 again to fix this (and i dont think its fixed at all)

but right now im at the point where windows is installed, grub is installed to the MBR, but the only options i have are 2 windows installations.

heres my fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000032d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32630   262100443+  83  Linux
/dev/sda2           32631       32643      104422+   7  HPFS/NTFS
/dev/sda3   *       32644       59335   214402048    7  HPFS/NTFS
/dev/sda4           59336       60801    11775645    5  Extended
/dev/sda5           59336       60801    11775613+  82  Linux swap / Solaris

```sda 1 is my karmic linux
sda 2 is system reserved (that windows thinks is another windows)
sda 3 is my windows 7
sda 4 and sda 5 are listed above

sort of weird that sda 3 is listed as boot because it really does boot the grub2 off sda1

anyway, this is what happens when i run update-grub (off the live cd)

```

Generating grub.cfg ...
Found Debian background: grub.png
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done

```which is not what i want. how can i get linux to appear again in the list? i havent touched my /etc/grub.d it is entirely default except i moved os_prober to 06 from 30 (so windows would be on top)

---

### Post by oldfred on 2010-05-17
Windows 7 installs in 2 partitions if it is a new install. It creates a 100MB boot partition and that partition has to have the boot flag. Linux does not use the boot flag, but some BIOS will not let you boot unless you have a boot flag on a primary partition.

Run this script and we will see if other things are missing:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by foolfoolz on 2010-05-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000032d4

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   524,200,949   524,200,887  83 Linux
/dev/sda2         524,200,950   524,409,794       208,845   7 HPFS/NTFS
/dev/sda3    *    524,410,880   953,214,975   428,804,096   7 HPFS/NTFS
/dev/sda4         953,216,775   976,768,064    23,551,290   5 Extended
/dev/sda5         953,216,838   976,768,064    23,551,227  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f4cff6dc-430d-4985-b98a-0356dc03ff9c   ext4                                     
/dev/sda2        321AE5A81AE56975                       ntfs       System Reserved               
/dev/sda3        2C2EF4A42EF467EA                       ntfs                                     
/dev/sda5        25f25cb0-25c1-4240-99db-8bf6aa1db998   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800x32
  set gfxpayload=keep
  # jordan sterling professional programmer added line above this one
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
insmod png
if background_image /usr/share/images/grub/grub.png ; then
  set color_normal=white/black
  set color_highlight=blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 321ae5a81ae56975
    chainloader +1
}
### END /etc/grub.d/06_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c ro single 
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4cff6dc-430d-4985-b98a-0356dc03ff9c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=25f25cb0-25c1-4240-99db-8bf6aa1db998 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/core.img
   1.2GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.8GB: boot/initrd.img-2.6.31-15-generic
   1.5GB: boot/initrd.img-2.6.31-16-generic
   1.7GB: boot/initrd.img-2.6.31-17-generic
   3.7GB: boot/initrd.img-2.6.31-19-generic
   4.4GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.7GB: boot/vmlinuz-2.6.31-15-generic
   1.2GB: boot/vmlinuz-2.6.31-16-generic
   1.6GB: boot/vmlinuz-2.6.31-17-generic
   3.5GB: boot/vmlinuz-2.6.31-19-generic
   4.0GB: boot/vmlinuz-2.6.31-20-generic
   4.4GB: initrd.img
   3.7GB: initrd.img.old
   4.0GB: vmlinuz
   3.5GB: vmlinuz.old

============================= sda3/grub/grub.cfg: =============================

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800x32
  set gfxpayload=keep
  # jordan sterling professional programmer added line above this one
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f4cff6dc-430d-4985-b98a-0356dc03ff9c
insmod png
if background_image /usr/share/images/grub/grub.png ; then
  set color_normal=white/black
  set color_highlight=blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 321ae5a81ae56975
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 2c2ef4a42ef467ea
    chainloader +1
}
### END /etc/grub.d/06_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg
```

---

### Post by oldfred on 2010-05-17
Your grub2 in the MBR is looking for sda3 which is now windows and your install is in sda1. You need to reinstall grub from a liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

You may want to do the full chroot version as your grub.cfg has no entry for you to boot. You could do it with manual entries:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Mnaual boot:
Try this at the Grub prompt if partition known:

root (hd0,1)
kernel /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
This should boot you into Ubuntu.
Open a terminal in Ubuntu and run

sudo update-grub

---

### Post by foolfoolz on 2010-05-17
alright well even thought i did that like 4 times earlier today, it worked this time

now i have my os prober on top which finds windows on sda2, followed by linux

what im going to do is rename 06_osprober to 30_ again so its on bottom, but i want to add a custom entry for sda3 on top.
is this the best way of doing this?

if i boot into sda2, i go right into the windows boot manager where i need to pick between Windows 7 and Windows 7. This sucks, but if i boot into sda3 im fine and it loads up nicely.

so how exactly would i set up a custom entry for sda2?

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows" {
set root=(hd0,1)
chainloader +2
}
EOF

```
like this and rename the 40_custom to something above 10? (i want windows on top, linux in #2)

---

### Post by oldfred on 2010-05-18
You can copy your 40_custom to 06_custom and put the full entry in 06_custom the osprober found, you may be able to just have set root & chainload as minimal entry:

menuentry "Windows 7 (loader) (on /dev/sda3)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 2c2ef4a42ef467ea
    chainloader +1
}

You also have some grub files in /grub in your sda3 partition. I would also delete those.

---

### Post by foolfoolz on 2010-05-18
yea that took care of it and i deleted the grub folder off sda3. thanks

---

