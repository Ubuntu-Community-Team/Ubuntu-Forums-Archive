---
title: "re-imaged my desktop and lost my Windows 7 partition in grub."
date: 2012-02-18
forum: General Help
---

### Post by cptrohn on 2012-02-18
So I needed to re-image my desktop and no Grub no longer gives me the option of booting in Windows 7 pro partition... (which I need for work)

If I run a ```
sudo update-grub
```  It comes back with this in a terminal.

```
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

And of course I checked my disk with gparted as well to be sure that my partitions were there as they should have been as well.

Now I have never really had to mess with the grub.conf file, is this what I am needing to do to be able to boot into 7 pro when I need to again?

Here is the output of the grub.conf
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Leppie on 2012-02-18
Could you download the [boot info script]("http://bootinfoscript.sourceforge.net/") and post the generated RESULTS.txt?

---

### Post by cptrohn on 2012-02-18
> **Leppie said:**
> Could you download the [boot info script]("http://bootinfoscript.sourceforge.net/") and post the generated RESULTS.txt?

Hi thanks....

I downloaded the script and followed the directions, but I am not seeing a results script anywhere...

This what I get when I run it.
[code]sudo bash ~/Desktop/boot_info_script060
/home/cptrohn/Desktop/boot_info_script060: /home/cptrohn/Desktop/boot_info_script060: is a directory[code]

---

### Post by Leppie on 2012-02-18
Try the following:
```
sudo bash ~/Desktop/boot_info_script060/boot_info_script060.sh

```

---

### Post by cptrohn on 2012-02-18
OK.. forgot to extract  duhh..

Here are the results.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

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

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   981,805,366   981,598,519   7 NTFS / exFAT / HPFS
/dev/sda3         981,807,102 1,953,523,711   971,716,610   5 Extended
/dev/sda5       1,937,276,928 1,953,523,711    16,246,784  82 Linux swap / Solaris
/dev/sda6         981,807,104 1,921,026,047   939,218,944  83 Linux
/dev/sda7       1,921,028,096 1,937,262,591    16,234,496  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1999.7 GB, 1999696297984 bytes
255 heads, 63 sectors/track, 243115 cylinders, total 3905656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 3,905,642,474 3,905,642,412   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        68C2EDCEC2EDA094                       ntfs       System Reserved
/dev/sda2        9E7EF74F7EF71F29                       ntfs       
/dev/sda5        0663c1cf-ecc2-42d0-b2f2-9c7dcab5c50e   swap       
/dev/sda6        688dc4f6-9301-4ea9-ac73-aa80282702ab   ext4       
/dev/sda7        0c6d1836-b9f5-4f6d-8f76-9dbad1fab1a7   swap       
/dev/sdb1        08A0ADA962A4F28A                       ntfs       HomeBackUp

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/9E7EF74F7EF71F29  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/HomeBackUp        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr1         /media/WD SmartWare      udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=688dc4f6-9301-4ea9-ac73-aa80282702ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=688dc4f6-9301-4ea9-ac73-aa80282702ab ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=688dc4f6-9301-4ea9-ac73-aa80282702ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=688dc4f6-9301-4ea9-ac73-aa80282702ab ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 688dc4f6-9301-4ea9-ac73-aa80282702ab
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 68C2EDCEC2EDA094
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=688dc4f6-9301-4ea9-ac73-aa80282702ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0c6d1836-b9f5-4f6d-8f76-9dbad1fab1a7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  8d 42 0c 8b 4a ec 33 c8  e8 1b b7 ea ff b8 98 13  |.B..J.3.........|
00000010  24 08 e9 0b c5 fe ff 8d  4d e8 e9 c0 59 e5 ff 8b  |$.......M...Y...|
00000020  4d f0 e9 2a c1 f4 ff 8b  54 24 08 8d 42 0c 8b 4a  |M..*....T$..B..J|
00000030  e4 33 c8 e8 f0 b6 ea ff  b8 d4 13 24 08 e9 e0 c4  |.3.........$....|
00000040  fe ff ff 75 08 e8 cf c7  ea ff 59 c3 ff 75 08 e8  |...u......Y..u..|
00000050  c5 c7 ea ff 59 c3 ff 75  08 e8 bb c7 ea ff 59 c3  |....Y..u......Y.|
00000060  ff 75 08 e8 b1 c7 ea ff  59 c3 ff 75 08 e8 a7 c7  |.u......Y..u....|
00000070  ea ff 59 c3 ff 75 08 e8  9d c7 ea ff 59 c3 ff 75  |..Y..u......Y..u|
00000080  08 e8 93 c7 ea ff 59 c3  ff 75 08 e8 89 c7 ea ff  |......Y..u......|
00000090  59 c3 ff 75 08 e8 7f c7  ea ff 59 c3 ff 75 08 e8  |Y..u......Y..u..|
000000a0  75 c7 ea ff 59 c3 ff 75  08 e8 6b c7 ea ff 59 c3  |u...Y..u..k...Y.|
000000b0  ff 75 08 e8 61 c7 ea ff  59 c3 ff 75 08 e8 57 c7  |.u..a...Y..u..W.|
000000c0  ea ff 59 c3 ff 75 08 e8  4d c7 ea ff 59 c3 ff 75  |..Y..u..M...Y..u|
000000d0  08 e8 43 c7 ea ff 59 c3  ff 75 08 e8 39 c7 ea ff  |..C...Y..u..9...|
000000e0  59 c3 8b 54 24 08 8d 42  0c 8b 4a e8 33 c8 e8 35  |Y..T$..B..J.3..5|
000000f0  b6 ea ff b8 1c 14 24 08  e9 25 c4 fe ff 8b 54 24  |......$..%....T$|
00000100  08 8d 42 0c 8b 8a 74 ff  ff ff 33 c8 e8 17 b6 ea  |..B...t...3.....|
00000110  ff 8b 4a f8 33 c8 e8 0d  b6 ea ff b8 04 15 24 08  |..J.3.........$.|
00000120  e9 fd c3 fe ff 8b 54 24  08 8d 42 0c 8b 8a 6c ff  |......T$..B...l.|
00000130  ff ff 33 c8 e8 ef b5 ea  ff 8b 4a f8 33 c8 e8 e5  |..3.......J.3...|
00000140  b5 ea ff b8 5c 15 24 08  e9 d5 c3 fe ff ff 75 e0  |....\.$.......u.|
00000150  e8 c4 c6 ea ff 59 c3 8d  4d e0 e9 86 03 ef ff 8d  |.....Y..M.......|
00000160  4d ec e9 02 be ee ff 8d  8d 94 fe ff ff e9 07 10  |M...............|
00000170  f4 ff 8b 54 24 08 8d 42  0c 8b 8a 90 fe ff ff 33  |...T$..B.......3|
00000180  c8 e8 a2 b5 ea ff 8b 4a  70 33 c8 e8 98 b5 ea ff  |.......Jp3......|
00000190  b8 a4 15 24 08 e9 88 c3  fe ff ff 75 e4 e8 77 c6  |...$.......u..w.|
000001a0  ea ff 59 c3 8d 4d e4 e9  39 03 ef ff 8d 4d f0 e9  |..Y..M..9....M..|
000001b0  b5 bd ee ff 8d 8d 94 fe  ff ff e9 ba 0f f4 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 50  f3 38 00 e8 f7 00 00 fe  |.......P.8......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 f3 38 00 00  |...........P.8..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by Leppie on 2012-02-18
the following section indicates that windows should still have an entry in the grub menu:
```
### BEGIN /etc/grub.d/30_os-prober ### 
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
     insmod part_msdos
     insmod ntfs     set root='(hd0,msdos1)'
     search --no-floppy --fs-uuid --set=root 68C2EDCEC2EDA094
     chainloader +1 
} 
### END /etc/grub.d/30_os-prober ###

