---
title: "Windows Ubuntu dual boot install woes MBR missing"
date: 2011-01-18
forum: General Help
---

### Post by TheAp on 2011-01-18
So for a while I have had Windows 7 installed on my Pc, and recently installed Ubuntu on a second hard drive in order to dual boot. The problem is that my Windows Os is on C: drive but I think the MBR was on the second hard drive (because of problems during original install) once I installed Ubuntu 10 via live cd, windows will no longer boot. SOOOO... I followed almost every fix guide here which said to use a windows repair disk to run bootrec.exe./FixMbr. Now I cannot boot either OS. When booting I get the BIOS screen and then a message that says no Operating system. Please help!

I also tried the other options in the bootrec.exe and also the auto repair thing and the auto repair says that the file system is corrupt...

---

### Post by Quackers on 2011-01-18
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by TheAp on 2011-01-19
```

            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdg

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdg2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdg5 starts 
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

/dev/sda1    *          2,048   601,374,719   601,372,672  83 Linux
/dev/sda2         601,376,766   625,141,759    23,764,994   5 Extended
/dev/sda5         601,376,768   625,141,759    23,764,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg2    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sdg5              16,128 2,930,272,064 2,930,255,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        65ee541f-b338-4f80-a0ba-8f02a3491357   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c1367d2-039b-4433-81cb-a054753088d6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       MAIN DISK                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg2: PTTYPE="dos" 
/dev/sdg5        ACE998D9FE2BF308                       ntfs       Media Storage                 
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
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
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 24483ab0483a809a
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
UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c1367d2-039b-4433-81cb-a054753088d6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 262.1GB: boot/grub/core.img
 279.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
 262.2GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
 262.2GB: vmlinuz
    .6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by TheAp on 2011-01-19
```

            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdg

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdg2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdg5 starts 
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

/dev/sda1    *          2,048   601,374,719   601,372,672  83 Linux
/dev/sda2         601,376,766   625,141,759    23,764,994   5 Extended
/dev/sda5         601,376,768   625,141,759    23,764,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg2    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sdg5              16,128 2,930,272,064 2,930,255,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        65ee541f-b338-4f80-a0ba-8f02a3491357   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c1367d2-039b-4433-81cb-a054753088d6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       MAIN DISK                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg2: PTTYPE="dos" 
/dev/sdg5        ACE998D9FE2BF308                       ntfs       Media Storage                 
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
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
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 24483ab0483a809a
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
UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c1367d2-039b-4433-81cb-a054753088d6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 262.1GB: boot/grub/core.img
 279.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
 262.2GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
 262.2GB: vmlinuz
    .6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by TheAp on 2011-01-19
Accidental Duplicate Post Please Delete

---

### Post by Quackers on 2011-01-19
deleted

---

### Post by Quackers on 2011-01-19
Which hard drive is set to boot first in the bios please?
For the moment Ubuntu cannot boot, as you don't have grub installed. We can fix that.

---

### Post by TheAp on 2011-01-19
i have tried setting them all to boot first, but right now i think it was on the dvd drive.

---

