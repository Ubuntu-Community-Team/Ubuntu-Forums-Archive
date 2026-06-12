---
title: "multiboot XP,Lubuntu,Kubuntu"
date: 2011-01-11
forum: General Help
---

### Post by bachor on 2011-01-11
I did lots of research here in on google and it is bit confusing.

 I want to install Lubuntu and Ubuntu together with XP.

 Right now Im having XP on primary and  Ubuntu 10 on Extended.

 I want to keep XP as is, and use Extended for Multiboot Linux OSes.

 I'd like to have it encrypted, and shared /HOME would be nice too.

 Here is my bootscript:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   BLKID Error_Log Log Log1 
                       Mount_Error PT sda1 sda2 sda5 sda6 Tmp_Log Trash 
                       NOTICE TO USERS This computer system is the private 
                       property of The owner, whether individual, corporate 
                       or government. It is for authorized use only. Users 
                       (authorized or unauthorized) have no explicit or 
                       implicit expectation of privacy. Any or all uses of 
                       this system and all files on this system may be 
                       intercepted, monitored, recorded, copied, audited, 
                       inspected, and disclosed to your employer, to 
                       authorized site, government, and law enforcement 
                       personnel, as well as authorized officials of 
                       government agencies, both domestic and foreign. By 
                       using this system, the user consents to such 
                       interception, monitoring, recording, copying, 
                       auditing, inspection, and disclosure at the discretion 
                       of such personnel or officials. Unauthorized or 
                       improper use of this system may result in civil and 
                       criminal penalties and administrative or disciplinary 
                       action, as appropriate. By continuing to use this 
                       system you indicate your awareness of and consent to 
                       these terms and conditions of use. LOG OFF IMMEDIATELY 
                       if you do not agree to the conditions stated in this 
                       warning. BLKID Error_Log Log Log1 Mount_Error PT sda1 
                       sda2 sda5 sda6 Tmp_Log Trash
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,382,884    29,382,822   7 HPFS/NTFS
/dev/sda2          29,382,946   234,440,703   205,057,758   f W95 Ext d (LBA)
/dev/sda5          29,382,948   193,486,859   164,103,912   b W95 FAT32
/dev/sda6         193,488,896   230,533,119    37,044,224  83 Linux
/dev/sda7         230,535,168   234,440,703     3,905,536  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CA31A03493A4A0                       ntfs       XP                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4AA8-1A27                              vfat                                     
/dev/sda6        e1a6c85d-59e6-4666-af0b-9780a35b3c94   ext4                                     
/dev/sda7        43bcb405-2d85-4c77-a753-1f31c8eb058b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/XP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01ca31a03493a4a0
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=43bcb405-2d85-4c77-a753-1f31c8eb058b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 112.1GB: boot/grub/core.img
 114.4GB: boot/grub/grub.cfg
 115.8GB: boot/initrd.img-2.6.35-23-generic
  99.1GB: boot/initrd.img-2.6.35-24-generic
 112.9GB: boot/vmlinuz-2.6.35-23-generic
 112.7GB: boot/vmlinuz-2.6.35-24-generic
  99.1GB: initrd.img
 115.8GB: initrd.img.old
 112.7GB: vmlinuz
 112.9GB: vmlinuz.old
``` Should I prepare partitions with Gparted [which I usually do] and then install Kubuntu from Alternate CD with LVM encryption,without Grub installation?
 Then install Lubuntu? 
And Grub2 should automatically find any bootable OS,right?

thank you

---

