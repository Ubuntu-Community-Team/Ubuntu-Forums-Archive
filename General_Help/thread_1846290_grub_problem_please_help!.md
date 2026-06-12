---
title: "grub problem please help!"
date: 2011-09-18
forum: General Help
---

### Post by sublimestyle on 2011-09-18
i just recently picked up a lenovo l420 laptop and was anxious to dual boot install ubuntu with the preloaded windows 7, so i installed 10.04 (to give a try for the LTS version), instead of installing the 11.04 that i have already on my desktop. 

finally got 10.04 to work with the wireless (pain in the *** because it doesnt work freshly installed) and decided to install the 11.04 anyways alongside the two other OSes. after booting 11.04 via USB and installing it successfully, i tried to boot up this version to no avail. i would get a screen that had whiteish discolored lines all striped going across the screen, and turned sour on the 11.04.

after doing a bit of research i found out this particular laptop model was offered preloaded in another country (The canadian site only offered windows 7 preloaded).

i figured what the hell ill delete the partitions and install "the perfect 10" on the laptop that it was meant to be on.

big mistake.

after deleting all partitions but the windows 7, backup partition, and lenovo rescue partition, i soon realized i couldnt boot up anything due to a "grub rescue" problem. 

stuck the version 10.10 in a USB and loaded it onto the laptop from the boot menu.

with a little advice here and there from searching up about the issue, I believe i managed to install the grub or atleast come a step closer to closing up this can of worms once and for all.

the only problem is i am lost from this point on.

when i boot up my system, i get the message
 "gnu grub version 1.98+20100804-5ubuntu3 etc.
 grub>                                                                    "

any ideas? id love to get this lovely new piece up and running.. :)

---

### Post by drs305 on 2011-09-18
At the grub prompt you could try typing "insmod normal" but that's a real long shot.

For us to get a good understanding of your boot files status, please download/extract/run the boot info script and post the contents of RESULTS.txt. You can run the script from the LiveCD.

Click on the "BIS" link in my signature line to take you to the script's web page.

---

### Post by sublimestyle on 2011-09-18
"insmod normal" didnt work but ill try to get the BIS running, though ill have to adapt to booting the live USB with no wireless abilities..

---

### Post by sublimestyle on 2011-09-18
finally! the live CD wasnt picking up on my keyboard but alls well now.

heres what it came up with:
```

  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 349571240 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 5 for (,msdos5)/boot/grub. No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8064.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   143,691,224   141,231,577   7 NTFS / exFAT / HPFS
/dev/sda3         467,914,752   488,394,751    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda4         143,691,774   467,914,751   324,222,978   5 Extended
/dev/sda5         143,691,776   455,626,751   311,934,976  83 Linux
/dev/sda6         455,628,800   467,914,751    12,285,952  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7743 MB, 7743995904 bytes
80 heads, 16 sectors/track, 11816 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    15,124,991    15,116,928   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F60A5C000A5BBC75                       ntfs       SYSTEM_DRV
/dev/sda2        542C5DA52C5D8342                       ntfs       Windows7_OS
/dev/sda3        788260A782606C16                       ntfs       Lenovo_Recovery
/dev/sda5        037a3ed7-4bda-4ec9-8f31-77a5f107e5dd   ext4       
/dev/sda6        e4c6fc47-8f6c-44d3-9500-c580a903677d   swap       
/dev/sdb1        F850-8CA3                              vfat       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/New Volume        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f60a5c000a5bbc75
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 542c5da52c5d8342
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
# / was on /dev/sda5 during installation
UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e4c6fc47-8f6c-44d3-9500-c580a903677d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 166.688579559 = 178.980499456  boot/grub/core.img                             1
 174.662540436 = 187.542474752  boot/grub/grub.cfg                             1
  68.944976807 = 74.029105152   boot/initrd.img-2.6.35-22-generic              2
  68.827754974 = 73.903239168   boot/vmlinuz-2.6.35-22-generic                 2
  68.944976807 = 74.029105152   initrd.img                                     2
  68.827754974 = 73.903239168   vmlinuz                                        2

```

---

### Post by drs305 on 2011-09-18
Grub is installed on your Windows partition. To restore Grub, boot a LiveCD/USB and:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not include the partition number in the second command.

Reboot and you should get the Grub 2 menu. If Windows isn't on the menu, after a successful boot, run:
```
sudo update-grub
```

---

### Post by sublimestyle on 2011-09-18
beautiful! worked like a charm!

got back my 10.10 and everythings great so far.. just gotta reinstall my wireless adapter package and im good to go! thanks a lot! :D

---

### Post by drs305 on 2011-09-18
Glad it's working. If you ever remove Grub2 you will probably have to do some work to get Windows working again. You'll definitely have to put Windows back on the MBR and most likely have to repair the sda1 partition, where Grub overwrote the Windows boot info. I'll leave that to you and the Windows users.

If you don't have any further Grub 2 issues, you can mark the thread 'SOLVED' via the Thread Tools link at the top right of the first post.

Happy Ubuntu-ing !

---

