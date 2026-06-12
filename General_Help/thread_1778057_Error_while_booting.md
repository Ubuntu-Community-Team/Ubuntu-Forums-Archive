---
title: "Error while booting"
date: 2011-06-08
forum: General Help
---

### Post by mosaic2s on 2011-06-08
Strange screen - never seen before.
I have a dual boot hdd. it gives the boot selection screen.
On selecting ubuntu OS, it says,

mounting /dev on /root/dev failed
sys failed
proc failed

target filesystem does not have /sbin/init
no init found.
try init=bootarg

busybox v1.13.3 built in shell 
then initramfs.
some numbers [248.934433] with generic-usb reporting.
this is happening again and again.
not sure if there is an hardware error that system is unable to resolve. or some file has been corrupted.

the other OS is working fine.

---

### Post by cbecker78 on 2011-06-08
Can you access that partition from a live cd session?

---

### Post by mosaic2s on 2011-06-09
yes.
booted into USB pendrive - trial mode.
able to mount both the OS partitions.
full access to folders available.

---

### Post by wildmanne39 on 2011-06-09
> **mosaic2s said:**
> yes.
booted into USB pendrive - trial mode.
able to mount both the OS partitions.
full access to folders available.
Hi,post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by mosaic2s on 2011-06-09
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 3828 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 30612 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   156,280,319   156,280,257   7 NTFS / exFAT / HPFS
/dev/sda2    *    156,280,320   976,592,819   820,312,500  83 Linux
/dev/sda3         976,592,894   976,773,119       180,226   5 Extended
/dev/sda5         976,592,896   976,773,119       180,224  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 995 MB, 995081728 bytes
31 heads, 62 sectors/track, 1011 cylinders, total 1943519 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     1,943,141     1,943,080   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
64 heads, 32 sectors/track, 15296 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32    31,326,207    31,326,176   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        826CF8B66CF8A657                       ntfs       
/dev/sda2        f6c55260-3f9f-4308-a023-0ee74e7e8f92   ext4       
/dev/sda5        83e7a6fc-d175-41a5-8f6a-037911e6d6c6   swap       
/dev/sdb1        0CF3-1EA8                              vfat       
/dev/sdc1        6E1E-91FD                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/826CF8B66CF8A657  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/f6c55260-3f9f-4308-a023-0ee74e7e8f92 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/6E1E-91FD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f6c55260-3f9f-4308-a023-0ee74e7e8f92
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 826cf8b66cf8a657
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f6c55260-3f9f-4308-a023-0ee74e7e8f92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=83e7a6fc-d175-41a5-8f6a-037911e6d6c6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 178.652828217 = 191.827013632  boot/grub/core.img                             1
 178.884590149 = 192.075866112  boot/grub/grub.cfg                             1
 178.715187073 = 191.893970944  boot/initrd.img-2.6.32-24-generic              1
 178.785118103 = 191.969058816  boot/initrd.img-2.6.32-30-generic              1
 160.274673462 = 172.093620224  boot/initrd.img-2.6.32-31-generic              2
  76.559539795 = 82.205179904   boot/initrd.img-2.6.32-32-generic              2
 178.664058685 = 191.839072256  boot/vmlinuz-2.6.32-24-generic                 1
 178.670127869 = 191.845588992  boot/vmlinuz-2.6.32-30-generic                 1
 178.791614532 = 191.976034304  boot/vmlinuz-2.6.32-31-generic                 1
 178.973201752 = 192.171012096  boot/vmlinuz-2.6.32-32-generic                 1
  76.559539795 = 82.205179904   initrd.img                                     2
 160.274673462 = 172.093620224  initrd.img.old                                 2
 178.973201752 = 192.171012096  vmlinuz                                        1
 178.791614532 = 191.976034304  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)



```

---

### Post by oldfred on 2011-06-09
Boot script looks normal to me. 

Have you tried without both flash drives plugged in. Sometimes search can cause issues. But error does seem to be related to USB somehow.

If you use e at grub menu and remove quiet splash you will see each line as it boots. It may still end at your [248.934433] but that is saying it mostly booted? Unless other errors are before that. Boot is also in log files. You can look in /var/log/messages or other log files in /var/log in your install (not liveCD boot, so it may be /media/var/log).


Minor point not related to any  of your issues. Grub does not use boot flag. Windows need to boot flag to directly boot or to do repairs. So if you ever have to repair windows then you need the boot flag on sda1. You can use gparted from liveCD to move it.

---

### Post by mosaic2s on 2011-06-10
thanks oldfred.
the system booted fine with no USB device plugged in. for now we are working on it. will check if it fails again.

will set up boot flag to sda1.

---

### Post by mosaic2s on 2011-06-18
the system is playing up again.
boots fine in other OS. but not in ubuntu. same error.

I am presuming it is hardware related but how is the other OS running but not linux!

---

### Post by oldfred on 2011-06-18
If you can boot XP from grub2 menu but not Ubuntu, it says you are booting but there is some issue with Ubuntu loading. Did you install new drivers or make some system changes? Uninstall something vital?

Have you tried recovery mode?

At grub menu, press for edit on Ubuntu boot line. Remove quiet splash and it will show the boot process line by line. It goes by quick buy may show an error or stop at the issue. The same info is in log files (log file view or in /var/log) that you can view once booted or from liveCD.

---

### Post by mosaic2s on 2011-06-28
relocated the hdd to another comp - same error. so i formatted the hdd. system runs fine.
did not boot from usb drive at that time.

---

