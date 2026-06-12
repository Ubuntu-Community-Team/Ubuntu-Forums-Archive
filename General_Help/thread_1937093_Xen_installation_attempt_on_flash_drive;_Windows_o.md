---
title: "Xen installation attempt on flash drive; Windows on internal hard disk wont boot"
date: 2012-03-07
forum: General Help
---

### Post by ranpkri55 on 2012-03-07
I am posting my question here since I have a wubi-installation of Ubuntu.

My system is setup like this:
80 GB hard disk with Windows XP on C:/, with Ubuntu 10.04 as a WUBI install, 2 other partitions just for data.(So very less data on C:/). Everything was perfect for more than a year.  

My work required me to install Xen ( [http://xen.org/](http://xen.org/)), so I wanted to try it out on a 16 GB USB flash drive; did not want to disturb my existing configuration. 

So I installed Fedora16 (has grub2) on my USB drive, and followed instructions from [http://wiki.xen.org/wiki/Fedora_16_Dom0](http://wiki.xen.org/wiki/Fedora_16_Dom0) and installed Xen. As part of the install, grub2 entries are written to make Xen available on the boot menu. 

I assumed grub2 would be installed on my USB drive, but apparently not. I am not sure what exactly has happened, but now when I select XP from the boot menu, I get a BSOD error and it wont boot. 

But my WUBI-ubuntu boots fine, and I can access my C:/ from Ubuntu.

I am guessing my MBR entries were overwritten/corrupted by the xen installation.

I am posting my results.txt from the bootinfo script. Please help since I need both XP/Ubuntu.



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub.cfg

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda2          61,432,560    92,897,279    31,464,720   7 NTFS / exFAT / HPFS
/dev/sda3          92,897,280   145,333,439    52,436,160   7 NTFS / exFAT / HPFS
/dev/sda4         145,333,440   195,365,519    50,032,080   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       1be9ccb7-38c4-4cea-9a2d-2ed14c61c130   ext4       
/dev/sda1        0650458050457807                       ntfs       XP
/dev/sda2        92880643880625F7                       ntfs       Ubuntu
/dev/sda3        AE88EC6788EC300F                       ntfs       New Volume
/dev/sda4        3848F2C948F28542                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-38-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-38-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu, Linux 2.6.32-38-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-38-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu, Linux 2.6.32-37-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-37-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu, Linux 2.6.32-37-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-37-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu, Linux 2.6.32-36-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-36-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-36-generic
}
menuentry "Ubuntu, Linux 2.6.32-36-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-36-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-36-generic
}
menuentry "Ubuntu, Linux 2.6.32-34-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-34-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, Linux 2.6.32-34-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-34-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, Linux 2.6.32-33-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-33-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, Linux 2.6.32-33-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-33-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 92880643880625f7
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0650458050457807
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   2.874477386 = 3.086446592    boot/grub/grub.cfg                             1
  10.371326447 = 11.136126976   boot/initrd.img-2.6.32-24-generic              1
  10.394142151 = 11.160625152   boot/initrd.img-2.6.32-25-generic              1
  10.523094177 = 11.299086336   boot/initrd.img-2.6.32-33-generic              1
   5.503833771 = 5.909696512    boot/initrd.img-2.6.32-34-generic              2
   2.050708771 = 2.201931776    boot/initrd.img-2.6.32-36-generic              2
  11.410743713 = 12.252192768   boot/initrd.img-2.6.32-37-generic              2
  11.540710449 = 12.391743488   boot/initrd.img-2.6.32-38-generic              2
  10.382667542 = 11.148304384   boot/vmlinuz-2.6.32-24-generic                 1
  10.444755554 = 11.214970880   boot/vmlinuz-2.6.32-25-generic                 1
  10.510990143 = 11.286089728   boot/vmlinuz-2.6.32-33-generic                 1
  10.899673462 = 11.703435264   boot/vmlinuz-2.6.32-34-generic                 1
  11.199028015 = 12.024864768   boot/vmlinuz-2.6.32-36-generic                 1
  11.401916504 = 12.242714624   boot/vmlinuz-2.6.32-37-generic                 1
  11.603588104 = 12.459257856   boot/vmlinuz-2.6.32-38-generic                 1
  11.540710449 = 12.391743488   initrd.img                                     2
  11.410743713 = 12.252192768   initrd.img.old                                 2
  11.603588104 = 12.459257856   vmlinuz                                        1
  11.401916504 = 12.242714624   vmlinuz.old                                    1

================================ sda3/grub.cfg: ================================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub2-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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

set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.i686' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 52f32ea6-0cae-42f9-8bb9-2f40065dd665
	echo	'Loading Linux 3.1.0-7.fc16.i686 ...'
	linux	/vmlinuz-3.1.0-7.fc16.i686 root=/dev/mapper/vg_fedorau-root ro rd.md=0 rd.dm=0 rd.lvm.lv=vg_fedorau/swap  KEYTABLE=us quiet SYSFONT=latarcyrheb-sun16 rhgb rd.luks=0 rd.lvm.lv=vg_fedorau/root LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.i686.img
}
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.i686 (recovery mode)' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 52f32ea6-0cae-42f9-8bb9-2f40065dd665
	echo	'Loading Linux 3.1.0-7.fc16.i686 ...'
	linux	/vmlinuz-3.1.0-7.fc16.i686 root=/dev/mapper/vg_fedorau-root ro single rd.md=0 rd.dm=0 rd.lvm.lv=vg_fedorau/swap  KEYTABLE=us quiet SYSFONT=latarcyrheb-sun16 rhgb rd.luks=0 rd.lvm.lv=vg_fedorau/root LANG=en_US.UTF-8
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.i686.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0650458050457807
	drivemap -s (hd0) ${root}
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

