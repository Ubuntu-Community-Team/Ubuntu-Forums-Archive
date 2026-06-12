---
title: "Windows XP Home with Ubuntu 10.04"
date: 2010-08-07
forum: General Help
---

### Post by kevin899 on 2010-08-07
Hi, yesterday I tried installing Ubuntu 10.04 Desktop on an ASUS EEE PC 1005HA with a USB flash drive. The partitioning on the hard drive was a little strange; I'll explain that later in this post.

Please keep things simple, I'm new to Ubuntu.

My problem right now is that when I try to boot Windows XP (the bootloader now is GRUB one-point-nine-eight) I get a blinking underscore that goes nowhere. Ubuntu boots fine and is fully working. Originally I was still able to read the Windows XP NTFS partition in Ubuntu, but after I tried to tinker with the boot sector using testdisk, Ubuntu gave me an error 13 MFT does not match and refuses to mount the drive anymore. In GRUB, the six boot options are Ubuntu, Ubuntu recovery mode, memory test, some other memory test, Windows XP Home, and Windows NT (the recovery partition that came with the computer.)

Now, here's the thing with the partitions:
When installing, there seemed to be four partitions even though I only knew of three partitions on the hard drive, one being for the OS, one being storage, and one being the hidden recovery partition. The fourth one was a 42 MB unformatted NTFS partition that I think was between the Windows XP partition and the storage partition. This is before me tinkering with it. I proceeded to shrink the Windows XP partition from 77 GB to 40 GB and the free space came up as "unusable". Since the installer told me that I could undo the action, I tried deleting the mysterious 42 MB partition and the freed up space became usable. I installed Ubuntu on there, and now I have the problem. I have searched the net and this seems to be a moderately common problem so it may or may not have to do with the partitions thing.

RESULTS.TXT:
>                                                                      
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,000,062    80,000,000   7 HPFS/NTFS
/dev/sda2         151,123,455   302,230,844   151,107,390  17 Hidden HPFS/NTFS
/dev/sda3         302,230,845   310,230,844     8,000,000  1c Hidden W95 FAT32 (LBA)
/dev/sda4          80,001,024   144,001,023    64,000,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AE0A82DE0A7EE17                       ntfs                                     
/dev/sda2        A000B2F200B2CF12                       ntfs       Storage                       
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4        c7242935-d380-415f-a193-497810d19a29   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c7242935-d380-415f-a193-497810d19a29 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c7242935-d380-415f-a193-497810d19a29 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set c7242935-d380-415f-a193-497810d19a29
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ae0a82de0a7ee17
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=c7242935-d380-415f-a193-497810d19a29 /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


  54.3GB: boot/grub/core.img
  54.8GB: boot/grub/grub.cfg
  41.2GB: boot/initrd.img-2.6.32-21-generic
  54.8GB: boot/vmlinuz-2.6.32-21-generic
  41.2GB: initrd.img
  54.8GB: vmlinuz

---

