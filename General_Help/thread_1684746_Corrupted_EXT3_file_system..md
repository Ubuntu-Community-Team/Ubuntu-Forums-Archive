---
title: "Corrupted EXT3 file system."
date: 2011-02-09
forum: General Help
---

### Post by SmartFox on 2011-02-09
Hi, guys!
I am using Ubuntu since release 8.10, but it is first time when i can`t solve problem :(

Problems had begun when i tried to create new NTFS partition on unallocated disk space with Paragon Partition Manager (damn, that was stupid). Process was aborted with error (later i finally made it with Gparted without problems)

After reboot mine Ubuntu say:
```
Errors were found while checking the disk drive for /
Press F to attempt to fix errors, I to ignore, S to skip mounting or M for manual recovery.
```I pressed "F" but that had help only for a boot and doesn`t really fix error :`(

Later i booted from liveCD and had checked partition (/dev/sdb1; file system - ext3) with gparted (result - aborted fixing process with error)
Now i can`t even boot from that partition and even mount it from other linux system.

mine fdisk -l
```

/dev/sdb1   *           1        5957    47849568   83  Linux  -  problematic partition (unmountable)
/dev/sdb2            5958       29983   192988845    7  HPFS/NTFS
/dev/sdb3           29984      113905   674103460+   7  HPFS/NTFS
/dev/sdb4          113906      121602    61826152+   f  W95 Ext'd (LBA)
/dev/sdb5          113906      121602    61819904   83  Linux  -  fresh ubuntu

```When i run "fsck.ext3 /dev/sdb1", result:
```
fsck.ext3: Group descriptors look bad... trying backup blocks...
/dev/sdb1: clean, 438985/2992416 files, 7558358/11962392 blocks
```but it will have no effect...

When i try to mount it - "mount: Stale NFS file handle"

PhotoRec recover most of my files, but i need complete partition.

P.S.: HDD is new - no bad blocks. Help me please, you are my last hope. Sorry for bad English.

---

### Post by SmartFox on 2011-02-10
Anyone, please say something...

---

### Post by SciFi-Bob on 2011-02-10
Could it be the "max 4 primary partitions" limit?
I have not tried it for some time, and it is possible that there no longer is such a limit, but I remember I had problems in Ubuntu/Debian with more than 4 primary partitions.

Just a thought..

---

### Post by oldfred on 2011-02-10
Post this to see if we can see anything.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Some partition managers do not handle Linux partitions well.

