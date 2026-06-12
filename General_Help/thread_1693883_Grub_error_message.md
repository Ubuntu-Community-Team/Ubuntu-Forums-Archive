---
title: "Grub error message"
date: 2011-02-23
forum: General Help
---

### Post by An Sanct on 2011-02-23
When booting, I get this error:

> error: no argument specified
press any key to continue...


And then after a few seconds, the boot goes on normally.

A quick search (google + forum), found me [this thread]("http://ubuntuforums.org/showthread.php?t=1662142"), but that solution doesn't work for me, I still get this error... what can I do?

---

### Post by An Sanct on 2011-02-26
Anybody?

---

### Post by Starfleet on 2011-02-26
I've not seen this error on any of my machines and so I am probably not that helpful to you. I take it you are running a dual boot, is that correct?  In this situation I wonder if a reload of grub might solve the problem. I have found from time to time a reload can save lots of hard work and is simple to do. You may have seen the link below but it's there anyway in case it helps. It's all things Grub. 

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Good luck

---

### Post by An Sanct on 2011-02-27
Thank you Starfleet.

Yes, I am running both Maverick and Natty on my comp. I've already reloaded grub, but It doesn't help. It seems as if the grub command "vga=xxx" is the thing, that is spoiling my boot.

---

### Post by Rubi1200 on 2011-02-27
Please do the following either from within Ubuntu or the LiveCD:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Also post the contents of /etc/default/grub

---

### Post by An Sanct on 2011-02-28
Here's the results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Be.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders, total 125206528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   125,204,479   125,202,432  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   272,630,893   272,630,860 Linux or Data
/dev/sdb2   1,886,416,896 1,953,523,711    67,106,816 Linux Swap
/dev/sdb3     272,631,808   545,261,567   272,629,760 Linux or Data
/dev/sdb4     545,261,568 1,886,416,895 1,341,155,328 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62    15,683,519    15,683,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       88ffeb6a-50a5-4040-ad40-9cb379d719e4   ext3                                     
/dev/sda1        f66f4cf1-1e93-4b57-9acc-66845f7810f2   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        22d0d4b1-72d4-4125-99ff-8fc403b05d93   ext4                                     
/dev/sdb2        59f2578d-350e-482a-b998-c361fcfe5c39   swap                                     
/dev/sdb3        186cb39f-297e-441a-a5a6-b934d8ff4c22   ext4       sec                           
/dev/sdb4        dc1356bf-6675-4a6f-b07a-eb4979b378e2   ext4       warehouse                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        DAFA-329C                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/f66f4cf1-1e93-4b57-9acc-66845f7810f2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb4        /media/warehouse         ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-2-generic
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
UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 /               ext4    errors=remount-ro 0       1

#swap after
UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0
#warehouse
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2  /media/warehouse  ext4  defaults,noatime  0  0


=================== sda1: Location of files loaded by Grub: ===================


  15.2GB: boot/grub/core.img
  49.7GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-22-generic
   2.5GB: boot/initrd.img-2.6.35-25-generic
  15.3GB: boot/vmlinuz-2.6.35-22-generic
  15.3GB: boot/vmlinuz-2.6.35-25-generic
   2.5GB: initrd.img
   1.1GB: initrd.img.old
  15.3GB: vmlinuz
  15.3GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
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
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-5-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-4-generic ...'
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-3-generic ...'
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-2-generic ...'
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-2-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single splash
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0
#warehouse
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2  /media/warehouse  ext4  defaults,noatime  0  0
=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  41.0GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.38-2-generic
   2.2GB: boot/initrd.img-2.6.38-3-generic
   2.2GB: boot/initrd.img-2.6.38-4-generic
   3.6GB: boot/initrd.img-2.6.38-5-generic
    .5GB: boot/vmlinuz-2.6.38-2-generic
   1.1GB: boot/vmlinuz-2.6.38-3-generic
   2.1GB: boot/vmlinuz-2.6.38-4-generic
   3.2GB: boot/vmlinuz-2.6.38-5-generic
   3.6GB: initrd.img
   2.2GB: initrd.img.old
   3.2GB: vmlinuz
   2.1GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f8 00 00 00 00 00  |........>.......|
00000020  82 4f ef 00 b8 3b 00 00  00 00 00 00 02 00 00 00  |.O...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 9c 32 fa da 20  20 20 20 20 20 20 20 20  |..).2..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 10 2f 16 00  66 ba 00 00 00 00 bb 00  |}.f../..f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

---

