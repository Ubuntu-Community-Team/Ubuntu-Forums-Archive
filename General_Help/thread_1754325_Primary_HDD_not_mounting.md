---
title: "Primary HDD not mounting"
date: 2011-05-09
forum: General Help
---

### Post by Flobbadob on 2011-05-09
Hoping someone can assist me here as I'm a relative newbie to Linux.

I have a Lenovo W500 laptop with clean install of Ubuntu 10.04 as the sole OS. Performed an update last night via the Update Manager and after rebooting, I was presented with a "Loading, please wait..." and it hung there.

I have a bootable USB with Ubuntu 10.04 and if I boot to this and launch Gparted, I can see that /dev/sda1 is not mounted.
I have visited a number of forums trying to find out what the issue is,  and believing the issue is with Grub, I've tried the following:

mount /dev/sda1 /mnt/
        grub-install --root-directory=/mnt /dev/sda        

Now, when I boot, it flashes "Grub loading" and then an "Error file not found" and then I'm presented with a double sized curser blinking in the top left corner and it hangs there.

Here's the disk info:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed7b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67831268

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15501    15624976+   b  W95 FAT32


Thanks in advance.

---

### Post by Quackers on 2011-05-09
Welcome to UF :-)
From the live desktop and after opening gparted, can you right-click on the sda1 partition and select check? If so, what happens?

---

### Post by Flobbadob on 2011-05-09
Hi Quackers

Here's the output:

[SIZE=1]GParted 0.5.1[/SIZE]
 [SIZE=1]Libparted 2.2[/SIZE]
    [SIZE=1]**Check and repair file system (ext4) on /dev/sda1**  00:00:14    ( SUCCESS ) [/SIZE]   [SIZE=1]    [/SIZE]    [SIZE=1] calibrate /dev/sda1  00:00:00    ( SUCCESS ) [/SIZE]   [SIZE=1]    [/SIZE]     [SIZE=1][I]path: /dev/sda1
start: 2048
end: 299808767
size: 299806720 (142.96 GiB)[/I][/SIZE]         [SIZE=1] check file system on /dev/sda1 for errors and (if possible) fix them  00:00:14    ( SUCCESS ) [/SIZE]   [SIZE=1]    [/SIZE]     [SIZE=1]***e2fsck -f -y -v /dev/sda1***[/SIZE]    [SIZE=1]    [/SIZE]     [SIZE=1][I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  202332 inodes used (2.16%)
     444 non-contiguous files (0.2%)
     152 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 176562/87
17989643 blocks used (48.00%)
       0 bad blocks
       7 large files

  146696 regular files
   24326 directories
      61 character device files
      26 block device files
       0 fifos
     575 links
   31188 symbolic links (25560 fast symbolic links)
      26 sockets
--------
  202898 files
[/I][/SIZE]       [SIZE=1][I]e2fsck 1.41.11 (14-Mar-2010)
[/I][/SIZE]            [SIZE=1] grow file system to fill the partition  00:00:00    ( SUCCESS ) [/SIZE]   [SIZE=1]    [/SIZE]     [SIZE=1]***resize2fs /dev/sda1***[/SIZE]    [SIZE=1]    [/SIZE]     [SIZE=1][I]resize2fs 1.41.11 (14-Mar-2010)
The filesystem is already 37475840 blocks long.  Nothing to do!

[/I][/SIZE]             [SIZE=1]========================================[/SIZE]

---

### Post by Flobbadob on 2011-05-10
I've also run the boot info script if this helps:



[CODE][                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
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
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,250,015    31,249,953   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        df71ad8d-ce18-4d48-b379-3457505cb5fd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        15DB-45CC                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=77a9c294-dfc3-4ed4-8cb2-6b4bb7c68fea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b9b5c335-e051-4c21-8857-4a862a671be3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 129.0GB: boot/grub/core.img
 116.1GB: boot/grub/grub.cfg
  93.1GB: boot/initrd.img-2.6.32-28-generic
 129.0GB: boot/vmlinuz-2.6.32-28-generic
  93.1GB: initrd.img
 129.0GB: vmlinuz/CODE]

---

### Post by Hedgehog1 on 2011-05-10
I am not sure that the "grub-install --root-directory" functionality works for the grub in 10.04.  Can we have you try it the ***'old fashioned***' way just to be safe?

Please boot off your **10.04** LiveCD/LiveUSB, select TRY
In the Terminal (Menu to: Applications >> Accessories >> Terminal), copy and paste these one at a time:
  
```
sudo mount /dev/sd**a1** /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
grub-install /dev/sd**a**
``````
update-grub
``````
exit
```                                  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```

***The Hedge***

:KS

p.s. your post above needs to end with **[**/CODE] instead of /CODE]

---

### Post by Quackers on 2011-05-10
There seems to be a discrepancy! :-)
You said in post 1 that you installed 10.04 as the sole OS but sda1 reports Debian 6.0 as the operating system
```
sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Debian GNU/Linux 6.0
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

Does Debian 6.0 use grub2 or grub legacy?

---

### Post by Flobbadob on 2011-05-10
Thanks for responding Hedgehog1. Followed your instructions and  performed all tasks. Now when I boot I get to the purple screen with  "Loading, please wait..." and it just hangs there.

Quackers - I have no idea about the Debian reference, but I installed Ubuntu 10.04 and told it to use the entire disk.

---

### Post by Hedgehog1 on 2011-05-10
> **Flobbadob said:**
> Thanks for responding Hedgehog1. Followed your instructions and  performed all tasks. Now when I boot I get to the purple screen with  "Loading, please wait..." and it just hangs there.

Quackers - I have no idea about the Debian reference, but I installed Ubuntu 10.04 and told it to use the entire disk.

Flobbadob,

I cannot help but think you are leading us all down the garden path here.

The purple screen is part of the 11.04 release, not the 10.04 release.

Are you sure you are not mixing your distros and creating a ***franken-buntu*** on us?


Are you in a situation where you can select one LiveCD, and install that completely?  I know you are using the LiveUSB right now, but I am concerned that your are not installing what you think you are installing from it...

***The Hedge***

:KS

---