Did you try testdisk to see what it saw?
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by SmartFox on 2011-02-11
Thank you for reply. Here`s RESULTS.txt :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

[B]sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: Stale NFS file handle[/B]

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

&#1044;&#1080;&#1089;&#1082; /dev/sda: 320.1 &#1043;&#1073;, 320072933376 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 38913 cylinders, &#1079;&#1072;&#1075;&#1072;&#1083;&#1086;&#1084; 625142448 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1110;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,523,784   123,523,722   7 HPFS/NTFS
/dev/sda2         123,523,785   625,137,344   501,613,560   f W95 Ext d (LBA)
/dev/sda5         123,523,848   625,137,344   501,613,497   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 1000.2 &#1043;&#1073;, 1000204886016 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 121601 cylinders, &#1079;&#1072;&#1075;&#1072;&#1083;&#1086;&#1084; 1953525168 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1110;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    95,699,198    95,699,136  83 Linux
/dev/sdb2          95,699,205   481,676,894   385,977,690   7 HPFS/NTFS
/dev/sdb3         481,676,895 1,829,883,815 1,348,206,921   7 HPFS/NTFS
/dev/sdb4       1,829,883,825 1,953,536,129   123,652,305   f W95 Ext d (LBA)
/dev/sdb5       1,829,883,904 1,953,523,711   123,639,808  83 Linux

/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5502F82223B6C4B0                       ntfs       Se7en                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        44AC4955AC4942A2                       ntfs       WD_290                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1496e976-8c60-4c0e-b634-6f8436632ea7   ext3                                     
/dev/sdb2        5C041F01041EDDB8                       ntfs       Home                          
/dev/sdb3        412A319B4726E8B2                       ntfs       Storage                       
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        c602c799-2eb6-4645-b408-40072d161df2   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
set locale_dir=($root)/boot/grub/locale
set lang=uk
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
menuentry 'Ubuntu, &#1079; Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=c602c799-2eb6-4645-b408-40072d161df2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, &#1079; Linux 2.6.32-28-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1110;&#1076;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    echo    '&#1047;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1077;&#1085;&#1085;&#1103; Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=c602c799-2eb6-4645-b408-40072d161df2 ro single 
    echo    '&#1047;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1077;&#1085;&#1085;&#1103; &#1087;&#1077;&#1088;&#1074;&#1080;&#1085;&#1085;&#1086;&#1075;&#1086; ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, &#1079; Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c602c799-2eb6-4645-b408-40072d161df2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, &#1079; Linux 2.6.32-24-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1110;&#1076;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    echo    '&#1047;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1077;&#1085;&#1085;&#1103; Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c602c799-2eb6-4645-b408-40072d161df2 ro single 
    echo    '&#1047;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1077;&#1085;&#1085;&#1103; &#1087;&#1077;&#1088;&#1074;&#1080;&#1085;&#1085;&#1086;&#1075;&#1086; ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c602c799-2eb6-4645-b408-40072d161df2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5502f82223b6c4b0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=c602c799-2eb6-4645-b408-40072d161df2 /               ext4    errors=remount-ro 0       1

=================== sdb5: Location of files loaded by Grub: ===================


 997.1GB: boot/grub/core.img
 954.3GB: boot/grub/grub.cfg
 997.9GB: boot/initrd.img-2.6.32-24-generic
 997.9GB: boot/initrd.img-2.6.32-28-generic
 997.9GB: boot/vmlinuz-2.6.32-24-generic
 997.9GB: boot/vmlinuz-2.6.32-28-generic
 997.9GB: initrd.img
 997.9GB: initrd.img.old
 997.9GB: vmlinuz
 997.9GB: vmlinuz.old
```](*,)


Ouput of TestDisk:

