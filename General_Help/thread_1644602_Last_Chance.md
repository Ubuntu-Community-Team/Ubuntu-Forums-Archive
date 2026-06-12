---
title: "Last Chance"
date: 2010-12-13
forum: General Help
---

### Post by Flipper628 on 2010-12-13
Is there any way to retrieve the data saved under Ubuntu from Vista, before I unistall. I've tried the methods from the megathread to bring back my GRUB menu bt they have failed. The only way it appears I'll get Ubuntu back is to reinstall, but I'm going to lose anything I didn't have backed up. This will be the second time GRUB has brought me down entirely. I love Ubuntu, but this is giving me second thoughts...

---

### Post by Rubi1200 on 2010-12-13
Hi,
are you talking about a Wubi install?

What exactly did you try and what did not work?

Please be more specific.

Thanks.

---

### Post by Flipper628 on 2010-12-13
It was a wubi install. I've upgraded twice and am currently on 10.10. Grub failed to come up a few days ago so I'm stuck. I went to the GRUB megathread for solutions, but nothing worked. I do get a command prompt when I start up, but that's it.

---

### Post by Rubi1200 on 2010-12-13
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Read the information carefully please.

From what you are saying you have problem #2 and need solution#3, which uses solution #1.

If anything is unclear, let me know.

---

### Post by jim_deadlock on 2010-12-13
Before you do anything else, try this:

```
sudo rm /etc/X11/xorg.conf
```

10.10 doesn't need xorg.conf and on new upgrades it often results in the symptoms you're describing.

---

### Post by Flipper628 on 2010-12-13
> [SIZE=3]**Problem #2:**[/SIZE]

You have Wubi installed and are able to boot Windows normally. 

However, attempting to boot Ubuntu leads to a number of possible failures including, but not limited to, the following:

computer reboots without user interaction, a black screen with or  without any error messages, loadfont errors, file not found errors, and  the like.

These issues affect the following versions: 10.04, 10.04.1, and 10.10

The solutions for each version are somewhat different and will be noted next to the relevant solution.

> [SIZE=3]**Solution #2 (10.04 upgraded to 10.10):**[/SIZE]

If it is a 10.04 to 10.10 upgrade, boot into Windows make a backup of  the wubildr file and then copy the c:\ubuntu\winboot\wubildr file over  the c:\wubildr file.


This is what I ascertained. I followed the steps above for the solution. Only difference is that now I get a command prompt screen in grub instead of the computer simply rebooting...

Thanks for your help, BTW.

---

### Post by Flipper628 on 2010-12-13
Jim, I do that from a live cd, I presume?

---

### Post by Rubi1200 on 2010-12-13
Okay, the next step is to try this from the LiveCD/USB:

Try using solution #1, which involves editing the grub.cfg file.

Make sure you substitute the partition number with the correct partition for your particular setup.

edit: will all due respect to jim_deadlock, but I do not believe the solution suggested will work. This is a Wubi install and the symptoms you describe are outlined in the thread I linked to.

---

### Post by Flipper628 on 2010-12-13
how do I determine the correct partition number in vista? I'm in Computer Management, but not sure I see it there...

---

### Post by jwbrase on 2010-12-13
Frankly, if you've been using Wubi long enough to upgrade twice, you probably should be using an install in a dedicated partition rather than Wubi. Wubi is meant for testing Ubuntu out while leaving a simple means to uninstall if it doesn't work out. For several reasons, it's better to use a custom install if you're keeping Ubuntu on your machine permanently.

---

### Post by Flipper628 on 2010-12-13
> Frankly, if you've been using Wubi long enough to upgrade twice, you  probably should be using an install in a dedicated partition rather than  Wubi. Wubi is meant for testing Ubuntu out while leaving a simple means  to uninstall if it doesn't work out. For several reasons, it's better  to use a custom install if you're keeping Ubuntu on your machine  permanently.

Frankly, you're right. I do plan to keep it permanently. But there is some data I'd like to retreive first if possible. Then I can repartition and get it set up right.

---

### Post by jim_deadlock on 2010-12-13
You should be able to just run that command from the command prompt you say you're getting. This happened to me when I first upgraded to 10.10 - just run in and then reboot with your power button or whatever. Your problem may be more complex but it's worth a try.

---

### Post by Rubi1200 on 2010-12-13
> **jwbrase said:**
> Frankly, if you've been using Wubi long enough to upgrade twice, you probably should be using an install in a dedicated partition rather than Wubi. Wubi is meant for testing Ubuntu out while leaving a simple means to uninstall if it doesn't work out. For several reasons, it's better to use a custom install if you're keeping Ubuntu on your machine permanently.
Agreed, but the OP has asked for our help to fix the Wubi install and I, personally, would like to try that first.

@Flipper628
use a LiveCD and post the output of the following command from the terminal:
```
sudo fdisk -l
```

By the way, if all you want to do is recover your data, please read the thread again as there are 2 methods detailed as to how that can be done.

If you wish to continue trying to repair this install, follow the solutions I posted.

---

### Post by Flipper628 on 2010-12-13
I'll be a few minutes... boots slow from live cd.

---

### Post by WorMzy on 2010-12-13
If your root.disk is intact, then I believe you can mount it from the LiveCD, or from a partition install, you can extract the information from it that way.

```
sudo mount -t ext4 -o loop /media/Windows/ubuntu/disks/root.disk /mnt
```

---

### Post by Flipper628 on 2010-12-13
From the Grub command prompt: Error: Sudo unknown command

Gotta pick up this fight tomorrow, as it's time to go to work. I hope you helpful folks are around tomorrow! Thanks much!
--

