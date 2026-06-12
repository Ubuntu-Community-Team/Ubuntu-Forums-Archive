---
title: "Help fixing grub- computer won't boot."
date: 2011-12-26
forum: General Help
---

### Post by josephellengar on 2011-12-26
EDIT: Never mind, I was able to adapt commands from an old thread to fix it.


Hi. I am trying to fix grub right now, which is not loading after I did a system restore through Clonezilla. I have tried to do a chroot into the filesystem, but I don't really know what I'm doing, so if anyone could please give me commands, I'd really appreciate that. This is what my boot info script looks like (/dev/sdc is the live usb that I am using to run off of- the native hard drives are sda and sdb).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /menu.lst /syslinux.cfg /grub.exe /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   147,212,287   146,802,688   7 NTFS / exFAT / HPFS
/dev/sda3         147,212,288   252,069,887   104,857,600  83 Linux
/dev/sda4         252,069,888   312,580,095    60,510,208  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   616,749,055   616,748,993   7 NTFS / exFAT / HPFS
/dev/sdb2         616,751,102   625,141,759     8,390,658   5 Extended
/dev/sdb5         616,751,104   625,141,759     8,390,656  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8005 MB, 8005787648 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15636304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,631,244    15,631,182   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 11.10 amd64
/dev/loop1                                              squashfs   
/dev/sda1        A0BEA0DFBEA0AEEA                       ntfs       SYSTEM
/dev/sda2        70C6388CC6385496                       ntfs       OS
/dev/sda3        cd10c0ee-fa36-447e-9ce2-39b2d6891fa3   ext4       
/dev/sda4        229df84b-e7d7-450b-8bc4-738f078cd050   ext4       
/dev/sdb1        74912E3D2459A0BE                       ntfs       STORAGE
/dev/sdb5        53b9abb4-b601-47e4-ad70-25b2156979c8   swap       
/dev/sdc1        94E4-7D13                              vfat       TOOLKIT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /mnt                     ext4       (rw)
/dev/sdc1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=cd10c0ee-fa36-447e-9ce2-39b2d6891fa3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=cd10c0ee-fa36-447e-9ce2-39b2d6891fa3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root cd10c0ee-fa36-447e-9ce2-39b2d6891fa3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root A0BEA0DFBEA0AEEA
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 70C6388CC6385496
    drivemap -s (hd0) ${root}
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=cd10c0ee-fa36-447e-9ce2-39b2d6891fa3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=229df84b-e7d7-450b-8bc4-738f078cd050 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=53b9abb4-b601-47e4-ad70-25b2156979c8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

================================ sdc1/menu.lst: ================================

--------------------------------------------------------------------------------
#default 0 
#timeout 30 
color NORMAL HIGHLIGHT HELPTEXT HEADING 
splashimage=(hd0,0)/splash.xpm.gz 
foreground=000000 
background=FFFFFF 
 
title AVG Rescue CD 100.100826 (Anti-Virus + Anti-Spyware) 
find --set-root /avg.iso 
map /avg.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Balder DOS 10 
map --unsafe-boot /balder10.img (fd0) 
map --hook 
chainloader --force (fd0)+1 
rootnoverify (fd0) 
 
title Clonezilla 20100921 (Alternative) 
find --set-root /clonezilla/live/initrd1.img 
kernel /clonezilla/live/vmlinuz1 boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run='ocs-live-general' ocs_live_extra_param='' ocs_live_keymap='' ocs_live_batch='no' ocs_lang='' vga=788 ip=frommedia nosplash live-media-path=/clonezilla/live toram=filesystem.squashfs 
initrd /clonezilla/live/initrd1.img 
 
title Gparted 0.6.4-1  
find --set-root /gparted/live/initrd1.img 
kernel /gparted/live/vmlinuz1 boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run='ocs-live-general' ocs_live_extra_param='' ocs_live_keymap='' ocs_live_batch='no' ocs_lang='' vga=788 ip=frommedia nosplash live-media-path=/gparted/live toram=filesystem.squashfs 
initrd /gparted/live/initrd1.img 
 
title DBAN 1.0.7 (Drive Nuker) 
find --set-root /dban-1.0.7_i386.iso 
map --mem /dban-1.0.7_i386.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title DSL 4.4.10 
find --set-root /dsl-4.4.10-initrd.iso 
map --mem /dsl-4.4.10-initrd.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title Kaspersky Rescue CD 10.0.21.5 (Virus Scanner) 
find --set-root /rescue/rescue.iso 
map /rescue/rescue.iso (0xff) 
map --hook 
root (0xff) 
chainloader (0xff) 
 
title Memtest86+ 3.5 
find --set-root /memtest86+-4.00.iso 
map --mem /memtest86+-4.00.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title NT Password & Registy Editor 080802 
find --set-root /cd080802.iso 
map /cd080802.iso  (hd32) 
map --hook 
chainloader (hd32) 
 
title OphCrack 3.3.1 
kernel /ophcrack/boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin 
initrd /ophcrack/boot/rootfs.gz  
 
title Parted Magic 4.10 
find --set-root /pmagic-4.10.iso 
map /pmagic-4.10.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title Puppy Linux 4.3.1 
find --set-root /puppy/pup-431.sfs 
kernel /puppy/vmlinuz 
initrd /puppy/initrd.gz 
 
title Redo Backup and Recovery 
find --set-root --ignore-floppies --ignore-cd /redobackup.iso 
map --heads=0 --sectors-per-track=0 /redobackup.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Spinrite 6.0 
map --mem /SpinRite.img (fd0) 
map --hook 
chainloader (fd0)+1 
rootnoverify (fd0) 
 
title TinyCore 2.11.3 
find --set-root /tinycore_2.11.3.iso 
map /tinycore_2.11.3.iso (0xff) || map --mem /tinycore_2.11.3.iso (0xff) 
map --hook 
chainloader (0xff) 
 
title Ubuntu 10.04 32 bit 
find --set-root /ubuntu-10.04-desktop-i386.iso 
map /ubuntu-10.04-desktop-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.04-desktop-i386.iso splash 
initrd /casper/initrd.lz 
 
title Ubuntu 10.04 64 bit 
find --set-root /ubuntu-10.04-desktop-amd64.iso 
map /ubuntu-10.04-desktop-amd64.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.04-desktop-amd64.iso splash 
initrd /casper/initrd.lz 
 
title Ubuntu 11.10 64 bit 
find --set-root /ubuntu-11.10-desktop-amd64.iso 
map /ubuntu-11.10-desktop-amd64.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-11.10-desktop-amd64.iso splash 
initrd /casper/initrd.lz 
 
title Ultimate Boot CD 5.0.1 
find --set-root /ubcd501.iso 
map /ubcd501.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Boot From Hard Drive 
map (hd0) (hd1) 
map (hd1) (hd0) 
map --hook 
chainloader (hd0)+1 
rootnoverify (hd0) 
 
title Grub4Dos Command Line 
commandline 
 
title Reboot 
reboot 
 
 
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default grub
LABEL grub
KERNEL grub.exe--------------------------------------------------------------------------------

========================= sdc1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

