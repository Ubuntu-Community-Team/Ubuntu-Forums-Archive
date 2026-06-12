---
title: "Help, Grub rescue unknown filesystem error."
date: 2010-06-27
forum: General Help
---

### Post by freshprints on 2010-06-27
hey, so today i decided to install ubuntu from a live cd onto my desktop, after having installed it onto my laptop several months ago. My original live cd is lost, so i created a new one and put it into my computer and entered the setup. 
Heres where things start to go down hill, my computer is a packard bell ixtreme x5620 UK. under windows seven in my computer i have the c drive with windows installed and then a d drive called data which has nothing on it. It was like this when i bought the computer with seven pre-installed ( this means no install disc) 
Back to the live cd install, i go through all the normal steps and get to the select disk space (step 4) i come across a problem, i had assumed i would be able to install ubuntu on the seperate d drive ( my assumption being that the computer has two hard disk drives) but the options i have are Erase and use the entire disk = 640 GB ATA WDC WD6400AAKKS-0. long story short i created an extended partition with two logical partitions and installed ubuntu fine. After install i rebooted into windows to see if it still worked and it was fine. Reboot again to go into ubuntu and then i get this error: Grub Rescue: unknown filesystem. 

i have booted into live cd and gone through the install till step 4 to see if the partitions are regonized and this is what it shows. (also i am a noob so i dont know why windows vista is mentioned)

Windows Vista (loader) (/dev/sda1) 14GB
Windows 7 (loader) (/dev/sda2) 104.9MB
/dev/sda3 312.9GB
/dev/sda5 147.9GB
ubuntu 10.04 LTS (10.04) (/dev/sda6) 139.8GB
Swap 9/dev/sda7) 6.0GB
/dev/sda/sda8 19.5 GB

I welcome any help, and i would be happy to simply remove the linux install as i do not have a windows 7 install disk. 

Thank you.

---

### Post by Rubi1200 on 2010-06-27
Hi,
if you can boot the computer with a LiveCD then follow this link and the instructions. It will help people here offer some solutions for you.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Don't forget to use the # tags when you post back again.

Good luck!

---

### Post by freshprints on 2010-06-27
```
      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden HPFS/NTFS
/dev/sda2    *     27,265,024    27,469,823       204,800   7 HPFS/NTFS
/dev/sda3          27,469,824   638,687,231   611,217,408   7 HPFS/NTFS
/dev/sda4         638,696,266 1,250,258,624   611,562,359   5 Extended
/dev/sda5         638,696,268   927,484,286   288,788,019  83 Linux
/dev/sda6         927,485,952 1,200,476,159   272,990,208  83 Linux
/dev/sda7       1,200,478,208 1,212,119,039    11,640,832  82 Linux swap / Solaris
/dev/sda8       1,212,120,378 1,250,258,624    38,138,247  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B00C05E80C05AB04                       ntfs       PQSERVICE                     
/dev/sda2        2E84063D840607D3                       ntfs       SYSTEM RESERVED               
/dev/sda3        96AC2876AC2852D3                       ntfs       Packard Bell                  
/dev/sda4: PTTYPE="dos" 
/dev/sda5        87a97a95-3fac-4e2b-a3c1-a01ef7309d87   ext3                                     
/dev/sda6        a04e88a2-7357-49f5-8e3c-5294d7d71ca0   ext4                                     
/dev/sda7        3f81c080-cb83-44c7-ab47-ca66819b879d   swap                                     
/dev/sda8        cb344711-ca37-4f08-ba5c-9fb72e2b2aed   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /media/cb344711-ca37-4f08-ba5c-9fb72e2b2aed ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a04e88a2-7357-49f5-8e3c-5294d7d71ca0
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a04e88a2-7357-49f5-8e3c-5294d7d71ca0
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a04e88a2-7357-49f5-8e3c-5294d7d71ca0
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a04e88a2-7357-49f5-8e3c-5294d7d71ca0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a04e88a2-7357-49f5-8e3c-5294d7d71ca0
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a04e88a2-7357-49f5-8e3c-5294d7d71ca0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a04e88a2-7357-49f5-8e3c-5294d7d71ca0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
```

here we go, thanks.

---

### Post by freshprints on 2010-06-27
im not quite sure how this forum works, but, bump?

---

