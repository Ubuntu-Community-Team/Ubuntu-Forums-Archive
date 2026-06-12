---
title: "Grub and RAID0 makes sad Ubuntu?"
date: 2011-01-26
forum: General Help
---

### Post by paranoiid on 2011-01-26
Today I tried installing Ubuntu. After 8 hours, I'm now inside my own computer again. On Ubuntu, which wouldn't ever want to install on RAID4 (the partition of the RAID that I had assigned for it).

I'm totally, totally new to this but the Grub thing seem to dislike raid. My Windows 7 was installed on that RAID and now it refuses to let me back in. 

Here's the boot script thing: 
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

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_bfacdjdfi_RAID1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
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
    Boot files/dirs:   

isw_bfacdjdfi_RAID3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

/dev/sda3 ends after the last sector of /dev/sda

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
/dev/sdd2         416,696,320   480,583,679    63,887,360  83 Linux
/dev/sdd3         480,585,726   488,396,799     7,811,074   5 Extended
/dev/sdd5         480,585,728   488,396,799     7,811,072  82 Linux swap / Solaris


Drive: isw_bfacdjdfi_RAID ___________________ _____________________________________________________

Disk /dev/mapper/isw_bfacdjdfi_RAID: 640.1 GB, 640141230080 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250275840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bfacdjdfi_RAID1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_bfacdjdfi_RAID2            206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/mapper/isw_bfacdjdfi_RAID3        102,400,000 1,188,556,799 1,086,156,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_bfacdjdfi_RAID1 76A8DE94A8DE51EB                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID2 6C5C591D5C58E2FE                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID3 F4E07EEAE07EB28A                       ntfs                                     
/dev/mapper/isw_bfacdjdfi_RAID: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb1        1C50F41850F3F67C                       ntfs       Warez                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        D2A27BB5A27B9D23                       ntfs       Music                         
/dev/sdd2        356d6307-dffc-48b4-b2ed-0d20b93c4db9   ext4                                     
/dev/sdd3: PTTYPE="dos" 
/dev/sdd5        6e4d423a-97b6-4f99-88a7-b1d2facadcdd   swap                                     
/dev/sdd: PTTYPE="dos" 
error: and: No such file or directory
error: /dev/mapper//dev/sda:: No such file or directory
error: /dev/mapper//dev/sdc:: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
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

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd2        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdd2/boot/grub/menu.lst: ===========================

Windows 7
root (hd0,0)
savedefault
makeactive
chainloader +1

=========================== sdd2/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos2)'
search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos2)'
search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
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
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=356d6307-dffc-48b4-b2ed-0d20b93c4db9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=356d6307-dffc-48b4-b2ed-0d20b93c4db9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=356d6307-dffc-48b4-b2ed-0d20b93c4db9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=356d6307-dffc-48b4-b2ed-0d20b93c4db9 ro single 
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
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 356d6307-dffc-48b4-b2ed-0d20b93c4db9
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

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=356d6307-dffc-48b4-b2ed-0d20b93c4db9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=6e4d423a-97b6-4f99-88a7-b1d2facadcdd none            swap    sw              0       0

