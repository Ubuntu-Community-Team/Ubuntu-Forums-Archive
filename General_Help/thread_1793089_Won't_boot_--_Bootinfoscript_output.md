---
title: "Won't boot -- Bootinfoscript output"
date: 2011-06-29
forum: General Help
---

### Post by maizuddin35 on 2011-06-29
Hello !!!

I have problem dealing with the ubuntu boot. I just can't boot into my Ubuntu. 

You can refer to this previous thread of mine here [http://ubuntuforums.org/showthread.php?t=1792084&page=2]("http://ubuntuforums.org/showthread.php?t=1792084&page=2")... from a problem to another problem. I thought , everything are fixed , but then, after rebooted the computer, I cant boot into ubuntu anymore. 

Here are the **Bootinfoscript output**

```
          Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdg.

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
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......pY.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1408976 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdg1 starts at sector 
                       0. But according to the info from fdisk, sdg1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   154,253,311   154,046,464   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    90,529,791    90,527,744  83 Linux
/dev/sdb2         879,118,334   976,771,071    97,652,738   5 Extended
/dev/sdb5         879,118,336   967,006,207    87,887,872   b W95 FAT32
/dev/sdb6         967,008,256   976,771,071     9,762,816  82 Linux swap / Solaris
/dev/sdb3          90,529,792   879,116,287   788,586,496  83 Linux
/dev/sdb4         976,771,072   976,773,119         2,048  82 Linux swap / Solaris


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f3d53f1a-0540-48af-9bfd-599db553c24b   ext3       
/dev/sda1        E400C42400C3FF92                       ntfs       System Reserved
/dev/sda2        CCF4D290F4D27C60                       ntfs       
/dev/sdb3        9934b0eb-d3bb-4cfd-bfed-a9ca461d4058   ext2       
/dev/sdb5        0B9F-6BCE                              vfat       
/dev/sdg1        69C8-E24A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/f3d53f1a-0540-48af-9bfd-599db553c24b ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/CCF4D290F4D27C60  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/0B9F-6BCE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdg1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1440x900-24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set E400C42400C3FF92
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a0dd71cf-c4c4-4bb2-8b56-ad4cdc7ab80d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 212.897018433 = 228.596432896  boot/grub/core.img                             2
 212.879016876 = 228.577103872  boot/grub/grub.cfg                             1
 212.775547028 = 228.466003968  boot/initrd.img-2.6.35-28-generic              9
 212.734748840 = 228.422197248  boot/initrd.img-2.6.35-30-generic              8
 212.754364014 = 228.443258880  boot/vmlinuz-2.6.35-28-generic                 3
 212.766460419 = 228.456247296  boot/vmlinuz-2.6.35-30-generic                 3
 212.734748840 = 228.422197248  initrd.img                                     8
 212.734748840 = 228.422197248  initrd.img.old                                 8
 212.766460419 = 228.456247296  vmlinuz                                        3
 212.766460419 = 228.456247296  vmlinuz.old                                    3

========================= sdg1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdg1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdg1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  a4 81 00 00 5d 01 00 00  57 0f f4 4d 57 0f f4 4d  |....]...W..MW..M|
00000010  57 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |W..M............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 50 91 a0 00  |............P...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 f7 d4 05 cc  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 68 5a 4c c6  68 5a 4c c6 68 5a 4c c6  |....hZL.hZL.hZL.|
00000090  57 0f f4 4d 68 5a 4c c6  00 00 00 00 00 00 00 00  |W..MhZL.........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 ac 09 00 00  65 0f f4 4d 65 0f f4 4d  |........e..Me..M|
00000110  65 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |e..M............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 ca 91 a0 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 89 d5 05 cc  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 38 aa da ba  38 aa da ba 38 aa da ba  |....8...8...8...|
00000190  65 0f f4 4d 38 aa da ba  00 00 00 00 00 00 00 00  |e..M8...........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

I hope anybody will come by and help up , and I know , you guys will. your help are greatly appreciated .

thanks to doas777 for helping me out earlier.

---

### Post by idoitprone on 2011-06-29
> **maizuddin35 said:**
> Hello !!!

I have problem dealing with the ubuntu boot. I just can't boot into my Ubuntu. 

You can refer to this previous thread of mine here [http://ubuntuforums.org/showthread.php?t=1792084&page=2](http://ubuntuforums.org/showthread.php?t=1792084&page=2)... from a problem to another problem. I thought , everything are fixed , but then, after rebooted the computer, I cant boot into ubuntu anymore. 

Here are the **Bootinfoscript output**

```
          Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdg.

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
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......pY.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1408976 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdg1 starts at sector 
                       0. But according to the info from fdisk, sdg1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   154,253,311   154,046,464   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    90,529,791    90,527,744  83 Linux
/dev/sdb2         879,118,334   976,771,071    97,652,738   5 Extended
/dev/sdb5         879,118,336   967,006,207    87,887,872   b W95 FAT32
/dev/sdb6         967,008,256   976,771,071     9,762,816  82 Linux swap / Solaris
/dev/sdb3          90,529,792   879,116,287   788,586,496  83 Linux
/dev/sdb4         976,771,072   976,773,119         2,048  82 Linux swap / Solaris


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f3d53f1a-0540-48af-9bfd-599db553c24b   ext3       
/dev/sda1        E400C42400C3FF92                       ntfs       System Reserved
/dev/sda2        CCF4D290F4D27C60                       ntfs       
/dev/sdb3        9934b0eb-d3bb-4cfd-bfed-a9ca461d4058   ext2       
/dev/sdb5        0B9F-6BCE                              vfat       
/dev/sdg1        69C8-E24A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/f3d53f1a-0540-48af-9bfd-599db553c24b ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/CCF4D290F4D27C60  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/0B9F-6BCE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdg1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1440x900-24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1440x900-24<<,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 9934b0eb-d3bb-4cfd-bfed-a9ca461d4058
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set E400C42400C3FF92
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=9934b0eb-d3bb-4cfd-bfed-a9ca461d4058 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a0dd71cf-c4c4-4bb2-8b56-ad4cdc7ab80d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 212.897018433 = 228.596432896  boot/grub/core.img                             2
 212.879016876 = 228.577103872  boot/grub/grub.cfg                             1
 212.775547028 = 228.466003968  boot/initrd.img-2.6.35-28-generic              9
 212.734748840 = 228.422197248  boot/initrd.img-2.6.35-30-generic              8
 212.754364014 = 228.443258880  boot/vmlinuz-2.6.35-28-generic                 3
 212.766460419 = 228.456247296  boot/vmlinuz-2.6.35-30-generic                 3
 212.734748840 = 228.422197248  initrd.img                                     8
 212.734748840 = 228.422197248  initrd.img.old                                 8
 212.766460419 = 228.456247296  vmlinuz                                        3
 212.766460419 = 228.456247296  vmlinuz.old                                    3

========================= sdg1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdg1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdg1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  a4 81 00 00 5d 01 00 00  57 0f f4 4d 57 0f f4 4d  |....]...W..MW..M|
00000010  57 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |W..M............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 50 91 a0 00  |............P...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 f7 d4 05 cc  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 68 5a 4c c6  68 5a 4c c6 68 5a 4c c6  |....hZL.hZL.hZL.|
00000090  57 0f f4 4d 68 5a 4c c6  00 00 00 00 00 00 00 00  |W..MhZL.........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 ac 09 00 00  65 0f f4 4d 65 0f f4 4d  |........e..Me..M|
00000110  65 0f f4 4d 00 00 00 00  00 00 01 00 08 00 00 00  |e..M............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 ca 91 a0 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 89 d5 05 cc  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 38 aa da ba  38 aa da ba 38 aa da ba  |....8...8...8...|
00000190  65 0f f4 4d 38 aa da ba  00 00 00 00 00 00 00 00  |e..M8...........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```I hope anybody will come by and help up , and I know , you guys will. your help are greatly appreciated .

thanks to doas777 for helping me out earlier.

quick fix, go to your bios and change your boot order. From the looks of it... you grub on sda is broken(the windows hardrive), however sdb appears to be working. If it does not boot, press e at the grub entry and edit the hardrive number.
from 
```
set root='(hd1,msdos3)
```'
to
```
set root='(hd0,msdos3)'
```
When you are in,
rune the command
 ```
