---
title: "after installation: nothing happens when booting"
date: 2011-02-13
forum: General Help
---

### Post by Binary&lt;ind on 2011-02-13
Hello everybody,

Today I am trying to install ubuntu 10.10 32 bits on my computer.

I used to be running debian on dual boot with windows XP,

After a failed attempt at upgrading my debian to squeeze (screen problems) I decided to abandon debian and switch to ubuntu.

Therefore, I downloaded the CD image and went for the installationm everything seemed to go wellm I installed it on the disk that was previously used by my debian. Then When rebooting after Installm at the moment where the GRUB is supposed to startm nothing happens. nothing : no message. etc

I am sorry because you must have 10 messages a day about dual boot problems.. looking at previous posts I did not find something similar. I see that you ask people to run the boot info script here is the result (next post).

thank you very much

---

### Post by Binary&lt;ind on 2011-02-13
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/mapper/isw_cjibehcaad_ARRAY and 
    looks on the same drive in partition #1 for (,msdos1)/boot/grub.

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_cjibehcaad_ARRAY1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

isw_cjibehcaad_ARRAY2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub.cfg /boot.ini /ntldr /NTDETECT.COM

isw_cjibehcaad_ARRAY3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   600,565,759   600,563,712  83 Linux
/dev/sdc2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sdc5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   976,751,999   976,751,937   c W95 FAT32 (LBA)


Drive: isw_cjibehcaad_ARRAY ___________________ _____________________________________________________

Disk /dev/mapper/isw_cjibehcaad_ARRAY: 500.0 GB, 499994853376 bytes
255 heads, 63 sectors/track, 60787 cylinders, total 976552448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cjibehcaad_ARRAY1                 63       112,454       112,392  de Dell Utility
/dev/mapper/isw_cjibehcaad_ARRAY2   *        112,455   966,807,764   966,695,310   7 HPFS/NTFS
/dev/mapper/isw_cjibehcaad_ARRAY3        966,807,765   976,543,154     9,735,390  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_cjibehcaad_ARRAY1 07D7-0812                              vfat       DellUtility                   
/dev/mapper/isw_cjibehcaad_ARRAY2 4E109B33109B214F                       ntfs                                     
/dev/mapper/isw_cjibehcaad_ARRAY3                                        vfat       DellRestore                   
/dev/mapper/isw_cjibehcaad_ARRAY: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        edda309d-a363-467b-9fc0-169c9ab8b0ea   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        9576ba70-a89e-4fe9-930b-963d246f7432   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        CA3C-EFDE                              vfat       GIGAFLIMS                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        455C-A758                              vfat       LURRYBURRY                    
/dev/sde: PTTYPE="dos" 
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cjibehcaad_ARRAY
isw_cjibehcaad_ARRAY1
isw_cjibehcaad_ARRAY2
isw_cjibehcaad_ARRAY3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_cjibehcaad_ARRAY2 /media/4E109B33109B214F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/isw_cjibehcaad_ARRAY3 /media/DellRestore       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/mapper/isw_cjibehcaad_ARRAY1 /media/DellUtility       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/GIGAFLIMS         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/edda309d-a363-467b-9fc0-169c9ab8b0ea ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=edda309d-a363-467b-9fc0-169c9ab8b0ea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=edda309d-a363-467b-9fc0-169c9ab8b0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set edda309d-a363-467b-9fc0-169c9ab8b0ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/mapper/isw_cjibehcaad_ARRAY1)" {
    insmod part_msdos
    insmod fat
    set root='(/dev/mapper/isw_cjibehcaad_ARRAY,msdos1)'
    search --no-floppy --fs-uuid --set 07d7-0812
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/mapper/isw_cjibehcaad_ARRAY2)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_cjibehcaad_ARRAY,msdos2)'
    search --no-floppy --fs-uuid --set 4e109b33109b214f
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=edda309d-a363-467b-9fc0-169c9ab8b0ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=9576ba70-a89e-4fe9-930b-963d246f7432 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
 270.7GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-25-generic-pae
 154.7GB: boot/vmlinuz-2.6.35-25-generic-pae
    .9GB: initrd.img
 154.7GB: vmlinuz

======================= isw_cjibehcaad_ARRAY2/grub.cfg: =======================

