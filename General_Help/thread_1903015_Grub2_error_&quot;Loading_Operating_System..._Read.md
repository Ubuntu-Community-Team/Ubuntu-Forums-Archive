---
title: "Grub2 error: &quot;Loading Operating System... Read Error&quot;"
date: 2012-01-01
forum: General Help
---

### Post by sailor420 on 2012-01-01
Hi all,

I recently had to reinstall Windows on my machine, which obviously took over the MBR. So I booted to a live-disk (on a USB key), then ran boot-repair to re-install Grub on all of the MBRs. This part went fine, but now I am having a very interesting issue--if I do not have the live USB key inserted into the computer, I get the following error when Grub is loading (i.e. before it shows the menu of OSes to select from):

```
Loading operating system...
Read error
```

This only happens when the USB key is not inserted.

Here are the things I have tried thus far to resolve this:
[LIST=1]
[*]Boot into Ubuntu, eject the USB key, then re-run boot-repair
[*]Boot into Ubuntu, run sudo grub-install /dev/sdX for each of my discs, then run sudo update-grub
[*]Change the boot order in my bios to see if setting one of the non-windows drives to boot first would help
[/LIST]

None of this has resolved the issue. I was posting for help originally in the boot-repair thread (link below), but this seems to be a bit bigger than just boot-repair, so I'm bringing it out to the wider audience.

Boot-repair thread: [http://ubuntuforums.org/showthread.php?t=1769482&page=11](http://ubuntuforums.org/showthread.php?t=1769482&page=11)

Info on my discs and partitions: [http://paste.ubuntu.com/789290/](http://paste.ubuntu.com/789290/)

Any help is much appreciated!

---

### Post by drs305 on 2012-01-01
Here is the RESULTS.txt:
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for ??.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for ??.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdi.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdi1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......#.V9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 4271888 of /dev/sdi1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 90.0 GB, 90028302336 bytes
42 heads, 25 sectors/track, 167463 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   175,833,087   175,831,040   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   899,290,716   899,290,654   7 NTFS / exFAT / HPFS
/dev/sdb2         899,291,134   976,771,071    77,479,938   5 Extended
/dev/sdb5         899,291,136   973,502,463    74,211,328  83 Linux
/dev/sdb6         973,504,512   976,771,071     3,266,560  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   122,881,184   122,881,122   7 NTFS / exFAT / HPFS
/dev/sdc2         122,882,046 1,250,242,559 1,127,360,514   f W95 Extended (LBA)
/dev/sdc5         245,762,433 1,250,242,559 1,004,480,127   7 NTFS / exFAT / HPFS
/dev/sdc6         229,156,864   245,762,047    16,605,184  82 Linux swap / Solaris
/dev/sdc7         122,882,048   229,154,815   106,272,768  83 Linux


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1    *             16     7,813,119     7,813,104   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FABC8229BC81E10D                       ntfs       
/dev/sdb1        8A54B81254B7FF4F                       ntfs       New Volume
/dev/sdb5        c022f957-8ac3-4315-951b-6b008398ad15   ext4       
/dev/sdb6        f0eea78e-726d-4d27-8ae0-95d01ce14ea7   swap       
/dev/sdc1        865443BC5443AE2D                       ntfs       
/dev/sdc5        E2A4C997A4C96E9B                       ntfs       PRIMARY_DATA
/dev/sdc6        4ed185d4-bbef-49a7-8663-103a50de0a93   swap       
/dev/sdc7        cebfa7ea-e787-4f08-83d6-4bc7be74186b   ext4       
/dev/sdi1        6DCE-0F75                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdi1        /media/6DCE-0F75         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root FABC8229BC81E10D
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 865443BC5443AE2D
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=cebfa7ea-e787-4f08-83d6-4bc7be74186b ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=cebfa7ea-e787-4f08-83d6-4bc7be74186b ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
# Commented out by Dropbox
# UUID=c022f957-8ac3-4315-951b-6b008398ad15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f0eea78e-726d-4d27-8ae0-95d01ce14ea7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//galadriel/myth	/home/ravenel/myth	smbfs	rw,_netdev,user=ravenel,password=eleven12
UUID=c022f957-8ac3-4315-951b-6b008398ad15 / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

====================== sdb5/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 437.332664490 = 469.582372864  boot/grub/core.img                             1
 452.969791412 = 486.372610048  boot/grub/grub.cfg                             1
 429.320026398 = 460.978868224  boot/initrd.img-2.6.38-11-generic              2
 433.325428009 = 465.279635456  boot/initrd.img-3.0.0-12-generic               2
 433.330692291 = 465.285287936  boot/initrd.img-3.0.0-14-generic               2
 437.761054993 = 470.042353664  boot/vmlinuz-2.6.38-11-generic                 1
 440.737739563 = 473.238544384  boot/vmlinuz-3.0.0-12-generic                  1
 431.640083313 = 463.470010368  boot/vmlinuz-3.0.0-14-generic                  1
 430.200386047 = 461.924147200  initrd.img.old                                 2
 431.640083313 = 463.470010368  vmlinuz                                        1
 440.737739563 = 473.238544384  vmlinuz.old                                    1

================= sdb5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 447.309211731 = 480.294608896  boot/extlinux/chain.c32                        1
 432.948818207 = 464.875253760  boot/extlinux/extlinux.conf                    1

============== sdb5: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdc7/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos7)'
search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos7)'
  search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
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
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=cebfa7ea-e787-4f08-83d6-4bc7be74186b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=cebfa7ea-e787-4f08-83d6-4bc7be74186b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root cebfa7ea-e787-4f08-83d6-4bc7be74186b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root FABC8229BC81E10D
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro splash vga=794 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root c022f957-8ac3-4315-951b-6b008398ad15
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c022f957-8ac3-4315-951b-6b008398ad15 ro recovery nomodeset splash vga=794
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 865443BC5443AE2D
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

