---
title: "Sudden mount error, and then GRUB after attempted repair"
date: 2011-04-19
forum: General Help
---

### Post by Sanjima on 2011-04-19
Alright. @.@; I'll try to explain this as best I can, as I at this point have no idea what's going on.

Just a few minutes ago, something strange happened to my system while running Ubuntu and the best way I could explain it was that the window system like I guess partially crashed.
Windows showed up as jumbled pieced together strips and bits of other windows and what not.

I tried rebooting. I managed to open the shut down dialogue and remembered the Alt+R hotkey to press the reboot button, so I managed to reboot the system properly.

When ubuntu tried booting then, it got haulted and said something about failing to mount a drive, and gave the option to skip mounting or perform a manual recovery.
My knowledge of linux in general is modestly limited so I chose to simply restart with the LiveCD (which i'm running on currently) and look to the forums for help.

The closest thing I could find to my problem was something about Grub becoming damaged, so I attempted to reinstall Grub as per the instructions in the forums. My guess is my partition table is set up strangely (since I have a dual-boot setup between Windows 7 and Ubuntu) and grub got improperly configured/reinstalled or something of the like.

So now when I try to boot from my hard disk, I come up with a black screen with the white letters reading something about missing files, and a "Grub recovery" prompt or something similar.

I'm not sure what other information I could give, but I'll be happy to give any that's needed about my system.

I'm running Ubuntu 10.10 64-bit on a laptop, single hard drive, and I think four separate partitions on it which are for windows 7, windows 7's recovery partition, ubuntu's main ext4 partition, and ubuntu's swap partition.

I can provide fdisk reports of my setup as well if that might help. I'm just not sure what else to put in here.


*edit: Here's my system's reports from fdisk and blkid
[IMG]http://img690.imageshack.us/img690/7453/screenshothii.png[/IMG]

---

### Post by matt_symes on 2011-04-19
Hi

From the LiveCD download the boot info script in my signature and run it. The instructions are on the download page.

Post the results back here between code tags as such [noparse] ```
 file 
``` [/noparse].

This will give us an overview of your system and help us work out what the problem is.

Kind regards

---

### Post by Sanjima on 2011-04-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   540,207,103   540,000,256   7 HPFS/NTFS
/dev/sda3         540,209,150   625,141,759    84,932,610   5 Extended
/dev/sda5         624,142,336   625,141,759       999,424  82 Linux swap / Solaris
/dev/sda6         540,209,152   624,142,335    83,933,184  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        78E09845E0980B8E                       ntfs       System Reserved               
/dev/sda2        50B8AB74B8AB56EE                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f82c528c-0c09-4b9d-92e5-25f697eb1ef6   swap                                     
/dev/sda6        5651dc58-e57e-4c27-b483-cd8cd1d147af   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/5651dc58-e57e-4c27-b483-cd8cd1d147af ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5651dc58-e57e-4c27-b483-cd8cd1d147af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5651dc58-e57e-4c27-b483-cd8cd1d147af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5651dc58-e57e-4c27-b483-cd8cd1d147af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5651dc58-e57e-4c27-b483-cd8cd1d147af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5651dc58-e57e-4c27-b483-cd8cd1d147af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 78e09845e0980b8e
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5651dc58-e57e-4c27-b483-cd8cd1d147af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f82c528c-0c09-4b9d-92e5-25f697eb1ef6 none            swap    sw              0       0
pri=1

=================== sda6: Location of files loaded by Grub: ===================


 309.0GB: boot/grub/grub.cfg
 278.1GB: boot/initrd.img-2.6.35-22-generic
 283.8GB: boot/initrd.img-2.6.35-28-generic
 306.7GB: boot/vmlinuz-2.6.35-22-generic
 306.9GB: boot/vmlinuz-2.6.35-28-generic
 283.8GB: initrd.img
 278.1GB: initrd.img.old
 306.9GB: vmlinuz
 306.7GB: vmlinuz.old
```*edit: I forgot to thank you for the reply and prompt instructions xD thank you, I hope you can find out what's wrong with my system


If it helps, what seemed to have caused the grub error was the following terminal instructions:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
After doing that, I had that missing files grub error at startup, with the "grub recovery" prompt.

---

### Post by matt_symes on 2011-04-19
Hi

There are a number of issues with your system at the moment.

```
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
```

Grub stage 1 is looking in the wrong partition. It's looking in sda1 and it should be looking in sda6.

```
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
```

You are also missing the second stage boot loader /boot/grub/core.img in sda6.

These two issues need to be addressed before looking at the windows partitions (which i am not so au fait with).

The first thing you need to do is reinstall grub. So from the LiveCD copy and paste these commands into the terminal.

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Enter your password. It will not be echoed to the screen. This is normal.

Reboot your PC into Ubuntu and enter

```
sudo update-grub
```

For your reference these commands are taken from drs305's tutorial here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Kind regards

---

### Post by Sanjima on 2011-04-19
Alright, grub installation codes have been executed. now rebooting, I'll edit this post to tell you what comes up.

Thanks again! ^^

update: Wow, that fixed everything in one swift kick xD Thank you so much, I guess Grub just got damaged somehow, and I seemed to have been on the right path to fix it but I told it to look to the wrong partition to load from.
So all is well now, thank you again so much xD

---

### Post by matt_symes on 2011-04-19
Hi

Try booting into your windows installs to make sure there is no problem there.

If things are all good then please mark this thread as solved.

Kind regards

---

