---
title: "Upgrading to 10.04 killed my grub"
date: 2010-05-24
forum: General Help
---

### Post by polardude1983 on 2010-05-24
I had just finished upgrading my system to 10.04 and it restarted my pc and now i can't boot my pc anymore

All i have is this at the beginning

```

GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue>_

```

pls help

---

### Post by polardude1983 on 2010-05-24
Here is what i get from the boot info script

```

                   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 322263 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 483391 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   530,916,119   530,916,057  83 Linux
/dev/sda2         530,916,120   613,072,529    82,156,410   7 HPFS/NTFS
/dev/sda3         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ea90e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   522,112,499   522,112,437  83 Linux
/dev/sdb2         522,112,500   976,768,064   454,655,565  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005a551

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6876c9c2-22b4-42ee-9eff-0a2f61a305af   ext4                                     
/dev/sda5        726999da-9ea3-48d1-acd0-9cfc0e40fae5   swap                                     
/dev/sdb1        5d3a56c5-3254-4a23-938e-c498929a658a   ext3       Backup                        
/dev/sdb2        4918d811-79f5-4355-98e2-cca5ab1174ae   ext3       Extra Hard Drive              
/dev/sdg1        2815-7974                              vfat       Cruzer                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdg1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
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
search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      linux /boot/vmlinuz-2.6.32-22-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
      initrd      /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      echo  'Loading Linux 2.6.32-22-generic ...'
      linux /boot/vmlinuz-2.6.32-22-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      linux /boot/vmlinuz-2.6.32-10-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
      initrd      /boot/initrd.img-2.6.32-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      echo  'Loading Linux 2.6.32-10-generic ...'
      linux /boot/vmlinuz-2.6.32-10-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      linux16     /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
      insmod ext2
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
      linux16     /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=726999da-9ea3-48d1-acd0-9cfc0e40fae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
    .2GB: boot/grub/stage2
 122.5GB: boot/initrd.img-2.6.32-10-generic
  53.8GB: boot/initrd.img-2.6.32-22-generic
  17.2GB: boot/vmlinuz-2.6.32-10-generic
  40.8GB: boot/vmlinuz-2.6.32-22-generic
  37.8GB: grub/core.img
  53.8GB: initrd.img
  40.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
 
  

```

---

### Post by magneze on 2010-05-24
One of my machines did this. Follow these instructions, you should be ok:

[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

Searching on the forums I saw that this was raised many times before release. Who knows what QA let this one through. :mad:

---