```If it does not show after a reboot anyway, you could create a separate script for your windows entry:
```
sudo touch /etc/grub.d/35_win7 && sudo chmod a+x /etc/grub.d/35_win7 && sudo vim /etc/grub.d/35_win7
```Then paste something like this into the file:
```
echo "Adding Windows 7 on sda2" >&2
cat << EOF
menu**entry** "Windows 7 (loader) (on /dev/sda1) --class windows --class os {
     insmod part_msdos
     insmod ntfs
     set root='(hd0,msdos1)'
     search --no-floppy --fs-uuid --set=root 68C2EDCEC2EDA094
     chainloader +1 
}
EOF
```Save and exit the file and run update-grub:
```
sudo update-grub
```

---

### Post by cptrohn on 2012-02-18
Yeah, it's showing it's there...  The machine is just not giving me the option to choose which OS to boot into to after a few reboots and a couple of complete poweroffs.

Just boots straight in the ubuntu partition... weird, never had it happen to me before and have reimaged plenty of times.

I'll give that script a try and see what happens.... 

Thanks much for all your help!

---

### Post by Leppie on 2012-02-18
Do you get the Grub menu at all when booting?

---

### Post by cptrohn on 2012-02-18
> **Leppie said:**
> Do you get the Grub menu at all when booting?

Nope.. no grub menu at all.

Now after I log into ubuntu I can mount my NTFS filesystem and get to  my files on windows though...

Just kinda weird really.

---

### Post by cptrohn on 2012-02-18
and when I run ```
sudo fdisk -l
```


I get this back..
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   981805366   490799259+   7  HPFS/NTFS/exFAT
/dev/sda3       981807102  1953523711   485858305    5  Extended
/dev/sda5      1937276928  1953523711     8123392   82  Linux swap / Solaris
/dev/sda6       981807104  1921026047   469609472   83  Linux
/dev/sda7      1921028096  1937262591     8117248   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Leppie on 2012-02-19
> **cptrohn said:**
> Nope.. no grub menu at all.

So probably the menu just stays hidden.
Could you post your /etc/defaults/grub?

---

### Post by cptrohn on 2012-02-22
Hey thanks Leppie... Yeah I had to do a little fudging but got it to see it.  Thanks.

---

