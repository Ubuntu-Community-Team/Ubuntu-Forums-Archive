---
title: "Multi Boot Trouble"
date: 2011-09-28
forum: General Help
---

### Post by sleepingsword on 2011-09-28
Hi,

I am having a bit of a battle with Multi Booting

I have installed Ubuntu on Disk 1 (see below for my disk setup according to Windows)

Once Ubuntu installed I rebooted and Grub was not present like I have seen with previous Ubuntu installs. Just the normal Windows boot loader showing my 3 Windows installs.

So I tried using EasyBCD to fix my boot menu, I added an entry for Ubuntu, selected Type: Grub 2 (which is supposed to automatically search)

When rebooted I selected Ubuntu and I just get a Grub command prompt thing: Grub>

When I installed and was setting up my partitions there is an option: 'Device for boot loader information'

I left this as the default dev\sda (this happens to be my H: ) 

dev\sda is not my main system drive and I assume this is why it does not work, I tried switching the drive from D: to H: I also tried /Boot 

When H: is selected the Windows Boot menu reports a problem, when D: or /Boot is selected I get the Grub command prompt thing Grub>

My easyBCD config is as follows:

[INDENT][I]There are a total of 4 entries listed in the bootloader.

Default: Windows 7 Games
Timeout: 30 seconds
EasyBCD Boot Device: D:\

Entry #1
Name: Windows 7 Games
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Windows XP Audio
BCD ID: {ntldr}
Drive: D:\
Bootloader Path: \ntldr

Entry #3
Name: Windows 8 Developer Preview
BCD ID: {f6becebb-db83-11e0-869e-8dd2113c75ae}
Drive: N:\
Bootloader Path: \Windows\system32\winload.exe

Entry #4
Name: Linux
BCD ID: {f6becec2-db83-11e0-869e-8dd2113c75ae}
Drive: D:\
Bootloader Path: \NST\AutoNeoGrub0.mbr
[/I][/INDENT]


My Drive setup as follows:

Disk 0
D: OS XP (System, Active, Primary Partition) 
C: OS Windows 7 (Page File, Crash Dump, Logical Drive) 
Disk 1
F: Storage (Primary)
N: OS Windows 8 (Primary)
/Boot
/Swap
/
/Home
Disk 2
G: Storage (Primary)
Disk 3
H: Storage (Primary)
Disk 4
I: Storage (Active, Primary)
K: Storage (Primary)
Disk 5
L: Storage (Primary)
Disk 6
J: Storage (Primary)


Any help is appreciated :)

---

### Post by oldfred on 2011-09-28
Some here like EasyBCD and it seems to work for many. But if you have more than one Hard Drive why not install grub2's boot loader to another drive. I normally suggest each drive has a system and its boot loader on that drive, but you do not have to have that.

To see where everything is installed. (Does not show BCD info which you posted).

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by sleepingsword on 2011-09-28
Thanks here is the text file (I had to boot a live CD to get this, I dont know if that effects the result)

**I am not using the two drives labeled XP old / Windows 7 Old