### Post by Rubi1200 on 2011-02-28
An Sanct,
do me a favor please. There is a new version of the boot info script which is being worked on. It will hopefully avoid information like this:
> Grub 2 is installed in the MBR of /dev/sda and looks for Be.```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=0c8e808eba272af5ef8b5f4df4654f350526d17b'
```Then move the script to the Desktop as before and run this command in the terminal:

```
sudo apt-get install gawk
```and then:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
Post the results back here as before.
Thanks.

---

### Post by An Sanct on 2011-02-28
Okay, I followed your commands ... and here are the results:

(Note, that this time it was not from a live USB)

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders, total 125206528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   125,204,479   125,202,432  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34   272,630,893   272,630,860 Data partition (Windows/Linux)
/dev/sdb2   1,886,416,896 1,953,523,711    67,106,816 Swap partition (Linux)
/dev/sdb3     272,631,808   545,261,567   272,629,760 Data partition (Windows/Linux)
/dev/sdb4     545,261,568 1,886,416,895 1,341,155,328 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f66f4cf1-1e93-4b57-9acc-66845f7810f2   ext4       
/dev/sdb1        22d0d4b1-72d4-4125-99ff-8fc403b05d93   ext4       
/dev/sdb2        59f2578d-350e-482a-b998-c361fcfe5c39   swap       
/dev/sdb3        186cb39f-297e-441a-a5a6-b934d8ff4c22   ext4       sec
/dev/sdb4        dc1356bf-6675-4a6f-b07a-eb4979b378e2   ext4       warehouse

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb4        /media/warehouse         ext4       (rw,noatime,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-2-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 /               ext4    errors=remount-ro 0       1

#swap after
UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0
#warehouse
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2  /media/warehouse  ext4  defaults,noatime  0  0

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.229518890 = 15.278829568   boot/grub/core.img                             1
  46.318191528 = 49.733779456   boot/grub/grub.cfg                             2
   1.079101562 = 1.158676480    boot/initrd.img-2.6.35-22-generic              2
   2.383632660 = 2.559406080    boot/initrd.img-2.6.35-25-generic              2
  14.255016327 = 15.306207232   boot/vmlinuz-2.6.35-22-generic                 1
  14.259059906 = 15.310548992   boot/vmlinuz-2.6.35-25-generic                 1
   2.383632660 = 2.559406080    initrd.img                                     2
   1.079101562 = 1.158676480    initrd.img.old                                 2
  14.259059906 = 15.310548992   vmlinuz                                        1
  14.255016327 = 15.306207232   vmlinuz.old                                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
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
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /boot/vmlinuz-2.6.38-5-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-5-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-4-generic ...'
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-3-generic ...'
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-2-generic ...'
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-2-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f66f4cf1-1e93-4b57-9acc-66845f7810f2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 ro single splash
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0
#warehouse
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2  /media/warehouse  ext4  defaults,noatime  0  0--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  36.161923409 = 38.828569600   boot/grub/core.img                             1
  76.320935249 = 81.948980224   boot/grub/grub.cfg                             2
   1.382325172 = 1.484260352    boot/initrd.img-2.6.38-2-generic               3
   2.077347755 = 2.230535168    boot/initrd.img-2.6.38-3-generic               3
   2.072987556 = 2.225853440    boot/initrd.img-2.6.38-4-generic               3
   3.381588936 = 3.630953472    boot/initrd.img-2.6.38-5-generic               3
   0.515908241 = 0.553952256    boot/vmlinuz-2.6.38-2-generic                  1
   1.097962379 = 1.178928128    boot/vmlinuz-2.6.38-3-generic                  2
   1.992493629 = 2.139423744    boot/vmlinuz-2.6.38-4-generic                  2
   3.055012703 = 3.280294912    boot/vmlinuz-2.6.38-5-generic                  1
   3.381588936 = 3.630953472    initrd.img                                     3
   2.072987556 = 2.225853440    initrd.img.old                                 3
   3.055012703 = 3.280294912    vmlinuz                                        1
   1.992493629 = 2.139423744    vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

```

---

### Post by Rubi1200 on 2011-02-28
Thanks for the results again :-)

Which device is set in BIOS to boot first sda or sdb?

I notice you have a GPT disk on sdb and you are using Natty. Perhaps the error you are seeing is related to the fact that 11.04 is still in alpha?

---

### Post by An Sanct on 2011-02-28
Thank you Rubi1200.

Boot in BIOS is normally set to sda.

Yes, Natty is alpha, I'm well aware of this and always keep a live USB near, if it breaks GRUB or something else (it has already happened...). Well, Natty is alpha, but that should not interfere with how Maverick is booting (from sda grub, last reinstalled from a live Maverick USB onto sda).

Its kind of a minor problem, since it seems to be just a warning and not actually an error.

I guess, I'm going to mark this thread as solved.

---

