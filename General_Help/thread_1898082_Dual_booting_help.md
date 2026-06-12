---
title: "Dual booting help"
date: 2011-12-20
forum: General Help
---

### Post by bradleyG on 2011-12-20
Hi, I am trying to install Ubuntu 11.10 x64 to my desktop alongside windows 7 and I am running into some trouble for some reason.

I have windows 7 installed on a 60Gb SSD and I also have a 1TB HDD in my machine that i use for storage of windows files etc.

I figured since I have a bunch of space that I'm not using I could make a little ubuntu setup on the 1TB HDD. I put Ubuntu on a flash drive with the program they suggest on the website and booted from it. I then chose to install it with the first option "Install alongside windows". I created about a 150Gb partition for Ubuntu using the installer and let it install. It said it was done installing and needed to be restarted so I clicked restart now and then my computer booted into windows as expected.

What I would like to know is how can I get the option to choose which OS I want to boot into upon starting my computer.

I don't know if this helps at all but this is how it is setup:
[IMG]http://i1232.photobucket.com/albums/ff370/B-Rad_G/partition.png[/IMG]

My PC's specs are:
Mobo: Asus crosshair IV formula 
CPU: AMD Phenom II x6 1100t
RAM: Corsair vengeance DDR3 1600mhz 8Gb
GPU: AMD Radeon HD 6950 2Gb
PSU: Corsair GS600

Thanks for any help :)

---

### Post by oldfred on 2011-12-20
Post this from liveCD/USB so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk

Sometimes if only minor fixes are required this work and can run script:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bradleyG on 2011-12-20
Here it is:
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   117,227,519   117,020,672   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,657,449,994 1,657,447,947   7 NTFS / exFAT / HPFS
/dev/sdb2       1,657,450,494 1,953,523,711   296,073,218   5 Extended
/dev/sdb5       1,657,450,496 1,936,750,591   279,300,096  83 Linux
/dev/sdb6       1,936,752,640 1,953,523,711    16,771,072  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        684C40654C40305C                       ntfs       System Reserved
/dev/sda2        6A0649E10649AEBF                       ntfs       
/dev/sdb1        9000C23900C22656                       ntfs       WD
/dev/sdb5        efdbfe6a-9ae4-4f82-87dc-e5ee278af68d   ext4       
/dev/sdb6        6aa00fa0-e2d8-4cae-9144-9ff3e6f0f62e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/DSPORT_DVD_21     udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=efdbfe6a-9ae4-4f82-87dc-e5ee278af68d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=efdbfe6a-9ae4-4f82-87dc-e5ee278af68d ro recovery nomodeset 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root efdbfe6a-9ae4-4f82-87dc-e5ee278af68d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 684C40654C40305C
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=efdbfe6a-9ae4-4f82-87dc-e5ee278af68d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6aa00fa0-e2d8-4cae-9144-9ff3e6f0f62e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  c4 48 85 f6 48 0f 44 f0  ff 50 10 48 8d 35 36 0d  |.H..H.D..P.H.56.|
00000010  31 00 41 89 c5 48 89 df  e8 43 79 e6 ff 45 85 ed  |1.A..H...Cy..E..|
00000020  75 39 41 8b 44 24 04 48  8d 35 42 0d 31 00 41 c7  |u9A.D$.H.5B.1.A.|
00000030  44 24 04 00 00 00 00 48  89 ef 41 89 04 24 48 8b  |D$.....H..A..$H.|
00000040  5c 24 08 48 8b 6c 24 10  4c 8b 64 24 18 4c 8b 6c  |\$.H.l$.L.d$.L.l|
00000050  24 20 48 83 c4 28 e9 15  f1 f8 ff 44 89 ee 48 89  |$ H..(.....D..H.|
00000060  ef e8 fa b0 f5 ff 48 8b  5c 24 08 48 8b 6c 24 10  |......H.\$.H.l$.|
00000070  4c 8b 64 24 18 4c 8b 6c  24 20 48 83 c4 28 c3 90  |L.d$.L.l$ H..(..|
00000080  48 89 5c 24 e0 48 89 6c  24 e8 48 89 fb 4c 89 64  |H.\$.H.l$.H..L.d|
00000090  24 f0 4c 89 6c 24 f8 48  83 ec 28 e8 10 f3 f8 ff  |$.L.l$.H..(.....|
000000a0  48 8d 15 f1 0c 31 00 48  8d 35 8f 3b 26 00 48 89  |H....1.H.5.;&.H.|
000000b0  c7 e8 ba 8a e6 ff 48 89  c7 48 89 c5 e8 ff f2 f8  |......H..H......|
000000c0  ff 48 8d 15 f8 0c 31 00  48 8d 35 19 0d 31 00 48  |.H....1.H.5..1.H|
000000d0  89 c7 e8 99 8a e6 ff 48  8b 70 08 48 89 df 49 89  |.......H.p.H..I.|
000000e0  c4 48 85 f6 48 0f 44 f0  ff 50 10 48 8d 35 26 0d  |.H..H.D..P.H.5&.|
000000f0  31 00 41 89 c5 48 89 df  e8 63 78 e6 ff 45 85 ed  |1.A..H...cx..E..|
00000100  75 39 41 8b 44 24 04 48  8d 35 32 0d 31 00 41 c7  |u9A.D$.H.52.1.A.|
00000110  44 24 04 00 00 00 00 48  89 ef 41 89 04 24 48 8b  |D$.....H..A..$H.|
00000120  5c 24 08 48 8b 6c 24 10  4c 8b 64 24 18 4c 8b 6c  |\$.H.l$.L.d$.L.l|
00000130  24 20 48 83 c4 28 e9 35  f0 f8 ff 44 89 ee 48 89  |$ H..(.5...D..H.|
00000140  ef e8 1a b0 f5 ff 48 8b  5c 24 08 48 8b 6c 24 10  |......H.\$.H.l$.|
00000150  4c 8b 64 24 18 4c 8b 6c  24 20 48 83 c4 28 c3 90  |L.d$.L.l$ H..(..|
00000160  48 89 5c 24 e0 48 89 6c  24 e8 48 89 fb 4c 89 64  |H.\$.H.l$.H..L.d|
00000170  24 f0 4c 89 6c 24 f8 48  83 ec 28 e8 30 f2 f8 ff  |$.L.l$.H..(.0...|
00000180  48 8d 15 e1 0c 31 00 48  8d 35 af 3a 26 00 48 89  |H....1.H.5.:&.H.|
00000190  c7 e8 da 89 e6 ff 48 89  c7 48 89 c5 e8 1f f2 f8  |......H..H......|
000001a0  ff 48 8d 15 e8 0c 31 00  48 8d 35 cf 20 31 00 48  |.H....1.H.5. 1.H|
000001b0  89 c7 e8 b9 89 e6 ff 48  8b 70 08 48 89 df 00 fe  |.......H.p.H....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 a5 10 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  a5 10 00 f0 ff 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2011-12-20
Script looks normal. 

If booting into Windows directly you must be booting from sda, the internal drive. 

Have you tried booting from sdb, the external. You should be able to boot using a one time key (f12 on my system). To make it permanent you can change BIOS to boot external before internal. If external is not plugged in, then BIOS should default to internal drive.

---

### Post by oscarivera9 on 2011-12-20
> **oldfred said:**
> Script looks normal. 

If booting into Windows directly you must be booting from sda, the internal drive. 

Have you tried booting from sdb, the external. You should be able to boot using a one time key (f12 on my system). To make it permanent you can change BIOS to boot external before internal. If external is not plugged in, then BIOS should default to internal drive.

Yes,
 basically you need to go into the BIOS and in the boot options you need to make sure that you boot off of the 1TB hard drive because that's where Grub is.  Grub is the bootloader that allows you to choose which operating system you would like to use.  Once that's done and working properly, then you can customize Grub to boot according to your needs.

---

