---
title: "Remove windows and move Ubuntu to C:\ ?"
date: 2010-12-12
forum: General Help
---

### Post by Shalika on 2010-12-12
I have Windows XP installed in C: drive. C: - 80 GB NTFS
And I have installed Ubuntu inside windows in E:\ drive with 15GB disk 
E : - 80 GB 
I have data inside E: drive 60GB 

Now I need to remove windows and Move Ubuntu to the C: Drive then Expand the Ubuntu to 80GB.. 

How to do this ?

---

### Post by DeMus on 2010-12-12
> **Shalika said:**
> I have Windows XP installed in C: drive. C: - 80 GB NTFS
And I have installed Ubuntu inside windows in E:\ drive with 15GB disk 
E : - 80 GB 
I have data inside E: drive 60GB 

Now I need to remove windows and Move Ubuntu to the C: Drive then Expand the Ubuntu to 80GB.. 

How to do this ?

If you have installed Ubuntu inside Windows (with Wubi) then it won't run anymore when you delete Windows. Ubuntu is located inside a Windows folder.
If you want to delete Windows you have to re-install Ubuntu the normal way (without Wubi) and partition the disk as you want it. For example:
Partition 1: 25GB for /
Partition 2: (Ram-size of your computer) for swap
Partition3: rest for /home

The 25GB for / could be smaller if you don't intend to install lots of programs. That way /home can become larger for more data storage.

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

I hope it is not a Wubi install. Instead of guessing your setup, I would suggest to boot Ubuntu and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

That way, we'll make sure we don't run you into troubles by guessing your setup blindly.

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by Shalika on 2010-12-12
> **sikander3786 said:**
> I would suggest to boot Ubuntu and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,830,869   163,830,807   7 HPFS/NTFS
/dev/sda2         163,830,870   625,137,344   461,306,475   f W95 Ext d (LBA)
/dev/sda5         163,830,933   327,661,739   163,830,807   7 HPFS/NTFS
/dev/sda6         327,661,803   491,492,609   163,830,807   7 HPFS/NTFS
/dev/sda7         491,492,673   625,137,344   133,644,672   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       da1458a9-0e2d-4c76-aec1-b0ba27fade9c   ext4                                     
/dev/sda1        960C194A0C192731                       ntfs       Samsung 1                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        048C788F8C787CCC                       ntfs       Samsung 2                     
/dev/sda6        EEB05A3DB05A0C89                       ntfs       Samsung 3                     
/dev/sda7        01CAD1D77E8D3E40                       ntfs       Samsung 4                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5        /media/Samsung 2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/Samsung 1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Samsung 4         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr="Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /tutag=hjghfq /kernel=tukernel.exe 

======================== sda6/Wubi/boot/grub/grub.cfg: ========================

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
}

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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set eeb05a3db05a0c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set eeb05a3db05a0c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set eeb05a3db05a0c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set eeb05a3db05a0c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 960c194a0c192731
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

============================= sda6/Wubi/etc/fstab: =============================

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

================= sda6/Wubi: Location of files loaded by Grub: =================


  13.1GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-23-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
  10.9GB: boot/vmlinuz-2.6.35-23-generic
    .9GB: initrd.img
    .8GB: initrd.img.old
  10.9GB: vmlinuz
  10.9GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2010-12-12
Wubi installs can be migrated to the hard-drive.

I recommend you read this guide by forum member bcbc first and then come back if you have specific questions:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

