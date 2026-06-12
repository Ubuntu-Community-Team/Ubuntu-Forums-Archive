---
title: "Gparted not displaying patition information"
date: 2011-06-29
forum: General Help
---

### Post by JASONFUSARO on 2011-06-29
Gparted is not displaying drive partition information, so it is utterly useless to me, and once (&^%$#@ again I am back in LIMBO!!!

See the attached screenshots.


Now the problem with searching for help online is that the commands that are given are with the assumption that both systems are identical, ie. all software packages that exist on the helpers machine are working on the helpees machine, which seems to be the major bottleneck to getting help that works.


I once again had my system working like a charm and one install attempt has bogged me down.

What I need is to get Gparted working. Once that works then Distro installs will work also I hope. Because they don't recognize anything as being installed either. 


I wen't through testdisk about 40 times already, I must be doing something wrong.

```

I think it has something to do with the alighnment.



Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, [COLOR="Red"]60801 cylinders[/COLOR]
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200780    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       10240    82051987+   7  HPFS/NTFS
/dev/sda3           10241       [COLOR="red"]11579[/COLOR]    10755516    b  W95 FAT32
/dev/sda4           [COLOR="red"]11580[/COLOR]       60802   395383747+   f  W95 Ext'd (LBA)
/dev/sda5           11580       [COLOR="red"]22187[/COLOR]    85207552   83  Linux
/dev/sda6           [COLOR="red"]22188[/COLOR]       26927    38067048   83  Linux
/dev/sda7           26927       31729    38572032   83  Linux
/dev/sda8           31729       35171    27648000   83  Linux
/dev/sda9           35171       38613    27648000   83  Linux
/dev/sda10          38613       41800    25600000   83  Linux
/dev/sda11          41800       45250    27705344   83  Linux
/dev/sda12          45250       47892    21221376   83  Linux
/dev/sda13          47892       57108    74033928   83  Linux
/dev/sda14          59608       [COLOR="Red"]60802[/COLOR]     9590796   82  Linux swap / Solaris


fdisk output


Disk /dev/sda - 500 GB / 465 GiB - CHS [COLOR="red"]60801[/COLOR] 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

check_FAT: Unusual number of reserved sectors 8 (FAT), should be 1.                  
 1 * FAT32                    0   1  1    24 254 61     401560 [GRUB_Boot]
 2 P HPFS - NTFS             25   0  1 10239 254 63  164103975 [WindowsVista]
 3 P FAT32                10240   0  1 11578 254 60   21511032
 4 E extended LBA         11579   0  1 60801 254 63  790767495
 5 L Linux                11579   2  1 22186 218 41  170415104 [UbuntuStudio32bi]
   X extended             22187   0  1 26926  33 45   76134159
 6 L Linux                22187   1  1 26926  33 45   76134096 [ZenWalk]
   X extended             26926  65  1 31728  65 17   77144147
 7 L Linux                26926  66 21 31728  65 17   77144064 [Chakra]
   X extended             31728  96  1 35170 102  4   55296112
 8 L Linux                31728  97 50 35170 102  4   55296000 [Zorin]
   X extended             35170 133  1 38612 138 54   55296099
 9 L Linux                35170 134 37 38612 138 54   55296000 [Toorox]
   X extended             38612 170  1 41799 184 49   51200086
10 L Linux                38612 171 24 41799 184 49   51200000 [Mepis]
   X extended             41799 216  1 45249   2  1   55410769
11 L Linux                41799 217 19 45249   2  1   55410688 [ArchLinux]
   X extended             45249  33  1 47891  18 63   42442848
12 L Linux                45249  34 34 47891  18 63   42442752 [Fedora15]
   X extended             47891  50  1 57107 254 59  148067951
13 L Linux                47891  51 33 57107 254 59  148067856 [LinuxBuildEnviro]
  X extended             59607  14  1 60801  15 38   19181711
14 L Linux Swap           59607  15 57 [COLOR="red"]60801[/COLOR]  15 38   19181592                       
14 L

[Quick Search]  [ Backup ]
                            Try to locate partition


```



Why they are different I have no clue (values highlighted in [COLOR="red"]RED[/COLOR]


Once I solve this problem, what I need is the simplest and safest method to install Vista without screwing anything up.



[COLOR="Red"]**[SIZE="3"][SIZE="4"]BOOT INFO SCRIPT[/SIZE][/SIZE]**[/COLOR]

I can't seem to find a straight forward answer to fixing the alighnment issues after scouring the WEB, any help will be appreciated.




```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   [COLOR="Red"][B]According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63[/B][/COLOR].
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   [B][COLOR="red"]According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 164505600.[/COLOR][/B]
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /grub/core.img /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  7.0
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Chakra Linux (2011.04 - 
                       Aida) () ()
    Boot files:        /boot/grub/menu.lst /boot/burg/burg.cfg /etc/fstab 
                       /boot/burg/core.img

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  [COLOR="red"][B] Grub Legacy (v0.97) is installed in the boot sector 
                       of sda10 and looks at sector 653473792 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #11 for /boot/grub/menu.lst.[/B][/COLOR]
    Operating System:  MEPIS Linux 11.0
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.........f....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  [COLOR="red"][B]Syslinux looks at sector 2401720 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.[/B][/COLOR]
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             [COLOR="red"]63[/COLOR]       401,622       401,560   b W95 FAT32
/dev/sda2             401,625   164,505,599   164,103,975   7 NTFS / exFAT / HPFS
/dev/sda3         164,505,600   186,016,631    21,511,032   b W95 FAT32
/dev/sda4         186,016,635   976,784,129   790,767,495   f W95 Extended (LBA)
/dev/sda5         186,016,761   356,431,864   170,415,104  83 Linux
/dev/sda6         356,434,218   432,568,313    76,134,096  83 Linux
/dev/sda7         432,570,368   509,714,431    77,144,064  83 Linux
/dev/sda8         509,716,480   565,012,479    55,296,000  83 Linux
/dev/sda9         565,014,528   620,310,527    55,296,000  83 Linux
/dev/sda10        620,312,576   671,512,575    51,200,000  83 Linux
/dev/sda11        671,514,624   726,925,311    55,410,688  83 Linux
/dev/sda12        726,927,360   769,370,111    42,442,752  83 Linux
/dev/sda13        769,372,160   917,440,015   148,067,856  83 Linux
/dev/sda14        957,587,456   976,769,047    19,181,592  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7969 MB, 7969177600 bytes
246 heads, 62 sectors/track, 1020 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,557,039    15,556,978   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       c1b373f5-0c60-412f-bd35-77e7a00cce73   ext3       
/dev/sda1        C5A1-9CC6                              vfat       GRUB_Boot
/dev/sda10       44c39e41-b7d6-4e1b-87ea-e95e52d19d7f   ext3       Mepis
/dev/sda11       7d67d1c3-9a9f-464a-875a-7fb9d4ff328d   ext4       ArchLinux
/dev/sda12       b5e76b29-5858-4243-813a-4df73aff426a   ext4       Fedora15
/dev/sda13       5a65c4cf-c53f-458b-93aa-1d6dc34b326c   ext4       LinuxBuildEnviro
/dev/sda14       444c6212-e5e4-4747-9440-d21c987a10d3   swap       
/dev/sda2        0C91DEF3340A81DC                       ntfs       WindowsVista
/dev/sda3        CBCC-C0D1                              vfat       
/dev/sda5        66b21291-db1d-40b0-a01b-c75fc85ca2c8   ext4       UbuntuStudio32bi
/dev/sda6        d87417e5-d3b9-4121-81ec-0822cbe6455f   ext4       ZenWalk
/dev/sda7        a3b3cf37-9a99-401a-a55f-cef5b98b3d55   ext3       Chakra
/dev/sda8        21aa691f-5bf0-4b29-8ed3-9b3d4069ff50   ext3       Zorin
/dev/sda9        e65807a8-5580-443b-8467-1b030399b4dc   ext4       Toorox
/dev/sdb1        C349-00BA                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda10       /media/Mepis             ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda11       /media/ArchLinux         ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda12       /media/Fedora15          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda13       /media/LinuxBuildEnviro  ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/UbuntuStudio32bi  ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/ZenWalk           ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/Chakra            ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /media/Zorin             ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9        /media/Toorox            ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 /               ext4    errors=remount-ro 0       1
UUID=444c6212-e5e4-4747-9440-d21c987a10d3 none            swap    sw              0       0
/dev/sda3    /boot     ext3        defaults     0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 110.826653004 = 118.999212544  boot/grub/core.img                             1
 124.947048664 = 134.160871936  grub/core.img                                  1

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sda5        swap             swap        defaults         0   0
/dev/sda7        /                ext4        defaults,noatime 1   1
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 178.086590767 = 191.219020800  boot/initrd.splash                             1
 178.089985847 = 191.222666240  boot/vmlinuz                                   1
 178.089985847 = 191.222666240  boot/vmlinuz-2.6.37.4                          1

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Chakra GNU/Linux
title  Chakra GNU/Linux  [/boot/vmlinuz26]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=========================== sda7/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=burg
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -neda { command="set theme_name=neda" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set a3b3cf37-9a99-401a-a55f-cef5b98b3d55
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/444c6212-e5e4-4747-9440-d21c987a10d3 root=/dev/disk/by-uuid/a3b3cf37-9a99-401a-a55f-cef5b98b3d55 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26 Fallback' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set a3b3cf37-9a99-401a-a55f-cef5b98b3d55
	echo	'Loading Linux vmlinuz26 ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/444c6212-e5e4-4747-9440-d21c987a10d3 root=/dev/disk/by-uuid/a3b3cf37-9a99-401a-a55f-cef5b98b3d55 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26 Fallback (recovery mode)' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set a3b3cf37-9a99-401a-a55f-cef5b98b3d55
	echo	'Loading Linux vmlinuz26 ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/444c6212-e5e4-4747-9440-d21c987a10d3 root=/dev/disk/by-uuid/a3b3cf37-9a99-401a-a55f-cef5b98b3d55 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/20_memtest86+ ###
### END /etc/burg.d/20_memtest86+ ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	savedefault
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 576f791e-fca0-4941-9021-e124e0cab080
	linux /vmlinuz-2.6.38-8-generic root=UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 ro quiet splash vt.handoff=7
	initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	savedefault
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 576f791e-fca0-4941-9021-e124e0cab080
	linux /vmlinuz-2.6.38-8-generic root=UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 ro single
	initrd /initrd.img-2.6.38-8-generic
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=a3b3cf37-9a99-401a-a55f-cef5b98b3d55 / ext3 defaults 0 0
UUID=444c6212-e5e4-4747-9440-d21c987a10d3 swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 233.804771423 = 251.045961728  boot/burg/burg.cfg                             1
 233.848155975 = 251.092545536  boot/burg/core.img                             1
 233.830806732 = 251.073916928  boot/grub/menu.lst                             1
 233.797737122 = 251.038408704  boot/kernel26-fallback.img                     5
 233.876674652 = 251.123167232  boot/kernel26.img                              2
 233.847957611 = 251.092332544  boot/vmlinuz26                                 2

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=21aa691f-5bf0-4b29-8ed3-9b3d4069ff50 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=312e0bf6-8d8a-4d99-bf72-7a43fa39a87f none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
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
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set e65807a8-5580-443b-8467-1b030399b4dc
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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set e65807a8-5580-443b-8467-1b030399b4dc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
insmod vbe
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 576f791e-fca0-4941-9021-e124e0cab080
	linux /vmlinuz-2.6.38-8-generic root=UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 ro quiet splash vt.handoff=7
	initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 576f791e-fca0-4941-9021-e124e0cab080
	linux /vmlinuz-2.6.38-8-generic root=UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 ro single
	initrd /initrd.img-2.6.38-8-generic
}
menuentry "Slackware Linux (7.0) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d87417e5-d3b9-4121-81ec-0822cbe6455f
	linux /boot/vmlinuz-2.6.37.4 root=/dev/sda7
}
menuentry "Chakra Linux (2011.04_20110521-1) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set a3b3cf37-9a99-401a-a55f-cef5b98b3d55
	linux /boot/vmlinuz26 root=/dev/sda8
	initrd /boot/kernel26.img
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 21aa691f-5bf0-4b29-8ed3-9b3d4069ff50
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=21aa691f-5bf0-4b29-8ed3-9b3d4069ff50 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 21aa691f-5bf0-4b29-8ed3-9b3d4069ff50
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=21aa691f-5bf0-4b29-8ed3-9b3d4069ff50 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

========================== sda9/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
default 0

timeout 5

title Toorox
kernel /boot/vmlinuz root=/dev/sda10 vga=791 nomce noapic lang=us
#initrd /boot/initrd.gz

title Windows
root (hd0,0)
chainloader +1
makeactive
boot
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
/proc      /proc       proc   defaults             0 0
/sys       /sys        sysfs  noauto               0 0
/dev/fd0   /media/floppy auto   users,noauto,exec    0 0
/dev/dvd /media/dvd  auto   users,noauto,exec,ro 0 0
none       /dev/shm    tmpfs  nodev,nosuid,noexec  0 0
# Added by KNOPPIX
/dev/sda3 /media/sda3 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda4 /media/sda4 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda5 none swap sw 0 0
# Added by KNOPPIX
/dev/sda6 /media/sda6 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda7 /media/sda7 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda8 /media/sda8 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda9 /media/sda9 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda10 /media/sda10 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda11 /media/sda11 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda12 /media/sda12 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda13 /media/sda13 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda14 /media/sda14 ext3 noauto,users,exec 0 0
/dev/sda10 / ext4 defaults 0 1
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 289.878292084 = 311.254446080  boot/grub/core.img                             1
 275.738941193 = 296.072433664  boot/grub/grub.cfg                             1
 289.546474457 = 310.898159616  boot/grub/grub.conf                            1
 289.546474457 = 310.898159616  boot/grub/menu.lst                             1
 289.546657562 = 310.898356224  boot/grub/stage2                               1
 289.549999237 = 310.901944320  boot/vmlinuz                                   1
 275.737239838 = 296.070606848  grub/core.img                                  1

========================== sda10/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda11, newest kernel
root (hd0,10)
kernel /boot/vmlinuz root=/dev/sda11 nomce quiet splash vga=788 
initrd /boot/initrd.img
boot

title MEPIS at sda11, kernel 2.6.36-1-mepis-smp
root (hd0,10)
kernel /boot/vmlinuz-2.6.36-1-mepis-smp root=/dev/sda11 nomce quiet splash vga=788 
initrd /boot/initrd.img-2.6.36-1-mepis-smp
boot

title 
root (hd0,9)
kernel /boot/vmlinuz root=/dev/sda10

title Ubuntu, with Linux 2.6.38-8-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.38-8-generic root=UUID=66b21291-db1d-40b0-a01b-c75fc85ca2c8 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic

title 
root (hd0,6)
kernel /boot/vmlinuz-2.6.37.4 root=/dev/sda7

title 
root (hd0,7)
kernel /boot/vmlinuz26 root=/dev/sda8
initrd /boot/kernel26.img

title Ubuntu, with Linux 2.6.38-8-generic
root (hd0,8)
kernel /boot/vmlinuz-2.6.38-8-generic root=UUID=21aa691f-5bf0-4b29-8ed3-9b3d4069ff50 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic

title MEMTEST
kernel /boot/memtest86+.bin

--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda11 / ext3 defaults,noatime 1 1
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ext3 noauto,users,exec,relatime 0 0
/dev/sda2 /mnt/sda2 ntfs-3g noauto,users,noexec,uid=1000,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sda3 /mnt/sda3 ext3 noauto,users,exec,relatime 0 0
/dev/sda5 /mnt/sda5 ext4 noauto,users,exec,relatime 0 0
/dev/sda6 /mnt/sda6 ext4 noauto,users,exec,relatime 0 0
/dev/sda7 /mnt/sda7 ext3 noauto,users,exec,relatime 0 0
/dev/sda8 /mnt/sda8 ext3 noauto,users,exec,relatime 0 0
/dev/sda9 /mnt/sda9 ext4 noauto,users,exec,relatime 0 0
/dev/sda10 /mnt/sda10 ext3 noauto,users,exec,relatime 0 0
/dev/sda12 /mnt/sda12 ext4 noauto,users,exec,relatime 0 0
/dev/sda13 /mnt/sda13 ext4 noauto,users,exec,relatime 0 0
/dev/sda14 swap swap sw,pri=1 0 0
/dev/sdb1 /mnt/sdb1 ntfs-3g noauto,users,noexec,uid=1000,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr0 /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 311.569343567 = 334.545035264  boot/grub/menu.lst                             1
 311.600708008 = 334.578712576  boot/grub/stage2                               2
 311.662345886 = 334.644895744  boot/initrd.img                                5
 311.662345886 = 334.644895744  boot/initrd.img-2.6.36-1-mepis-smp             5
 311.574028015 = 334.550065152  boot/vmlinuz                                   2
 311.574028015 = 334.550065152  boot/vmlinuz-2.6.36-1-mepis-smp                2

========================== sda11/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#  Linux           Grub
# -------------------------
#  /dev/sda        (hd0)
#  /dev/sda3       (hd0,2)
#  /dev/sdb2       (hd1,1)

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# Boot entries follow.
# Each is implicitly numbered from 0 in the order of appearance below.

# You can use the commented entry to boot another system; copy and adjust
# it as many times as you want for all of your other installed systems.
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,11)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/7d67d1c3-9a9f-464a-875a-7fb9d4ff328d ro quiet resume=/dev/disk/by-uuid/a2bc74c5-4b82-4d85-9383-a72e43d26311   
initrd /boot/kernel26.img

# (1) Arch Linux fallback (useful if you change your hard disk/mainboard)
title  Arch Linux Fallback
root   (hd0,11)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/7d67d1c3-9a9f-464a-875a-7fb9d4ff328d ro
initrd /boot/kernel26-fallback.img

# (2) Optional entry for the system on sda1
#title sda1
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=7d67d1c3-9a9f-464a-875a-7fb9d4ff328d / ext4 defaults 0 1
UUID=a2bc74c5-4b82-4d85-9383-a72e43d26311 swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 322.334018707 = 346.103517184  boot/grub/menu.lst                             1
 320.526985168 = 344.163229696  boot/grub/stage2                               1
 320.539062500 = 344.176197632  boot/kernel26-fallback.img                     2
 322.334011078 = 346.103508992  boot/kernel26.img                              1
 322.330619812 = 346.099867648  boot/vmlinuz26                                 1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
timeout 300

menu title Zorin OS 5 64 bit
menu background splash.png
menu color title 1;37;44 #ffffffff #00000000 std

label live
menu label Boot the Live System
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label xforcevesa
menu label Boot Live in safe graphics mode
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --

label install
menu label Start the installer directly
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

label textonly
menu label Boot Live in textonly mode
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper textonly initrd=/casper/initrd.gz quiet --

label debug
menu label Boot the Live System without splash and show boot info
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz nosplash --

label memtest
menu label Run the memory test
kernel /isolinux/memtest
append -

label hd
menu label Boot from the first hard disk
localboot 0x80
append -


--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff 66 0f 1f 44 00 00  48 8d 0d 41 5b fd ff 48  |..f..D..H..A[..H|
00000010  8d 7c 24 70 31 f6 31 d2  e8 43 47 fd ff 49 8b 45  |.|$p1.1..CG..I.E|
00000020  00 4c 89 ef 4c 89 ac 24  30 01 00 00 ff 50 08 48  |.L..L..$0....P.H|
00000030  8d 74 24 70 48 8d bc 24  30 01 00 00 e8 8f 47 fd  |.t$pH..$0.....G.|
00000040  ff 48 8b bc 24 30 01 00  00 48 85 ff 74 06 48 8b  |.H..$0...H..t.H.|
00000050  07 ff 50 10 48 8d 35 05  5b fd ff 48 8d 7c 24 70  |..P.H.5.[..H.|$p|
00000060  e8 cb 4a fd ff e9 a9 fe  ff ff 66 0f 1f 44 00 00  |..J.......f..D..|
00000070  48 8d 44 24 50 41 0f b7  ce 48 89 ea 4c 89 ef 48  |H.D$PA...H..L..H|
00000080  89 c6 48 89 04 24 e8 15  bc ff ff 41 83 c6 01 e9  |..H..$.....A....|
00000090  7f fe ff ff 48 8d bc 24  40 01 00 00 e8 4f 3e fd  |....H..$@....O>.|
000000a0  ff 48 8b 7c 24 50 48 8b  6c 24 58 48 39 fd 48 89  |.H.|$PH.l$XH9.H.|
000000b0  fb 0f 84 8f f8 ff ff 66  0f 1f 84 00 00 00 00 00  |.......f........|
000000c0  48 89 df e8 28 3e fd ff  48 83 c3 08 48 39 dd 75  |H...(>..H...H9.u|
000000d0  ef e9 6b f8 ff ff 48 83  f8 01 0f 86 65 04 00 00  |..k...H.....e...|
000000e0  48 8b 6a 08 48 8b 55 08  48 8b 45 10 48 29 d0 48  |H.j.H.U.H.E.H).H|
000000f0  c1 f8 03 85 c0 0f 84 d7  fc ff ff 48 85 c0 0f 84  |...........H....|
00000100  35 04 00 00 31 c9 31 db  eb 61 66 0f 1f 44 00 00  |5...1.1..af..D..|
00000110  48 85 ff 74 1b 48 8d 4c  24 50 48 8d b4 24 70 01  |H..t.H.L$PH..$p.|
00000120  00 00 48 89 0c 24 e8 e5  3f fd ff 48 8b 7c 24 58  |..H..$..?..H.|$X|
00000130  48 83 c7 08 48 89 7c 24  58 48 8d bc 24 70 01 00  |H...H.|$XH..$p..|
00000140  00 e8 aa 3d fd ff 48 8b  55 08 48 8b 45 10 83 c3  |...=..H.U.H.E...|
00000150  01 48 29 d0 48 c1 f8 03  39 c3 0f 83 72 fc ff ff  |.H).H...9...r...|
00000160  89 d9 48 39 c8 0f 86 ce  03 00 00 48 8b 34 ca 48  |..H9.......H.4.H|
00000170  8d bc 24 70 01 00 00 48  83 c6 28 e8 d0 46 fd ff  |..$p...H..(..F..|
00000180  48 8b 7c 24 58 48 3b 7c  24 60 75 84 48 8d 44 24  |H.|$XH;|$`u.H.D$|
00000190  50 48 8d 94 24 70 01 00  00 48 89 fe 48 89 c7 48  |PH..$p...H..H..H|
000001a0  89 04 24 e8 78 1b 00 00  eb 8f 49 8d bd 10 01 00  |..$.x.....I.....|
000001b0  00 48 8d 8c 24 ac 01 00  00 48 29 c2 e8 7f 00 fe  |.H..$....H).....|
000001c0  ff ff 83 fe ff ff 7e 00  00 00 00 54 28 0a 00 fe  |......~....T(...|
000001d0  ff ff 05 fe ff ff 70 5d  28 0a 0f b7 89 04 00 00  |......p](.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by coffeecat on 2011-06-30
> **JASONFUSARO said:**
> I wen't through testdisk about 40 times already, I must be doing something wrong.

Going through testdisk 40 times was the mistake. There's a known bug in testdisk that does this (from your boot script output):

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       401,622       401,560   b W95 FAT32
/dev/sda2             401,625   164,505,599   164,103,975   7 NTFS / exFAT / HPFS
/dev/sda3         164,505,600   186,016,631    21,511,032   b W95 FAT32
/dev/sda4         186,016,635   [COLOR="Red"]976,784,129 [/COLOR]  790,767,495   f W95 Extended (LBA)
/dev/sda5         186,016,761   356,431,864   170,415,104  83 Linux
/dev/sda6         356,434,218   432,568,313    76,134,096  83 Linux
/dev/sda7         432,570,368   509,714,431    77,144,064  83 Linux
/dev/sda8         509,716,480   565,012,479    55,296,000  83 Linux
/dev/sda9         565,014,528   620,310,527    55,296,000  83 Linux
/dev/sda10        620,312,576   671,512,575    51,200,000  83 Linux
/dev/sda11        671,514,624   726,925,311    55,410,688  83 Linux
/dev/sda12        726,927,360   769,370,111    42,442,752  83 Linux
/dev/sda13        769,372,160   917,440,015   148,067,856  83 Linux
/dev/sda14        957,587,456   976,769,047    19,181,592  82 Linux swap / Solaris

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

The last sector of your extended partition (as it appears in the partition table) is beyond the physical end of the drive. This impossibility confuses Gparted, as described in this article by forum member srs5694:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

There is a fix described there involving the use of sfdisk, but don't use that because since he wrote that article, srs5694 has developed the utility fixparts which will fix this. See here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You've highlighted some other things in your boot script output, some of which probably do not matter or are not relevant. I haven't gone through all your post with a fine tooth comb (it's a bit overwhelming!), but I suggest you fix the partition table inconsistency with fixparts and then see if you have any residual problems.

---

### Post by JASONFUSARO on 2011-06-30
GREAT!! Thank You:biggrin:


Now were back, but the UbuntuStudio option of the multi boot menu runs Zorin.


Is the problem related to the start and end values?

If so what would be the simplest method ie. (application) to correct the problem. 
 


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029370

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200780    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       10240    82051987+   7  HPFS/NTFS
/dev/sda3           10241       [COLOR="red"]**11579**[/COLOR]    10755516    b  W95 FAT32
/dev/sda4           11580       60802   395376144+   f  W95 Ext'd (LBA)
/dev/sda5           [COLOR="Red"]**11580       22187**[/COLOR]    85207552   83  Linux
/dev/sda6           [COLOR="red"]**22188**[/COLOR]       26927    38067048   83  Linux
/dev/sda7           26927       31729    38572032   83  Linux
/dev/sda8           31729       35171    27648000   83  Linux
/dev/sda9           35171       38613    27648000   83  Linux
/dev/sda10          38613       41800    25600000   83  Linux
/dev/sda11          41800       45250    27705344   83  Linux
/dev/sda12          45250       47892    21221376   83  Linux
/dev/sda13          47892       57108    74033928   83  Linux
/dev/sda14          59608       60802     9590796   82  Linux swap / Solaris
/dev/sda15          57109       59217    16935936   83  Linux
/dev/sda16          59217       59607     3135488   82  Linux swap / Solaris

```




Thanks again

---

### Post by JASONFUSARO on 2011-06-30
Offtrack question

Once I get UbuntuStudio booting, will it be possible to use the Web browsers and their settings which I have already setup in UbuntuStudio? 

In other words is there a simple way to run them from any of the Distros I am working in. or should I move then to a created partition named something like SharedBrowsers and then from any distro use the particular browser.


I already have Opera,Firefox,Midori,Chromium, and a few more with settings and bookmarks and I don't want to have to redo everything from each Distro I run?

---

### Post by coffeecat on 2011-06-30
> **JASONFUSARO said:**
> Now were back, but the UbuntuStudio option of the multi boot menu runs Zorin.

You have such a medley of grub2 grub.cfg, legacy grub menu.lst and burg config files showing in your bootscript output that I have no idea what you are booting with. The boot script doesn't help because it says you have testdisk installed in the mbr - normally it would tell you which bootloader.

You need to reconfigure the configuration file for whichever bootloader you are using. If it's grub2 or legacy grub I can help you. Burg - no.

> **JASONFUSARO said:**
> Is the problem related to the start and end values?

In a word - no. If you are worried about start and end values of your partitions, you need to look at the output of 'fdisk -lu' which reports in sectors, rather than 'fdisk -l' which reports in cylinders. The occasional 1MiB gaps between some logical partitions is of no consequence.

> **JASONFUSARO said:**
> Offtrack question

Once I get UbuntuStudio booting, will it be possible to use the Web browsers and their settings which I have already setup in UbuntuStudio? 

In other words is there a simple way to run them from any of the Distros I am working in. or should I move then to a created partition named something like SharedBrowsers and then from any distro use the particular browser.


I already have Opera,Firefox,Midori,Chromium, and a few more with settings and bookmarks and I don't want to have to redo everything from each Distro I run?

With Firefox, you can import or export your bookmarks as a bookmarks.html file or bookmarks.json file. Chromium will import or export *html files. I don't know about the others, but if they can't import/export html files compatible with Firefox/Chromium then I don't know how you would do it.

---

### Post by JASONFUSARO on 2011-07-01
Thanks to the help of coffeecat and previously idoitprone and others I got things working, these guys are super forum members as I am sure there are plenty more.


But unfortunately other problems have forced me into a corner again and I am solving the problem by reinstalling the damned and starting from scratch.


But following the simple rules of:

 BACKING UP BEFORE EVERY MAJOR CHANGE
       MBR
       FULL PARTITION OF EACH DISTRO
       
 BACKUP OF THE BACKUPS

IF space permits Backup of the backups;) just being funny


RE-READING ALL PERTINENT INFORMATION BEFORE DOING SOMETHING CRITICAL


When things are working in Linux there is no comparison to Windows.


But when something goes wrong! Watch out, major learning curve involved in becoming Linux proficient.

---