```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdc3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdc8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 33200 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /ldlinux.sys /IO.SYS /MSDOS.SYS /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
196 heads, 27 sectors/track, 184575 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             27   362,364,407   362,364,381   7 NTFS / exFAT / HPFS
/dev/sdb2         362,364,928   976,771,071   614,406,144   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   771,969,023   771,966,976   7 NTFS / exFAT / HPFS
/dev/sdc2         771,969,024   874,369,023   102,400,000   7 NTFS / exFAT / HPFS
/dev/sdc3         874,371,070   976,771,071   102,400,002   5 Extended
/dev/sdc5         874,371,072   874,872,831       501,760  83 Linux
/dev/sdc6         874,874,880   890,497,023    15,622,144  82 Linux swap / Solaris
/dev/sdc7         890,499,072   910,366,719    19,867,648  83 Linux
/dev/sdc8         910,368,768   976,771,071    66,402,304  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 8487 MB, 8487174144 bytes
255 heads, 63 sectors/track, 1031 cylinders, total 16576512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             63    16,576,511    16,576,449   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20BCFD26BCFCF75E                       ntfs       1TB New Apps
/dev/sdb1        C870D2CB70D2BF7E                       ntfs       OLD XP Music 200GB
/dev/sdb2        0EF01FA8F01F9555                       ntfs       OLD Windows 7 300GB New
/dev/sdc1        F0D6B259D6B22030                       ntfs       Audio Appz
/dev/sdc2        FC1A91ED1A91A4E4                       ntfs       Windows 8
/dev/sdc5        7e896314-8205-4203-9dbd-17c93ed8a199   ext2       
/dev/sdc6        e7f1cd4c-8002-4560-a58c-c1c85055455c   swap       
/dev/sdc7        beac963c-c05a-4e27-8062-073cb2f799d6   ext4       
/dev/sdc8        ced27015-faff-4bfe-8c6a-e44a919e6b78   ext4       
/dev/sdd1        EEB2C881B2C8502F                       ntfs       1TB Appz Archive
/dev/sde1        B08EA03B8E9FF7D4                       ntfs       Downloads
/dev/sdf1        C6AE8086AE80712B                       ntfs       1TB Samples
/dev/sdg1        3C5B-9124                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/7e896314-8205-4203-9dbd-17c93ed8a199 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7        /media/beac963c-c05a-4e27-8062-073cb2f799d6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc8        /media/ced27015-faff-4bfe-8c6a-e44a919e6b78 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdg1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

--------------------------------------------------------------------------------

============================= sdc5/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos7)'
search --no-floppy --fs-uuid --set=root beac963c-c05a-4e27-8062-073cb2f799d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root 7e896314-8205-4203-9dbd-17c93ed8a199
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 7e896314-8205-4203-9dbd-17c93ed8a199
	linux	/vmlinuz-2.6.38-8-generic root=UUID=beac963c-c05a-4e27-8062-073cb2f799d6 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 7e896314-8205-4203-9dbd-17c93ed8a199
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=beac963c-c05a-4e27-8062-073cb2f799d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 7e896314-8205-4203-9dbd-17c93ed8a199
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 7e896314-8205-4203-9dbd-17c93ed8a199
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 417.063098907 = 447.818092544  grub/grub.cfg                                  1
 416.993561745 = 447.743427584  initrd.img-2.6.38-8-generic                   53
 416.941434860 = 447.687456768  vmlinuz-2.6.38-8-generic                      20

=============================== sdc7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc7 during installation
UUID=beac963c-c05a-4e27-8062-073cb2f799d6 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc5 during installation
UUID=7e896314-8205-4203-9dbd-17c93ed8a199 /boot           ext2    defaults        0       2
# /home was on /dev/sdc8 during installation
UUID=ced27015-faff-4bfe-8c6a-e44a919e6b78 /home           ext4    defaults        0       2
# swap was on /dev/sdc6 during installation
UUID=e7f1cd4c-8002-4560-a58c-c1c85055455c none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdg1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdg1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdg1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

Unknown BootLoader on sdc3

00000000  ed f2 74 16 0f 0e ea 72  62 6d 35 16 e1 6b e1 19  |..t....rbm5..k..|
00000010  d9 4a 88 31 e1 c9 97 4c  26 20 b0 31 20 11 cb ad  |.J.1...L& .1 ...|
00000020  5d e1 ec 8f a1 94 c8 8e  26 82 dc 24 81 26 c9 de  |].......&..$.&..|
00000030  5e 88 8a e0 f5 0e d0 cb  36 5e 9b 1d 56 c9 a3 8f  |^.......6^..V...|
00000040  3c 5f 81 28 91 e2 f6 77  1b d5 ca bb a2 c8 48 1c  |<_.(...w......H.|
00000050  b2 a0 28 99 d8 39 cd 55  68 86 ae b1 f1 27 1f 67  |..(..9.Uh....'.g|
00000060  c7 43 40 f5 27 d7 cd cc  d8 1c 55 a9 a5 d2 5a a3  |.C@.'.....U...Z.|
00000070  eb 45 a6 86 e9 9e 55 e7  81 42 a0 9a 0d ad 13 99  |.E....U..B......|
00000080  10 98 9c 1b d2 77 06 e6  ee 68 91 d0 03 c2 03 86  |.....w...h......|
00000090  44 16 6c 72 b9 5e e9 7b  df 26 ac d9 9c 50 b5 62  |D.lr.^.{.&...P.b|
000000a0  d9 60 78 41 2f d2 ed 9e  db 3f 45 57 23 1b 64 a8  |.`xA/....?EW#.d.|
000000b0  d0 86 86 1c 6e 07 3c 6c  4f 5f 10 0d 56 c9 2a ce  |....n.<lO_..V.*.|
000000c0  1f 82 d7 06 cb c2 7a 67  eb b7 a6 32 bc 10 b0 f8  |......zg...2....|
000000d0  ac b2 21 a6 c6 76 13 97  93 2d 42 ba 46 48 1e 6c  |..!..v...-B.FH.l|
000000e0  32 04 cc da 72 65 1d d8  dd 8e c1 9c e2 01 6a f9  |2...re........j.|
000000f0  8f 0a 0b 83 93 2c ee 2f  ac 39 f8 00 23 19 41 66  |.....,./.9..#.Af|
00000100  6c 44 72 6e 8e de 6e 8f  b8 dd 87 23 cc 75 ac 89  |lDrn..n....#.u..|
00000110  af 90 9e 1b 43 de 8f 44  da 72 2b 50 86 ab 6e 3c  |....C..D.r+P..n<|
00000120  be e2 2d 8e 87 6b b8 8e  8f a0 7a 5f 4b 10 99 f2  |..-..k....z_K...|
00000130  6b 64 d5 63 27 4b bd 86  f6 0e 0e 57 d8 62 01 50  |kd.c'K.....W.b.P|
00000140  a4 7c 90 36 3e 37 57 18  e4 e3 4d b6 38 71 23 22  |.|.6>7W...M.8q#"|
00000150  95 6d 95 1c 59 35 e1 c6  cb 80 e5 e7 1b 78 c6 88  |.m..Y5.......x..|
00000160  30 a1 07 a7 88 4d 93 b4  79 f0 f4 79 6e ef 26 a5  |0....M..y..yn.&.|
00000170  75 59 49 53 10 6b 1e 4d  d0 da de e4 f7 d9 be f5  |uYIS.k.M........|
00000180  dc 47 d0 3a 4a 12 0f 92  92 8c 98 43 57 d4 ef 57  |.G.:J......CW..W|
00000190  b3 23 51 6b 09 50 71 f0  d1 cb 9e 26 d2 77 4d de  |.#Qk.Pq....&.wM.|
000001a0  8f dd 5e 26 cd da 48 55  5f c5 26 e4 ec 89 a3 b4  |..^&..HU_.&.....|
000001b0  dc 4c cf 39 0e 40 29 24  43 e4 93 c4 aa cc 00 fe  |.L.9.@)$C.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a8 07 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a8  07 00 00 68 ee 00 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-09-28
I do not see grub2's boot loader installed anywhere. It normally defaults to sda, unless you tell it otherwise. But when you install Windows to a second or more drive it usually puts its boot loader into sda & Windows 7 creates the boot/recovery partition on sda.

It looks like you had XP first, as Windows moved the Windows 7 boot files to the XP boot partition. Windows always moves boot files as it can only boot from one active (boot flag) partition.

For standard desktops without RAID or LVM, I do not recommend a separate /boot partition as it makes it a bit hard to fix and understand how it works.

Since it looks like you boot sdb with Windows I would install grub2's boot loader to sdc. But you do not show any core.img which is part of grub2. I think you will have to chroot into your system and install fully reinstall grub from that.

Be sure to also mount the /boot partition
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[URL="http://ubuntuforums.org/showthread.php?t=1470597"]
[/URL]

---

### Post by sleepingsword on 2011-09-28
Many thanks oldfred the problem is now solved :)

I followed this guide: [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html") and it worked a treat!


Thanks Again!

---

### Post by oldfred on 2011-09-28
Glad it worked.

Link is a good presentation of chrooting. Essentially the same as the link I posted, but with more graphics.:)

---