sudo update-grub
```

I will recommend unpluging your ubuntu hardrive and rescue your windows boot loader on the windows harddrive. Replug your ubuntu device and make sure it always boot first.

---

### Post by maizuddin35 on 2011-06-29
yes , my sda is broken, my windows harddrive is broken , and sdb is still active. 

the actual thing is, I can load into grub, in the grub , there is only boot into (recover mode) and i have 2 (recover mode) and a windows.

---

### Post by maizuddin35 on 2011-06-29
by the way , thank you for helping me out, I hope this will do the trick, I'm still at my work place, and will be updating my thread here later..; thank you.

---

### Post by maizuddin35 on 2011-06-29
I don't understand the part where "I am 'in' and update-grub" cause when I edit the part you asked me to do, after that, I'm not sure what I should do, where should I go next...

what I did after I edit the above code is...Ctrl+x for boot.

---

### Post by maizuddin35 on 2011-06-29
I don't understand the part where "I am 'in' and update-grub" cause when I edit the part you asked me to do, after that, I'm not sure what I should do, where should I go next...

what I did after I edit the above code is...Ctrl+x for boot.

---

### Post by maizuddin35 on 2011-06-29
I had done some .. thing.. I think, but it aint working. 
i already change the "set root =" and boot it , and yet again, I am in the (recovery mode) .

I had **sudo fsck  **and again. same result.

---

### Post by oldfred on 2011-06-29
The grub in sda may work. Either grub or the script do not specify drive but it works. Grub was installed to my sda and said partition 7. I only have 3 partitions on sda and it booted sdc7 correctly.

But I think it is better to boot from the drive the system is on. And to have the bootloader for a system on the same drive. Then each drive can be booted on its own or if on drive fails you can still boot the  other.

The boot script shows both standard boot entry and recovery mode. Once you are in or fully booted into your Ubuntu intall you can run the 
```
sudo udpate-grub
```

I would set BIOS to boot sdb. And reinstall a windows boot loader to sda.

#To make sure grub reinstalls to sdb on grub updates. From your working Ubuntu once booted.
#to get grub to remember where to reinstall on updates:
```
sudo dpkg-reconfigure grub-pc
```
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
```
sudo debconf-show grub-pc
```

---

### Post by maizuddin35 on 2011-07-01
I was wondering, should I get into the live cd to boot?

---

### Post by oldfred on 2011-07-01
Did you try booting and installing grub to sdb? If that does not work then you need to use liveCD to reinstall grub2's boot loader to the MBR of sdb. 

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by maizuddin35 on 2011-07-03
I followed oldfred instruction #8 and the process told me to install the grub in all the partition, and I did that. I update-grub and it updated nicely. 

The grub shows everything in their proper place now. There is :

```
elementary-jupiter,with Linux 2.6.38.mgtk.38
elementary-jupiter, with Linux 2.6.38.mgtk.38(recovery mode)
elementary-jupiter, with Linux 2.6.35-30-generic
elementary-jupiter, with Linux 2.6.35-30-generic (recover mode)
```

**BUT**  when I Enter the 3rd choice or the first choice, it end up to be like this:

```
install : Disconnected from Plymouth :: plymoputh main process(3100) killed by SEGV signal