### BEGIN /etc/grub.d/90_persistent ###
### END /etc/grub.d/90_persistent ###
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub.cfg                                       1

---

### Post by ranpkri55 on 2012-03-07
Forgot to add this info:

I tried to 'repair' my XP installation with a Windows XP cd, but when I chose the 'repair XP' option after booting from the CD, it gave me an error message which was something like "NO hard disk detected. Setup will quit":confused:

---

### Post by ranpkri55 on 2012-03-08
Bump! Can somebody help please.

---

### Post by bcbc on 2012-03-09
There is a grub.cfg on /dev/sda3 that was put there by Fedora, and it's pointing at (hd0, msdos1) - hd0 normally means /dev/sda; however it also has your windows entry that it thinks is on (/dev/sda,msdos1) and based on the UUIDs it looks like it considers these to be different (windows one is correct and fedora one is different to that)

But why the grub.cfg ended up on /dev/sda3 is strange.

I can't see any obvious causes for the blue screen, and since Wubi is booting it means that the Windows boot manager is functional (i.e. the drive MBR (windows bootloader) and boot sector on /dev/sda1 is functional. So... it's a little puzzling.

Can't see anything obvious :(

---

### Post by ranpkri55 on 2012-03-09
I am puzzled, but happy that Ubuntu boots without XP itself working. 

Lets look at some workarounds for now. 

Say, In case I want to 'restore' my system to how it was before, can I do it ? If so, which files do I need to delete. 

Another thing I was thinking was just format C:/ and reinstall windows, but this would mean my Ubuntu will also be gone right, since its 'inside' windows ? 
Now the WUBI option doesnt seem that smart after all :(

---

### Post by bcbc on 2012-03-09
I don't know how to 'restore'  by deleting files since it's not clear what's causing the blue screen. The bootinfoscript only shows a few files of interest and there's nothing that clearly shows anything that'd cause a blue screen of death.

There are ways to avoid losing your current install if you restore windows...
e.g. 
1. [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi to a normal dual boot
or 
2. backup the \ubuntu\disks\*.disk files, reinstall windows, reinstall the same release of Wubi, replace the *.disk files. Caveat, if the partition numbering has changed or grub is using the partition UUID to boot (not in your case) then you have to manually override the first time you boot.

Note if you choose to migrate the wubi and then install windows, it will overwrite the grub2 bootloader. So, keep an ubuntu cd/usb handy in order to reinstall the bootloader.

---

### Post by ranpkri55 on 2012-03-12
Thanks a lot for your suggestions! 

I migrated by wubi to a separate partition, then installed a fresh copy of win7, and restored back my bootloader. Now I have a dual-boot setup working great. 

Your migration script worked wonderfully too. Thanks again.

---

### Post by bcbc on 2012-03-13
Cool! Always happy to hear when things work out well.

---

