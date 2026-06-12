---
title: "&quot;udevd inotify_add_watch failed invalid argument error&quot;"
date: 2012-05-12
forum: General Help
---

### Post by ChemMeister on 2012-05-12
After a recent update I get the error mentioned in the title after I select Ubuntu 12.04 (I haev dual boot with Windows 7). The following are the results from running the bootinfo script. Thanks in advance.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_dbjhicdcc_Volume0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 2be2c013-c02e-46d1-b8e8-b5decb24fde8 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdc1 
                       and looks at sector 97085488 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

isw_dbjhicdcc_Volume01: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_dbjhicdcc_Volume02: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   488,282,111   488,280,064  83 Linux
/dev/sdc2         488,284,158   976,771,071   488,486,914   5 Extended
/dev/sdc5         488,284,160   976,771,071   488,486,912  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   312,580,095   312,578,048  82 Linux swap / Solaris


Drive: isw_dbjhicdcc_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_dbjhicdcc_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dbjhicdcc_Volume01   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_dbjhicdcc_Volume02            206,848 3,907,037,183 3,906,830,336   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dbjhicdcc_Volume0p1 704403284402F120                       ntfs       System Reserved
/dev/mapper/isw_dbjhicdcc_Volume0p2 46CC044DCC0439A7                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        2be2c013-c02e-46d1-b8e8-b5decb24fde8   ext4       
/dev/sdc5        0c6ac779-5182-4e80-908d-f6a5b5b74431   swap       
/dev/sdd1        730eac32-9fc3-4e50-808c-60d48cd19e94   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dbjhicdcc_Volume0
isw_dbjhicdcc_Volume0p1
isw_dbjhicdcc_Volume0p2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_dbjhicdcc_Volume0p2 /media/46CC044DCC0439A7  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/2be2c013-c02e-46d1-b8e8-b5decb24fde8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=2be2c013-c02e-46d1-b8e8-b5decb24fde8 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=2be2c013-c02e-46d1-b8e8-b5decb24fde8 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=2be2c013-c02e-46d1-b8e8-b5decb24fde8 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=2be2c013-c02e-46d1-b8e8-b5decb24fde8 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 2be2c013-c02e-46d1-b8e8-b5decb24fde8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_dbjhicdcc_Volume0p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set=root 704403284402F120
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/mapper/isw_dbjhicdcc_Volume0p2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos2)'
    search --no-floppy --fs-uuid --set=root 46CC044DCC0439A7
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=2be2c013-c02e-46d1-b8e8-b5decb24fde8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0c6ac779-5182-4e80-908d-f6a5b5b74431 none            swap    sw              0       0
# swap was on /dev/sdd1 during installation
UUID=730eac32-9fc3-4e50-808c-60d48cd19e94 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_dbjhicdcc_Volume01


Unknown BootLoader on isw_dbjhicdcc_Volume02



========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/mapper/isw_dbjhicdcc_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dbjhicdcc_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dbjhicdcc_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dbjhicdcc_Volume02: No such file or directory


```

---