---

### Post by Rubi1200 on 2010-12-13
And I have to go to bed!

Please read the thread I linked to, you should find all the answers there.

I will look in on this thread tomorrow morning and try to help further.

---

### Post by Flipper628 on 2010-12-14
Another day and back to the live disk...

---

### Post by Rubi1200 on 2010-12-14
Use the LiveCD to boot the computer, making sure BIOS is set to boot from the CD/DVD drive.

Choose to try NOT install Ubuntu.

Run this command (Applications > Accessories > Terminal)
```
sudo fdisk -l
```
lowercase L not 1

Post the results back here.

If you want to recover your data, try using [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

You can do that from within Windows if you want.

I assume you can still boot into Windows, right?

---

### Post by Flipper628 on 2010-12-14
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fd11db0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14594   115682304    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

---

### Post by Flipper628 on 2010-12-14
...and yes, I still have Windows just fine.

again, since thread jumped...

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fd11db0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14594   115682304    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

---

### Post by jim_deadlock on 2010-12-14
Have you deleted /etc/X11/xorg.conf yet?

---

### Post by Rubi1200 on 2010-12-14
> **Flipper628 said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fd11db0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27 [COLOR=Red] Unknown[/COLOR]
[COLOR=Red]Partition 1 does not end on cylinder boundary.[/COLOR]
/dev/sda2   *         192       14594   115682304    7  HPFS/NTFS
[COLOR=Red]Partition 2 does not end on cylinder boundary[/COLOR].
It seems you may have more than just a problem with your Wubi install:
see my highlighting above.

Please run the boot info script linked at the bottom of my post.

There are instructions included, and then post the results back here.

---

### Post by Flipper628 on 2010-12-14
I had also tried the command line the other poster suggested to try to mount the disk:

sudo mount -t ex4 -o loop /media/SQ004239V06/ubuntu/disks/root.disk /mnt

It returned an error:

mount: unknown filesystem type 'ex4'

---

### Post by Flipper628 on 2010-12-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   234,438,655   231,364,608   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6279c6a4-1e63-4fb2-8e99-205120129087   ext4                                     
/dev/sda1        00B8EA2FB8EA2340                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        0842EF0542EEF67A                       ntfs       SQ004239V06                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0842ef0542eef67a
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 0842ef0542eef67a
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0842ef0542eef67a
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

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   6.2GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.31-14-generic
  15.2GB: boot/initrd.img-2.6.32-24-generic
   7.6GB: boot/initrd.img-2.6.35-23-generic
   1.6GB: boot/vmlinuz-2.6.31-14-generic
  14.1GB: boot/vmlinuz-2.6.32-24-generic
    .8GB: boot/vmlinuz-2.6.35-23-generic
   7.6GB: initrd.img
  15.2GB: initrd.img.old
    .8GB: vmlinuz
  14.1GB: vmlinuz.old

---

### Post by Rubi1200 on 2010-12-14
> **Flipper628 said:**
> I had also tried the command line the other poster suggested to try to mount the disk:

sudo mount -t ex4 -o loop /media/SQ004239V06/ubuntu/disks/root.disk /mnt

It returned an error:

mount: unknown filesystem type 'ex4'
It did not work because it was a) the wrong syntax and parameters and b) you need to mount the partition first BEFORE trying to loop mount the root.disk

Here are the commands you can try:
```
sudo mkdir /media/win 
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
I am assuming sda2 is the Windows partition because the boot flag is on it.

This should mount the root.disk and you can try and access your files. 

The Ubuntu folders are located in /mnt if you mounted Wubi as   instructed earlier in the guide. Your HOME folder contents are found at   /mnt/home/<your_user_name>/

---

### Post by Flipper628 on 2010-12-14
> Have you deleted /etc/X11/xorg.conf yet?

The  command to do so failed.

---

### Post by Flipper628 on 2010-12-14
I've got it mounted! Found my files.

---

### Post by Rubi1200 on 2010-12-14
> **Flipper628 said:**
> I've got it mounted! Found my files.
Excellent!

First things first, save whatever is important before trying anything else.

---

### Post by bcbc on 2010-12-14
> **Rubi1200 said:**
> It did not work because it was a) the wrong syntax and parameters and b) you need to mount the partition first BEFORE trying to loop mount the root.disk

Here are the commands you can try:
```
sudo mkdir /media/win 
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
I am assuming sda2 is the Windows partition because the boot flag is on it.

This should mount the root.disk and you can try and access your files. 

The Ubuntu folders are located in /mnt if you mounted Wubi as   instructed earlier in the guide. Your HOME folder contents are found at   /mnt/home/<your_user_name>/

+1 to what Rubi1200 says. You should listen to Rubi1200. Deleting the xorg.conf is not going to do anything (good or bad).

So, now that you can mount your wubi root.disk, you can follow the instructions in Rub1200's thread to get your Wubi install booting again (problem #2, Solution #1)

And then if you want to migrate your wubi install to partition, just use the link provided in Rubi1200's thread (bottom of post #1).

If you just wanted to backup your data from the wubi install, there was a link in that thread to a tool called ext2read - that would have been the simplest.

---

### Post by Flipper628 on 2010-12-14
Going to back up that stuff, uninstall wubi and try to do a real install. Thanks so much for the help!

---

### Post by Rubi1200 on 2010-12-14
You are more than welcome :)

And, a big thanks to bcbc for jumping in and helping too :D

---

### Post by Flipper628 on 2010-12-14
Thanks, all...now on to stage two.

---