```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   * Linux                    0   1  1  5956 254 57   95699136
Directory /

No file found, filesystem seems damaged.















Use Right arrow to change directory, c to copy,
    h to hide deleted files, q to quit

```in testdisk.log i found:
```
Results
   * Linux                    0   1  1  5956 254 57   95699136
     EXT3 Large file Sparse superblock, 48 GB / 45 GiB
```full testdisk.log :
```


Fri Feb 11 20:53:29 2011
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-28-generic (#55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       625142448 sectors
/dev/sda: user_max   625142448 sectors
/dev/sda: native_max 625142448 sectors
/dev/sda: dco        625142448 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       1953525168 sectors
/dev/sdb: user_max   1953525168 sectors
/dev/sdb: native_max 1953525168 sectors
/dev/sdb: dco        1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA WDC WD3200YS-01P
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - ATA WDC WD10EARS-00M

Partition table type (auto): Intel
Disk /dev/sdb - 1000 GB / 931 GiB - ATA WDC WD10EARS-00M
Partition table type: Intel

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
NTFS at 5957/0/1
NTFS at 29983/0/1
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
 1 * Linux                    0   1  1  5956 254 57   95699136
     EXT3 Large file Sparse superblock, 48 GB / 45 GiB
 2 P HPFS - NTFS           5957   0  1 29982 254 63  385977690 [Home]
     NTFS, 197 GB / 184 GiB
 3 P HPFS - NTFS          29983   0  1 113904 254 54 1348206921 [Storage]
     NTFS, 690 GB / 642 GiB
 4 E extended LBA         113905   0  1 121601 254 63  123652305
 5 L Linux                113905   1 17 121601  57 56  123639808
     EXT4 Large file Sparse superblock Recover, 63 GB / 58 GiB
Partition table type (auto): Intel
Disk /dev/sdb - 1000 GB / 931 GiB - ATA WDC WD10EARS-00M
Partition table type: Intel

Analyse Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 5957/0/1
NTFS at 29983/0/1
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 * Linux                    0   1  1  5956 254 57   95699136
 2 P HPFS - NTFS           5957   0  1 29982 254 63  385977690 [Home]
 3 P HPFS - NTFS          29983   0  1 113904 254 54 1348206921 [Storage]
 4 E extended LBA         113905   0  1 121601 254 63  123652305
 5 L Linux                113905   1 17 121601  57 56  123639808
Computes LBA from CHS for Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121602 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121602 255 63

recover_EXT2: s_block_group_nr=0/365, s_mnt_count=0/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 11962392
recover_EXT2: part_size 95699136
     Linux                    0   1  1  5956 254 57   95699136
     EXT3 Large file Sparse superblock, 48 GB / 45 GiB
NTFS at 5957/0/1
filesystem size           385977690
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               24123601
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           5957   0  1 29982 254 63  385977690 [Home]
     NTFS, 197 GB / 184 GiB
NTFS at 29983/0/1
filesystem size           1348206921
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               91990198
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          29983   0  1 113904 254 54 1348206921 [Storage]
     NTFS, 690 GB / 642 GiB

recover_EXT2: s_block_group_nr=0/471, s_mnt_count=16/36, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 15454976
recover_EXT2: part_size 123639808
     Linux                113905   1 17 121601  57 56  123639808
     EXT4 Large file Sparse superblock Recover, 63 GB / 58 GiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * Linux                    0   1  1  5956 254 57   95699136
     EXT3 Large file Sparse superblock, 48 GB / 45 GiB
   P HPFS - NTFS           5957   0  1 29982 254 63  385977690 [Home]
     NTFS, 197 GB / 184 GiB
   P HPFS - NTFS          29983   0  1 113904 254 54 1348206921 [Storage]
     NTFS, 690 GB / 642 GiB
   L Linux                113905   1 17 121601  57 56  123639808
     EXT4 Large file Sparse superblock Recover, 63 GB / 58 GiB


dir_partition inode=2
   * Linux                    0   1  1  5956 254 57   95699136
     EXT3 Large file Sparse superblock, 48 GB / 45 GiB
ext2fs_dir_iterate failed with error 2133571402.
Directory /

interface_write()
 1 * Linux                    0   1  1  5956 254 57   95699136
 2 P HPFS - NTFS           5957   0  1 29982 254 63  385977690 [Home]
 3 P HPFS - NTFS          29983   0  1 113904 254 54 1348206921 [Storage]
 4 E extended LBA         113905   0  1 121601 254 63  123652305
 5 L Linux                113905   1 17 121601  57 56  123639808
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
write_all_log_i386: CHS: 113905/0/1,lba=1829883825

TestDisk exited normally.
```:(:(:(

---

### Post by oldfred on 2011-02-11
We seem to be seeing a lot of testdisk writing the extended partition beyond the end of the drive. You need to fix that. It may prevent other repairs from running as not being able to correctly read a partition table stops many processes.

I would first backup partition table and save to an external device.

Backup partition table to text file
sudo sfdisk -d /dev/sdb > PT.txt

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Some have fixed it just by reading the PT.txt file back in. Or editing PT.txt file. 
Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

A few have had this work. Not sure what internal process checks sizes.
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sdb
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit


I have not seen:
**Stale NFS file handle**

---

### Post by P4man on 2011-02-11
Im no expert, but this appears to be a BIOS problem? Can your bios handle such large drives? Is it configured for LBA? Also possible, the hdd is jumpered to limit the capacity to, what is it, 32 or 48GB?

---

### Post by Spyderkid on 2011-02-11
If you don't need the stuff can't you just format it?

---

### Post by SmartFox on 2011-02-18
**[oldfred]("http://www1.ubuntuforums.org/member.php?u=852711")**, i fixed overlaping partition error according to the second instruction and i did that:

```
fdisk /dev/sdb
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
```

now i have: (fdisk /dev/sdb; option; p)

```
/dev/sdb1   *           1        5957    47849568   83  Linux
/dev/sdb2            5958       29983   192988845    7  HPFS/NTFS
/dev/sdb3           29984      113905   674103460+   7  HPFS/NTFS
/dev/sdb4          113906      121602    61820671+   f  W95 Ext'd (LBA)
/dev/sdb5          113906      121602    61819904   83  Linux
```

(option v)

```
Remaining 1611 unallocated 512-byte sectors
```

but i still can`t mount sdb1 =(((((

```
root@smartfox-pc:/home/smartfox# mount -t ext3 /dev/sdb1 /media/abc
mount: Stale NFS file handle
```

---

### Post by Zill on 2011-02-18
> **SmartFox said:**
> ...but i still can`t mount sdb1 =(((((

```
root@smartfox-pc:/home/smartfox# mount -t ext3 /dev/sdb1 /media/abc
mount: Stale NFS file handle
```
No guarantees but you could try to force unmounting to release the stale file handle:
```
umount -f /dev/sdb1*
```
followed by a reboot.

---

### Post by edug on 2011-02-18
[SIZE=4]i have a Western Digital 2.0TB harddrive. was formated with NTFS format and has it just crashed unexpectedly and it has all the data that puts bread on my table.
On mac it needs to be formated when i put it on an Ubuntu and look at it via the Disk utility it says Unknown partition and i can not get anything via it..

when i check the partition table with fdisk -l it looks at the partition 
#Disk /dev/sdb doesn't contain a valid partition table#

have tried all sorts of things but heading to no where! if i do not recover this will loose my job.... please help????? Please community people i need your assistance like ASAP!
[/SIZE]

---

### Post by matt_symes on 2011-02-18
Hi

@edug Try test disc to recover the partition table.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Don't use such a large silly font. It will garner you no friends. And don't hijack threads. Start your own!!

Kind regards

---

### Post by SmartFox on 2011-02-18
**@ [Zill]("http://ubuntuforums.org/member.php?u=53885")**, 

```
smartfox@smartfox-pc:~$ sudo umount -f /dev/sdb1
umount2: Invalid argument
umount: /dev/sdb1: &#1085;&#1077; &#1087;&#1110;&#1076;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1081; ( that mean isn`t mounted )
```Strange but gparted detect it normally

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=183817&stc=1&d=1298048068[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=183818&stc=1&d=1298048068[/IMG]

---

### Post by oldfred on 2011-02-18
I do not remember now if it was the same or slightly different. I suggested running e2fsck on a partition and it would not unmount. The workaround was to download Slitaz and run the file check from that and it worked.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by SmartFox on 2011-02-18
```
root@slitaz:/home/tux# e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1: Resize inode not valid.  

/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)

```then **e2fsck -f -y -v /dev/sdb1** =

```
Inode 2897 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2913 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2929 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2945 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2961 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2977 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 2993 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 3009 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

.............bla-bla-bla-bla...................
.............bla-bla-bla-bla...................
.............bla-bla-bla-bla...................

Inode 8161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 28738 has illegal block(s).  Clear? yes

Illegal block #17 (1298067533) in inode 28738.  CLEARED.
Inode 46781 has illegal block(s).  Clear? yes

Illegal block #17 (1298067533) in inode 46781.  CLEARED.
Inode 48409 has illegal block(s).  Clear? yes

Illegal block #17 (1298067533) in inode 48409.  CLEARED.
Inode 61820 has illegal block(s).  Clear? yes

Illegal block #17 (1298067533) in inode 61820.  CLEARED.
Relocating group 0's block bitmap from 4 to 1283...
Relocating group 0's inode bitmap from 5 to 1284...
Relocating group 0's inode table from 6 to 9036...
Relocating group 1's block bitmap from 32772 to 34051...
Relocating group 1's inode bitmap from 32773 to 34052...
Relocating group 1's inode table from 32774 to 34053...
Relocating group 3's block bitmap from 98308 to 99587...
Relocating group 3's inode bitmap from 98309 to 99588...
Error allocating 511 contiguous block(s) in block group 3 for inode table: Could not allocate block in ext2 filesystem
Relocating group 5's block bitmap from 163844 to 165123...
Relocating group 5's inode bitmap from 163845 to 165124...
Relocating group 5's inode table from 163846 to 186178...
Relocating group 7's block bitmap from 229380 to 230401...
Relocating group 7's inode bitmap from 229381 to 230402...
Relocating group 7's inode table from 229382 to 230403...
Relocating group 9's block bitmap from 294916 to 296036...
Relocating group 9's inode bitmap from 294917 to 296037...
Error allocating 511 contiguous block(s) in block group 9 for inode table: Could not allocate block in ext2 filesystem
Relocating group 25's block bitmap from 819204 to 820225...
Relocating group 25's inode bitmap from 819205 to 820226...
Relocating group 25's inode table from 819206 to 820227...
Relocating group 27's block bitmap from 884740 to 885761...
Relocating group 27's inode bitmap from 884741 to 885762...
Relocating group 27's inode table from 884742 to 885763...
Relocating group 49's block bitmap from 1605636 to 1606915...
Relocating group 49's inode bitmap from 1605637 to 1606916...
Error allocating 511 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem
Relocating group 81's block bitmap from 2654212 to 2655233...
Relocating group 81's inode bitmap from 2654213 to 2655234...
Relocating group 81's inode table from 2654214 to 2655235...
Relocating group 125's block bitmap from 4096004 to 4097025...
Relocating group 125's inode bitmap from 4096005 to 4097026...
Relocating group 125's inode table from 4096006 to 4097027...
Relocating group 243's block bitmap from 7962628 to 7963715...
Relocating group 243's inode bitmap from 7962629 to 7963716...
Error allocating 511 contiguous block(s) in block group 243 for inode table: Could not allocate block in ext2 filesystem
Relocating group 343's block bitmap from 11239428 to 11240457...
Relocating group 343's inode bitmap from 11239429 to 11240458...
Error allocating 511 contiguous block(s) in block group 343 for inode table: Could not allocate block in ext2 filesystem
e2fsck: aborted
root@slitaz:/home/tux#
```

Hahhh... new "surprice" :-?

```
smartfox@smartfox-pc:~$ sudo mount /dev/sdb1 /media/abc
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

then i tried

```
root@smartfox-pc:/home/smartfox# fsck -y -b 819200 /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1: clean, 438985/2992416 files, 7558358/11962392 blocks
```

and again ((((((((

```
root@smartfox-pc:/home/smartfox# mount -t ext3 /dev/sdb1 /media/abc
mount: Stale NFS file handle
```

i think this is end....

---

### Post by oldfred on 2011-02-18
If you do not have good backups I would run photorec or similar tools to recover some data.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)

---

### Post by SmartFox on 2011-02-20
**oldfred**, it worked!!! I love you, man! :D You saved my files!!! :)

Here's how I did:

1) Using [**this**]("http://ubuntuforums.org/showpost.php?p=10434656&postcount=49") instruction i format superblocks, check inodes on partition and rebuilt journal

2) Finally I was able to mount it, but there was only one directory lost+found without any access (even root couldn`t)

3) Then using testdisc i got to "lost+found" (using P to list files) and found container with my home directory

4) And finally simply copied him to other HDD (using C)

problem [SIZE=5]**[SOLVED]**[/SIZE]  :guitar:

---

### Post by oldfred on 2011-02-20
Glad we managed to find something that worked.

---

