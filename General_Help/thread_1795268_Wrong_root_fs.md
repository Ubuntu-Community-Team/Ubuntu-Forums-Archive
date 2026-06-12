---
title: "Wrong root fs?"
date: 2011-07-02
forum: General Help
---

### Post by mcemsi on 2011-07-02
Hi guys,

I installed 2 new hard disks and created one ext 4 partition on each of them.

After rebooting busybox tells me that there is no /sbin/init

Thanks a lot in advance.

mcemsi

---

### Post by dino99 on 2011-07-02
to partition hdds, they must be unmounted

---

### Post by mcemsi on 2011-07-02
There are 3hdds installed in the system

on one there is the xubuntu installation.


I installed 2 new disks and created ext4 partitions with kde partition manager, but after the reboot busybox appeared telling me that there is no /sbin/init

---

### Post by Rubi1200 on 2011-07-02
Post the output of the boot info script so we can get a better overview of what is going on please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mcemsi on 2011-07-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.........$....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1418392 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdd1 starts at sector 
                       0. But according to the info from fdisk, sdd1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder, zusammen 2930277168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,282,111   488,280,064  83 Linux
/dev/sda2         488,284,158   494,141,439     5,857,282   5 Extended
/dev/sda5         488,284,160   494,141,439     5,857,280  82 Linux swap / Solaris
/dev/sda3         494,143,335 2,542,157,729 2,048,014,395   b W95 FAT32


Drive: sdb _____________________________________________________________________

Platte /dev/sdb: 2000.4 GByte, 2000398934016 Byte
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdc _____________________________________________________________________

Platte /dev/sdc: 2000.4 GByte, 2000398934016 Byte
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdd _____________________________________________________________________

Platte /dev/sdd: 4005 MByte, 4005527552 Byte
124 Köpfe, 62 Sektoren/Spur, 1017 Zylinder, zusammen 7823296 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        12bf9242-2f64-4ef6-8d6a-602c246566e0   ext4       
/dev/sda3        2decb32e-988b-4968-9b2a-fafd77b5a5cf   ext4       
/dev/sda5        948d9119-c8a5-4fef-803e-f811bfcea28f   swap       
/dev/sdb1        8f851e0c-8159-4e0b-a378-6aca1d168089   ext4       R1
/dev/sdc1        2b65b28f-8156-4002-b050-d48817d74f72   ext4       R2
/dev/sdd1        8A98-C435                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro   quiet splash irqpoll
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro   quiet splash irqpoll
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro   quiet splash irqpoll
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 12bf9242-2f64-4ef6-8d6a-602c246566e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
/dev/sda3       /home/martin/Desktop/file     ext4         defaults              0 0
# / was on /dev/sda1 during installation
UUID=12bf9242-2f64-4ef6-8d6a-602c246566e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=948d9119-c8a5-4fef-803e-f811bfcea28f none            swap    sw              0       0


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.133998871 = 55.978455040   boot/grub/core.img                             1
   2.407611847 = 2.585153536    boot/grub/grub.cfg                             1
  52.258388519 = 56.112017408   boot/initrd.img-2.6.32-21-generic              1
  54.039764404 = 58.024755200   boot/initrd.img-2.6.32-28-generic              1
  54.052742004 = 58.038689792   boot/initrd.img-2.6.32-32-generic              1
  52.132167816 = 55.976488960   boot/vmlinuz-2.6.32-21-generic                 1
  52.262153625 = 56.116060160   boot/vmlinuz-2.6.32-28-generic                 1
  54.043525696 = 58.028793856   boot/vmlinuz-2.6.32-32-generic                 1
  54.052742004 = 58.038689792   initrd.img                                     1
  54.039764404 = 58.024755200   initrd.img.old                                 1
  54.043525696 = 58.028793856   vmlinuz                                        1
  52.262153625 = 56.116060160   vmlinuz.old                                    1

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sde 

=============================== StdErr Messages: ===============================

./boot_info_script.sh: Zeile 1579: [: 2.73495e+09: Ganzzahliger Ausdruck erwartet.

```

---

### Post by Rubi1200 on 2011-07-03
I don't see anything immediately wrong with the results.

Did you change any settings in BIOS?

I assume the 2 new drives are for storage?

In any event, try reinstalling GRUB from the LiveCD:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Reboot and back in Ubuntu run this command:

```
sudo update-grub
```

---

### Post by mcemsi on 2011-07-03
Thanks for the fast reply!

The 2 devices should operate in a software raid in a virtualized FreeNas.


Everything seems to work again now!

Best support i ever got!

Thanks a lot

---

### Post by Rubi1200 on 2011-07-03
Excellent! I am glad this worked and you are back up and running :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

