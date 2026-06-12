---
title: "how to install Grub 2"
date: 2010-08-04
forum: General Help
---

### Post by trappleye on 2010-08-04
About two months ago I got a free computer with no operating system installed. The first operating system I installed is Ubuntu 10.4. Last week I purchased windows 7 and just installed it today which modified my MBR and I can only boot to windows. I didn't have grub installed before so I have nothing to restore from. I have linux on /dev/sda1 and windows on /dev/sda2 followed by my swap. 

I've searched through these forms ([https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)) but can only find help for restoring grub 2 if you've had it installed previously.

I've run "sudo grub-install --root-directory=/mnt/ /dev/sda1", but it failed with the following: 

/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

I don't think I want to use --force, I'd rather install to MBR, how do I do that?

---

### Post by Rubi1200 on 2010-08-04
> **trappleye said:**
> About two months ago I got a free computer with no operating system installed. The first operating system I installed is Ubuntu 10.4. Last week I purchased windows 7 and just installed it today which modified my MBR and I can only boot to windows. I didn't have grub installed before so I have nothing to restore from. I have linux on /dev/sda1 and windows on /dev/sda2 followed by my swap. 
 
I've searched through these forms ([https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)) but can only find help for restoring grub 2 if you've had it installed previously.
 
I've run "sudo grub-install --root-directory=/mnt/ /dev/sda1", but it failed with the following: 
 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
 
I don't think I want to use --force, I'd rather install to MBR, how do I do that?
You would normally install GRUB to sda not sda1 as you tried; hence the error messages.
 
However, just to make sure now what is going on, please boot the computer with the Ubuntu CD choosing to try not install.
 
Then click on the link at the bottom of my post and follow the instructions there.
 
Post the results back here and we will try and help you resolve this.

---

### Post by trappleye on 2010-08-04
Thanks, here are the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    40,965,749    40,963,702  83 Linux
/dev/sda2    *     40,965,750   299,724,704   258,758,955   7 HPFS/NTFS
/dev/sda3         299,732,990   312,498,175    12,765,186   5 Extended
/dev/sda5         299,732,992   312,498,175    12,765,184  82 Linux swap / Solaris


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
/dev/sda1        2e2bd1d6-64d1-4f23-999a-8b706ea11b3c   ext4                                     
/dev/sda2        5845352B55CCA09A                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        24760811-f1be-4dc1-8506-d0ef956974b1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4B8A-05EA                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
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
search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e2bd1d6-64d1-4f23-999a-8b706ea11b3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=2e2bd1d6-64d1-4f23-999a-8b706ea11b3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24760811-f1be-4dc1-8506-d0ef956974b1 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.32-21-generic
   1.1GB: boot/initrd.img-2.6.32-23-generic
   1.1GB: boot/initrd.img-2.6.32-24-generic
    .9GB: boot/vmlinuz-2.6.32-21-generic
    .9GB: boot/vmlinuz-2.6.32-23-generic
    .7GB: boot/vmlinuz-2.6.32-24-generic
   1.1GB: initrd.img
   1.1GB: initrd.img.old
    .7GB: vmlinuz
    .9GB: vmlinuz.old

---

### Post by trappleye on 2010-08-04
Yeah, I had my 16GB USB drive plugged in at the same time.

---

### Post by Rubi1200 on 2010-08-04
Thanks.
 
The easiest thing to do now is use the LiveCD again and follow the guide you linked to in your first post.
 
But, this time what you want to do is this:
 
```
 
sudo mount /dev/sd**a1** /mnt

```
 
and then
 
```
 
sudo grub-install --root-directory=/mnt/ /dev/sda

```
 
Then reboot and do
 
```
 
sudo update-grub

```
 
GRUB should recognize Windows and you will be able to dual-boot without any issues.
 
If you run into any difficulties, let us know.

---

### Post by theozzlives on 2010-08-04
Boot the live CD and go to terminal.
```
sudo -i
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by trappleye on 2010-08-04
That did the trick, thanks.

---

### Post by karhtibala on 2010-08-04
thanks for your info to install Grub2.it is so clear and simple to understand.its great to know and working too good.it saves all our time.i will surely try it.










----------------------------------------------
[URL="http://www.*****************.com"]
[/URL][Budget Hotels Kanyakumari]("http://www.*****************.com")[URL="http://www.*****************.com"]
[/URL]

---

