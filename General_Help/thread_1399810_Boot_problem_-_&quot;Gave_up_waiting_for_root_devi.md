---
title: "Boot problem - &quot;Gave up waiting for root device.&quot;, (initramfs)"
date: 2010-02-06
forum: General Help
---

### Post by joaqal on 2010-02-06
Hello:

I installed Ubuntu 9.10 and things were working fine. Today however my laptop will not boot. It shows me the GNU GRUB screen asking me to choose between any kernel version 2.6.31-[14, 16, 17, 19]-generic both normal versions and "recovery mode" versions (before it chose one of these options automatically after a few seconds). 

If I choose the non-recovery mode kernels (any version), it eventually gets stuck in a black screen. After pressing any key, I get this message:

------------
Gave up waiting for root device. Common problems:
... ...(shows a list of three common problems)
ALERT! /dev/disk/by-uuid/(a long id) does not exist. Dropping to a shell!
BusyBox v1.13.3 ...
(initramfs)
------------

If I try one of the  "recovery mode" kernel versions (any and all), I get the same message but the last few lines printed out before this same message are:

-------------
Begin: Waitin for root file system... ...
Done.
Gave up waiting for root device. (etc.)
-----------

Thanks in advance for your help.

---

### Post by drs305 on 2010-02-06
joaqal,

First, welcome to Ubuntu and the Ubuntu forums.  :-)

Please boot the LiveCD and run the boot info script from the following link. Make sure to post the results inside "code" brackets by clicking the # icon in the post's menu.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If you feel the need to experiment, you can try editing the menu entry in the Grub 2 menu. It may work and it wouldn't take long to try:

1. Highlight an old, working kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY"  with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.

If it doesn't work, post the script results. If it does, run "sudo update-grub" and then post the results if it doesn't reboot properly.

