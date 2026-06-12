---
title: "Losing my mind... (Grub, Windows 7, Unknown Filesystem)"
date: 2011-01-26
forum: General Help
---

### Post by paranoiid on 2011-01-26
(Currently writing this using the LiveCD, and my sanity is very, very low.)

The day started as usual until I got the very bright idea to install Ubuntu. A new OS along side W7, that sounded great. I checked some guides on the Internet, it was all very straight forward. Install it and Grub will show you the OS:es when you boot up.

I installed Ubuntu, rebooted. After the BIOS messages the screen goes blank and my screen on-button begins to blink, as if trying to find a signal, I press enter, it reboots instantly. After BIOS messages I get to a screen that says "GRUB error: uknown filesystem              grub rescue>"

I've looked through everything here and nothing works. I've tried to fix the mbr-thingy using Windows Repair and even though it says "one partition was updated with new boot-thingy" when I reboot, I get into that very same grub rescue.

I think my setup has something to do with it. I run RAID0 (2x360Gb hard drives), first having C: at 50Gb and then the rest as F: for programs and such. What I did was that I shrunk the F: part and then used that as partition for Ubuntu. 

Also please have a look at these screenshots, my partitiontables and such seems completely wacky thanks to the raid: 

[IMG]http://data.fuskbugg.se/dipdip/__________________________________Screenshot.png[/IMG]

[IMG]http://data.fuskbugg.se/dipdip/___________Screenshot-1.png[/IMG]

Where should the boot-loader go? I'm very, very new at this. I've had Ubuntu Netbook remix on my netbook for a time but still treat me as an utter beginner. 

Please help, I beg of you. You can have all of my kingdom and riches.

---

### Post by Mark Phelps on 2011-01-26
To fix Win7, you have to generally run Startup Repair three times.  It only fixes one thing at a time and MBR repair is one of the last things it does.

---

### Post by Rubi1200 on 2011-01-26
Not only should you follow the advice posted by Mark Phelps, but when you are done and Windows is booting normally again (we hope), then stop and take a deep breath.

Once you have done that, boot a LiveCD and do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results, we can advise you as to the next step to either recover Ubuntu or whatever else you decide to do.

---

### Post by paranoiid on 2011-01-26
> **Mark Phelps said:**
> To fix Win7, you have to generally run Startup Repair three times.  It only fixes one thing at a time and MBR repair is one of the last things it does.

But I did it manually through the repair-cmd thing! And it's all so f*cking weird. It says I have 2 Windows 7 copies, one in G and one in F. I don't have W7 in either G and F but G has the same size as the Partition of my Windows 7 (about 50Gb) but when I try to select that it says that my LiveCD can't do anything about it since it is another version (which is very weird, considering I used it to actually install W7)

ALSO: After doing that whole grub install root directory process in both RAID2 and RAID4 I now get "No module name found." error instead. And it isn't helping my sanity!

---

### Post by paranoiid on 2011-01-26
> **Rubi1200 said:**
> Not only should you follow the advice posted by Mark Phelps, but when you are done and Windows is booting normally again (we hope), then stop and take a deep breath.

Once you have done that, boot a LiveCD and do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results, we can advise you as to the next step to either recover Ubuntu or whatever else you decide to do.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
 => Grub 2 is installed in the MBR of /dev/mapper/isw_bfacdjdfi_RAID and looks 
    on the same drive in partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_bfacdjdfi_RAID1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
Failed to open $MFT/$BITMAP: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/dm-2': No such file or directory
Failed to open $MFT/$BITMAP: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/dm-2': No such file or directory

isw_bfacdjdfi_RAID2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

isw_bfacdjdfi_RAID3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_bfacdjdfi_RAID4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/sda3         102,400,000 1,188,556,799 1,086,156,800   7 HPFS/NTFS
/dev/sda4       1,188,556,800 1,250,275,327    61,718,528  83 Linux

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,465,145,343 1,465,143,296   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   416,695,999   416,695,937   7 HPFS/NTFS


Drive: isw_bfacdjdfi_RAID ___________________ _____________________________________________________

Disk /dev/mapper/isw_bfacdjdfi_RAID: 640.1 GB, 640141230080 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250275840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bfacdjdfi_RAID1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_bfacdjdfi_RAID2            206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/mapper/isw_bfacdjdfi_RAID3        102,400,000 1,188,556,799 1,086,156,800   7 HPFS/NTFS
/dev/mapper/isw_bfacdjdfi_RAID4      1,188,556,800 1,250,275,327    61,718,528  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_bfacdjdfi_RAID1 76A8DE94A8DE51EB                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID2 6C5C591D5C58E2FE                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID3 F4E07EEAE07EB28A                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID4 fa3079d2-71b3-4029-a6b9-dcc7867f4710   ext4                                     
/dev/mapper/isw_bfacdjdfi_RAID: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb1        1C50F41850F3F67C                       ntfs       Warez                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        D2A27BB5A27B9D23                       ntfs       Music                         
/dev/sdd: PTTYPE="dos" 
error: and: No such file or directory
error: /dev/mapper//dev/sda:: No such file or directory
error: /dev/mapper//dev/sdc:: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: discovered: No such file or directory
error: formats: No such file or directory
error: "isw": No such file or directory
error: isw)!: No such file or directory
error: "pdc": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bfacdjdfi_RAID
isw_bfacdjdfi_RAID1
isw_bfacdjdfi_RAID2
isw_bfacdjdfi_RAID3
isw_bfacdjdfi_RAID4

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============ isw_bfacdjdfi_RAID2: Location of files loaded by Grub: ============


    ??GB: boot/grub/core.img

=================== isw_bfacdjdfi_RAID4/boot/grub/grub.cfg: ===================

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
set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
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
    set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
    search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fa3079d2-71b3-4029-a6b9-dcc7867f4710 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
    search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fa3079d2-71b3-4029-a6b9-dcc7867f4710 ro single 
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
    set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
    search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bfacdjdfi_RAID,msdos4)'
    search --no-floppy --fs-uuid --set fa3079d2-71b3-4029-a6b9-dcc7867f4710
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

======================== isw_bfacdjdfi_RAID4/etc/fstab: ========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bfacdjdfi_RAID4 /               ext4    errors=remount-ro 0       1

============ isw_bfacdjdfi_RAID4: Location of files loaded by Grub: ============


 621.5GB: boot/grub/core.img
 632.3GB: boot/grub/grub.cfg
 620.2GB: boot/initrd.img-2.6.35-22-generic
 621.7GB: boot/vmlinuz-2.6.35-22-generic
 620.2GB: initrd.img
 621.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=======Devices which don't seem to have a corresponding hard drive==============

sdc: "pdc" and "isw" formats discovered (using isw)! sda: "pdc" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: only one argument allowed for this option
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
ERROR: only one argument allowed for this option

```EDIT: after doing the grub reinstall in the drive letter option (thought you were supposed to do it in the drive letter and partition path) I now get the error: "File not found." 
So I have gone from: " unknown filesystem" , to " module not found" , to " file not found." 

It feels like I'm just stumbling in the dark here, trying to press buttons and nothing works. Now including in the price is also my princess, my kingdom and my riches.

EDIT2: Now when I install it to a partion of sdd1 I got into Ubuntu. I thought it was because I installed the boot loader to the RAID (not RAID#) but when i tried to install it once more on RAID4 i got the same unknown filesystem error.

---

