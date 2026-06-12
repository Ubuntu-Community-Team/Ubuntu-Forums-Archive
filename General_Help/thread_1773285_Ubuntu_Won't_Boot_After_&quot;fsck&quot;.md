---
title: "Ubuntu Won't Boot After &quot;fsck&quot;"
date: 2011-06-01
forum: General Help
---

### Post by vedster on 2011-06-01
Recently I was getting slower disk performance so I ran this command

```
sudo touch /forcefsck
```

After this, my computer was not even booting up. After selecting the kernel from GRUB I was presented with a blinking dash ( - ). Fast forward a couple of other things I finally get to the Ubuntu splash screen with it saying (Checking disks.. ). After that finished, it rebooted automatically and did it again. Later it proceeded to the usual Ubuntu boot screen and just got stuck there. There is a button on my keyboard that is used for switching displays, I clicked that and was provided information regarding the boot process. 

The place it got stuck on was 
```
Stopping System V runlevel compatibility   [OK]  
```

After that, nothing happens. I have no idea where to go from here, any suggestions? 


P.S. My windows partition is fully functioning.

I have also attached my results for the Boot Info script. This might help with information about the boot, partitions, etc.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   714,756,095   714,346,496   7 NTFS / exFAT / HPFS
/dev/sda3         714,756,096   976,560,127   261,804,032   f W95 Extended (LBA)
/dev/sda5         714,758,144   976,560,127   261,801,984   7 NTFS / exFAT / HPFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8AB25C8EB25C811D                       ntfs       SYSTEM
/dev/sda2        289073B890738B58                       ntfs       
/dev/sda4        2C33-35FD                              vfat       HP_TOOLS
/dev/sda5        de9d5191-151a-4345-a3a2-930962ea1c87   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 289073b890738b58
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
search --no-floppy --fs-uuid --set 289073b890738b58
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
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-24-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, Linux 2.6.35-24-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8ab25c8eb25c811d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 289073b890738b58
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set de9d5191-151a-4345-a3a2-930962ea1c87
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
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

  11.348415375 = 12.185268224   boot/grub/grub.cfg                             1
   1.515625000 = 1.627389952    boot/initrd.img-2.6.35-24-generic              2
  16.226562500 = 17.423138816   boot/initrd.img-2.6.35-25-generic              2
  13.513000488 = 14.509473792   boot/initrd.img-2.6.35-27-generic              2
   0.977989197 = 1.050107904    boot/initrd.img-2.6.35-28-generic              2
   1.281250000 = 1.375731712    boot/vmlinuz-2.6.35-24-generic                 2
  14.949356079 = 16.051748864   boot/vmlinuz-2.6.35-25-generic                 1
  12.899250031 = 13.850464256   boot/vmlinuz-2.6.35-27-generic                 1
  15.178150177 = 16.297414656   boot/vmlinuz-2.6.35-28-generic                 1
   0.977989197 = 1.050107904    initrd.img                                     2
  13.513000488 = 14.509473792   initrd.img.old                                 2
  15.178150177 = 16.297414656   vmlinuz                                        1
  12.899250031 = 13.850464256   vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=de9d5191-151a-4345-a3a2-930962ea1c87 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root de9d5191-151a-4345-a3a2-930962ea1c87
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8AB25C8EB25C811D
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 289073B890738B58
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sda5 when migrated
UUID=de9d5191-151a-4345-a3a2-930962ea1c87    /    ext4    errors=remount-ro    0    1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 394.978309631 = 424.104730624  boot/grub/core.img                             1
 449.016326904 = 482.127609856  boot/grub/grub.cfg                             1
 411.890167236 = 442.263699456  boot/initrd.img-2.6.38-8-generic               2
 368.749332428 = 395.941580800  boot/vmlinuz-2.6.38-8-generic                  1
 411.890167236 = 442.263699456  initrd.img                                     2
 368.749332428 = 395.941580800  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 fd 35 33 2c 4e  4f 20 4e 41 4d 45 20 20  |..).53,NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by Rubi1200 on 2011-06-02
