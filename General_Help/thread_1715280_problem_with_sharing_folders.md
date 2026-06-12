---
title: "problem with sharing folders"
date: 2011-03-26
forum: General Help
---

### Post by g_lev on 2011-03-26
Hello.
I have 2 HD. on one i installed Ubuntu and the other i formated from Ubuntu as FAT32.
on Ubuntu i have 3 accounts; one admin and 2 users.
now i have few problems:
1. wean I log in the users account they can't see the other HD and they required to enter admin password to mount the device.
2. when I try entering the device from the network sharing i get an error (failed windows sharing) and i can't log the the folders.
3. I can't access the shared HD from a windows vista computer.

any help would be appreciated.

thank you.

---

### Post by Morbius1 on 2011-03-26
So you want to have access from other local login users on the same box. And you also want access from across the network.

** [1] Run the following command:**
```
sudo blkid -c /dev/null
```You will get an output that looks something like this [COLOR=Blue]as an example[/COLOR]:
> /dev/sdb1: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat" **[2] Make a permanent home for that partition:**
```
sudo mkdir /media/HD2
```**[3] Edit fstab as root:**
```
gksu gedit /etc/fstab
```**[4] Add a line to fstab to automount the partition:**
```
UUID=C4DB-C1B0 /media/HD2 vfat utf8,umask=000,uid=1000 0 1
```Then save fstab

** [5] Run the following command to test for errors and mount the new partition:**
```
sudo mount -a
```**[6] Share the new partition to the network:**

Now Open Nautilus:
Right click on /media/HD2
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - say yes even though it will not change anything

Done

---

### Post by g_lev on 2011-03-27
thank you for your reply. 
I did 1 - 5 as you told me but on 5 I got an error (can't remember what it was). and now I can't log in to Ubuntu. I get the ubuntu spalsh screen but once it's doen loading it reboots by itself over and over again. 
tried to log in as recovery > same deal. reboots over and over.
:cry:

---

### Post by g_lev on 2011-03-27
Here is what i get after running [boot_info_script]("http://ubuntuforums.org/showthread.php?t=1699437")
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   952,197,119   952,195,072  83 Linux
/dev/sda2         952,199,166   976,771,071    24,571,906   5 Extended
/dev/sda5         952,199,168   976,771,071    24,571,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c3fd7846-72b3-44fe-8904-f9251947b7b9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        89c0bebf-d152-4e87-b513-a24497937894   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA7B-5E84                              vfat       ž_žùž_ ž_ž_                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
set locale_dir=($root)/boot/grub/locale
set lang=he
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=c3fd7846-72b3-44fe-8904-f9251947b7b9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=c3fd7846-72b3-44fe-8904-f9251947b7b9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3fd7846-72b3-44fe-8904-f9251947b7b9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c3fd7846-72b3-44fe-8904-f9251947b7b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=89c0bebf-d152-4e87-b513-a24497937894 none            swap    sw              0       0
# my second partitotion
EA7B-5E84 /media/HD2 vfat utf8,umask=000,uid=1000 0 1

=================== sda1: Location of files loaded by Grub: ===================


 330.8GB: boot/grub/core.img
 172.0GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-28-generic-pae
 330.8GB: boot/vmlinuz-2.6.35-28-generic-pae
   1.2GB: initrd.img
 330.8GB: vmlinuz


---

### Post by Morbius1 on 2011-03-27
Your fstab say this:
>  EA7B-5E84 /media/HD2 vfat utf8,umask=000,uid=1000 0 1
It should say this:
>  [COLOR=Blue]**UUID=**[/COLOR]EA7B-5E84 /media/HD2 vfat utf8,umask=000,uid=1000 0 1

---

### Post by g_lev on 2011-03-27
> **Morbius1 said:**
> Your fstab say this:

It should say this:

thank you for your reply.
could you guide me how to fix this (since my computer will not log in but jest reboot all the time).
thank you.

---

### Post by Morbius1 on 2011-03-27
Use the InstallCD. Boot into the InstallCD, mount the partition that holds fstab, modify the file, save it and reboot the machine.

---

### Post by g_lev on 2011-03-28
working great!
thank you very very much for your king help.
=D> :guitar:

---