### Post by amsterdamharu on 2011-01-19
Before you messed up the grub mbr with Windows you should have had a working menu entry for windows 7, your grub.cfg (it's the menu after the bios) shows the following:

```
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 24483ab0483a809a
    chainloader +1
}
```

Did you not see this when you booted before and choose to "fix" things with the Windows CD?

So Ubuntu is using the first harddisk and Windows is using the second one, what you can do is boot with a live CD and repair grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
From the live Cd you can execute the following commands:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
If there are any errors please select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by Quackers on 2011-01-19
OK, so from the live cd desktop please open System > Admin > gparted.
On the right side towards the top you will see a little box showing /dev/sda with a little down arrow. Click the arrow then select /dev/sdb from the drop down box and in the main window sdb will be shown.
Right-click on sdb1 and select "manage flags" then in the new window check the box marked "boot" then OK the window. CLick on the green arrow to apply the change.
Then reboot, but go into your bios and set the Windows drive (probably the second one) as second boot device (behind dvd drive if no dvd is in the drive) and save the change and reboot.
Hopefully Windows will now boot.

---

### Post by amsterdamharu on 2011-01-19
Ok, got the double post too. The post didn't show and got a server timeout.

---

### Post by amsterdamharu on 2011-01-19
Ok, got the double post too. The post didn't show and got a server timeout.

---

### Post by Quackers on 2011-01-19
OK, so from the live cd desktop please open System > Admin > gparted.
On the right side towards the top you will see a little box showing /dev/sda with a little down arrow. Click the arrow then select /dev/sdb from the drop down box and in the main window sdb will be shown.
Right-click on sdb1 and select "manage flags" then in the new window check the box marked "boot" then OK the window. CLick on the green arrow to apply the change.
Then reboot, but go into your bios and set the Windows drive (probably the second one) as second boot device (behind dvd drive if no dvd is in the drive) and save the change and reboot.
Hopefully Windows will now boot.

---

### Post by Quackers on 2011-01-19
I have replied to your post already but my post has not appeared.
I'm sorry, but I just can't post any more. Nothing is appearing and it's impossible to help you like this. If this message ever gets to the thread I apologise. I will return later on and help if I can.

---

### Post by TheAp on 2011-01-19
OK did that successully. Here is what i get now. 

Rebooted
Selected one of my two 300 gig HDD to boot first (wild guess as to which is which)
Got this message: 
"Windows Failed to start a recent hardware or software change.. yada yada"

... Then it reccommends using the repair disk.

I rebooted and got the Linux OS boot chooser, and the same message.

Should i do use the Win7 Repair Disk?

---

### Post by TheAp on 2011-01-19
OK did that successully. Here is what i get now. 

Rebooted
Selected one of my two 300 gig HDD to boot first (wild guess as to which is which)
Got this message: 
"Windows Failed to start a recent hardware or software change.. yada yada"

... Then it reccommends using the repair disk, and says the boot selection failed because a required device is inaccessible.

I rebooted and got the Linux OS boot chooser, and the same message.

Should i do use the Win7 Repair Disk?

---

### Post by TheAp on 2011-01-19
THe vista boot file is there because i installed Win7 over it. Long speech avoided, I had problems during install, and so the vista boot file is still there. is there any way to get rid of it? or use it?

---

### Post by Quackers on 2011-01-19
Hi, sorry for my absence. So that we can see if anything has changed will you please re-run the boot script and post the new output, thanks.

---

### Post by TheAp on 2011-01-20
```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
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

/dev/sda1    *          2,048   601,374,719   601,372,672  83 Linux
/dev/sda2         601,376,766   625,141,759    23,764,994   5 Extended
/dev/sda5         601,376,768   625,141,759    23,764,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sdc5              16,128 2,930,272,064 2,930,255,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        65ee541f-b338-4f80-a0ba-8f02a3491357   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c1367d2-039b-4433-81cb-a054753088d6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       MAIN DISK                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        ACE998D9FE2BF308                       ntfs       Media Storage                 
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


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
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
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
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 24483ab0483a809a
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
UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c1367d2-039b-4433-81cb-a054753088d6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 262.1GB: boot/grub/core.img
 279.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
 262.2GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
 262.2GB: vmlinuz
    .6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by amsterdamharu on 2011-01-20
I assume grub starts normal and you get a menu where you can choose between Ubuntu and Windows. When you choose "Windows Vista (loader) (on /dev/sdb1)"  you get an error saying something like "Windows Failed to start a recent hardware or software change.. yada yada".

If it was XP it would be as easy as just changing the boot.ini to tell Windows loader where to find Windows (harddisk and partition). Since Vista I have no idea because I've never used it and have no experience with it.

You could try removing the Ubuntu harddisk and see if it boots with only Windows in there. I suspect it'll work just fine it's just that you have to tell the Windows loader to look on the second harddisk.

I am not totally sure you need drivemap in grub for your Windows entry, it is used for DOS operating systems but Win 7 is much bigger boy that DOS I think:
[http://www.gnu.org/software/grub/manual/grub.html#drivemap](http://www.gnu.org/software/grub/manual/grub.html#drivemap)

---

### Post by Quackers on 2011-01-20
According to the script output you have Windows 7 on sdb. The Windows loader is correct and Ubuntu is picking it up. There should be no reason why you cannot boot Win 7 from the grub menu, if the Ubuntu drive is set to boot first.
What is happening when you try that?

Windows may want a chkdsk to be run.

---

### Post by TheAp on 2011-01-20
```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
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

/dev/sda1    *          2,048   601,374,719   601,372,672  83 Linux
/dev/sda2         601,376,766   625,141,759    23,764,994   5 Extended
/dev/sda5         601,376,768   625,141,759    23,764,992  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sdc5              16,128 2,930,272,064 2,930,255,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        65ee541f-b338-4f80-a0ba-8f02a3491357   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c1367d2-039b-4433-81cb-a054753088d6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       MAIN DISK                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        ACE998D9FE2BF308                       ntfs       Media Storage                 
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


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
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 ro single 
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
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 65ee541f-b338-4f80-a0ba-8f02a3491357
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 24483ab0483a809a
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
UUID=65ee541f-b338-4f80-a0ba-8f02a3491357 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c1367d2-039b-4433-81cb-a054753088d6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 262.1GB: boot/grub/core.img
 279.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
 262.2GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
 262.2GB: vmlinuz
    .6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by TheAp on 2011-01-20
> **amsterdamharu said:**
> I assume grub starts normal and you get a menu where you can choose between Ubuntu and Windows. When you choose "Windows Vista (loader) (on /dev/sdb1)"  you get an error saying something like "Windows Failed to start a recent hardware or software change.. yada yada". 

That is part of the problem. The Vista boot file is there, but I don't have Vista installed anymore (thank god/allah)

> 

You could try removing the Ubuntu harddisk and see if it boots with only Windows in there. I suspect it'll work just fine it's just that you have to tell the Windows loader to look on the second harddisk.

 

Tried it...

> 

I am not totally sure you need drivemap in grub for your Windows entry, it is used for DOS operating systems but Win 7 is much bigger boy that DOS I think:
[http://www.gnu.org/software/grub/man/ual/grub.html#drivemap]("http://www.gnu.org/software/grub/manual/grub.html#drivemap")

Sorry, you went over my head there... Can you dumb it down a grade level for a newbie?

Thanks again for your help you guys.

---

### Post by amsterdamharu on 2011-01-20
If you only have the Windows harddisk in there it still doesn't boot? That is strange because grub and your Ubuntu intstall are completely out of the picture. You should repair it with the Windows disc and see if it starts and then maybe add the Ubuntu harddisk (as first harddsik)

Using drivemap is for an OS that can only start if it's on the first harddisk like DOS. I think you don't need that for win7 so leave that for now.

---

### Post by TheAp on 2011-01-20
ok I tried the unplugging the hard drives again, and it still didnt work. THen I figured out which was which, and Un-plugged the UBuntu HDD and booted into the repair CD for Win7, and the first thing it said was that the startup options were wrong, it fixed it , then rebooted, and Win7 started! 

Now I am scared to plug the other HD back in!

---

### Post by amsterdamharu on 2011-01-20
Do you know what are the primary and secondary Sata ports? Do you know if you inserted the harddisk as first or second one?

Check your bios and see if it's plugged in on the primary or secondary. If it's secondary you should be able to plug in the Ubuntu harddisk (I think ....). I don't know too much about Windows and why it complains when you add a harddisk. I know how to fix this in XP.

---

### Post by TheAp on 2011-02-02
Sorry about the delay. this forum has been jacked up. Problem is solved. Thanks very much.:guitar:
How do i mark this as solved??

---

### Post by amsterdamharu on 2011-02-02
Good to hear you solved your problem, you can mark it solved using the "thread tools" on the top of the page.

---

