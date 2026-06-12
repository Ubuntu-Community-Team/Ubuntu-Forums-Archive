---
title: "Grub , how to load winXp from another HDD?"
date: 2011-05-31
forum: General Help
---

### Post by evilheart on 2011-05-31
hi , i have two HDD  , one of 80 GB with Lubuntu and a broken windows , the other HDD is 160 GB with  another Win Xp , but it seems its windows boot loader is broken , or  the windows boot loader was essentially on the 80 GB HDD and  was replaced by GRUB , 
GRUB only detect the WinXp on the 80 GB HDD. 

how can i make GRUB detect winXp on the 160 GB HDD?
thanks in advace

---

### Post by garvinrick4 on 2011-05-31
While in Ubuntu: Open a terminal and:
```
sudo update-grub
```
Thats if Lubuntu comes with os-prober already installed, do not know but needs
os-prober to find other operating systems.
Package: os-prober                       
State: installed
Automatically installed: no
Version: 1.44ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 197 k
Depends: libc6 (>= 2.4)
Description: utility to detect other OSes on a set of drives
 This package detects other OSes available on a system and outputs the results
 in a generic machine-readable format.
##So if does not work try:
```
sudo apt-get install os-prober
```
```
sudo update-grub
```

---

### Post by oldfred on 2011-05-31
If the updates suggested by garvinrick4 do not work, post the boot info script. Windows often combines all boot files into one boot partition as that is the only way windows works. Grub then can only boot the one windows with the boot files. With XP you can often copy boot files and update boot.ini, and possibly the partition boot sector and make it work.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by evilheart on 2011-06-01
thanks guys here is the results , my windows is on sda1 , the broken one is on sdb1


                 ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 08010ced-9011-45ac-bdcb-d0488812211a root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 NTFS / exFAT / HPFS
