---
title: "Problems with bootloader after installing 9.10"
date: 2011-03-06
forum: General Help
---

### Post by sudouser on 2011-03-06
I'm a fairly new Linux user, with my first Linux distro being Ubuntu 10.10, which I first installed around November on my laptop.  Initially I tried installing it on my desktop, but the liveCD would give me a blank screen every time, no matter how many USB installers I tried.  I had given up on my desktop when it installed without a hiccup on my first try with my laptop, until now.  I've tried Kubuntu and Xubuntu, both giving me the same problem.  Non-'buntu distros gave me no problems however.  I tried Ubuntu 10.04 without success.  But to my surprise Ubuntu 9.10 gave me no troubles (at first) and I am typing from it currently.  When it was done installing, it asked if I wanted it to add a bootloader, and I said no because I wasn't sure if it was going to install GRUB, and I already had the Windows bootloader installed.  When I restarted I found out that the last part of my sentence was no longer true, and I had to reinstall from the liveCD to get a bootloader.

So now I have GRUB installed, but Windows 7 is not appearing in the options.  I edited /boot/grub/menu.lst to this
```
default 0

timeout 15

title Windows 7
rootnoverify (hd0,0)
chainloader (hd0,0)+1

title Ubuntu 9.10
root (hd0,1)
chainloader +1

map (hd0) (hd1)
map (hd1) (hd0)
```But none of that changed the options when GRUB comes up at startup.

I then changed /etc/grub.d/40_custom to the following
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" {
insmod chain
insmod ntfs
search --fs-uuid --set ee42c3ea42c3b61d
chainloader +1
}

```but /boot/grub/grub.cfg has this at the end
```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```so it's ignoring my changes

I can still access my C:\ drive from Ubuntu, and everything appears to be in working order, so it's not as if Windows is corrupted.

Any help would be greatly appreciated, I've spent just about all day today and yesterday trying to fix this on my own, when I should have been studying for midterms, so hopefully this isn't too hard to fix and I can actually sleep tonight :P

Once I get my bootloader issue resolved I'll be updating to 10.04 and then 10.10, which I shouldn't have any trouble with.

---

### Post by sudouser on 2011-03-06
I found a script which finds information about each partition, including the bootloader location.  Here are the results
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=386f4000-3e26-470c-905c-8df1e8e38c6d)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5dab5dab

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    390,829,320   976,768,064   585,938,745  83 Linux
/dev/sda2                  63   390,829,319   390,829,257   5 Extended
/dev/sda5                 126   390,829,319   390,829,194  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54d96a05

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,748,721,663 1,748,719,616   7 HPFS/NTFS
/dev/sdb2       1,748,721,664 1,953,519,615   204,797,952  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 16.0 GB, 16039018496 bytes
256 heads, 25 sectors/track, 4894 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *          2,224    31,326,207    31,323,984   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        39b1f36a-4a0a-40d7-9f15-e417f1c59eb0   ext2       Volume                        
/dev/sda5        18c81378-9149-4cb1-a03a-0337542667a7   swap                                     
/dev/sdb1        EE42C3EA42C3B61D                       ntfs       Main Drive                    
/dev/sdb2        386f4000-3e26-470c-905c-8df1e8e38c6d   ext2                                     
/dev/sdg1        9ED9-FD0A                              vfat       MULTIBOOT                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext2       (rw,errors=remount-ro)
/dev/sdg1        /media/MULTIBOOT         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb2/boot/grub/menu.lst: ===========================

default 0

timeout 15

title Windows 7
rootnoverify (hd0,0)
chainloader (hd0,0)+1

title Ubuntu 9.10
root (hd0,1)
chainloader +1

map (hd0) (hd1)
map (hd1) (hd0)

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 386f4000-3e26-470c-905c-8df1e8e38c6d
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 386f4000-3e26-470c-905c-8df1e8e38c6d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=386f4000-3e26-470c-905c-8df1e8e38c6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 386f4000-3e26-470c-905c-8df1e8e38c6d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=386f4000-3e26-470c-905c-8df1e8e38c6d ro single 
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
menuentry "'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b6fdacca-acd7-45b7-a448-9bfe4c099a5c
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=b6fdacca-acd7-45b7-a448-9bfe4c099a5c ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b6fdacca-acd7-45b7-a448-9bfe4c099a5c
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=b6fdacca-acd7-45b7-a448-9bfe4c099a5c ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b6fdacca-acd7-45b7-a448-9bfe4c099a5c
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b6fdacca-acd7-45b7-a448-9bfe4c099a5c ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b6fdacca-acd7-45b7-a448-9bfe4c099a5c
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b6fdacca-acd7-45b7-a448-9bfe4c099a5c ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=386f4000-3e26-470c-905c-8df1e8e38c6d /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=18c81378-9149-4cb1-a03a-0337542667a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 948.1GB: boot/grub/core.img
 948.1GB: boot/grub/grub.cfg
 948.1GB: boot/grub/menu.lst
 948.0GB: boot/initrd.img-2.6.31-14-generic
 948.0GB: boot/vmlinuz-2.6.31-14-generic
 948.0GB: initrd.img
 948.0GB: vmlinuz

================================ sdg1/menu.lst: ================================

default 0 
timeout 30 
color NORMAL HIGHLIGHT HELPTEXT HEADING 
splashimage=/splash.xpm.gz 
foreground=FFFFFF 
background=000000 
 
# Suggested by Erhan Sohail 
title Boot First Hard Drive (HDD) 
map (hd0) (hd1) 
map (hd1) (hd0) 
map --hook 
chainloader (hd0)+1 
rootnoverify (hd0) 
 
title Restart 
reboot 
 
title Shutdown 
halt 
 
title --- Custom MultiBoot Entries --- 
root 
 
title Ubuntu 10.10 (GNOME Desktop x86) 
find --set-root /ubuntu-10.10-desktop-i386.iso 
map /ubuntu-10.10-desktop-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.10-desktop-i386.iso splash 
initrd /casper/initrd.lz 
 
title Balder DOS image (FreeDOS) 
find --set-root /balder10.img 
map --unsafe-boot /balder10.img (fd0) 
map --hook 
chainloader --force (fd0)+1 
rootnoverify (fd0) 
 
title DSL 4.4.10 
find --set-root /dsl-4.4.10-initrd.iso 
map /dsl-4.4.10-initrd.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
# Suggested by Ambriel 
title Lubuntu 10.10 (LXDE Lightweight Desktop x86) 
find --set-root /lubuntu-10.10.iso 
map /lubuntu-10.10.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/lubuntu.seed boot=casper persistent iso-scan/filename=/lubuntu-10.10.iso floppy.allowed_drive_mask=0 splash 
initrd /casper/initrd.lz 
 
# Start Suggested by Erhan Sohail 
title TinyCore 
find --set-root /tinycore-current.iso 
map /tinycore-current.iso (0xff) || map --mem /tinycore-current.iso (0xff) 
map --hook 
chainloader (0xff) 
 
title SliTaz 3.0 
find --set-root /slitaz-3.0.iso 
map --heads=0 --sectors-per-track=0 /slitaz-3.0.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Linux Mint 10 
find --set-root /linuxmint-10-gnome-cd-i386.iso 
map /linuxmint-10-gnome-cd-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/linuxmint-10-gnome-cd-i386.iso floppy.allowed_drive_mask=0 splash 
initrd /casper/initrd.lz 

=================== sdg1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

