---
title: "Can only mount  4 out of 5 partions on USB drive"
date: 2011-04-25
forum: General Help
---

### Post by jecook on 2011-04-25
I have a problem with mounting one of the 5 NTFS partitions on my external USB hard drive.

On attempting to mount the drive I get the following message:

> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, none is already mounted on none
mount failedInitially I thought this was due to having the drive plugged in on boot rather than plugging in after boot and letting UBUNTU recognise the partitions, but having tried this it was not the case.

I then thought perhaps the partition had a problem so I copied the data off the partition (sdb6) deleted the partition and then recreated then copying data back. This did not solve the problem.

I then tried to recreate all the partitions on another external USB drive (using a Windows Utility called Partition Wizard) I removed existing partitions on the new drive and then copied each partition from the old drive to the new un-partitioned drive. This did not solve the problem.

Having tried copying partitions (previous paragraph) I thought perhaps I had also copied the problem so I deleted all the partitions on the second drive again, then created 5 new empty ntfs partitions and then copied the data files from each partition on the original drive. This did not solve the problem.

Throughout the above partitioning/copying operations I kept the same drive labels and order of partitions so that links (for both Windows and Ubuntu) were unchanged.

I have run the boot_info_script with the following result:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,779,263    16,777,216  12 Compaq diagnostics
/dev/sda2    *     16,779,264   148,344,209   131,564,946   7 HPFS/NTFS
/dev/sda3         148,344,210   271,434,239   123,090,030   7 HPFS/NTFS
/dev/sda4         271,437,822   312,580,095    41,142,274   5 Extended
/dev/sda5         271,437,824   308,387,839    36,950,016  83 Linux
/dev/sda6         308,389,888   312,580,095     4,190,208  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,639,569   195,639,507   7 HPFS/NTFS
/dev/sdb2         195,639,570   976,768,064   781,128,495   f W95 Ext d (LBA)
/dev/sdb5         195,639,633   390,925,709   195,286,077   7 HPFS/NTFS
/dev/sdb6         390,925,773   586,211,849   195,286,077   7 HPFS/NTFS
/dev/sdb7         586,211,913   781,497,989   195,286,077   7 HPFS/NTFS
/dev/sdb8         781,498,053   976,768,064   195,270,012   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D8444E9A444E7B70                       ntfs       PQSERVICE                     
/dev/sda2        A47AC1277AC0F758                       ntfs       ACER                          
/dev/sda3        01CBE628E0814680                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3d1fbb19-1047-436e-9376-bba4c94a25f5   ext4       Ubuntu                        
/dev/sda6        2e6459fd-75d2-4fd2-9bcf-3ab4e9001715   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1C5C6AFB5C6ACF58                       ntfs       APOLLO                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4A22AB1422AB0453                       ntfs       APOLLO Music                  
/dev/sdb6        01CBF6C3DEF03190                       ntfs       APOLLO Reports 1              
/dev/sdb7        7AF6DC35F6DBEEFF                       ntfs       APOLLO Reports 2              
/dev/sdb8        30DE0128DE00E7C4                       ntfs       APOLLO Backups                
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /media/APOLLO Reports 2  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/APOLLO Music      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/APOLLO            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/APOLLO Backups    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro single 
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
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d8444e9a444e7b70
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a47ac1277ac0f758
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

=============================== sda5/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 /               ext4    errors=remount-ro 0       1
/dev/sdb6       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 145.5GB: boot/grub/core.img
 143.5GB: boot/grub/grub.cfg
 139.9GB: boot/initrd.img-2.6.35-22-generic
 146.2GB: boot/initrd.img-2.6.35-28-generic
 145.6GB: boot/vmlinuz-2.6.35-22-generic
 145.9GB: boot/vmlinuz-2.6.35-28-generic
 146.2GB: initrd.img
 139.9GB: initrd.img.old
 145.9GB: vmlinuz
 145.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 33 02 00 fe  |............3...|
000001d0  ff ff 05 fe ff ff 02 d0  33 02 00 f8 3f 00 00 00  |........3...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200I would be grateful if someone could offer an explanation as to what is causing the problem and advise how I can get this volume mounted.

Could it be one of the files on the partition that is causing the problem?

Cheers
Jon

---