=================== sdd2: Location of files loaded by Grub: ===================


 224.2GB: boot/grub/core.img
 215.7GB: boot/grub/grub.cfg
 224.2GB: boot/grub/menu.lst
 214.4GB: boot/initrd.img-2.6.35-22-generic
 214.4GB: boot/initrd.img-2.6.35-24-generic
 224.3GB: boot/vmlinuz-2.6.35-22-generic
 224.3GB: boot/vmlinuz-2.6.35-24-generic
 214.4GB: initrd.img
 214.4GB: initrd.img.old
 224.3GB: vmlinuz
 224.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3



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
ERROR: only one argument allowed for this option
```

My Windows 7 is on RAID2 (or isw_*lotsofsigns*RAID2) I believe. How do I get back in? I've been googling for 2 hours, tried everything I've come across but alas, nothing... I'm here on my bare knees: please help!

---

### Post by ronparent on 2011-01-26
Is the win install on a raid 0 set. Which drives comprise that set? 

This statement makes no sense to me. It is the correct location for a grub 2 boot loader to boot to a raid but doesn't point to a valid partition to load grub.
> => Grub 2 is installed in the MBR of /dev/mapper/isw_bfacdjdfi_RAID and looks 
    on the same drive in partition #2 for (,msdos2)/boot/grub.

This statement makes no sense since there is no Ubuntu (or grub) at that location.
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

If you can give me some idea of what is in whch disk or array I can probably tell you what to fix.

---

### Post by paranoiid on 2011-01-27
> **ronparent said:**
> Is the win install on a raid 0 set. Which drives comprise that set? 

This statement makes no sense to me. It is the correct location for a grub 2 boot loader to boot to a raid but doesn't point to a valid partition to load grub.


This statement makes no sense since there is no Ubuntu (or grub) at that location.


If you can give me some idea of what is in whch disk or array I can probably tell you what to fix.
RAID = the drive letter to the raid, the entire disk. 
RAID1 = the 100mb windows 7 takes for system things.
RAID2 = my 50gb windows 7 partition
RAID3 = my (about)540gb partition for games/programs
RAID4 = my linux partition. (about 30Gb)

---

### Post by psusi on 2011-01-27
It looks like you have two drives in a raid with windows, and one that is on its own where you have installed Ubuntu.  The problem is that you put the boot loader on the raid, and it is trying to boot from the raid instead of the third drive, which isn't going to work.

If you want Ubuntu on the third drive, then just install grub there too and set your bios to boot from that instead of the raid.

---

### Post by ronparent on 2011-01-27
Your drive tally doesn't agree with the result.txt from the boot script. The results shows no RAID4? The output of 'ls /dev/mapper' agrees with that. You are showing an Ubuntu 10,10 install on sdd but no grub boot loader points to that location. There is a possibility that the win 7 install is in accessibly be cause of some corruption to the raid but we can dealt with that later. 

> The problem is that you put the boot loader on the raid, and it is trying to boot from the raid instead of the third drive, which isn't going to work.
This statement is just incorrect because I personally boot from a raid MBR to some installs both on raid and non raid drives with no problems. We do have to verify what drive your boot is set to in bios to correctly fix the boot instruction.

Providing the Ubuntu install you show is correct, I would suggest just a simple reinstall of grub 2 to rewrite the grub MBR on the raid (providing the raid is the first drive in the bios boot order) to load the grub menu on sdc.
 
The instructions for reinstalling grub are here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

To help you along, in your case you would boot to the live cd and open a terminal window. In that window write:
```
sudo mount /dev/sdd2 /mnt
```
This instruction mounts your Ubuntu install to the /mnt location in your live cd file system. You then reinstall  grub to that location and rewrite the MBR on the raid so that it is directed to that install with the following:
```
sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_bfacdjdfi_RAID
```

If this is not where you intended to install to, we can fix it after you have verifyed that everything works including the win 7. Post how you make out.

---

### Post by psusi on 2011-01-27
> **ronparent said:**
> 
This statement is just incorrect because I personally boot from a raid MBR to some installs both on raid and non raid drives with no problems. We do have to verify what drive your boot is set to in bios to correctly fix the boot instruction.

It won't work in his case because grub is looking for /boot on the raid, and it isn't there.

---

### Post by ronparent on 2011-01-27
That is why I instructed him to reinstall grub. Then the grub will be found on sdd2. There may be other problems that we might be better able to fix once at least the install on sdd is working.

---

### Post by paranoiid on 2011-01-27
> **ronparent said:**
> That is why I instructed him to reinstall grub. Then the grub will be found on sdd2. There may be other problems that we might be better able to fix once at least the install on sdd is working.

Tried that. In that same place you instructed me too, it went from "Unknown filesystem" to "Module not found."

But I reinstalled Windows 7 (the raid was fine) and downloaded EasyBCD, added Grubs 2 to the boot menu and now I can dual boot.

And well it did go very much smoother than doing it from the Linux side.

---

### Post by ronparent on 2011-01-27
Glad to hear it is working out. I don't know why the instructions I gave you didn't work. Although there seems to be remnants of grub 1 in that directory a reinstall should have handled that. 

> sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

But I wouldn't agonize over that. Whatever works is fine. Good luck from here.

---

