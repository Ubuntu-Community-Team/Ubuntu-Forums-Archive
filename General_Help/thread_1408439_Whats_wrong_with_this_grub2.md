---
title: "Whats wrong with this grub2 ?"
date: 2010-02-16
forum: General Help
---

### Post by Ric95 on 2010-02-16
I'm having a hard time booting an install on parition 3.
sda2 = windoze7
sda3 = Gentoo Linux (ext3)
sda4 = xubuntu :)   (ext3)
Following this thread[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+configure]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+configure"), and using the xubuntu entry as example, I make this entry in my /etc/grub.d/40_custom entry:
> menuentry "Gentoo linux-zen" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set fc5ba4f6-10b2-4c0a-8871-05ca54bb162
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=fc5ba4f6-10b2-4c0a-8871-05ca54bb162d ro   quiet splash
	initrd	/boot/gentoo-kernel
}
I used "ls -l /dev/disk/by-uuid " to get the uuid for sda3.
When I run "update-grub" is says its finding linux on sda3 (among the others) and its there in /boot/grub/grub.cfg , but it doesn't show as an option during boot. 
What have I done wrong ?

---

### Post by oldfred on 2010-02-16
Are you sure you are editing the grub that is booting. This script tells a lot about the boot process.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Ric95 on 2010-02-16
Thanks oldfred. Thats a nice script to know about. I've run it and already noticed one problem. I forgot I formated sda3 as reiserfs. I'll change that first. 
Do you see anything else wrong?
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8aa629b1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       186,367       184,320   7 HPFS/NTFS
/dev/sda2             192,780   221,536,349   221,343,570   7 HPFS/NTFS
/dev/sda3         221,536,350   282,968,909    61,432,560  83 Linux
/dev/sda4         282,968,910 1,250,258,624   967,289,715  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A909B8B909B7C3F                       ntfs       SYSTEM                        
/dev/sda2        A44CEE044CEDD0DA                       ntfs       HP                            
/dev/sda3        fc5ba4f6-10b2-4c0a-8871-05ca54bb162d   reiserfs                                 
/dev/sda4        29b5d638-812b-4fd5-855b-21dacdafd875   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/LinuxOS           reiserfs   (rw)


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>			<mountpoint>	<type>		<opts>		<dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/sda4		/media		auto		defaults	0  0
/dev/sda3		/		ext3		noatime		0 1
#/dev/swap		none		swap		sw		0 0
/dev/cdrom		/mnt/cdrom	auto		noauto,ro	0 0
#/dev/fd0		/mnt/floppy	auto		noauto		0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm			/dev/shm	tmpfs		nodev,nosuid,noexec	0 0

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 29b5d638-812b-4fd5-855b-21dacdafd875
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 29b5d638-812b-4fd5-855b-21dacdafd875
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=29b5d638-812b-4fd5-855b-21dacdafd875 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}

### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0a909b8b909b7c3f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo linux-zen" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set fc5ba4f6-10b2-4c0a-8871-05ca54bb162d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=fc5ba4f6-10b2-4c0a-8871-05ca54bb162d ro   quiet splash
	initrd	/boot/zentoo6
}### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=29b5d638-812b-4fd5-855b-21dacdafd875 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2	/media/Windows	auto	defaults	0	0
/dev/sda3	/media/LinuxOS	reiserfs	defaults	0	0

=================== sda4: Location of files loaded by Grub: ===================


 301.8GB: boot/grub/core.img
 301.7GB: boot/grub/grub.cfg
 301.8GB: boot/initrd.img-2.6.31-14-generic
 301.8GB: boot/initrd.img-2.6.31-19-generic
 301.8GB: boot/vmlinuz-2.6.31-14-generic
 301.8GB: boot/vmlinuz-2.6.31-19-generic
 301.8GB: initrd.img
 301.8GB: initrd.img.old
 301.8GB: vmlinuz
 301.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```
* some xubuntu entries omitted to save space.

---

### Post by oldfred on 2010-02-16
I have not used reiserfs. but grub2 has a mod for that.

insmod ext2   should this be reiserfs ?? in your gentoo boot.

---

### Post by audiomick on 2010-02-16
> **oldfred said:**
> 
insmod ext2   should this be reiserfs ?? in your gentoo boot.
I have no idea either way, but I notice the grub.cfg entry for the Ubuntu on sda5, which is ext3, also has that.

---

### Post by Ric95 on 2010-02-16
> insmod ext2 should this be reiserfs ?? in your gentoo boot.
No, when I have two linux installs I only have grub installed on one. In gentoo I didn't even bother emerging it, as I use gentoo to tinker with until broken ( above all, know thyself ;) ). So I'll use the Xubuntu install for a stable base to boot from. 
I'm not sure if "reiserfs" is the correct notation (I couldn't fine any docs covering that), but a search has shown that grub2 may have a problem with that reiser. I'll try installing reiserfsprogs and get back to you.

---

### Post by Ric95 on 2010-02-17
I found the right format for grub2 here;
[http://ubuntuforums.org/showthread.php?p=8839847#post8839847]("http://ubuntuforums.org/showthread.php?p=8839847#post8839847")
so I wrote 40_custom this way:
```
echo "adding Gentoo" >&2
cat << EOF
menuentry "Gentoo linux-zen" {
set root=(hd0,3)
linux /boot/gentoo6 root=/dev/sda3
}
EOF
```
I still haven't seen a good explanation of grub2 syntax, but this works. 
Unfortunately, the kernel is expecting ext3, and has a problem with reiserfs (weird, I compiled reiser in-kernel...)
I love Gentoo. But this is why I like an OS that 'just works' on the next partition. When Gentoo is my only OS, I tend to spend more time working on it than using it. 

thanks guys.:guitar:

---