/dev/sda2          51,199,155   312,560,639   261,361,485   f W95 Extended (LBA)
/dev/sda5          51,199,218   174,080,339   122,881,122   7 NTFS / exFAT / HPFS
/dev/sda6         174,080,403   312,560,639   138,480,237   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    13,563,929    13,563,867   7 NTFS / exFAT / HPFS
/dev/sdb2          13,565,950   156,296,384   142,730,435   f W95 Extended (LBA)
/dev/sdb5          39,086,208    78,172,289    39,086,082   b W95 FAT32
/dev/sdb6          78,172,353   117,258,434    39,086,082   b W95 FAT32
/dev/sdb7         117,258,498   156,296,384    39,037,887   b W95 FAT32
/dev/sdb8          13,565,952    38,053,887    24,487,936  83 Linux
/dev/sdb9          38,055,936    39,086,079     1,030,144  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        46E024EBE024E343                       ntfs       
/dev/sda5        CCACD5CAACD5AF68                       ntfs       Shippoden
/dev/sda6        36E8DCCDE8DC8C8D                       ntfs       Islamic
/dev/sdb1        158E090EC31BF0C9                       ntfs       amera
/dev/sdb5        6F6B-B04A                              vfat       POWER SYS
/dev/sdb6        71C0-188C                              vfat       GAMES
/dev/sdb7        7413-C480                              vfat       NARUTO
/dev/sdb8        08010ced-9011-45ac-bdcb-d0488812211a   ext4       
/dev/sdb9        93ed9f1a-0939-4894-a22b-a2cc07507020   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /media/POWER SYS         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb8        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=08010ced-9011-45ac-bdcb-d0488812211a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=08010ced-9011-45ac-bdcb-d0488812211a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 08010ced-9011-45ac-bdcb-d0488812211a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 158E090EC31BF0C9
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

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=08010ced-9011-45ac-bdcb-d0488812211a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=93ed9f1a-0939-4894-a22b-a2cc07507020 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.625663757 = 7.114252288    boot/grub/core.img                             1
  12.882724762 = 13.832720384   boot/grub/grub.cfg                             1
   8.165664673 = 8.767815680    boot/initrd.img-2.6.38-8-generic               1
   6.623035431 = 7.111430144    boot/vmlinuz-2.6.38-8-generic                  1
   8.165664673 = 8.767815680    initrd.img                                     1
   6.623035431 = 7.111430144    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  0e 04 d8 04 30 33 7b fd  6a 48 ed 29 44 71 25 7b  |....03{.jH.)Dq%{|
00000010  a0 81 99 11 d0 60 57 ae  0f 99 00 3f da 54 55 3f  |.....`W....?.TU?|
00000020  75 14 5c 8f 83 5e ac e7  dd 90 37 7f 84 04 e6 41  |u.\..^....7....A|
00000030  0b f8 a5 44 80 af 04 c4  c7 fb 89 93 23 8b 8a 6e  |...D........#..n|
00000040  69 6d 9c 3f 2c 2c 9b d1  3b ee d8 49 1d e5 80 98  |im.?,,..;..I....|
00000050  59 23 18 10 92 d2 dd ed  06 29 cc b0 32 af 55 26  |Y#.......)..2.U&|
00000060  ec 99 91 44 25 e3 a1 a4  63 5e a1 7b f4 a7 69 a8  |...D%...c^.{..i.|
00000070  7f f7 a6 dc 89 7c c6 1a  6b d6 dd 81 ae d7 92 fe  |.....|..k.......|
00000080  78 03 3b d5 00 c3 12 c0  4d fb 20 2e 30 48 7f e4  |x.;.....M. .0H..|
00000090  19 bd 82 30 2c 41 3d 21  ed c4 c9 ad 5f 88 39 b4  |...0,A=!...._.9.|
000000a0  c1 42 c0 60 53 5d 9f 58  18 09 c3 17 79 b2 3e 4a  |.B.`S].X....y.>J|
000000b0  a2 de 70 56 ff 9d 15 3a  88 86 12 f1 32 6a b9 41  |..pV...:....2j.A|
000000c0  5e e0 4a 5f 3d 80 1c da  5c fe e6 44 7a 1e 88 00  |^.J_=...\..Dz...|
000000d0  ea 12 4e 58 39 a1 91 cd  6a 59 03 39 1e ff ef 4d  |..NX9...jY.9...M|
000000e0  1f e3 17 f9 6a 05 c1 c4  49 fb fa 3c 2d ad 4b 21  |....j...I..<-.K!|
000000f0  2e df 06 47 e1 ae af c2  50 75 0a aa 2e 9e 6f f9  |...G....Pu....o.|
00000100  1d 14 e1 e4 52 a9 b8 8b  b3 82 e7 96 80 79 b8 0c  |....R........y..|
00000110  84 c4 24 62 b1 97 2d 87  7f ec 3d fb 2f 4e be f7  |..$b..-...=./N..|
00000120  79 10 92 23 e0 ae 8e 13  92 82 16 b3 de 06 e0 64  |y..#...........d|
00000130  70 09 b2 c8 18 cd b7 bc  28 74 d4 6b c4 20 e0 a7  |p.......(t.k. ..|
00000140  96 e4 d0 91 fd 06 07 99  f4 99 50 25 a5 2a ce 9b  |..........P%.*..|
00000150  2a c0 4e 2b b2 02 14 4a  0f 1b ff c8 80 03 cf de  |*.N+...J........|
00000160  a9 e2 11 70 4b 03 ab a1  33 ef a1 a4 3c f0 8d 34  |...pK...3...<..4|
00000170  f2 0e 8b 9b 6f 76 f2 a2  e7 ee 40 c5 e8 24 c0 60  |....ov....@..$.`|
00000180  44 67 f1 bb d2 85 71 8a  15 dc 85 85 a8 e0 cc 2c  |Dg....q........,|
00000190  9b 07 2a 24 09 5f 6a 10  a2 07 04 b5 b2 ea 84 04  |..*$._j.........|
000001a0  94 55 db 9b ec bd e5 19  3a 8b 35 2b 36 f2 51 94  |.U......:.5+6.Q.|
000001b0  08 fb 69 20 38 4d 51 a8  84 6d ab bd be f9 00 01  |..i 8MQ..m......|
000001c0  c1 ff 0b fe ff ff 82 68  85 01 02 68 54 02 00 fe  |.......h...hT...|
000001d0  ff ff 05 fe ff ff 84 d0  d9 03 41 68 54 02 00 00  |..........AhT...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
umount: /tmp/BootInfo0/sda6: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by Rebelli0us on 2011-06-01
**update-grub** should fix it and add a new entry to your grub boot menu. It uses info from boot.ini on your broken XP partition, but if that XP was a windows dual boot (with no boot.ini) then you gonna need some hands on help.

---

### Post by garvinrick4 on 2011-06-01
##sda has no boot files in sda1 windows xp and is the 160 gig drive:
Use this below from:[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") : Bookmark link for yourself:

XP fix boot 
How to restore the Windows install  XP bootloader For this you will need your Windows install XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows install grub XP administrator password. This will leave you at at a command line, so type in the following two commands: 

```
 fixboot 
``````
 fixmbr 
``````
 exit
```  ## If you have no XP disk use this for sda drive:##Using an Ubuntu install disk using Try Ubuntu open a terminal with internet working:

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```##May show error messages about the rest of lilo missing, ignore, we just want MBR


##sdb your 80 gig drive has Ubuntu 11.04 Natty on it in sdb8:
Put in a live CD (an install CD and using Try Ubuntu) and when it boots up
open a terminal and use these commands, copy and paste:
```
sudo mount /dev/sdb8 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
``````
sudo umount /mnt
``````
reboot
```This should get your house in order. YOU WILL have to boot off of sdb and do an:
```
sudo update-grub
```and set your BIOS to boot off of sdb instead of sda since Ubuntu linux is in sdb drive:

##When you boot sda first in order of boot you will only get that drives Windows install:
##When you boot sdb first in order of boot you will get all installs because using grub2 from Ubuntu install
to boot with.

---

### Post by evilheart on 2011-06-02
> **garvinrick4 said:**
> ##sda has no boot files in sda1 windows xp and is the 160 gig drive:
Use this below from:[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") : Bookmark link for yourself:

XP fix boot 
How to restore the Windows install  XP bootloader For this you will need your Windows install XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows install grub XP administrator password. This will leave you at at a command line, so type in the following two commands: 

```
 fixboot 
``````
 fixmbr 
``````
 exit
```  ## If you have no XP disk use this for sda drive:##Using an Ubuntu install disk using Try Ubuntu open a terminal with internet working:

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```##May show error messages about the rest of lilo missing, ignore, we just want MBR


##sdb your 80 gig drive has Ubuntu 11.04 Natty on it in sdb8:
Put in a live CD (an install CD and using Try Ubuntu) and when it boots up
open a terminal and use these commands, copy and paste:
```
sudo mount /dev/sdb8 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
``````
sudo umount /mnt
``````
reboot
```This should get your house in order. YOU WILL have to boot off of sdb and do an:
```
sudo update-grub
```and set your BIOS to boot off of sdb instead of sda since Ubuntu linux is in sdb drive:

##When you boot sda first in order of boot you will only get that drives Windows install:
##When you boot sdb first in order of boot you will get all installs because using grub2 from Ubuntu install
to boot with.

thanks guys , i tried this method , but when i tried fixmbr on sda1 the windows repair gave me a warning message , 

it says that fixmbr may damage my partition table , because windows found non- standard something . 

i tried updating grub again , but it still can't detect WinXp on sda1 , also it still gives me Y&#547;Y&#547; or something like that at the bootscreen.

---

### Post by oldfred on 2011-06-02
The error message at the end of the boot script may indicate that you need to run chkdsk on sda6. Linux will not mount NTFS partitions if it needs chkdsk so it does not damage it more, so that chkdsk then might not be able to fix it. Chkdsk should not hurt anyway and should be run periodically on NTFS partitions.

> umount: /tmp/BootInfo0/sda6: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by evilheart on 2011-06-02
> **oldfred said:**
> The error message at the end of the boot script may indicate that you need to run chkdsk on sda6. Linux will not mount NTFS partitions if it needs chkdsk so it does not damage it more, so that chkdsk then might not be able to fix it. Chkdsk should not hurt anyway and should be run periodically on NTFS partitions.


XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

sd6 ?? but my windows are on sda1 , and sdb1 ,  
unfortunately the problem still exist , i used chkdsk /r on both sda1 , sdb1 , but grub still can't detect winXp on sda1.

by the way , the warning it gives me after using fixmbr is because there is non-standard master boot record.

---

### Post by oldfred on 2011-06-02
You run chkdsk on all NTFS and FAT partitions, just like to run e2fsck on Linux ext2, ext3 or ext4 partitions.

---

### Post by evilheart on 2011-06-06
thanks guys , after googling , i found how to solve the problem 

it seems that my other windows installation , didn't even had boot.inin ,ntldr, ntdetect.com files  !!!!

so even bootcfg , bootfix , chkdsk /r had no effects , even bootcfg wasn't able to detect my windows installation.

i just copied ntdlr , ntdetect.com from the windows CD , from the i386 folder to the windows partition , created another boot.ini file , the script is in that site 

[http://neosmart.net/wiki/display/EBCD/Rebuilding+Boot.ini]("http://neosmart.net/wiki/display/EBCD/Rebuilding+Boot.ini")

[http://help.wugnet.com/windows/bootcfg-find-Windows-OS-ftopict615929.html]("http://help.wugnet.com/windows/bootcfg-find-Windows-OS-ftopict615929.html")
then 

```
sudo update-grub
```

and grub detected it.

i hope that help someone else

---