clien connectedfrom 1099...
```

and some more other stuffs, that I don't actually understand , and how to write this thing...

---

### Post by maizuddin35 on 2011-07-03
I think I will remove the linux-generic-38 . What do you think?

---

### Post by oldfred on 2011-07-03
I hope you did not install to all the partitions. It gives you the option to install that way, but you should not as I posted.

You seem to be able to boot with recovery mode? Then grub is working but you have video issues or some other parameter that needs to be set.

These are Ubuntu parameters:

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Do you get a login and then a command line?
#To see video:
sudo lshw | grep -A 11 display
#Reconfigure graphics
sudo dpkg-reconfigure -phigh xserver-xorg
startx
#or now preferred to restart gdm, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

---

### Post by maizuddin35 on 2011-07-03
oh my, I installed on all partition , because that is what the system recommended , and I was thought, it is the right way ..is it not?

yes, I get into login in a command line, there I just login, but then, it is just a command line...

---

### Post by oldfred on 2011-07-03
After you login try running those command and report any errors.

You also can try updates. But I think it is more of a video issue or other parameter.

Normally you cannot get into system, so you have to chroot from a liveCD, but you do not need to.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Installing to the Linux partitions will not cause any issues. Install to windows PBR destroys windows boot but windows can be repaired.

---

### Post by maizuddin35 on 2011-07-04
how to chroot into the system? can use sudo -i only? then run all those command in a live cd mode?

---

### Post by oldfred on 2011-07-04
If you can boot to command line you do not need chroot. But then you do need sudo on every line or use sudo -i and you do not have to type it for every line.

If you cannot boot your system to command line using recovery mode, then you have to chroot into it.

This is chroot to reinstall grub.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by maizuddin35 on 2011-07-04
is it advisable to chroot into the system root using live cd?

---

### Post by oldfred on 2011-07-04
If you can boot to a login and a command line you do not have to chroot. If you cannot boot your system,  then you have to use liveCD and chroot to get into your system.

Have you tried recovery mode?

The instructions on installing the boot loader everywhere were just wrong. Elsewhere it will tell you that installing grub2's boot loader to a partition is not recommended as it is unreliable. If you install and boot from the MBR then it is fine.

---

### Post by maizuddin35 on 2011-07-04
this is some error/failed-to-load when I login using the command line :

[CODE]login:Mon Jul 4 08:12:39 MYT 2011 on tty1
(i cant see the whole word)parts:failed to exec /etc/update-motd.d/10-help-text: Exec format error
...parts:/etc/update-mpotd.d/10-help-text exited with return code 1
..ix maizuddin35 2.6.35-30-generic #54-Ubuntu SMPTue Jun 7 18:40:23
elementary-jupiter
[CODE]

does this error-failed output bring something to you?

---

### Post by maizuddin35 on 2011-07-04
leave the latest reply behind...

I already successfully chroot into the system via live cd, thank you for the link , it is very very helpful, now, im waiting for it to update and dist-upgrade, and some other thing that you told me to do ...

will be update later ... 

thank you again :D

---

### Post by maizuddin35 on 2011-07-05
I try to followed this link, on installing back grub
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
and here is the output : please look at the last part of the result

```