Hi vedster,
just want to get some things clear before recommending a course of action.

1. you appear to have a working Wubi install and a separate partition with Ubuntu 11.04 which appears to have been migrated; was this by design?

2. which install is giving you problems and on which partition did you run the fsck?

Once we have this information, I can suggest some things to try.

Thanks.

---

### Post by vedster on 2011-06-02
Oh yes, I should've mentioned that.
The Wubi install is very old and I've migrated to a dedicated partition 4 months ago. The problem is with the dedicated partition.

---

### Post by Rubi1200 on 2011-06-02
There doesn't appear to be anything wrong with the results from an initial look, but sometimes this can be deceptive.

Here are some things to try and narrow the problem down:

1. when the computer boots and you see the entry for Ubuntu on sda5 press "e" to edit.

Using the arrow keys, navigate to the line that ends with quiet splash and add nomodeset so it looks like this:
> quiet splash nomodeset

Then "Ctrl" + "x" to boot.

I want to see if this is a graphics issue rather than a booting problem. Let me know how this works out.

The use of nomodeset is a generic boot option; for more information see here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If doing this solves the problem, we can make it more permanent.

If not, go to the next step.

2. reinstall the GRUB bootloader from the LiveCD:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
When the command completes reboot the computer taking out the CD.

When you boot back into Ubuntu, run the following command:
```
sudo update-grub

```

If this also does not help, go to the next step.

3. go into BIOS and check if it sees the whole 500GB drive. If there is an option to enable the large drive option, do so.

Your GRUB files are towards the end of the drive and this may be causing complications.

I can explain some methods to deal with this, but first try the other steps and tell me what BIOS shows before we go there.

If any of this is unclear, just ask and I will try and explain better.

---

### Post by vedster on 2011-06-02
I added the nodomeset option, after doing that I was presentes with the blinking line and then this
```
Intel ips 0000:00:1f:6: failed to get i915 symbols, graphics turbo disabled*

Ubuntu 11.04 localhost.localdomain tty1

Localhost.localdomain login:
```

---

### Post by Rubi1200 on 2011-06-02
It seems this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651104](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651104)