=============================== sdc7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc7 during installation
UUID=cebfa7ea-e787-4f08-83d6-4bc7be74186b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f0eea78e-726d-4d27-8ae0-95d01ce14ea7 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=4ed185d4-bbef-49a7-8663-103a50de0a93 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.756526947 = 112.481464320  boot/grub/core.img                             1
 102.776203156 = 110.355107840  boot/grub/grub.cfg                             1
  59.979682922 = 64.402694144   boot/initrd.img-3.0.0-12-generic               2
  66.773818970 = 71.697842176   boot/vmlinuz-3.0.0-12-generic                  1
  59.979682922 = 64.402694144   initrd.img                                     2
  66.773818970 = 71.697842176   vmlinuz                                        1

=========================== sdi1/boot/grub/grub.cfg: ===========================

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

============================== sdi1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdi1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdi1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdi1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  7c ba a8 fd 59 8f 70 d1  96 34 91 4b 95 3e 30 35  ||...Y.p..4.K.>05|
00000010  83 4f c2 46 cd 11 6b 1b  a8 90 8d 55 c1 f7 dd 84  |.O.F..k....U....|
00000020  d5 74 68 75 da 97 6e d9  00 07 09 79 a7 f6 60 4e  |.thu..n....y..`N|
00000030  69 79 5a 4b 3c 71 6d 2a  41 3d 22 8d e0 62 7e 60  |iyZK<qm*A="..b~`|
00000040  63 95 e6 b7 fd 86 af eb  79 a7 2b 27 3f cb 5d a5  |c.......y.+'?.].|
00000050  77 47 bd 42 18 57 8f eb  2c 57 e5 1d 3b 66 54 75  |wG.B.W..,W..;fTu|
00000060  86 32 ff 23 ef ad ea 8d  62 ee 09 7a c1 1e 26 c2  |.2.#....b..z..&.|
00000070  7f 1a ce f7 a1 3f ac ca  90 24 74 37 c0 a0 61 85  |.....?...$t7..a.|
00000080  0e da a4 b3 5c 18 a9 09  ca 30 d0 70 7d 47 5b cc  |....\....0.p}G[.|
00000090  9b 4e 1f a9 07 4d 76 d1  4e 6a 31 4e 09 39 c6 37  |.N...Mv.Nj1N.9.7|
000000a0  31 fb 06 ea d1 fe 97 90  6e 3f e5 96 38 7c 23 10  |1.......n?..8|#.|
000000b0  f4 b5 6d be d7 c9 29 b9  20 4a 53 2e b2 7b 13 24  |..m...). JS..{.$|
000000c0  e5 57 dc 47 6c 8b f7 a1  99 e0 bb d5 08 69 fd 4b  |.W.Gl........i.K|
000000d0  e8 4f cf 9f 7c 02 1d 94  1e 6f f3 7b 25 cd 92 fc  |.O..|....o.{%...|
000000e0  5b e7 df b8 f3 e1 f6 9a  02 ec 1e c7 c3 a7 06 6d  |[..............m|
000000f0  8d 01 98 f0 fe 99 09 bb  0f fb d0 9c 54 ed 20 91  |............T. .|
00000100  b7 aa 43 e7 0f 9d 5a 24  0b 6f 22 17 21 a5 46 b6  |..C...Z$.o".!.F.|
00000110  03 8a 2e b1 6a 1d 48 74  12 96 99 42 67 58 d9 56  |....j.Ht...BgX.V|
00000120  e2 89 f6 19 92 ce 9b cb  fd 27 10 20 e5 6f 1a a0  |.........'. .o..|
00000130  c7 42 bb 24 e1 ef 42 89  3e ad e8 c6 07 da 62 29  |.B.$..B.>.....b)|
00000140  fe 69 9b 77 0e c9 8e b8  c1 fa c7 f3 3f 11 af f7  |.i.w........?...|
00000150  7b 92 79 d5 b0 c3 bb 3b  a6 49 ee 04 2c c9 10 8b  |{.y....;.I..,...|
00000160  43 72 21 b1 50 6c a1 87  e8 d0 22 7a 52 e7 1d 6b  |Cr!.Pl...."zR..k|
00000170  13 c1 17 71 3f b6 3e 70  db 96 20 a3 02 99 c3 01  |...q?.>p.. .....|
00000180  0d 8c 32 0a 8c d1 d4 23  88 c5 5b de c7 e1 65 c0  |..2....#..[...e.|
00000190  11 96 43 80 97 d1 f8 09  0e 36 de 44 d6 7d 0c de  |..C......6.D.}..|
000001a0  79 39 7a 90 4a 2e e1 15  6b bc e1 dd 1c 79 8c 9d  |y9z.J...k....y..|
000001b0  97 7c eb e3 f6 32 61 e2  96 53 18 61 2b 57 00 fe  |.|...2a..S.a+W..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 6c 04 00 fe  |...........`l...|
000001d0  ff ff 05 fe ff ff 02 60  6c 04 00 e0 31 00 00 00  |.......`l...1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".
To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".
To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".

ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-12-31__19h24 ****************
boot-repair version : 3.02-0ppa23~oneiric
clean version : 3.02-0ppa15~oneiric
internet: connected
clean-gui version : 3.02-0ppa33~oneiric
/usr/share/clean/clean-gui-update.sh: line 153: 32078 Terminated              while true; do
done
LIVESESSION is : no
BYTES_BEFORE_PART[1] (sdc) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[2] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[4] (sdi) = 16 sectors * 512 bytes = 8192 bytes.
OSPROBER: /dev/sdc7:The OS now in use - Ubuntu 11.10 CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb5:Ubuntu 11.10 (11.10):Ubuntu:linux
/dev/sdc1:Windows 7 (loader):Windows1:chain
BLKID: /dev/sda1: UUID="FABC8229BC81E10D" TYPE="ntfs"
/dev/sdb1: LABEL="New Volume" UUID="8A54B81254B7FF4F" TYPE="ntfs"
/dev/sdb5: UUID="c022f957-8ac3-4315-951b-6b008398ad15" TYPE="ext4"
/dev/sdb6: UUID="f0eea78e-726d-4d27-8ae0-95d01ce14ea7" TYPE="swap"
/dev/sdc1: UUID="865443BC5443AE2D" TYPE="ntfs"
/dev/sdc5: LABEL="PRIMARY_DATA" UUID="E2A4C997A4C96E9B" TYPE="ntfs"
/dev/sdc6: UUID="4ed185d4-bbef-49a7-8663-103a50de0a93" TYPE="swap"
/dev/sdc7: UUID="cebfa7ea-e787-4f08-83d6-4bc7be74186b" TYPE="ext4"
/dev/sdi1: UUID="6DCE-0F75" TYPE="vfat"
sdc7 contains The OS now in use - Ubuntu 11.10 (linux)
sda1 contains Windows 7 (windows)
sdb5 contains Ubuntu 11.10 (linux)
sdc1 contains Windows 7 (windows)
4 disks with OS, 4 OS : 2 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sdc disk.
Total of 1 OS detected on sda disk.
Total of 1 OS detected on sdb disk.
Total of 2 OS detected on sdc disk.
sdc contains minimum one OS
sda contains minimum one OS
sdb contains minimum one OS
mount: mount point /media/6DCE-0F75/dev does not exist
mount: mount point /media/6DCE-0F75/dev/pts does not exist
mount: mount point /media/6DCE-0F75/proc does not exist
mount: mount point /media/6DCE-0F75/sys does not exist
chroot: failed to run command `grub-install': No such file or directory
umount: /media/6DCE-0F75/dev/pts: not found
umount: /media/6DCE-0F75/dev: not found
umount: /media/6DCE-0F75/proc: not found
umount: /media/6DCE-0F75/sys: not found
FDISK
Disk /dev/sda: 90.0 GB, 90028302336 bytes
42 heads, 25 sectors/track, 167463 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b7044d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   175833087    87915520    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c69f04b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   899290716   449645327    7  HPFS/NTFS/exFAT
/dev/sdb2       899291134   976771071    38739969    5  Extended
/dev/sdb5       899291136   973502463    37105664   83  Linux
/dev/sdb6       973504512   976771071     1633280   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26082608

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   122881184    61440561    7  HPFS/NTFS/exFAT
/dev/sdc2       122882046  1250242559   563680257    f  W95 Ext'd (LBA)
/dev/sdc5       245762433  1250242559   502240063+   7  HPFS/NTFS/exFAT
/dev/sdc6       229156864   245762047     8302592   82  Linux swap / Solaris
/dev/sdc7       122882048   229154815    53136384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdi: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          16     7813119     3906552    b  W95 FAT32

Disk /dev/sda: 90.0 GB, 90028302336 bytes
42 heads, 25 sectors/track, 167463 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b7044d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   175833087    87915520    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c69f04b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   899290716   449645327    7  HPFS/NTFS/exFAT
/dev/sdb2       899291134   976771071    38739969    5  Extended
/dev/sdb5       899291136   973502463    37105664   83  Linux
/dev/sdb6       973504512   976771071     1633280   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26082608

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   122881184    61440561    7  HPFS/NTFS/exFAT
/dev/sdc2       122882046  1250242559   563680257    f  W95 Ext'd (LBA)
/dev/sdc5       245762433  1250242559   502240063+   7  HPFS/NTFS/exFAT
/dev/sdc6       229156864   245762047     8302592   82  Linux swap / Solaris
/dev/sdc7       122882048   229154815    53136384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdi: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          16     7813119     3906552    b  W95 FAT32
TABLE_TYPE of sdc is MSDos
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdb is MSDos
TABLE_TYPE of sdi is MSDos
sdc7 : sdc, not-sepboot, grub, aptget, 64, with boot, , with-os, no-gpt, notEFItable, fstab-without-efi.
sda1 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda1, with-os, no-gpt, notEFItable, no-fstab.
sdb1 : sdb, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sdb1, no-os, no-gpt, notEFItable, no-fstab.
sdb5 : sdb, not-sepboot, grub, aptget, 64, with boot, /mnt/clean/sdb5, with-os, no-gpt, notEFItable, fstab-without-efi.
sdc1 : sdc, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sdc1, with-os, no-gpt, notEFItable, no-fstab.
sdc5 : sdc, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sdc5, no-os, no-gpt, notEFItable, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub, no-aptget, 32, with boot, /media/6DCE-0F75, no-os, no-gpt, notEFItable, no-fstab.
PARTED: Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 90.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  90.0GB  90.0GB  primary  ntfs         boot


Model: ATA Maxtor 3H500F0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  460GB  460GB   primary   ntfs
2      460GB   500GB  39.7GB  extended
5      460GB   498GB  38.0GB  logical   ext4
6      498GB   500GB  1672MB  logical   linux-swap(v1)


Model: ATA ST3640323AS (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  62.9GB  62.9GB  primary   ntfs            boot
2      62.9GB  640GB   577GB   extended                  lba
7      62.9GB  117GB   54.4GB  logical   ext4
6      117GB   126GB   8502MB  logical   linux-swap(v1)
5      126GB   640GB   514GB   logical   ntfs


Model: Staples Relay UFD (scsi)
Disk /dev/sdi: 4000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      8192B  4000MB  4000MB  primary  fat32        boot
MOUNT /dev/sdc7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ravenel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ravenel)
/dev/sdi1 on /media/6DCE-0F75 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda1 on /mnt/clean/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/clean/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /mnt/clean/sdb5 type ext4 (rw)
/dev/sdc1 on /mnt/clean/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /mnt/clean/sdc5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc5 sdc6 sdc7 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdh:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdi1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log lp0 mapper mcelog mei mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sdb sdb1 sdb2 sdb5 sdb6 sdc sdc1 sdc2 sdc5 sdc6 sdc7 sdd sde sdf sdg sdh sdi sdi1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdc7     ext4     50G  3.0G   45G   7% /
udev      devtmpfs    3.9G   12K  3.9G   1% /dev
tmpfs        tmpfs    1.6G  920K  1.6G   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    3.9G  164K  3.9G   1% /run/shm
/dev/sdi1     vfat    3.8G  1.1G  2.7G  28% /media/6DCE-0F75
/dev/sda1  fuseblk     84G   69G   16G  82% /mnt/clean/sda1
/dev/sdb1  fuseblk    429G  328G  102G  77% /mnt/clean/sdb1
/dev/sdb5     ext4     35G  8.4G   25G  26% /mnt/clean/sdb5
/dev/sdc1  fuseblk     59G   45G   15G  76% /mnt/clean/sdc1
/dev/sdc5  fuseblk    479G  290G  190G  61% /mnt/clean/sdc5
FDISK
Disk /dev/sda: 90.0 GB, 90028302336 bytes
42 heads, 25 sectors/track, 167463 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b7044d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   175833087    87915520    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c69f04b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   899290716   449645327    7  HPFS/NTFS/exFAT
/dev/sdb2       899291134   976771071    38739969    5  Extended
/dev/sdb5       899291136   973502463    37105664   83  Linux
/dev/sdb6       973504512   976771071     1633280   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26082608

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   122881184    61440561    7  HPFS/NTFS/exFAT
/dev/sdc2       122882046  1250242559   563680257    f  W95 Ext'd (LBA)
/dev/sdc5       245762433  1250242559   502240063+   7  HPFS/NTFS/exFAT
/dev/sdc6       229156864   245762047     8302592   82  Linux swap / Solaris
/dev/sdc7       122882048   229154815    53136384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdi: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          16     7813119     3906552    b  W95 FAT32
Logs saved into /var/log/clean/log/2011-12-31__19h24boot-repair34
Logs saved into /mnt/clean/sda1/clean/log/2011-12-31__19h24boot-repair34
Logs saved into /mnt/clean/sdb5/var/log/clean/log/2011-12-31__19h24boot-repair34
Logs saved into /mnt/clean/sdc1/clean/log/2011-12-31__19h24boot-repair34
combobox_ostoboot_bydefault_fillin
combobox_efi_fillin sdc7
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
combobox_separateboot_fillin
separate_bootpart and efi show_hide sdc7
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sdc7
set_radiobutton_place_alldisks
combobox_separateboot_fillin
separate_bootpart and efi show_hide sdc7
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sdc7
************************Before mainwindow appear
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, MBR_ACTION reinstall REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB 1 (sdc7) PART_TO_REINSTALL_GRUB_PURGE 1 (sdc7) FORCE_GRUB all NOFORCE_DISK sdc REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sdc (mbr) (sdc) USE_SEPARATEBOOTPART no (sdc5) grub-pc (sdc7)
/usr/share/clean/clean-gui-tab-other.sh: line 104:   400 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sdc7 (The OS now in use - Ubuntu 11.10)
RETOURCOMBO_ostoboot_bydefault : sdc7 (The OS now in use - Ubuntu 11.10)
combobox_separateboot_fillin
separate_bootpart and efi show_hide sdc7
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sdc7
RETOURCOMBO_efi (EFIPART_TO_USE) : sdc7
RETOURCOMBO_place_grub (NOFORCE_DISK) : sdc
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdc5
set_radiobutton_place_alldisks
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
combobox_separateboot_fillin
separate_bootpart and efi show_hide sdc7
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sdc7
set_radiobutton_place_alldisks
combobox_separateboot_fillin
separate_bootpart and efi show_hide sdc7
efi_show_hide 1 (no-gpt)
combobox_efi_fillin sdc7
RETOURCOMBO_place_grub (NOFORCE_DISK) : sdc
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdc5
RETOURCOMBO_efi (EFIPART_TO_USE) : sdc7
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdc5
RETOURCOMBO_efi (EFIPART_TO_USE) : sdc7
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdc5
RETOURCOMBO_efi (EFIPART_TO_USE) : sdc7
internet: connected
************************Before Repairing
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, MBR_ACTION nombraction REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION no (10.s) PART_TO_REINSTALL_GRUB 1 (sdc7) PART_TO_REINSTALL_GRUB_PURGE 1 (sdc7) FORCE_GRUB all NOFORCE_DISK sdc REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sdc (mbr) (sdc) USE_SEPARATEBOOTPART no (sdc5) grub-pc (sdc7)
internet: connected
/usr/share/clean/bootrepair-actions.sh: line 83:  7195 Terminated              while true; do
done
dpkg-preconfigure: unable to re-open stdin:

```

---

### Post by drs305 on 2012-01-01
I was thinking your primary OS would be sdc7, but the RESULTS.txt shows it is looking for partition 5. This indicates that you probably "grub-install"ed from your sdb5 OS. 

I think the problem with your sdb installation is the location on the drive. It is very deep into the drive, and your BIOS might have a 137GB limitation. This means it cannot 'see' the files beyond 137 GB until after it boots. 

Please check for this by booting Grub, pressing 'c' to get to the command line if not already there, and running these commands to check if Grub finds the boot files. Note if the drives change it might be hd0 or hd2.
```

ls (hd1,5)/boot  # Should see the kernel and initrd files
ls (hd1,5)/boot/grub # Should see lots of mod files and if you look closely, the grub.cfg file
```

---

### Post by sailor420 on 2012-01-01
Running those commands does show the files--the kernel and initrd files for /boot, and the mod and cfg files for /boot/grub.

What I don't understand is why it would work with the USB key inserted, but not work when it's out. What is it looking for on the USB key?

---

### Post by drs305 on 2012-01-01
At this point, what I would recommend is booting into your Ubuntu, then confirm the one that has booted with the "mount" command. See which partition is mounted as /.

I would then check your Internet connection to make sure it's working. **With the USB disconnected**, I would purge grub completely and reinstall it. The only 'danger' is that you purge it and lose your Internet connection, but that is not likely.

```
sudo purge grub-common # removes grub-common, grub-pc and a gfxpayload package.
sudo apt-get install grub-pc # Reinstalls them
```

When you purge, you will be warned about losing your bootloader. TAB to OK and ENTER.

When you install, it will ask if you have any options you want to add. Normally not, so just TAB to OK and ENTER.
It will also ask where to install. The spacebar puts an asterisk next to the drives you want to install to. Do NOT select any of the partitions, just the drive(s).

Watch the terminal. If it doesn't run 'update-grub' at the end of the installation do it manually.

---

### Post by YannBuntu on 2012-01-01
Hello Sailor,

1) Please could you connect your USB key, boot on Ubuntu, open a terminal (CTRL+ALT+T), then run the following command and **indicate us its output** :
```
ls -l /dev/disk/by-id | grep sd
```

2) Then reboot on your live-USB, choose "Try Ubuntu", connect internet, [install&run Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click on the "Advanced options", "GRUB location" tab, then select "OS to boot by default: _**sdb5**_", click "Apply", then **indicate us the new URL** that will appear. Then shut down the PC, disconnect the USB key, reboot the PC and tell us if a GRUB menu appears or not.

---

### Post by sailor420 on 2012-01-01
Just tried purging and reinstalling (installed to all disks); same thing still happening. Sigh.

Here is the output of the ls:
```


ls -l /dev/disk/by-id/ | grep sd
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 ata-Corsair_Force_3_SSD_114382000000071207B0 -> ../../sda
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-Corsair_Force_3_SSD_114382000000071207B0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 ata-Maxtor_3H500F0_H819N65H -> ../../sdb
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-Maxtor_3H500F0_H819N65H-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-Maxtor_3H500F0_H819N65H-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-Maxtor_3H500F0_H819N65H-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-Maxtor_3H500F0_H819N65H-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8 -> ../../sdc
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8-part6 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 ata-ST3640323AS_5VK05TF8-part7 -> ../../sdc7
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 scsi-SATA_Corsair_Force_3114382000000071207B0 -> ../../sda
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_Corsair_Force_3114382000000071207B0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 scsi-SATA_Maxtor_3H500F0_H819N65H -> ../../sdb
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_Maxtor_3H500F0_H819N65H-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_Maxtor_3H500F0_H819N65H-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_Maxtor_3H500F0_H819N65H-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_Maxtor_3H500F0_H819N65H-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8 -> ../../sdc
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8-part6 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 scsi-SATA_ST3640323AS_5VK05TF8-part7 -> ../../sdc7
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Generic_Mini_SD_Reader_058F412D8PB1-0:4 -> ../../sdi
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Generic_USB_CF_Reader_058F412D8PB1-0:1 -> ../../sdf
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Generic_USB_MS_Reader_058F412D8PB1-0:3 -> ../../sdh
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Generic_USB_SD_Reader_058F412D8PB1-0:0 -> ../../sde
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Generic_USB_SM_Reader_058F412D8PB1-0:2 -> ../../sdg
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 usb-Staples_Relay_UFD_4C532007300715111025-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 usb-Staples_Relay_UFD_4C532007300715111025-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 2012-01-01 14:21 wwn-0x5000c500101d88e3 -> ../../sdc
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 wwn-0x5000c500101d88e3-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 wwn-0x5000c500101d88e3-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 wwn-0x5000c500101d88e3-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 wwn-0x5000c500101d88e3-part6 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2012-01-01 14:21 wwn-0x5000c500101d88e3-part7 -> ../../sdc7
ravenel@glaurung:~$ 

```

Will do the rest of it now and let you know how it goes...

---

### Post by sailor420 on 2012-01-01
OK, results are at the following location: [http://paste.ubuntu.com/789861/](http://paste.ubuntu.com/789861/)

I installed to sdi7--when it booted, my three hard disks were assigned to sda (SSD), sdg (was sdb) and sdi (was sdc). SDI7 is my current Ubuntu install.

After rebooting, it's still doing the same thing...

---

### Post by sailor420 on 2012-01-01
OK, I got it working--by flashing my motherboard BIOS. Not sure what was going on. I noticed some other flaky stuff going on (e.g. sometimes when rebooting I couldn't get into the BIOS to change boot order), so I figured I'd see if there was a new BIOS. After flashing, it's now booting. Go figure.

Thanks for the help guys, it's much appreciated. Sorry this one was so annoying.

---

### Post by YannBuntu on 2012-01-01
Good job !
Just for our information, please could you run again Boot-Repair, click the "Create BootInfo report" button, and indicate the new URL ?

---

### Post by oldfred on 2012-01-01
Some BIOS do not let you boot at all if there is not a boot flag on a primary partition. The error may have not been grub but a BIOS error. These BIOS seem to assume Windows as the boot flag is a Windows requirement, but grub does not use boot flag. Lilo also uses the boot flag so some Linux systems also use a boot flag.

Then the BIOS update either fixed the BIOS or changed to newer defaults so you are booting from a drive with the boot flag.

---

### Post by YannBuntu on 2012-01-01
> **oldfred said:**
> Some BIOS do not let you boot at all if there is not a boot flag on a primary partition.

Thanks Oldfred, i didn't know this. Then I will try to add a new feature in Boot-Repair to easily solve this issue ( [https://blueprints.launchpad.net/boot-repair/+spec/check-boot-flag-presence](https://blueprints.launchpad.net/boot-repair/+spec/check-boot-flag-presence) ). What do you think about it, do you think it could be useful?
Among all the threads you have followed up, is there an example that you could link me please?

---

### Post by sailor420 on 2012-01-01
Yann,

Updated info report on pastebin:  [http://paste.ubuntu.com/790104/](http://paste.ubuntu.com/790104/)

Thanks again!

---

### Post by YannBuntu on 2012-01-02
> **sailor420 said:**
> Updated info report on pastebin:  [http://paste.ubuntu.com/790104/](http://paste.ubuntu.com/790104/)

Thanks! (apparently no big change, except sdi renamed into sdc... no clue to detect a BIOS problem...)

---

### Post by oldfred on 2012-01-02
@   	YannBuntu
Ubuntu's openID does not work on launch pad so I will just post this here, all from the forum anyway.

I do not know about Macs and how their efi works. Also not sure about RAID or LVM and how they work.

The BIOS on Intel motherboards (maybe others) seem to need a boot flag on a primary or else it will not let you start booting. Windows has to have a boot flag on a primary NTFS partition, grub does not use a boot flag, and lilo can use a boot flag on a logical to boot.

For MBR(msdos) disks I just normally suggest a boot flag on a primary partition, if not lilo booting. Some have the extended as the only primary and I have seen boot flags and grub installed to the PBR on that partition (the extended is still a primary). Not sure if it was an Intel but it did not cause issues with that system. Some put boot flag on logical which has no meaning unless using lilo as Windows will not directly boot a logical. meierfra was able to use lilo to directly boot a logical with XP.
I would not add boot flags to gpt drives, but check for efi and with type code ef00. If no efi partition then suggest bios_grub if no partition type ef02. I think the new UEFI systems do not have a UEFI/BIOS mode, but just check for a efi boot partition and if none found default to BIOS mode. Again not sure what Macs do?

Windows will only install to a NTFS primary partition with a boot flag if partition is created in advance, and usually Windows repairs only work on the primary boot partition which has the boot flag.  Not sure how Windows 7 knows to fix c: unless it really just repairs the 100MB boot partition and then that can be used to run chkdsk or other repairs on c:?

But gpt needs a bios_grub partition with BIOS or the efi partition with UEFI.
The efi partition has to be first and have the boot flag. In gparted it is called a boot flag but srs5694 points out it is not the same boot flag as MBR(msdos). He has solved boot issues with gpt and Intel motherboard needing a boot flag. Some systems have created a partition labeled efi in place of the vendor utilities partition. It is not an efi partition since it is not first nor usually gpt.

Other notes from srs5694:
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Info on not setting boot flag on gpt disks by ss5604 - April 11th, 2011, 08:32 PM
[http://ubuntuforums.org/archive/index.php/t-1722471.html](http://ubuntuforums.org/archive/index.php/t-1722471.html)
But I think he fixed a gpt disk with Intel that would not boot by adding a boot flag.
See srs5694 info on gpt & boot flag post - February 17th, 2011, 04:33 PM
[http://ubuntuforums.org/archive/index.php/t-1686929.html](http://ubuntuforums.org/archive/index.php/t-1686929.html)

Intel Boot Agent failed to find a bootable disk
[http://ubuntuforums.org/archive/index.php/t-1563699.html](http://ubuntuforums.org/archive/index.php/t-1563699.html)
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)
For anyone with same problems - Intel D510MO motherboard, Seagate 2TB hard drive. Tried Ubuntu 10.10, Ubuntu 10.4, desktop, server. Any version installed successfully, then a black screen with "no bootable device insert boot disk and press any key".
Problem solved by following srs5694's two posts.

Have you seen this thread with new test versions of bootinfoscript. 
[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

---

### Post by YannBuntu on 2012-01-04
Thanks a lot Oldfred, i will try to find the best way to implement this.

As a rough thought, i am thinking of adding an option (in the Advanced options of Boot-Repair) to let the user choose:
- if he wants to add a boot flag or not, (via a checkbox)
- and on which partition. (via a combobox)
The default would be:
- combobox would list all primary partitions located on MsDos disks
- default combobox entry would be the first Windows partition, else the first partition containing a non-Linux system, else the first NTFS partition
- checkbox unchecked (do not add flag) if GPT detected, or if flag detected on one primary partition of each disk

Concerning BIS, the GIT version looks promising. I could add an option in Boot-Repair to let the user choose the GIT version (instead of the stable one that would remain the default) if you think that could be useful.

---

### Post by oldfred on 2012-01-04
@YannBuntu
Your logic looks good.

I have also seen systems with more than one boot flag which cannot happen? Not sure with Windows 7 how you set it to the correct NTFS partition as Windows 7 usually has the 100MB hidden boot/repair partition and it is usually first, but not always in some custom installs.

Not sure how soon Gert will release the version of the bootinfoscript he is working on, it seems like most of the current questions are resolved, so I am hopeful that it will be soon.

---

### Post by imachavel on 2012-01-04
> **sailor420 said:**
> Running those commands does show the files--the kernel and initrd files for /boot, and the mod and cfg files for /boot/grub.

What I don't understand is why it would work with the USB key inserted, but not work when it's out. What is it looking for on the USB key?

I'll tell you the truth, I don't really know the answer to your question. I myself have had several problems with ubuntu grub. But never with dual booting linux. I had several problems dual booting windows(winblows) and linux, where the grub failed to recognize one or the other. With windows I tried repair console command line, and ran, not fix mbr, but another command which I forgot. This got the computer working for windows, but then linux partition at dev/sda, or was it dev/sdb I can't remember quit working for me. So I can the live cd, and got help from someone at this forum a long time ago, we purged grub 2 from the command line, and installed a legacy grub. Same issue still persisted. I never got it fixed. Now I run ubuntu on one partition, and linux mint on the other partition. works just fine. I use kvm and switch between this pc and another pc that runs windows 7, and on the ubuntu partition on this pc, I actually am virtualizing windows xp as guest. so far no problems.

Anyway I'm guessing that didn't help your problem too much. All your files backed up ok? Don't forget some things are impossible to fix. When you format the drive, us gparted to seperate the partitions accordingly. It might take a bit more work, but in the long run it's better, because you want contiguous partitions. Otherwise, if the partitions aren't contiguous, it will cause problems resizing partition space later. But then this probably won't effect your grub.

---

### Post by imachavel on 2012-01-04
> **oldfred said:**
> @YannBuntu
Your logic looks good.

I have also seen systems with more than one boot flag which cannot happen? Not sure with Windows 7 how you set it to the correct NTFS partition as Windows 7 usually has the 100MB hidden boot/repair partition and it is usually first, but not always in some custom installs.

Not sure how soon Gert will release the version of the bootinfoscript he is working on, it seems like most of the current questions are resolved, so I am hopeful that it will be soon.

this was solved? what does his fdisk -l look like now? Mine looks like this:

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT

:popcorn:

---

### Post by oldfred on 2012-01-04
@imachavel
You do not have a boot flag on sdb1. But if you are only booting Linux with grub or grub2 and your BIOS does not have to have a boot flag, then it does not really matter. It just is in my opinion better to have a boot flag on a primary partition just as a standard so those with Windows will have it or those with BIOS that have to have it even if they do not have Windows.

If only booting with Linux and you have a NTFS partition you need to use a Windows repairCD and run chkdsk every 40-60 boots. Ubuntu runs fsck on root regularly but cannot run filechks on NTFS.

---

