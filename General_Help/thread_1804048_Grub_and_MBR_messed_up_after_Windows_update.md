---
title: "Grub and MBR messed up after Windows update"
date: 2011-07-14
forum: General Help
---

### Post by Mitraidos on 2011-07-14
Hello,
I just started using Ubuntu 10.04 for development reasons and installed Ubuntu on a seperate harddrive with dualboot option with Windows 7.
Today Win 7 got an update and I mysteriously got bumped back to the grub screen after selecting Windows boot option, but my Ubuntu was ok. After that I probably did the worst I could, and googled the problem and tried out some years-old advices which messed up my ubuntu boot as well.
I am currently using my computer through Ubuntu Live Usb.

Here is the result of *sudo fdisk -l*

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05a62f81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        4631    37087232    7  HPFS/NTFS
/dev/sda3            4631        9730    40958976    7  HPFS/NTFS

Disk /dev/sdb: 16.1 GB, 16064184320 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c0fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1954    15687648+   c  W95 FAT32 (LBA)
```

Thanks in advance

---

### Post by Quackers on 2011-07-14
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mitraidos on 2011-07-14
Thanks for the reply. Here is my results.txt





```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

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
    Mounting failed:   
sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 136766728 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 5 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 129.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848    74,381,311    74,174,464   7 NTFS / exFAT / HPFS
/dev/sda3          74,381,312   112,972,642    38,591,331   7 NTFS / exFAT / HPFS
/dev/sda4         112,973,822   156,301,311    43,327,490   5 Extended
/dev/sda5         127,416,320   154,992,639    27,576,320  83 Linux
/dev/sda6         154,994,688   156,301,311     1,306,624  82 Linux swap / Solaris
/dev/sda7         112,973,824   126,691,327    13,717,504  83 Linux
/dev/sda8         126,693,376   127,412,223       718,848  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3959 MB, 3959422976 bytes
1 heads, 62 sectors/track, 124729 cylinders, total 7733248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            129     7,733,247     7,733,119   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5A4478CD4478ACFF                       ntfs       System Reserved
/dev/sda2        3C087EC6087E7F28                       ntfs       System
/dev/sda3        38D04A2AD049EEA6                       ntfs       Data
/dev/sda5        0023590e-fb77-43c0-aaca-eada3eb642fd   ext4       
/dev/sda6        73db6377-c27c-4e36-bdd1-e920f9271e5a   swap       
/dev/sda7        dc53bd04-db35-4a1f-9016-1e18ee34d232   ext4       
/dev/sda8        d5e38c76-b579-4881-bcbb-5d2d68af5171   swap       
/dev/sdc1        CB7D-1C09                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/0023590e-fb77-43c0-aaca-eada3eb642fd ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/CB7D-1C09         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-32-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-32-generic root=UUID=38D04A2AD049EEA6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.32-32-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-32-generic root=UUID=38D04A2AD049EEA6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=38D04A2AD049EEA6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 38D04A2AD049EEA6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=38D04A2AD049EEA6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5A4478CD4478ACFF
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   8.485076904 = 9.110781952    boot/grub/grub.cfg                             1
   0.367092133 = 0.394162176    boot/initrd.img-2.6.32-28-generic              1
   1.145202637 = 1.229651968    boot/initrd.img-2.6.32-32-generic              1
   0.521213531 = 0.559648768    boot/vmlinuz-2.6.32-28-generic                 1
   1.023052216 = 1.098493952    boot/vmlinuz-2.6.32-32-generic                 1
   1.145202637 = 1.229651968    initrd.img                                     1
   0.367092133 = 0.394162176    initrd.img.old                                 1
   1.023052216 = 1.098493952    vmlinuz                                        1
   0.521213531 = 0.559648768    vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0023590e-fb77-43c0-aaca-eada3eb642fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0023590e-fb77-43c0-aaca-eada3eb642fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5a4478cd4478acff
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=0023590e-fb77-43c0-aaca-eada3eb642fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=73db6377-c27c-4e36-bdd1-e920f9271e5a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  65.215484619 = 70.024593408   boot/grub/core.img                             1
  67.260078430 = 72.219959296   boot/grub/grub.cfg                             1
  65.264263153 = 70.076968960   boot/initrd.img-2.6.32-28-generic              1
  65.214069366 = 70.023073792   boot/vmlinuz-2.6.32-28-generic                 1
  65.264263153 = 70.076968960   initrd.img                                     1
  65.214069366 = 70.023073792   vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
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
search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=dc53bd04-db35-4a1f-9016-1e18ee34d232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=dc53bd04-db35-4a1f-9016-1e18ee34d232 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set dc53bd04-db35-4a1f-9016-1e18ee34d232
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5a4478cd4478acff
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=0023590e-fb77-43c0-aaca-eada3eb642fd ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0023590e-fb77-43c0-aaca-eada3eb642fd
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=0023590e-fb77-43c0-aaca-eada3eb642fd ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=dc53bd04-db35-4a1f-9016-1e18ee34d232 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d5e38c76-b579-4881-bcbb-5d2d68af5171 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  55.065788269 = 59.126439936   boot/grub/core.img                             1
  56.270175934 = 60.419641344   boot/grub/grub.cfg                             1
  55.190036774 = 59.259850752   boot/initrd.img-2.6.32-28-generic              1
  55.706909180 = 59.814838272   boot/initrd.img-2.6.32-32-generic              2
  55.001926422 = 59.057868800   boot/vmlinuz-2.6.32-28-generic                 1
  55.531414032 = 59.626401792   boot/vmlinuz-2.6.32-32-generic                 1
  55.706909180 = 59.814838272   initrd.img                                     2
  55.190036774 = 59.259850752   initrd.img.old                                 1
  55.531414032 = 59.626401792   vmlinuz                                        1
  55.001926422 = 59.057868800   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  eb 58 90 61 6e 64 72 6f  69 64 20 00 02 40 20 00  |.X.android ..@ .|
00000010  02 00 00 00 00 f0 00 00  10 00 04 00 00 00 00 00  |................|
00000020  70 ff 75 00 b0 03 00 00  00 00 00 00 02 00 00 00  |p.u.............|
00000030  01 00 02 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 09 1c 7d cb 4e  4f 20 4e 41 4d 45 20 20  |..)..}.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1997: 12337 Segmentation fault      ntfs-3g -o ro ${part} "${mountname}" 2>> ${Mount_Error}

```

---

### Post by Mitraidos on 2011-07-14
By the way,  I used to reach my windows filesystem. But now it says:
**Error mounting: mount exited with exit code 2: **

---

### Post by Mitraidos on 2011-07-14
I finally fixed the MBR by syslinux package. But it seems Windows cant access it either. Why would that happen?

---

### Post by Quackers on 2011-07-14
Because at some time you have installed grub to sda3, which is NTFS (probably your C: or D: drive in Windows). Now Windows can't find its way.
I would suggest that you repair the Windows bootloader with a Windows repair/installation disc and then re-install grub to the mbr of /dev/sda.

I thought you said you had installed Ubuntu on a separate drive. It doesn't appear so. It also appears that you have a wubi install in sda3 as well as 2 Ubuntu 10.04.2 Ubuntu installations.

---

### Post by Mitraidos on 2011-07-15
Yes, my wording was wrong. It was on a seperate *partition*, not *drive. *I'm having trouble booting Win7 Recovery disks atm. Will update if anything changes

---