root@ubuntu:/etc/default# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
Suggested packages:
  desktop-base
The following packages will be REMOVED:
  grub
The following NEW packages will be installed:
  grub-pc
0 upgraded, 1 newly installed, 1 to remove and 7 not upgraded.
Need to get 788kB of archives.
After this operation, 1,425kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/main grub-pc i386 1.98+20100804-5ubuntu3.3 [788kB]
Fetched 788kB in 2min 32s (5,175B/s)                                           
Preconfiguring packages ...
dpkg: grub: dependency problems, but removing anyway as you requested:
 startupmanager depends on grub | grub-pc; however:
  Package grub is to be removed.
  Package grub-pc is not installed.
(Reading database ... 185838 files and directories currently installed.)
Removing grub ...
Processing triggers for man-db ...
Selecting previously deselected package grub-pc.
(Reading database ... 185792 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3.3_i386.deb) ...
Processing triggers for man-db ...
Setting up grub-pc (1.98+20100804-5ubuntu3.3) ...

Creating config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38.mgtk.38
Found initrd image: /boot/initrd.img-2.6.38.mgtk.38
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
ls: cannot access /media/0B9F-6BCE: No such file or directory
done

```

---

### Post by maizuddin35 on 2011-07-05
I reboot my computer, and after choosing at the grub , I don't get into any command line or anything, blank screen only. what does this mean?

anyone..?oldfred.?

---

### Post by oldfred on 2011-07-05
Now you get grub menu?

Can you try booting recovery mode. 

I have not seen it suggest something. Did you not install a desktop?

> Suggested packages:
  desktop-base

---

### Post by maizuddin35 on 2011-07-05
yes, I can access to the grub menu now. but it seems that, it takes so much time to load, I don't know why. Right now, I'm at my work place, I leave my computer alone , maybe still loading, but I'm not really sure bout what is happening right now..

Just now, before, I chroot my system via live cd, and update some extra package to install . and when i sudo apt-get upgrade , gdm is one of the installation package that need to be install .

> Now you get grub menu?

Can you try booting recovery mode. 

I have not seen it suggest something. Did you not install a desktop?

Quote:
Suggested packages:
desktop-base


I'm not sure about "desktop-base" but I will try back install it, when I reach back home.

---

### Post by maizuddin35 on 2011-07-06
oldfred: I already installed desktop-base , like you suggest me to do .. and here is the output, the last part, show some missing firmware, 

> root@ubuntu:/# apt-get install desktop-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnome kde xfce4 wmaker
The following NEW packages will be installed:
  desktop-base
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,555kB of archives.
After this operation, 6,156kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  desktop-base
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe desktop-base all 5.0.6 [4,555kB]
Fetched 4,555kB in 5min 1s (15.1kB/s)                                          
Selecting previously deselected package desktop-base.
(Reading database ... 186120 files and directories currently installed.)
Unpacking desktop-base (from .../desktop-base_5.0.6_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Setting up desktop-base (5.0.6) ...
update-alternatives: using /usr/share/images/desktop-base/moreblue-orbit-wallpaper.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode.
update-alternatives: using /usr/share/images/desktop-base/moreblue-orbit-splash.png to provide /usr/share/images/desktop-base/desktop-splash (desktop-splash) in auto mode.
update-alternatives: using /usr/share/images/desktop-base/moreblue-orbit-grub.png to provide /usr/share/images/desktop-base/desktop-grub (desktop-grub) in auto mode.
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.38.mgtk.38
Found initrd image: /boot/initrd.img-2.6.38.mgtk.38
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
done
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38.mgtk.38
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169

I hope you can look at it ...

---

### Post by oldfred on 2011-07-06
Now it says you do not have gnome or KDE? Did you do a server install?

It seems like a lot of packages are missing? Did the install complete normally?

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)

from command line:

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

---

### Post by maizuddin35 on 2011-07-06
No, I do normal installation, I installed elementary os - jupiter that is based on ubuntu 10.04/10.10*(not sure) 

yes,I installed the os completely via usb stick. Everything when well till this come out : [http://ubuntuforums.org/showthread.php?t=1792084]("http://ubuntuforums.org/showthread.php?t=1792084"). I already update the graphic card driver in the os . 

that means, I need to reinstall back all of those thing.

and again, when I reboot after installed desktop-base just now, I end up hanging in a blank screen with this " _ "

---

### Post by oldfred on 2011-07-06
Do you get a grub menu? I think it should be hold shift key down to get grub menu. Then try repair/recovery version.

I think part of the issue is that this is not Ubuntu, I am trying Ubuntu fixes.

---

### Post by maizuddin35 on 2011-07-06
> **oldfred said:**
> Do you get a grub menu? I think it should be hold shift key down to get grub menu. Then try repair/recovery version.

I think part of the issue is that this is not Ubuntu, I am trying Ubuntu fixes.

I pretty sure that this os rely on ubuntu the most. I think . err.. 

right now, the grub menu are already shown. I have the grub menu everytime I boot and I can choose between recovery mode and the normal boot itself. 

I will try to install the respective package that you told me earlier. thank you oldfred

---

### Post by maizuddin35 on 2011-07-07
oldfred: I think , I want to reinstall back the OS. what do you think?, cause right now, the internet connection at my place is just sucky, I can't even connect into it anymore. I can only connect at my work place. 

Should I make a new topic? 

How can I reinstall back the os and still have the updated package and drivers?

---

### Post by oldfred on 2011-07-07
I really only know how to do reinstalls with a high speed connection to down load everything.

This may give some clues on how to save the downloads. But if you get things out of sync then you can have problems.

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by maizuddin35 on 2011-07-08
> **oldfred said:**
> I really only know how to do reinstalls with a high speed connection to down load everything.

This may give some clues on how to save the downloads. But if you get things out of sync then you can have problems.

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

thanks for the link oldfred. this thread is unsolve yet, I learn something from all this. Thank you :)

---

### Post by maizuddin35 on 2011-07-08
> **oldfred said:**
> 
Location of downloaded debs
/var/cache/apt/archives/

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

hold on, when I check on it , there is only partial and lock. what should I do? I didn't see anything else ,just that.

---

### Post by oldfred on 2011-07-08
Did you do any housekeeping. When you clean up system, it removes installed debs that it can redownload again. Saves space, but then you do not have the install files.

Running these commands housecleans system, but removes .debs. Did you run these? Or some of the gui tasks automatically run these commands to houseclean.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

---

### Post by maizuddin35 on 2011-07-09
> **oldfred said:**
> Did you do any housekeeping. When you clean up system, it removes installed debs that it can redownload again. Saves space, but then you do not have the install files.

Running these commands housecleans system, but removes .debs. Did you run these? Or some of the gui tasks automatically run these commands to houseclean.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

Yes. I did everything already. Thank you oldfred.

---

