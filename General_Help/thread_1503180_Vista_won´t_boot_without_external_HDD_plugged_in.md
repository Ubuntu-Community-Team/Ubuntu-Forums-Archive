---
title: "Vista won´t boot without external HDD plugged in"
date: 2010-06-06
forum: General Help
---

### Post by Manuwash on 2010-06-06
Hello fellas, second post regarding my linux adventures.

I been meaning to install some linux distro on my external hdd to enjoy the renowned desktop experience, so far I installed sabayon first but it wasn´t working very sharply and a friend of mine recommended me to just install ubuntu. Anyhow, since the first time I installed sabayon I could not boot vista when the external HDD is not plugged in. I get a grub rescue command prompt.

I don´t have a vista cd because my laptop came with the whole recovery function installed on a vista partition. I can boot that from the grub menu, from there I did a boot system restore, but I still get the same error.

I´d like to be able to boot vista without having the external HDD on of course, any help would be greatly appreciated.

---

### Post by Leppie on 2010-06-06
could you please download and run the boot info script and post the complete results?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Manuwash on 2010-06-06
Yeah well, problem is I am on vista right now, I installed ubuntu but I can´t boot it because of some graphic card issue. I can do anything you need but from windows. :sad:

---

### Post by confused57 on 2010-06-06
See darkod's post#4:
[http://ubuntuforums.org/showthread.php?t=1503124](http://ubuntuforums.org/showthread.php?t=1503124)

A little more detailed explanation:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by Manuwash on 2010-06-07
Well I tried installing lilo but now I am getting a bootmgr missing error, could it be because the instructions pointed to sda but I have windows vista on sda2 partition? I am at lost here, can´t seem to get back my normal vista boot for nothing :(

---

### Post by louieb on 2010-06-07
At this point - after you tried to fix the MBR with lilo - it should have worked - really need the output of the script Leppie asked for in post #2. 

It does not have to be run from Ubuntu - almost any Linux live CD will do the job. Unfortunately  - as far as I know - there is nothing you can run in Vista that will give the same information.

Or take a look at [Vista Recovery Disc — NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and [Restore XP,Vista or GRUB Bootloader]("http://ubuntuforums.org/showthread.php?t=740221")

---

### Post by Manuwash on 2010-06-07
There you go, those are the results ;)


>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29700d06

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2          20,973,568    89,192,447    68,218,880   7 HPFS/NTFS
/dev/sda3    *     89,192,448   156,299,263    67,106,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001910c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,728,574   209,728,512  83 Linux
/dev/sdb2         209,728,575   213,937,604     4,209,030  82 Linux swap / Solaris
/dev/sdb3         213,938,176   976,771,071   762,832,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA6852276851F315                       ntfs       RECOVERY                      
/dev/sda2        A66854136853E09B                       ntfs                                     
/dev/sda3        8A42C52342C514BB                       ntfs                                     
/dev/sdb1        86fa2ba0-e1e7-4e2f-86f6-f480346e5abd   ext4                                     
/dev/sdb2        b4730525-104b-4cbc-abde-7dcfc1775dba   swap                                     
/dev/sdb3        629C930E9C92DC3B                       ntfs       almacen                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /media/almacen           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/8A42C52342C514BB  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 86fa2ba0-e1e7-4e2f-86f6-f480346e5abd
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 86fa2ba0-e1e7-4e2f-86f6-f480346e5abd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=86fa2ba0-e1e7-4e2f-86f6-f480346e5abd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 86fa2ba0-e1e7-4e2f-86f6-f480346e5abd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=86fa2ba0-e1e7-4e2f-86f6-f480346e5abd ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aa6852276851f315
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set a66854136853e09b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=86fa2ba0-e1e7-4e2f-86f6-f480346e5abd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=b4730525-104b-4cbc-abde-7dcfc1775dba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .1GB: vmlinuz

---

### Post by oldfred on 2010-06-07
For windows to boot the boot flag has to be on the partition you want to boot to make it the active partition. Then the boot loader should find the correct partition to boot.

set boot flag on for sda2 (off for others)
sudo sfdisk -A2 /dev/sda

You can use gparted, right click on partition and manage flags or use Disk Utility in System, adminstration.

---

### Post by louieb on 2010-06-07
[LEFT]Which Vista entry works the 1st or 2nd? 
The 1st loads to sda1 , the 2nd loads to sda2.  
[/LEFT]
 
The command 
```
sudo lilo -M /dev/sda mbr
```
uses the boot flag to tell which partition to chainload from the mbr. Right now its on sda3 

you can use GParted  or the disk utility move the boot flag. - it need to be on the correct partition before running the **sudo lilo -M /dev/sda mbr **command. my guess is the boot flag s/b on sda2.  XP and Vista also expect the boot flag to be on the partition they boot from. -

---

### Post by Manuwash on 2010-06-08
Well right now I have ubuntu 9.10 installed and it&#347; grub is wholly installed on my external drive ( or at least thats what I specified on installation). So basically I can forget about ubuntu booting from the external hdd because it should be all set.

Now what you guys are saying is that I should change FROM windows, the boot flag to sda, meaning the C:/ drive in vista, so when I unplug the external HDD it will boot from there, and then get the Lilo boot mgr going, is that correct?

---

### Post by Leppie on 2010-06-08
> **Manuwash said:**
> Now what you guys are saying is that I should change FROM windows, the boot flag to sda, meaning the C:/ drive in vista, so when I unplug the external HDD it will boot from there, and then get the Lilo boot mgr going, is that correct?
you have to reset the mbr to factory defaults, like that it will search for the active partition on the drive. using the command as [louieb]("http://ubuntuforums.org/member.php?u=120176") indicated:
```
sudo lilo -M /dev/sda mbr
```will set the mbr to defaults. you may have to install lilo before being able to use it though:
```
sudo apt-get install lilo
```

---

