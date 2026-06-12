---
title: "WinXP lost after UBUNTU 10:10 install"
date: 2011-01-27
forum: General Help
---

### Post by madashell on 2011-01-27
hi Im new and as innocent as a newborn when it comes to Linux but after  having a positive experience running a previous version of Ubuntu (8:10 Intrepid Ibex)  I thought it may be nice to update to a more recent version so I  obtained the CD version of Ubuntu 10:10 Maverick Meerkat
My main OS is Windows XP Professional (SP3) and I installed and ran 8:10  as a programme within windows, unfortunately when I tried to do the  same with 10:10 I had a problem so decided to install on boot-up using  the option to run both OS side-by-side.
Now I have lost the option on boot-up to select which OS I want to use!  It automatically goes straight into the login page for the Ubuntu there  is no sign of WinXP
so PLEASE Help!
I am desperate :sad:  I have personal files on Windows I just can NOT lose! its only 4 days  since I put all my grand-daughters first birthday pictures and film on  there!

I have run : "sudo  update-grub"
and no windows show
I have also run the codes: " sudo grub-install /dev/sdc" & "sudo update-grub # just for good measure"
still no sign of windows
here is my most recent result report using Boot Info Script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/nvidia_ecgdcdff and looks on 
    the same drive in partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_ecgdcdff1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   105,172,513   105,172,451   7 HPFS/NTFS
/dev/sdc2         105,172,990   156,296,384    51,123,395   f W95 Ext d (LBA)
/dev/sdc5         124,792,983   156,296,384    31,503,402   7 HPFS/NTFS
/dev/sdc6         105,172,992   123,858,943    18,685,952  83 Linux
/dev/sdc7         123,860,992   124,792,831       931,840  82 Linux swap / Solaris


Drive: nvidia_ecgdcdff ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_ecgdcdff: 80.0 GB, 80026337280 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_ecgdcdff1   *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_ecgdcdff1 1024252124250AF4                       ntfs       Ayshea                        
/dev/mapper/nvidia_ecgdcdff: PTTYPE="dos" 
/dev/sda1        1024252124250AF4                       ntfs       Ayshea                        
/dev/sda                                                nvidia_raid_member                               
/dev/sdc1        3A6478AC64786C8F                       ntfs       Christopher                   
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        E298535898532A75                       ntfs       Caitlin                       
/dev/sdc6        6b8d583d-0135-40ee-9b61-bbee6229bfcf   ext4                                     
/dev/sdc7        ed133039-97ca-41e2-bd1c-c5e683cd3422   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6b8d583d-0135-40ee-9b61-bbee6229bfcf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=6b8d583d-0135-40ee-9b61-bbee6229bfcf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=ed133039-97ca-41e2-bd1c-c5e683cd3422 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


  60.4GB: boot/grub/core.img
  56.4GB: boot/grub/grub.cfg
  55.3GB: boot/initrd.img-2.6.35-22-generic
  55.2GB: boot/initrd.img-2.6.35-24-generic
  61.2GB: boot/vmlinuz-2.6.35-22-generic
  61.3GB: boot/vmlinuz-2.6.35-24-generic
  55.2GB: initrd.img
  55.3GB: initrd.img.old
  61.3GB: vmlinuz
  61.2GB: vmlinuz.old

========================== nvidia_ecgdcdff1/boot.ini: ==========================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```I have also used the code "sudo os-prober" and there is no information whatsoever!
thats as far as I have got, any help would be most appreciated, please remember I am very much a novice with Linux/Ubuntu & codes etc so please keep it as simple as possible
many thanks in anticipation
Guy

---

### Post by b0b138 on 2011-01-27
are you running raid?  Do you have 2 or 3 hard disks?

---