Note: There are more detailed ways of trying to get to a bootable system from the Grub 2 menu. If you want to try them, refer to:
[https://help.ubuntu.com/community/Grub2#Command Line Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by joaqal on 2010-02-06
Hi dsr305: 

Thanks! It is booting correctly now. I followed your advice precisely and editted th .16 kernel from the GNU GRUB boot menu. After updating grub, I tried kernels .16 and .19 and they both worked.

For others who might be having the same problem: sdXY for me was "sda7" (so the X was a letter for me) and I could figure this out from the script output "RESULTS.txt" (it is one of the Linux partitions) and by mounting the available drives from the "places" menu from inside LiveCD (to see which partition is data and not an OS). After mounting, the drives had a long id, and the mapping from id to "sda7" was found in RESULTS.txt.

Thanks again!

---

### Post by Danb5854 on 2010-03-03
I tried as you had listed and it worked after i noticed i had made the edit to the .19 kernel the first time instead of the .14...

---

### Post by mphatyonah on 2010-03-05
I am having the same problem. This is the second time that I have had boot problems after sudden shut down. Once from, I think a display freeze and one other time from a power failure without power backup. I have since learned about REISUB for an app. freeze.
 Anyway, is this problem because I have the root and home partition format as ext2? If that is the problem is there a way for me to make new partitions as ext3, then move the data to the new ext3 partitions?
 But first I need to rescue my root partition. Working......

---

### Post by mphatyonah on 2010-03-05
I hope someone can help me. Gparted partition information does not show a label or UUID for my root partition. I am really in the weeds. Right now I am afraid to do anything without knowing what I am doing. I use this desktop PC for my business. I do have a backup from a couple of days ago of all my data, so I am OK with that respect. I do not relish the idea of having to rebuild my entire system.:confused:[-o<

---

### Post by jthirt on 2010-03-05
Excellent! I love this community! :D

Thanks a lot for this. 

It took me some effort to convince my wife that her mum (who's not computer litterate at all, even barely litterate) should use ubuntu (UNR) over Windows 7 (on her new Samsung R730) for simplicity and after I completed the tuning for her the boot failed so I was on the grill again ... 

But here is the solution to the issue. I wish I understand where is the issue itself as I will not always be there to fix it.

I my case, I used ext4. So I don't thing this is the problem. 

Anyone knows what's triggering this problem?

JT

---

### Post by nahanchi on 2010-03-07
Thanks a lot drs305! You are a life saver!!

---

### Post by ChAoS.ct on 2010-05-10
I had the same very problem and your method worked flawlessly! It seems to me that something was wrong with a recent update (in my case I didn't update to lucid).

Thanks drs305!

---

### Post by lohith on 2010-10-16
Hi drs305,
I was very happy to see this post and your perfect solution. In the hope that it would work for me, I burned the latest 10.10 Ubuntu and tried to boot from this CD but it does not boot! My problem is explained here [http://newyork.ubuntuforums.org/showthread.php?p=9980525&posted=1#post9980525](http://newyork.ubuntuforums.org/showthread.php?p=9980525&posted=1#post9980525)
There is this '/sbin/modprobe -bv pci:vxxxxx' unexpected exit with status 0x0009 error before it says it gave up on root device.
I have no clue what's going on.
I remember I set the waiting time to select kernel to zero so it boots directly into the first choice with no wait. Do you think the system is booting into old kernel instead of new? How to change this wait time now at the initranfs prompt?
I would really appreciate your help.
Thanks in advance!

---

### Post by drs305 on 2010-10-16
> **lohith said:**
> Hi drs305,
I was very happy to see this post and your perfect solution. In the hope that it would work for me, I burned the latest 10.10 Ubuntu and tried to boot from this CD but it does not boot! My problem is explained here [http://newyork.ubuntuforums.org/showthread.php?p=9980525&posted=1#post9980525](http://newyork.ubuntuforums.org/showthread.php?p=9980525&posted=1#post9980525)
There is this '/sbin/modprobe -bv pci:vxxxxx' unexpected exit with status 0x0009 error before it says it gave up on root device.
I have no clue what's going on.
I remember I set the waiting time to select kernel to zero so it boots directly into the first choice with no wait. Do you think the system is booting into old kernel instead of new? How to change this wait time now at the initranfs prompt?
I would really appreciate your help.
Thanks in advance!

I don't know if this is a grub problem or if it is a problem after grub passes control to the kernel. I could be a bad UUID or root= setting but it also may be a failure with the kernel.

Please run the boot info script from the LiveCD and post the contents of RESULTS.txt. Perhaps we can find something that needs to be fixed. It will show us what the default kernel is and how long it's waiting. 

The script and instructions are found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Knowsnothing on 2010-11-02
I've got something similar.  I've tried your advice.  But to no avail:  [http://ubuntuforums.org/showthread.php?t=1611631](http://ubuntuforums.org/showthread.php?t=1611631)

---

### Post by drs305 on 2010-11-02
There are a few of these that have popped up in the past week, for now with no solution. Here is another one:  [http://ubuntuforums.org/showthread.php?t=1611213]("http://ubuntuforums.org/showthread.php?t=1611213")

I'm subscribed to that thread as well so if a solution is found I'll pass it on here.

---

### Post by kminney on 2010-11-04
Hi,
 Had the same problrm with 10.10. Used 9.1 live cd to get back in. I can't use my files or transfer the dics image to an external hard drive.
I'd just as soon start over by clearing the disc and reinstalling 9.1 if it's easier, if I could save my files and settings. 
Thanks in advance.
I did what was suggested and here is the record.
Kevin



```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x791f459c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,232,394    75,232,332  83 Linux
/dev/sda2          75,232,395    78,156,224     2,923,830   5 Extended
/dev/sda5          75,232,458    78,156,224     2,923,767  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa955cbf4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        d608374b-7931-4832-8788-593830b560ca   ext4                                     
/dev/sda5        e799e3d5-5318-4169-a561-19af3148cfe6   swap                                     
/dev/sdb1                                               vfat       VERBATIM                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/VERBATIM          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/d608374b-7931-4832-8788-593830b560ca ext4       (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d608374b-7931-4832-8788-593830b560ca ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d608374b-7931-4832-8788-593830b560ca ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d608374b-7931-4832-8788-593830b560ca
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d608374b-7931-4832-8788-593830b560ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e799e3d5-5318-4169-a561-19af3148cfe6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.7GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.31-14-generic.before_restore_2010-09-04_15.05.02.479476
  12.6GB: boot/initrd.img-2.6.35-22-generic
   1.5GB: boot/vmlinuz-2.6.35-22-generic
  12.6GB: initrd.img
   1.5GB: vmlinuz
```

---

### Post by drs305 on 2010-11-04
kminney,

During boot, hold down the SHIFT key to display the Grub2 menu. If it appears, highlight the first entry and press "e" to enter the edit mode.

Use the cursor to move to the start of the "search" line and hold the DEL key and remove the entire line. Then cursor to the "linux" and "initrd" lines and change them so they look like below.
> 
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
linux /boot/vmlinuz-2.6.35-22-generic root=[COLOR="Red"]/dev/sda1[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic

Once it looks like the above, press CTRL-x to boot. Let us know if it boots.  (I'll be off for a bit)

---

### Post by kminney on 2010-11-04
Unfortunately it says no kernal at that point.

---

### Post by drs305 on 2010-11-04
> **kminney said:**
> Unfortunately it says no kernal at that point.


Okay, try booting from the grub prompt:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

```

---

### Post by Romala on 2010-11-05
Dear friends,
there's the same problem on my PC as in the posted thread. I've tried to update Ubuntu from Live CD but update process has said> find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  
Grub works, but "rootdelay=90" and "root=/dev/sda1" in Grub menu have not helped.
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hdc and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/hdd
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

hdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

hdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

hdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, hdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hdc ___________________ _____________________________________________________

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hdc1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: hdd ___________________ _____________________________________________________

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hdd1              16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/hdd5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   961,570,574   961,570,512  83 Linux
/dev/sda2         961,570,575   976,768,064    15,197,490   5 Extended
/dev/sda5         961,570,638   976,768,064    15,197,427  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/evms/hdc1                                          ntfs                                     
/dev/evms/hdd5                                          ntfs                                     
/dev/evms/sda1   667da5eb-f73d-4df0-8818-890edab5c8b7   ext3                                     
/dev/evms/sda5   a453daf0-813e-4833-bda8-e23297071343   swap                                     
/dev/hda                                                iso9660                                  
/dev/hdc1                                               ntfs                                     
/dev/hdd5                                               ntfs                                     
/dev/sda1        667da5eb-f73d-4df0-8818-890edab5c8b7   ext3                                     
/dev/sda5        a453daf0-813e-4833-bda8-e23297071343   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

unionfs          /                        unionfs    (rw)
/dev/sda1        /mnt                     ext3       (rw)


================================ hdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 11111


================================ hdc1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 11111


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-24-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-386

title		Ubuntu 8.04.2, kernel 2.6.24-24-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
initrd		/boot/initrd.img-2.6.24-24-386

# title		Ubuntu 8.04.2, kernel 2.6.24-23-386
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-23-386

# title		Ubuntu 8.04.2, kernel 2.6.24-23-386 (recovery mode)
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
# initrd		/boot/initrd.img-2.6.24-23-386

# title		Ubuntu 8.04.2, kernel 2.6.24-22-386
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.24-22-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-22-386

# title		Ubuntu 8.04.2, kernel 2.6.24-22-386 (recovery mode)
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.24-22-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
# initrd		/boot/initrd.img-2.6.24-22-386

#title		Ubuntu 8.04.2, kernel 2.6.24-21-386
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-386

#title		Ubuntu 8.04.2, kernel 2.6.24-21-386 (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
#initrd		/boot/initrd.img-2.6.24-21-386

#title		Ubuntu 8.04.2, kernel 2.6.24-19-386
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-386

#title		Ubuntu 8.04.2, kernel 2.6.24-19-386 (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
#initrd		/boot/initrd.img-2.6.24-19-386

#title		Ubuntu 8.04.2, kernel 2.6.15-52-386
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-52-386

#title		Ubuntu 8.04.2, kernel 2.6.15-52-386 (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 ro single
#initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.04.2, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=667da5eb-f73d-4df0-8818-890edab5c8b7 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy                
UUID=a453daf0-813e-4833-bda8-e23297071343 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb5 -- converted during upgrade to edgy 
UUID=A8FCDB1BFCDAE29C /mnt/win ntfs-3g auto,gid=1001,umask=0,locale=ru_RU.utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 167.1GB: boot/grub/menu.lst
 167.2GB: boot/grub/stage2
 167.1GB: boot/initrd.img-2.6.15-52-386
 167.3GB: boot/initrd.img-2.6.24-24-386
 167.1GB: boot/initrd.img-2.6.24-24-386.bak
 167.3GB: boot/initrd.img-2.6.32-25-386
 167.3GB: boot/initrd.img-2.6.32-25-generic
 167.1GB: boot/vmlinuz-2.6.15-52-386
 167.2GB: boot/vmlinuz-2.6.24-24-386
 167.2GB: boot/vmlinuz-2.6.32-25-386
 167.2GB: boot/vmlinuz-2.6.32-25-generic
 167.3GB: initrd.img
 167.3GB: initrd.img.old
 167.2GB: vmlinuz
 167.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/hdd

00000000  33 ca 8e da bc 0a 7c fb  50 0f 50 1f fc be 1b 7e  |3.....|.P.P....~|
00000010  bf 1b 06 5a 57 bb e5 0b  f3 ae cb bf be 0f b1 0e  |...ZW...........|
00000020  38 6e 00 7e 09 7f 13 8b  c5 1a e2 fe cd 1a 8b ff  |8n.~............|
00000030  83 ce 10 4b 74 1b 38 2e  74 fe a0 bf 07 be 07 8b  |...Kt.8.t.......|
00000040  f0 ae 3c 0a 74 fe bb 0f  00 be 0e cf 10 eb f2 8a  |..<.t...........|
00000050  4e 1a e8 4e 00 7b 2a fe  46 1a 80 7e 04 0b 74 0b  |N..N.{*.F..~..t.|
00000060  80 7e 04 0e 74 0f a0 be  07 7f d2 8a 46 0a 06 8b  |.~..t.......F...|
00000070  46 0a 06 8b 56 0a 00 ea  21 0a 73 0f a0 be 07 eb  |F...V...!.s.....|
00000080  bc 8b 3e fe 7d 5f aa 7e  0b 8a 7e 1a 00 7e c8 aa  |..>.}_.~..~..~..|
00000090  b7 0f eb ab 8b fe 1e 5f  8b ff cb bf 05 0a 8a 5e  |......._.......^|
000000a0  00 be 08 cf 13 7a 23 8a  c1 2e 3f 9a 8a de 8a fe  |.....z#...?.....|
000000b0  43 ff e3 8b d1 8e d6 bb  06 da ee 4a f7 ea 39 5e  |C..........J..9^|
000000c0  0a 7f 23 7a 05 3b 46 0a  73 1e b8 0b 02 bb 00 7e  |..#z.;F.s......~|
000000d0  8b 4e 02 8b 56 0a cd 1b  73 5b 4f 7e 4e 3a e4 8a  |.N..V...s[O~N:..|
000000e0  56 0a cd 1b eb ee 8a 5e  00 6a bb aa 55 be 41 cf  |V......^.j..U.A.|
000000f0  13 7a 36 8b fb 5f aa 7f  30 fe c1 0b 74 2b 61 6a  |.z6.._..0...t+aj|
00000100  6a 0a 6a 0a ff 7e 0a ff  76 0a 6a 0a 68 0a 7c 6a  |j.j..~..v.j.h.|j|
00000110  01 6a 10 be 42 8b f4 cf  13 6b 61 7b 0e 4f 74 0b  |.j..B....ka{.Ot.|
00000120  32 ee 8a 5e 00 cf 13 eb  d6 6b f9 cb 49 6e 76 6b  |2..^.....k..Invk|
00000130  6c 6b 64 2a 70 6b 72 7e  69 7e 69 6f 6e 2a 74 6b  |lkd*pkr~i~ion*tk|
00000140  62 6e 65 0a 45 7a 72 6f  72 2a 6c 6f 61 6e 69 6e  |bne.Ezror*loanin|
00000150  67 2a 6f 7a 65 7a 61 7e  69 6e 67 2a 73 7b 73 7e  |g*ozeza~ing*s{s~|
00000160  65 6f 00 4f 69 7b 73 6b  6e 6f 20 6f 70 6f 72 6b  |eo.Oi{skno opork|
00000170  74 6b 6e 6f 20 7b 79 7b  74 6f 6d 0a 00 0a 00 0a  |tkno {y{tom.....|
00000180  00 0a 00 0a 00 0a 00 0a  00 0a 00 0a 00 0a 00 0a  |................|
00000190  00 0a 00 0a 00 0a 00 0a  00 0a 00 0a 00 0a 00 0a  |................|
000001a0  00 0a 00 0a 00 0a 00 0a  00 0a 00 0a 00 0a 00 0a  |................|
000001b0  00 0a 00 0a 00 2e 44 6b  c2 8e 60 ff 00 0a 00 00  |......Dk..`.....|
000001c0  01 01 0f fe ff ff c1 3e  00 00 80 0d 38 3a 00 00  |.......>....8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on hdd1

00000000  10 80 10 80 10 80 10 80  10 80 10 80 10 80 10 80  |................|
*
000001b0  10 80 10 80 10 80 10 80  10 80 10 80 10 80 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 41 0d 38 3a 00 00  |......?...A.8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

```
Appreciate your help, thank you

---

### Post by kminney on 2010-11-05
Hi, Tried you last suggestion and it went into kernal panic.

---

### Post by kminney on 2010-11-05
How can I get into my files to transfer them and do a reinstall?
I am running my computer of the live 9.1 cd and the os that is on there is 10.10.
Thanks,
K

---

### Post by Romala on 2010-11-05
liveCD
```

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="667da5eb-f73d-4df0-8818-890edab5c8b7" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="a453daf0-813e-4833-bda8-e23297071343" TYPE="swap"
/dev/evms/sda1: UUID="667da5eb-f73d-4df0-8818-890edab5c8b7" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/sda5: UUID="a453daf0-813e-4833-bda8-e23297071343" TYPE="swap"

```

---

### Post by drs305 on 2010-11-05
> **kminney said:**
> How can I get into my files to transfer them and do a reinstall?
I am running my computer of the live 9.1 cd and the os that is on there is 10.10.
Thanks,
K

From the LiveCD Desktop, mount your real Ubuntu installation, then use a file browser to copy transfer any files you want to save. Make sure you move them to a partition or external drive that won't be formatted/destroyed when you reinstall.

This assumes the files you want are on your Ubuntu partition and that it is on sda1. If your files are on a different partition, change *sda1* to the appropriate value.

```
sudo mount /dev/sda1 /mnt
nautilus /mnt
```

---

### Post by drs305 on 2010-11-05
Romala,

Which version of Ubuntu do you have installed on your computer? When you ran the update it was trying to download files from the Dapper repository.

If you are trying to update the 10.04 files on your real installation, you must boot the LiveCD and then use the *chroot* procedure to get into your Ubuntu install. This is the only way you will be able to update your real files.

If you are trying to do this from a Dapper CD, I don't know if even the chroot will work. It would be best to get a 10.04 CD, chroot into your Ubuntu partition, and install Grub2. The procedures for chrooting and installing Grub2 can be found here:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by woodmaster on 2010-11-07
same problems here...I can boot if I use the "e" and change to /dev/sda2, but the UUID matches perfectly.  A bit stumped why it does that?  Also, how can I change that permanently. I edited boot/grub/grub.cfg to make all the headers goto /dev/sda2, but when I run update-grub, they revert!  Thanks...

---

### Post by Romala on 2010-11-08
**drs305**, 
all works, thank you. Probably, it was 8.04 to 10.04 have not upgraded properly. 
But i have to make another steps in upgrading to Grub2: 
**1.** boot LiveCD 10.04, try to find a linux drive
```

sudo fdisk -l

```
(it occurs */dev/sdc1* - differing folder from such as before, in LiveCD 6.06)
mount it and update  
```

mkdir ~/mnt
sudo mount /dev/sdc1 ~/mnt
cd ~/mnt
sudo apt-get update
sudo apt-get upgrade
sudo umount /dev/sdc1

```
**2. ** reboot PC, change in Grub a string for booting on *kernel ... root=/dev/sdc1*, and Ubuntu 10.04 boots at last.
**3. ** steps "Why Chroot?" [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
**4. ** reboots PC. The first string in Grub is asking to try Grub 2 and save it. I' ve selected it, but it answered *"Filesystem type is unknown, type is ... "*. I've deleted string *root (hd2,0)* , and Grub2 have been loaded successfully. 
**5. ** boots Ubuntu, open a terminal and
```

sudo upgrade-from-grub-legacy

```
, select */dev/sdc* for Grub2.
**6. ** reboots PC.
**7. ** Grub 1.98 and Ubuntu 10.04 work.

---

### Post by AAlvares on 2011-02-11
Hi I have had this problem as well in ubuntu 10.10 with a dual boot
black screen, then it gave up waiting on root device. help?

I ran the script and have RESULTS.txt but I don't know what it should look like.
anyone?

---

### Post by farna on 2011-02-22
I tried editing grub as suggested in post #2. No dice. I've been fighting with this problem for a couple weeks now! I'm relatively new to Linux, but do know to search for solutions. I've tried the Linux Mint forums (I'm using Mint 10, which is Ubuntu 10.10 based) and Linux Questions. Several "solutions", but none work. 

Some solutions suggest booting from the Live CD (which boots and works fine!) and mounting the drive manually, but when I try that I get a "device doesn't exist" error. The first time I got that I used gparted to look at the drive, and it finds it fine, just says there is no boot info on it. 

I have an Athlon XP 2400+ processor, Radeon 8200 video card, 1 GB RAM, on an old FIC AZ31 motherboard (VIA KT133 chipset, VT 8363 North Bridge and 686A Super South), 120GB Maxtor 5400 rpm IDE hard drive.  Mint 7 (Ubuntu 9.04) boots and installs flawlessly on this system. I'd really like a solution! This is my "shop" experimenting machine. If I can't get Mint 10 (Ubuntu 10.10) to run on it I'm not about to attempt and upgrade on my main machine!



Here is the output from Bootinfo Script: 
```


Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #1 for (,msdos1)/boot/grub.
=> Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

File system:
Boot sector type: Unknown
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sda5: _________________________________________________________________________

File system:
Boot sector type: Unknown
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 239,933,439 239,931,392 83 Linux
/dev/sda2 239,935,486 240,119,807 184,322 5 Extended
/dev/sda5 239,935,488 240,119,807 184,320 82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 517 MB, 517521408 bytes
128 heads, 32 sectors/track, 246 cylinders, total 1010784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdc1 * 32 1,010,782 1,010,751 4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda: PTTYPE="dos"
/dev/sdc1 vfat LEXAR MEDIA
/dev/sdc: PTTYPE="dos"
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr1 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sdc1  /media/LEXAR MEDIA vfat  (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda5


Unknown BootLoader on sdc1

00000000 eb 3c 90 4d 53 57 49 4e 34 2e 31 00 02 10 01 00 |.<.MSWIN4.1.....|
00000010 02 00 02 00 00 f8 f7 00 20 00 80 00 20 00 00 00 |........ ... ...|
00000020 3f 6c 0f 00 80 00 29 00 00 00 00 4e 4f 20 4e 41 |?l....)....NO NA|
00000030 4d 45 20 20 20 20 46 41 54 31 36 20 20 20 33 c9 |ME FAT16 3.|
00000040 8e d1 bc fc 7b 16 07 bd 78 00 c5 76 00 1e 56 16 |....{...x..v..V.|
00000050 55 bf 22 05 89 7e 00 89 4e 02 b1 0b fc f3 a4 06 |U."..~..N.......|
00000060 1f bd 00 7c c6 45 fe 0f 38 4e 24 7d 20 8b c1 99 |...|.E..8N$} ...|
00000070 e8 7e 01 83 eb 3a 66 a1 1c 7c 66 3b 07 8a 57 fc |.~...:f..|f;..W.|
00000080 75 06 80 ca 02 88 56 02 80 c3 10 73 ed 33 c9 fe |u.....V....s.3..|
00000090 06 d8 7d 8a 46 10 98 f7 66 16 03 46 1c 13 56 1e |..}.F...f..F..V.|
000000a0 03 46 0e 13 d1 8b 76 11 60 89 46 fc 89 56 fe b8 |.F....v.`.F..V..|
000000b0 20 00 f7 e6 8b 5e 0b 03 c3 48 f7 f3 01 46 fc 11 | ....^...H...F..|
000000c0 4e fe 61 bf 00 07 e8 28 01 72 3e 38 2d 74 17 60 |N.a....(.r>8-t.`|
000000d0 b1 0b be d8 7d f3 a6 61 74 3d 4e 74 09 83 c7 20 |....}..at=Nt... |
000000e0 3b fb 72 e7 eb dd fe 0e d8 7d 7b a7 be 7f 7d ac |;.r......}{...}.|
000000f0 98 03 f0 ac 98 40 74 0c 48 74 13 b4 0e bb 07 00 [EMAIL="%7C.....@t.Ht"]|.....@t.Ht[/EMAIL]......|
00000100 cd 10 eb ef be 82 7d eb e6 be 80 7d eb e1 cd 16 |......}....}....|
00000110 5e 1f 66 8f 04 cd 19 be 81 7d 8b 7d 1a 8d 45 fe |^.f......}.}..E.|
00000120 8a 4e 0d f7 e1 03 46 fc 13 56 fe b1 04 e8 c2 00 |.N....F..V......|
00000130 72 d7 ea 00 02 70 00 52 50 06 53 6a 01 6a 10 91 |r....p.RP.Sj.j..|
00000140 8b 46 18 a2 26 05 96 92 33 d2 f7 f6 91 f7 f6 42 |.F..&...3......B|
00000150 87 ca f7 76 1a 8a f2 8a e8 c0 cc 02 0a cc b8 01 |...v............|
00000160 02 80 7e 02 0e 75 04 b4 42 8b f4 8a 56 24 cd 13 |..~..u..B...V$..|
00000170 61 61 72 0a 40 75 01 42 03 5e 0b 49 75 77 c3 03 [EMAIL="%7Caar.@u.B"]|aar.@u.B[/EMAIL].^.Iuw..|
00000180 18 01 27 0d 0a 49 6e 76 61 6c 69 64 20 73 79 73 |..'..Invalid sys|
00000190 74 65 6d 20 64 69 73 6b ff 0d 0a 44 69 73 6b 20 |tem disk...Disk |
000001a0 49 2f 4f 20 65 72 72 6f 72 ff 0d 0a 52 65 70 6c |I/O error...Repl|
000001b0 61 63 65 20 74 68 65 20 64 69 73 6b 2c 20 61 6e |ace the disk, an|
000001c0 64 20 74 68 65 6e 20 70 72 65 73 73 20 61 6e 79 |d then press any|
000001d0 20 6b 65 79 0d 0a 00 00 49 4f 20 20 20 20 20 20 | key....IO |
000001e0 53 59 53 4d 53 44 4f 53 20 20 20 53 59 53 7f 01 |SYSMSDOS SYS..|
000001f0 00 41 bb 00 07 60 66 6a 00 e9 3b ff 00 00 55 aa |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory

```

---

### Post by Rockcarver on 2011-02-22
Jthirt, My experience(and yours, look at the length of this thread) indicates that Ubuntu is NOT an appropriate OS for a computer newbie. To unstable, too buggy. If you don't understand coding at all, Ubuntu will just create frustration after the first honeymoon ends with a kernel panic.

---

### Post by mdhooge on 2011-03-25
> **Rockcarver said:**
> Jthirt, My experience(and yours, look at the length of this thread) indicates that Ubuntu is NOT an appropriate OS for a computer newbie. To unstable, too buggy. If you don't understand coding at all, Ubuntu will just create frustration after the first honeymoon ends with a kernel panic.

+1
I would even go farther and say that unless you have a PhD in computer science, you should not even try to switch on any electronic device!

---

### Post by coilwinder on 2011-04-23
to drs305:

Thanks!! You are a lifesaver!

Suddenly, and without any updates that I know of, I got dropped to the busybox initramfs prompt, with the gave up waiting for root device error.

I edited the GRUB2 menu option (pressing "e") from root=UUID=long number, to root=/dev/sdxy  (sda6 in my case), and it booted again :)

After running sudo update-grub it reverted to root=UUID... stuff again, but still boots (for the 3rd time so far...), so I don't really know what the issue was. Using Ubuntu 9.10 32-bit.


Thanks again!

---

### Post by drs305 on 2011-04-24
> **coilwinder said:**
> After running sudo update-grub it reverted to root=UUID... stuff again, but still boots (for the 3rd time so far...), so I don't really know what the issue was. Using Ubuntu 9.10 32-bit.

That's computers for ya!  Who knows? 

If it happens again there is the option to turn off UUIDs in the /etc/default/grub file by uncommenting one of the entries. Hopefully that won't happen.

By the way, get your 9.10 updated as you won't be able to do so for much longer. Even better, upgrade. There have been a lot of excellent improvements.

Happy Ubuntu-ing !

---

### Post by coilwinder on 2011-04-24
> That's computers for ya!  Who knows? Lol yeah :P
It still boots btw.

Thanks for the tip about /etc/default/grub file too!

> By the way, get your 9.10 updated as you won't be able to do so for much  longer. Even better, upgrade. There have been a lot of excellent  improvements.I think I will. It is about time to do a clean install soon anyway. As 11.04 is soon out, I'll wait for that.

In fact the Ubuntu 9.10 I got now, really started on my old computer. I didn't want to re-install everything at the time, so I found remastersys. Simply brilliant, it reinstalled my old Ubuntu on my new machine, software and everything.

The old computer (ish, somewhat rebuilt) is now running Ubuntu 10.04 64-bit since I wanted to test 64-bit also. From what little I gather and use I'd say 99% works. Oh and even though its the old computer, it boots faster (Not that its that important, as long as its within a reasonable time).

---

### Post by wonderfly on 2011-10-11
> **drs305 said:**
> joaqal,

First, welcome to Ubuntu and the Ubuntu forums.  :-)

Please boot the LiveCD and run the boot info script from the following link. Make sure to post the results inside "code" brackets by clicking the # icon in the post's menu.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If you feel the need to experiment, you can try editing the menu entry in the Grub 2 menu. It may work and it wouldn't take long to try:

1. Highlight an old, working kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY"  with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.

If it doesn't work, post the script results. If it does, run "sudo update-grub" and then post the results if it doesn't reboot properly.

Note: There are more detailed ways of trying to get to a bootable system from the Grub 2 menu. If you want to try them, refer to:
[https://help.ubuntu.com/community/Grub2#Command Line Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")
Thanks a lot to drs305. It works for me.

---

### Post by Tmpv on 2011-11-09
> **drs305 said:**
> joaqal,

First, welcome to Ubuntu and the Ubuntu forums.  :-)

Please boot the LiveCD and run the boot info script from the following link. Make sure to post the results inside "code" brackets by clicking the # icon in the post's menu.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you feel the need to experiment, you can try editing the menu entry in the Grub 2 menu. It may work and it wouldn't take long to try:

1. Highlight an old, working kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY"  with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.

If it doesn't work, post the script results. If it does, run "sudo update-grub" and then post the results if it doesn't reboot properly.

Note: There are more detailed ways of trying to get to a bootable system from the Grub 2 menu. If you want to try them, refer to:
[https://help.ubuntu.com/community/Grub2#Command Line Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")


10x drs305!!
Great post. Realy helped me out after my 2-days fight with my power cut problem. But i have one stupied question: after changing the GRUB settings and a successful boot, GRUB doesn't save my changes and i have to edit my kern every time i restart or shut down my laptop. 10x for the help in advance.

---

### Post by drs305 on 2011-11-09
> **Tmpv said:**
> GRUB doesn't save my changes and i have to edit my kern every time i restart or shut down my laptop. 10x for the help in advance.

In most cases, after booting, all you should have to do is run the following command to update the Grub menu. It will search your drives and update the UUIDs so that Grub looks in the proper location for the boot files.

```
sudo update-grub
```

---

### Post by chezzwizz on 2012-06-17
Looking at this thread, it seems as though most are having their problems solved. I however have tried the suggested solution and failed, but my situation is a little different in that the disks are changing their identifiers. (i.e. sometimes sdd1 is sdb1) I'm not sure why this problem keeps happening, but I have noticed that it only occurs on a cold boot, and to solve it I have to first boot into Windows then reboot and the drive ids will correct themselves. If non of this makes sense, I have run the bootinfo script once with a cold boot and again after booting into windows then rebooting as I described.

RESLUTS.txt:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 144450 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       194,559       192,512  83 Linux
/dev/sdb2             194,560   625,141,759   624,947,200  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7A0A34FC0A34B6CB                       ntfs       Potluck
/dev/sdb1        d133544b-00b1-4237-b6e6-6d8c406c55d5   ext4       
/dev/sdb2        0bf025fe-6476-4f36-adfc-cbeb394c77fe   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot                    ext4       (rw)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos2)'
search --no-floppy --fs-uuid --set=root 0bf025fe-6476-4f36-adfc-cbeb394c77fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos1)'
  search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-25-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-25-generic ...'
    linux    /vmlinuz-3.2.0-25-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-25-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-24-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /vmlinuz-3.2.0-24-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-23-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /vmlinuz-3.2.0-23-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5CF00923F009054C
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
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    3
               =                initrd.img-3.2.0-24-generic                    3
               =                initrd.img-3.2.0-25-generic                    8
               =                vmlinuz-3.2.0-23-generic                       2
               =                vmlinuz-3.2.0-24-generic                       2
               =                vmlinuz-3.2.0-25-generic                       2

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdd1 during installation
UUID=d133544b-00b1-4237-b6e6-6d8c406c55d5 /boot           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=da4d797c-08f2-489a-82f1-a1855511eab0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img                                     8
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

and RESULTS1.txt:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid d5ee7016-a6da-4f3e-bdf3-a88f5bcf9d58 root 
    set prefix=($root)/grub
    ---------------------------------------------------------------------------
    -----.
 => ReactOS is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/bcd

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdd1 
                       and looks at sector 144450 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   957,896,703   957,894,656   7 NTFS / exFAT / HPFS
/dev/sdb2         957,896,704   967,331,839     9,435,136   7 NTFS / exFAT / HPFS
/dev/sdb3         967,333,886   976,771,071     9,437,186   5 Extended
/dev/sdb5         967,333,888   976,771,071     9,437,184  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   293,044,223   292,837,376   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048       194,559       192,512  83 Linux
/dev/sdd2             194,560   625,141,759   624,947,200  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7A0A34FC0A34B6CB                       ntfs       Potluck
/dev/sdb1        CA78BC4A78BC3753                       ntfs       Data
/dev/sdb2        8EB47672B4765D21                       ntfs       Pagefile
/dev/sdb5        da4d797c-08f2-489a-82f1-a1855511eab0   swap       
/dev/sdc1        5CF00923F009054C                       ntfs       Boot
/dev/sdc2        0A3CF9263CF90E07                       ntfs       Win 7
/dev/sdd1        d133544b-00b1-4237-b6e6-6d8c406c55d5   ext4       
/dev/sdd2        0bf025fe-6476-4f36-adfc-cbeb394c77fe   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /boot                    ext4       (rw)
/dev/sdd2        /                        ext4       (rw,errors=remount-ro)


============================= sdd1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos2)'
search --no-floppy --fs-uuid --set=root 0bf025fe-6476-4f36-adfc-cbeb394c77fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos1)'
  search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-25-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-25-generic ...'
    linux    /vmlinuz-3.2.0-25-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-25-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-24-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /vmlinuz-3.2.0-24-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux    /vmlinuz-3.2.0-23-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /vmlinuz-3.2.0-23-generic root=UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root d133544b-00b1-4237-b6e6-6d8c406c55d5
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5CF00923F009054C
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
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    3
               =                initrd.img-3.2.0-24-generic                    3
               =                initrd.img-3.2.0-25-generic                    8
               =                vmlinuz-3.2.0-23-generic                       2
               =                vmlinuz-3.2.0-24-generic                       2
               =                vmlinuz-3.2.0-25-generic                       2

=============================== sdd2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=0bf025fe-6476-4f36-adfc-cbeb394c77fe /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdd1 during installation
UUID=d133544b-00b1-4237-b6e6-6d8c406c55d5 /boot           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=da4d797c-08f2-489a-82f1-a1855511eab0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img                                     8
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  c0 04 40 19 7c 05 80 fa  c0 04 40 19 7c 05 80 fa  |..@.|.....@.|...|
*
000001b0  c0 04 40 19 7c 05 80 fa  c0 04 40 19 7c 05 00 fe  |..@.|.....@.|...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 90 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

Any help or directional guidence would be awsome!

---

### Post by drs305 on 2012-06-17
> **chezzwizz said:**
> Any help or directional guidence would be awsome!

I'm consistently amazed by the variety of issues presented on these forums!  ;-)

From what I can tell, you get what you want when it thinks your Ubuntu is on sdd (1 for /boot, 2 for /)?

And in the first instance it only finds 2 of the 4 drives (or did you add more between boot info script runs?).

Anyway, if the above is correct, the constant is that sda is the same drive in each case. I would recommend you make sda your BIOS boot drive (if it isn't already), and make sure GRUB is properly installed in the sda MBR.

GRUB 2 is designed to be independent of device names to prevent just what you are describing. So from a normally-running Ubuntu, with it thinking it is on sdd:

```

sudo grub-install /dev/sda
sudo grub-install /dev/sdb
sudo update-grub

```


If this doesn't work please rerun the boot script.

---

### Post by chezzwizz on 2012-06-17
> **drs305 said:**
> 
And in the first instance it only finds 2 of the 4 drives (or did you add more between boot info script runs?).

That is where I am confused. Those drives are always there, and they are only detected after I boot into Windows and do a reboot without shutting down.

> 
Anyway, if the above is correct, the constant is that sda is the same drive in each case. I would recommend you make sda your BIOS boot drive (if it isn't already), and make sure GRUB is properly installed in the sda MBR.

I was trying to avoid this because sda is actually a removable drive (esata). I am also wondering how GRUB gets loaded mainly because I am running the GRUB installed on sdd. I use plop boot manager which launches grub, and plop detects and executes grub by calling sdd. I'm not sure why plop can see the drives and grub cannot.

Alas, if installing grub to sda is my only option, I may have to do some hardware reconfiguration.  This is not looking fun. :(

---

### Post by drs305 on 2012-06-17
> **chezzwizz said:**
> Alas, if installing grub to sda is my only option, I may have to do some hardware reconfiguration.  This is not looking fun. :(

No, I wouldn't do that yet. You introduced a lot of variables that I'm not familiar with and didn't consider. I'll give it some thought.  Maybe someone else will have an idea.

---

### Post by drs305 on 2012-06-17
I don't know how it could be related, but Grub 2 does have an install option regarding BIOS issues. Normally it is used in an attempt to circumvent older BIOS's 137GB read capability. That's not the only thing it can correct so it might be something you could try. If it doesn't help, you reverse it by just running the standard install command (sudo grub-install /dev/sdX).

I'll let you decide where you want to install it; sdX (MBR) or sdXY (partition):
```

sudo grub-install --disk-module=ata /dev/sdX
```

I'd ask if the (re)boot goes through plop or not but I wouldn't know what to do with the information either way.  ](*,)

---

### Post by chezzwizz on 2012-06-18
Got some time, tried as you suggested with no results. My question now is, what is the process that detects the hard drives at boot time, and is there anything anyone can think of that would force grub to look for all hard drives by UUID? (If this is indeed a grub responsibility.)

PS: I agree: ](*,), and yes it does boot through plop every time. I am wondering if just eliminating that boot manager would solve my problems. By replacing it with Grub of course.

---

### Post by drs305 on 2012-06-19
I have not seen Grub have problems of the sort you are describing. I don't have any experience with plop so I don't know how useful it is; I do know Grub2 does a good job booting a variety of OS's and I've never needed another bootloader.

There is a setting you can use in /etc/default/grub to disable UUIDs. > GRUB_DISABLE_LINUX_UUID=true
It's initial intent was to allow booting kernel's whose initramfs cannot handle UUIDs so I'm not sure it's your issue, but it is easy enough to try. Just run 'update-grub' after adding the entry and saving the file. To give it a complete test, I'd probably manually edit grub.cfg and also remove all the 'search' lines, which still retain the uuid's even after adding the above.

---

### Post by chezzwizz on 2012-07-12
I spent some more time and did a bunch of reading and research and I still have no idea what is going on, but, I did get it to boot without the "Gave up waiting for root device." message.

It still only detects my linux partition and my external, unless I first do a boot into Windows and then reboot and choose linux.

It does seem though that this is not a grub problem since I have promoted my linux disk to highest boot priority, eliminated my plop boot manager and created a Windows boot entry in grub. When I select the Windows 7 entry in grub, the disk is found and booted from just fine, it is only when I am booting into linux (before ever booting into windows) that the windows partitions are not detected.

I also found that there where some "udevd timeout killing /sbin/modprobe" messages as well as an "ata_id HDIO_GET_IDENTITY failed" message. (Again only before I ever do a boot into windows.)

So I don't know if anyone else is getting something similar, but in my case, this appears to have something to do with udev and not Grub.

---

### Post by drs305 on 2012-07-12
> **chezzwizz said:**
> When I select the Windows 7 entry in grub, the disk is found and booted from just fine, it is only when I am booting into linux (before ever booting into windows) that the windows partitions are not detected.

Again, you should wait for a Windows user, but here is a thought:

Is it possible that Windows runs chkdsk when it boots (or exits) and fixes errors that have occurred on the partition, whereas when you boot Ubuntu first the Windows partition errors haven't been corrected? I know that when there are disk errors Gparted and Ubuntu sometimes cannot see the Windows partitions.

---

### Post by chezzwizz on 2012-07-12
I will do some research into that, strangely enough, while doing all this, I did a resize on my ext4 partitions, and Gparted was able to detect the primary windows disk and its partitions, but not the other disk that has all ntfs partitions. This leads me to believe you may be on to something.

---