linux    /debian/linux   video=vesa:ywrap,mtrr vga=788 -- quiet
initrd    /debian/initrd.gz
boot

======================= isw_cjibehcaad_ARRAY2/boot.ini: =======================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /fastdetect /NoExecute=OptOut 

=========== isw_cjibehcaad_ARRAY2: Location of files loaded by Grub: ===========


    QtGB: grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  08 01 1f 01 2e 01 39 01  2b 01 2a 01 22 01 0c 01  |......9.+.*."...|
00000010  fa 00 d8 00 c0 00 bc 00  b2 00 9d 00 8b 00 8d 00  |................|
00000020  a7 00 bb 00 be 00 ad 00  94 00 90 00 9c 00 b6 00  |................|
00000030  e5 00 10 01 36 01 68 01  9e 01 d2 01 da 01 9c 01  |....6.h.........|
00000040  6d 01 83 01 9c 01 8d 01  8d 01 ac 01 c8 01 d8 01  |m...............|
00000050  de 01 e5 01 f0 01 05 02  f9 01 c5 01 a3 01 9f 01  |................|
00000060  bc 01 dc 01 ce 01 aa 01  8e 01 9a 01 b5 01 b0 01  |................|
00000070  b0 01 af 01 9c 01 94 01  ad 01 d8 01 f5 01 f1 01  |................|
00000080  eb 01 f4 01 ef 01 d7 01  b5 01 8b 01 6b 01 51 01  |............k.Q.|
00000090  41 01 42 01 44 01 68 01  8b 01 8f 01 9a 01 9e 01  |A.B.D.h.........|
000000a0  89 01 6e 01 60 01 6f 01  76 01 73 01 6e 01 50 01  |..n.`.o.v.s.n.P.|
000000b0  26 01 09 01 e2 00 9b 00  79 00 89 00 83 00 79 00  |&.......y.....y.|
000000c0  7d 00 83 00 b3 00 02 01  4f 01 7d 01 92 01 81 01  |}.......O.}.....|
000000d0  49 01 15 01 fa 00 dd 00  93 00 3e 00 10 00 f5 ff  |I.........>.....|
000000e0  eb ff 10 00 58 00 96 00  bd 00 00 01 6a 01 dc 01  |....X.......j...|
000000f0  52 02 e0 02 9f 03 69 04  25 05 dc 05 8c 06 15 07  |R.....i.%.......|
00000100  5e 07 90 07 af 07 90 07  44 07 f1 06 ae 06 4e 06  |^.......D.....N.|
00000110  c7 05 53 05 f1 04 82 04  03 04 85 03 25 03 e7 02  |..S.........%...|
00000120  b6 02 6a 02 11 02 cc 01  ac 01 9b 01 7e 01 61 01  |..j.........~.a.|
00000130  42 01 12 01 c1 00 62 00  0a 00 a7 ff 38 ff e5 fe  |B.....b.....8...|
00000140  a2 fe 65 fe 1d fe da fd  a6 fd 60 fd 01 fd 88 fc  |..e.......`.....|
00000150  fc fb 71 fb e1 fa 6b fa  ff d8 ff e0 00 10 41 56  |..q...k.......AV|
00000160  49 31 01 00 00 00 4e 80  00 00 4e 78 ff dd 00 04  |I1....N...Nx....|
00000170  00 00 ff db 00 84 00 08  06 06 07 06 06 08 07 07  |................|
00000180  07 09 09 08 0a 0c 14 0d  0c 0b 0b 0c 19 12 13 0f  |................|
00000190  14 1d 1a 1f 1e 1d 1a 1c  1c 20 24 2e 27 20 22 2c  |......... $.' ",|
000001a0  23 1c 1c 28 37 29 2c 30  31 34 34 34 1f 27 39 3d  |#..(7),01444.'9=|
000001b0  38 32 3c 2e 33 34 32 01  09 09 09 0c 0b 0c 00 fe  |82<.342.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi

---

### Post by oldfred on 2011-02-13
I do not know about LVM. And it does not look like you have a boot partition outside the LVM.

User with LVM & separate /boot
[http://ubuntuforums.org/showthread.php?t=1661290](http://ubuntuforums.org/showthread.php?t=1661290)

Essentially recommends boot partition with LVM.
[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

---

