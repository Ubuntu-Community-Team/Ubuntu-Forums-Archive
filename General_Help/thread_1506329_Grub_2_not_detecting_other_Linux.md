---
title: "Grub 2 not detecting other Linux"
date: 2010-06-10
forum: General Help
---

### Post by TheShader on 2010-06-10
Hello I'm using Ubuntu 10.04. I have 4 partitions on my laptop. 1 swap, 2 Ubuntu, 3 Windows XP and lastly a logical partition to test new Linux distros. I usually triple boot using Grub 2, I chose not to install any boot loader when installing a new Linux and after I run Ubuntu, and sudo update-grub and it detects the third OS automaticly.

However, I recently installed Pardus 2009.2 and did the same. But when I reboot I can't see the last entry in the menu. Please help :confused:

Output of sudo update-grub
```
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda3
Found Geronticus eremita (2009.2) on /dev/sda5
done

```

---

### Post by TheShader on 2010-06-10
bump

---

### Post by oldfred on 2010-06-10
It does say it found it.

Post this to see entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.


If your other installs use old grub I would just install the boot loader to the partition and create a chainboot entry in 40_custom that you would never have to change.

menuentry "Chainload Other Systems Grub Menu on sda5" {
set root=(hd0,5)
chainloader +1
}

---

### Post by TheShader on 2010-06-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 7413945 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 54596025 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 61791592 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  [0;33;01;37mPardus GNU/Linux 
                       [0;33;00;36m [0;33;01;36m([0;33;01;32m 
                       [0;33;01;36m) [0;37;40m
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

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

/dev/sda1                  63     4,000,184     4,000,122  82 Linux swap / Solaris
/dev/sda2           4,000,185    61,063,064    57,062,880  83 Linux
/dev/sda3          82,027,890   312,560,639   230,532,750   7 HPFS/NTFS
/dev/sda4          61,063,065    82,027,889    20,964,825   5 Extended
/dev/sda5    *     61,063,128    82,027,889    20,964,762  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 126 MB, 126353408 bytes
7 heads, 32 sectors/track, 1101 cylinders, total 246784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32       246,751       246,720   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d0ccb982-8e5e-4b9d-a9df-2b6008dd99a5   swap       PARDUS_SWAP                   
/dev/sda2        8725378d-151b-4008-b356-646705518636   ext4                                     
/dev/sda3        A448F14348F11530                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        94b1dd08-df6d-4d44-bcce-20d9cdbbeedd   ext4       PARDUS_ROOT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F866-5281                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev             /scratchbox/users/shader/dev none       (rw,bind)
/dev/pts         /scratchbox/users/shader/dev/pts none       (rw,bind)
/dev/shm         /scratchbox/users/shader/dev/shm none       (rw,bind)
/dev/sdb1        /media/F866-5281         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636 ro  vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636 ro single  vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8725378d-151b-4008-b356-646705518636 ro  vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8725378d-151b-4008-b356-646705518636 ro single  vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8725378d-151b-4008-b356-646705518636
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Pardus 2009.2 Geronticus eremita (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 94b1dd08-df6d-4d44-bcce-20d9cdbbeedd
	linux /boot/kernel-2.6.31.13-131 root=LABEL=PARDUS_ROOT splash=silent quiet vga=0x317
	initrd (hd0,4)/boot/initramfs-2.6.31.13-131
}
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set a448f14348f11530
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8725378d-151b-4008-b356-646705518636 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=1dc70a14-6d35-40e6-97e4-2710ae00ccc8 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  27.9GB: boot/grub/core.img
   8.4GB: boot/grub/grub.cfg
  28.3GB: boot/initrd.img-2.6.32-21-generic
  30.2GB: boot/initrd.img-2.6.32-22-generic
  28.0GB: boot/vmlinuz-2.6.32-21-generic
  30.1GB: boot/vmlinuz-2.6.32-22-generic
  30.2GB: initrd.img
  28.3GB: initrd.img.old
  30.1GB: vmlinuz
  28.0GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

========================== sda5/boot/grub/grub.conf: ==========================

default 0
gfxmenu /boot/grub/message
background 10333C
timeout 10

title Pardus 2009.2 Geronticus eremita
root (hd0,4)
kernel (hd0,4)/boot/kernel-2.6.31.13-131 root=LABEL=PARDUS_ROOT splash=silent quiet vga=0x317
initrd (hd0,4)/boot/initramfs-2.6.31.13-131

title Ubuntu0
root (hd0,0)
kernel (hd0,0)/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636 
ro  vga=791  quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.32-22-generic

title Ubuntu1
root (hd0,1)
kernel (hd0,1)/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636
ro  vga=791  quiet splash
initrd (hd0,1)/boot/initrd.img-2.6.32-22-generic

title Ubuntu2
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636
ro  vga=791  quiet splash
initrd (hd0,2)/boot/initrd.img-2.6.32-22-generic

title Ubuntu3
root (hd0,3)
kernel (hd0,3)/boot/vmlinuz-2.6.32-22-generic root=UUID=8725378d-151b-4008-b356-646705518636
ro  vga=791  quiet splash
initrd (hd0,3)/boot/initrd.img-2.6.32-22-generic

title Windows (ntfs) - sda3
rootnoverify (hd0,2)
makeactive 
chainloader +1

=============================== sda5/etc/fstab: ===============================

#*See the manpage fstab(5) for more information.
#
#   <fs>             <mountpoint>     <type>    <opts>               <dump/pass>
LABEL=PARDUS_ROOT    /                ext4      defaults,user_xattr,noatime 0 0
LABEL=PARDUS_SWAP    none             swap      defaults,sw          0 0
proc                 /proc            proc      nosuid,noexec        0 0
sysfs                /sys             sysfs     defaults             0 0
debugfs              /sys/kernel/debug debugfs   defaults             0 0
tmpfs                /dev/shm         tmpfs     nodev,nosuid,noexec  0 0
/dev/sda2            /mnt/sda2        ext4      defaults             0 0
/dev/sda3            /mnt/sda3        ntfs-3g   dmask=007,fmask=117,gid=6,locale=tr_TR.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  33.5GB: boot/grub/grub.conf
  33.5GB: boot/grub/menu.lst
  31.6GB: boot/grub/stage2
  39.3GB: boot/initramfs-2.6.31.13-131

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/vmlinuz-2.6.30.6-slitaz
```

I installed the legacy Grub of the third distro to the partition it's installed to, I updated grub 2 and it detected it but when I tried to start it it gave kernel panic. I could run the distro when I installed its Grub to the master partition(sda). So is it the best to chainload as you said? Also when I add that entry under 40_custom, will it disappear when I grub-update/update to newer kernels?

---

### Post by oldfred on 2010-06-10
the 40_custom entry will should stay unless you totally uninstalled grub and deleted the folders. Of course backups are always good and I run the boot info script and save a copy in my /home where it gets backed up.

the script must of had trouble parsing the sda5 operating system description, since it is just description I do not think it is an issue.

Since you have some grub installed to partitions, I would try the chainboot.

---

### Post by TheShader on 2010-06-10
Yep this worked! Thanks! However chainloading is a bit slower but it's the fault of Pardus, not Grub or Ubuntu :lolflag:

---

