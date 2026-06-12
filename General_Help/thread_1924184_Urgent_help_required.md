---
title: "Urgent help required"
date: 2012-02-12
forum: General Help
---

### Post by ank123 on 2012-02-12
My laptop had windows operating system already, I installed ubuntu 10.04 . I restarted my laptop. Now boot screen isn't coming. Only windows is getting loaded. How to fix the MBR using windows? Windows forums are useless. So I posted this query here.

---

### Post by k999 on 2012-02-12
Perhaps you didn't install GRUB on the MBR when you installed? You should be able to boot Ubuntu off the install CD and rerun GRUB from there.

---

### Post by raja.genupula on 2012-02-12
are you getting grub menu if you hold the Shift key while booting ?  If yes then boot into Ubuntu and change boot time to 10 sec By using **Grub Customizer** . 

If no grub menu then post the output of **bootinfoscript** .

Look at my signature for both the things.
All the best.

---

### Post by ank123 on 2012-02-12
here is the output of bootinfoscript

 ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda6 and looks at sector 377218976 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 9 for /boot/grub. According to the 
                       info in the boot sector, sda6 starts at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   284,651,934   284,242,335   7 NTFS / exFAT / HPFS
/dev/sda3         284,653,566   926,482,431   641,828,866   f W95 Extended (LBA)
/dev/sda5         466,642,944   581,601,279   114,958,336   7 NTFS / exFAT / HPFS
/dev/sda6         581,603,328   696,561,663   114,958,336   7 NTFS / exFAT / HPFS
/dev/sda7         696,563,712   811,522,047   114,958,336   7 NTFS / exFAT / HPFS
/dev/sda8         811,524,096   926,482,431   114,958,336   7 NTFS / exFAT / HPFS
/dev/sda9         284,653,568   459,147,263   174,493,696  83 Linux
/dev/sda10        459,149,312   466,640,895     7,491,584  82 Linux swap / Solaris
/dev/sda4         926,482,432   968,450,047    41,967,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        16182B7E182B5BCD                       ntfs       SYSTEM
/dev/sda10       f10e5c21-5f1a-472a-9323-c8a6232d86a7   swap       
/dev/sda2        C644AD6644AD5A47                       ntfs       
/dev/sda4        46D6D2D5D6D2C479                       ntfs       Recovery
/dev/sda5        C2740F50740F471F                       ntfs       New Volume
/dev/sda6        2ED81F12D81ED7C3                       ntfs       New Volume
/dev/sda7        84FE2DE3FE2DCDEC                       ntfs       New Volume
/dev/sda8        8E083D2D083D15A5                       ntfs       New Volume
/dev/sda9        05772ada-536f-40cf-85d2-91959946240f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
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
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
insmod tga
if background_image /usr/share/images/desktop-base/lccboot.tga ; then
  set color_normal=white/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=05772ada-536f-40cf-85d2-91959946240f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=05772ada-536f-40cf-85d2-91959946240f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=05772ada-536f-40cf-85d2-91959946240f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=05772ada-536f-40cf-85d2-91959946240f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 05772ada-536f-40cf-85d2-91959946240f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=05772ada-536f-40cf-85d2-91959946240f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f10e5c21-5f1a-472a-9323-c8a6232d86a7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 179.872051239 = 193.136144384  boot/grub/core.img                             1
 183.971519470 = 197.537914880  boot/grub/grub.cfg                             1
 135.878849030 = 145.898803200  boot/initrd.img-2.6.32-21-generic              1
 136.617141724 = 146.691538944  boot/initrd.img-2.6.32-24-generic              2
 179.866889954 = 193.130602496  boot/vmlinuz-2.6.32-21-generic                 1
 179.870651245 = 193.134641152  boot/vmlinuz-2.6.32-24-generic                 1
 136.617141724 = 146.691538944  initrd.img                                     2
 135.878849030 = 145.898803200  initrd.img.old                                 1
 179.870651245 = 193.134641152  vmlinuz                                        1
```
 
is it related to sda9?

---

### Post by penka on 2012-02-12
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
may be of some help

---

### Post by ank123 on 2012-02-12
@penka: that link won't help. Please read my question carefully

---

### Post by josephmills on 2012-02-12
you are going to have to load a live cd 
then look at this link Post #2 
[http://ubuntuforums.org/showthread.php?t=1851164](http://ubuntuforums.org/showthread.php?t=1851164) 


as I see from that great boot script that ubuntu is installed on 

sda9 

Try to install grub to it again. Let us know how it works out.

---

### Post by ank123 on 2012-02-13
Yeah, i got it. I finally managed to install grub boot loader into sda9. Thanks to those who responded to my call for help :D

---