this thread also discusses it:
[http://ubuntuforums.org/showthread.php?t=1594981](http://ubuntuforums.org/showthread.php?t=1594981)

In post # 25 onwards in the first link possible solutions are discussed.

In the second link, from about page 3 or so.

Hope this helps.

---

### Post by vedster on 2011-06-02
> The launchpad link said to do this
[QUOTE]There is a work around
1. add intel_ips to the blacklist
***echo "blacklist intel_ips" >> /etc/modprobe.d/blacklist.conf
2. add i915 and intel_ips to /etc/modules
***echo -e "i915/nintel_ips" >> /etc/modules


How do I do this?[/QUOTE]

EDIT: I got this to work, and ran the commands. However to no avail. Booting normally just ends up at the same spot and then adding nodomeset ends up going to the tty terminal directly. I also don't think this is a graphical issue as it suddenly popped up, also I've heard very few complaints about integrated intel graphics.

I should also add that if this is a graphical problem, I have a HP DM4-1050ca with an i5-450m Processor and Intel HD integrated graphics. No discrete GPU. 

So, what would the next step be?

---

### Post by Rubi1200 on 2011-06-03
>  So, what would the next step be? 	
To be honest, I don't really know.

But, in the second link I gave you take a look at post # 94. Apparently, there is also another possible method to deal with this.

Certainly worth trying in my opinion.

---

### Post by vedster on 2011-06-03
I have tried that already. :(

However, what I think the problem is after attempting to run fsck a bunch of times i ended up currupting some system files. Is there anyway I can repair all of those files? Maybe a command that is use to repair system files and packages? I really don't want to have to format that partition and install again..

---

### Post by Rubi1200 on 2011-06-04
I doubt fsck would have caused this kind of damage as you call it. The command is used to repair file-systems, not break them.

From what I have read this problem is a graphics/kernel issue and I would research more from that angle.

Sorry I can't be of more help with this as I don't think there is a quick and easy fix.

---

### Post by vedster on 2011-06-04
Alright, thanks for your help anyway. I've determined this is probably a hardware problem because of the tonnes of DRDY Errors. A failing hard drive or so. I've backed up everything off my home drive and now I'm running [this]("http://ubuntuforums.org/showpost.php?p=4587647&postcount=1") script. It reinstalls all packages without reinstalling Ubuntu, hopefully this recovers all the missing/corrupted packages. Hardware wise, I'll have to order a new hard drive ASAP. 

Anyway, thanks for all your help.

---

### Post by Romu on 2011-06-25
Hi,
I think we can suspect fsck as we are few people from the French ubuntu forums with this issue.

Personally, my PC did fsck this morning and now refuses to boot, stuck at the "Stopping System V..." trace.

I tried to start with holding the shift key to display the grub menu, no luck, I can't get it.

My PC is pretty new, a hardware problem is always possible, but this internal HP tests don't detect anything.

If someone has a fix or just a tip to make some progresses, I'll take it.

Thanks.

---

### Post by Romu on 2011-06-25
@rubi1200: I've just tried to boot with the "nomodeset" option, and same, always stuck to "Stopping System V...".

---

### Post by vedster on 2011-06-25
I'm sorry to hear that. The reason the computer doesn't boot is because of bad sectors on the hard drive currupting some of the essential system files. I played around with everything, even ran a script that reinstalls every single package. I hate to say this but the only thing you really CAN do is use a LiveCD and recover all your files. Format your harddrive and reinstall Ubuntu. That's what I had to do. Did you by any chance migrate from Wubi?

---

### Post by Romu on 2011-06-25
hi vedster and thanks for the help.

Before finding this thread, I created a new one and some has just given me a trick to try, its [here]("http://ubuntuforums.org/showthread.php?p=10979754#post10979754").

Now, i'm backuping my files, and give this trick a try, if it doesn't work, I'll re-install, and as I've seen I can now install Gnome 3 without installing Unity at all, that's not a bad thing.

I'll post the results of the tricks as soon as I could have tried it.

---

### Post by Romu on 2011-06-27
No change with the trick. I re-installed Ubuntu from scratch :(

---

### Post by Romu on 2011-06-27
@vedster: a little question, du you run Unity? or did you install Gnome3 on Natty?

We are now 4 people from France with the same problem, and all run Gnome3 on Natty.

---

### Post by dinomarc on 2011-07-27
> **Romu said:**
> @vedster: a little question, du you run Unity? or did you install Gnome3 on Natty?

We are now 4 people from France with the same problem, and all run Gnome3 on Natty.

Same here after installing gnome 3 it got screwed up. Luckily only on my testdrive.

---

### Post by vedster on 2011-07-27
I've had this problem a long time ago and a lot has changed. Nothing could fix my problems so I just re-formatted that partition and re installed Ubuntu from scratch. That actually solved all of my problems. After I reinstalled it, I did install gnome3 and it has been working perfectly fine since. I did use the ppa version though, not too sure what you used. I don't think gnome3 is the issue.

---

### Post by dinomarc on 2011-07-27
> **vedster said:**
> I've had this problem a long time ago and a lot has changed. Nothing could fix my problems so I just re-formatted that partition and re installed Ubuntu from scratch. That actually solved all of my problems. After I reinstalled it, I did install gnome3 and it has been working perfectly fine since. I did use the ppa version though, not too sure what you used. I don't think gnome3 is the issue.

Well never mind, i used the opportunity to install a daily build of Oneiric Ocelot.

---

