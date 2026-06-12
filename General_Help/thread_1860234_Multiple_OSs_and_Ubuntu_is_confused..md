---
title: "Multiple OSs and Ubuntu is confused."
date: 2011-10-14
forum: General Help
---

### Post by qaissi on 2011-10-14
OK so I know you are going to be asking why but lets just leave it as I have to and go from there.

I have 6 OSs installed to 4 hard drives.

Using Burg I can boot to each OS from the main Burg boot menu.

Kubuntu, Ubuntu 11.10, XP, Vista, Windows 7 all access the different drives (others for storage etc.) without any issues.

Ubuntu 11.04 - x64 has problems.  

When I open up Nautilus it shows all the drives as they should be.  However when I start mounting them it starts to have problems.

For example I will mount the Vista drive and it tells me it is already mounted.  I then mount the XP drive and it mounts but with the contents of the Vista drive.  The XP drive is no longer available to me because it is showing the contents of the Vista drive.

Now that was just an example.  It will happen with other drives at various times.

Also occasionally when rebooting Ubuntu will give me a message saying that XXXXX drive could not be mounted press S to Skip ....  etc.

It does not do it all the time but when it does I have to boot into any other OS and then reboot again to get Ubuntu 11.04 to mount the drives.

I have noticed in Disk utility that there are missing drives assignments.  For example I have:

SDC1, SDC2, SDC5, and SDC6 but no SDC3 or SDC4.  SDA4 is also missing.

Not sure if that matters or not.

I downloaded and ran the boot_info_script and it produced the following.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/burg.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/burg.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    99,700,892    99,698,845  83 Linux
/dev/sda2          99,702,782   234,584,063   134,881,282   5 Extended
/dev/sda5         195,524,608   234,584,063    39,059,456  82 Linux swap / Solaris
/dev/sda6          99,702,784   179,275,775    79,572,992  83 Linux
/dev/sda7         179,277,824   195,510,271    16,232,448  82 Linux swap / Solaris
/dev/sda3         234,597,195   976,768,064   742,170,870   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS
/dev/sdb3         204,802,048 1,953,519,615 1,748,717,568   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sdc2         204,797,950   976,771,071   771,973,122   5 Extended
/dev/sdc5         204,797,952   960,522,239   755,724,288  83 Linux
/dev/sdc6         960,524,288   976,771,071    16,246,784  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sdd2         204,802,048 1,953,519,615 1,748,717,568   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        efb01fcd-1506-4cd3-bbe3-74c9b1df0348   ext4       Kubuntu
/dev/sda3        623FE7E44584BA86                       ntfs       Customizations
/dev/sda5        34d6b39e-1f87-4323-9f2e-946ed4e576d2   swap       
/dev/sda6        225ccfa9-0faf-44a6-9f43-6340759456f7   ext4       Beta
/dev/sda7        ba6b8b96-e51e-4920-8afc-b8305d80acba   swap       
/dev/sdb1        A4B4D7AEB4D7816A                       ntfs       System Reserved
/dev/sdb2        6846E44046E4111C                       ntfs       Windows7
/dev/sdb3        525868745868592D                       ntfs       Storage
/dev/sdc1        84FCAB64FCAB4F6C                       ntfs       WindowsXP
/dev/sdc5        6f4faefd-fece-409d-8e05-098d6d3ec8aa   ext4       Ubuntu
/dev/sdc6        6ad97cfc-abef-4be0-a7a5-1bb6fdbd9b6f   swap       
/dev/sdd1        D834C35D34C33CEE                       ntfs       WindowsVista
/dev/sdd2        50CA7503CA74E69E                       ntfs       Media

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /media/Beta              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
if background_color 0,71,115; then
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root A4B4D7AEB4D7816A
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 84FCAB64FCAB4F6C
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 5cb254f2-534b-48bf-92a7-2408e5badd5e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 5cb254f2-534b-48bf-92a7-2408e5badd5e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 5cb254f2-534b-48bf-92a7-2408e5badd5e
	linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdc5
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 5cb254f2-534b-48bf-92a7-2408e5badd5e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos5)'
	search --no-floppy --fs-uuid --set=root 5cb254f2-534b-48bf-92a7-2408e5badd5e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Windows Vista (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root D834C35D34C33CEE
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34d6b39e-1f87-4323-9f2e-946ed4e576d2 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=d7554ca3-a63f-402b-bfba-bf911b40465f none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=76421b99-b719-4abc-98be-80a5f007c3bc none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.135509491 = 43.095175168   boot/grub/core.img                             1
  14.446372986 = 15.511674880   boot/grub/grub.cfg                             1
  14.503223419 = 15.572717568   boot/initrd.img-2.6.38-11-generic              2
   1.759101868 = 1.888821248    boot/vmlinuz-2.6.38-11-generic                 1
  14.503223419 = 15.572717568   initrd.img                                     2
   1.759101868 = 1.888821248    vmlinuz                                        1

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
search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=225ccfa9-0faf-44a6-9f43-6340759456f7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=225ccfa9-0faf-44a6-9f43-6340759456f7 ro recovery nomodeset 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 225ccfa9-0faf-44a6-9f43-6340759456f7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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
UUID=225ccfa9-0faf-44a6-9f43-6340759456f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ba6b8b96-e51e-4920-8afc-b8305d80acba none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.759002686 = 64.165740544   boot/grub/core.img                             1
  59.759010315 = 64.165748736   boot/grub/grub.cfg                             1
  74.721679688 = 80.231792640   boot/initrd.img-3.0.0-12-generic               2
  77.674995422 = 83.402891264   boot/vmlinuz-3.0.0-12-generic                  1
  74.721679688 = 80.231792640   initrd.img                                     2
  77.674995422 = 83.402891264   vmlinuz                                        1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

--------------------------------------------------------------------------------

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 6f4faefd-fece-409d-8e05-098d6d3ec8aa
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 6f4faefd-fece-409d-8e05-098d6d3ec8aa
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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

### BEGIN /etc/grub.d/10_linux_proxy ###
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
menuentry "Ubuntu, with Linux 2.6.38-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 6f4faefd-fece-409d-8e05-098d6d3ec8aa
	linux	/boot/vmlinuz-2.6.38-11-generic root=/dev/sdb5 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux_proxy ###

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

=========================== sdc5/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
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
set gfxmode=1280x1024
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
  load_string '+theme_menu { -gogo-noge-hot-legs { command="set theme_name=gogo-noge-hot-legs" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -what-am-i { command="set theme_name=what-am-i" }}'
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
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6f4faefd-fece-409d-8e05-098d6d3ec8aa
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 6f4faefd-fece-409d-8e05-098d6d3ec8aa
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux16	/boot/vmlinuz-2.6.38-11-generic root=UUID=6f4faefd-fece-409d-8e05-098d6d3ec8aa ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd16	/boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdd6)" --class beta --class os --group group_/dev/sdd6 {
	insmod ext2
	set root='(hd3,6)'
	search --no-floppy --fs-uuid --set 225ccfa9-0faf-44a6-9f43-6340759456f7
	linux16 /boot/vmlinuz-3.0.0-12-generic root=UUID=225ccfa9-0faf-44a6-9f43-6340759456f7 ro quiet splash vt.handoff=7
	initrd16 /boot/initrd.img-3.0.0-12-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 84fcab64fcab4f6c
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" --class windows1 --class os {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d834c35d34c33cee
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows2 --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a4b4d7aeb4d7816a
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdd1)" --class kubuntu --class os --group group_/dev/sdd1 {
	insmod ext2
	set root='(hd3,1)'
	search --no-floppy --fs-uuid --set efb01fcd-1506-4cd3-bbe3-74c9b1df0348
	linux16 /boot/vmlinuz-2.6.38-11-generic root=UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348 ro quiet splash vt.handoff=7
	initrd16 /boot/initrd.img-2.6.38-11-generic
}
}

### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6f4faefd-fece-409d-8e05-098d6d3ec8aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6ad97cfc-abef-4be0-a7a5-1bb6fdbd9b6f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 397.790092468 = 427.123859456  boot/burg/burg.cfg                             1
 397.799522400 = 427.133984768  boot/burg/core.img                             1
 397.793720245 = 427.127754752  boot/grub/core.img                             1
 397.866554260 = 427.205959680  boot/grub/grub.cfg                             1
 141.545898438 = 151.983751168  boot/initrd.img-2.6.38-11-generic              2
 141.468086243 = 151.900200960  boot/vmlinuz-2.6.38-11-generic                 1
 141.545898438 = 151.983751168  initrd.img                                     2
 141.468086243 = 151.900200960  vmlinuz                                        1


```

Any ideas would be greatly appreciated as I tend to us Ubuntu 11.04 as my primary OS.

---

### Post by drs305 on 2011-10-14
Although some partitions may mount automatically, since you are having problems I would manually add the entries for partitions you want mounted directly into /etc/fstab.

Also of interest, in your 11.04 fstab you have 3 swap partitions listed. You really only need one swap partition, Two of the swap entries point to partitions which aren't found by your system. These would generate the S Skip error messages. Note the comments may or may not be correct. Concentrate on the actual lines with the UUIDs.
> # swap was on /dev/sda5 during installation
UUID=34d6b39e-1f87-4323-9f2e-946ed4e576d2 none            swap    sw              0       0
[COLOR="Red"]# swap was on /dev/sdb6 during installation
UUID=d7554ca3-a63f-402b-bfba-bf911b40465f none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=76421b99-b719-4abc-98be-80a5f007c3bc none            swap    sw              0       0[/COLOR]

If you need help constructing the entries for your multiple partitions, this is an excellent thread:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by haresear on 2011-10-14
Concerning 'missing' drive assignments, I believe that is because sdX1-sdX4 are reserved for primary partitions, and logical partitions start at sdX5. For example, your sda drive has three primary partitions, sda1,sda2,sda3, with sda2 the extended partition, and your logical partitions start with sda5.

---

### Post by qaissi on 2011-10-14
Well thank you haresear - believe it or not that kind of makes sense.

Anyway I have been playing around with fstab for a while now and not getting too far.

This is my current fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                  proc  nodev,noexec,nosuid                 0  0  
# / was on /dev/sda5 during installation
UUID=6f4faefd-fece-409d-8e05-098d6d3ec8aa  /                      ext4  errors=remount-ro                   0  1  
# swap was on /dev/sda6 during installation
UUID=6ad97cfc-abef-4be0-a7a5-1bb6fdbd9b6f  none                   swap  sw                                  0  0  
/dev/sdd1                                  /media/WindowsVista    ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdd2                                  /media/Media  	  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdc1                                  /media/WindowsXP       ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb2                                  /media/Windows7        ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb3                                  /media/Common          ntfs  defaults                            0  0  
/dev/sda6                                  /media/Beta            ext4  defaults                            0  0  
/dev/sda3                                  /media/Customizations  ntfs  nls=iso8859-1,users,umask=000,user  0  0
/dev/sda1                                  /media/Kubuntu         ext4  defaults
```

With this fstab Ubuntu 11.04 will only load WindowsVista and Common.

I use the program Storage Device Manager to try to add these in.  Don't know if it makes a difference or not but I did the drives in reverse order hoping Storage Device Manager would not have such an issue with the drives.  It does not see them as I expect it to.  

For example when I start the program with a clean fstab and click on fda1 in the left window it calls it fdc3 in the right window????

Anyway I also include the output of blkid -c /dev/null

```
/dev/sda1: LABEL="Kubuntu" UUID="efb01fcd-1506-4cd3-bbe3-74c9b1df0348" TYPE="ext4" 
/dev/sda3: LABEL="Customizations" UUID="623FE7E44584BA86" TYPE="ntfs" 
/dev/sda5: UUID="34d6b39e-1f87-4323-9f2e-946ed4e576d2" TYPE="swap" 
/dev/sda6: LABEL="Beta" UUID="225ccfa9-0faf-44a6-9f43-6340759456f7" TYPE="ext4" 
/dev/sda7: UUID="ba6b8b96-e51e-4920-8afc-b8305d80acba" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="A4B4D7AEB4D7816A" TYPE="ntfs" 
/dev/sdb2: LABEL="Windows7" UUID="6846E44046E4111C" TYPE="ntfs" 
/dev/sdb3: LABEL="Common" UUID="525868745868592D" TYPE="ntfs" 
/dev/sdc1: LABEL="WindowsXP" UUID="84FCAB64FCAB4F6C" TYPE="ntfs" 
/dev/sdc5: LABEL="Ubuntu" UUID="6f4faefd-fece-409d-8e05-098d6d3ec8aa" TYPE="ext4" 
/dev/sdc6: UUID="6ad97cfc-abef-4be0-a7a5-1bb6fdbd9b6f" TYPE="swap" 
/dev/sdd1: LABEL="WindowsVista" UUID="D834C35D34C33CEE" TYPE="ntfs" 
/dev/sdd2: LABEL="Media" UUID="50CA7503CA74E69E" TYPE="ntfs" 
```

in the hopes that somebody else can figure this one out.

---

### Post by drs305 on 2011-10-14
First, make a backup of your current fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

Second, close out all your apps but gedit (or text editor):
```
sudo umount -a
```
You will get 'busy' messages for partitions which can't be unmounted. That is ok.

Do these mountpoints exist in /media?
WindowsVista, Media, WindowsXP, Windows7, Common, Beta, Customizations, Kubuntu
If not, create the mount points:
```
for i in WindowsVista Media WindowsXP Windows7 Common Beta Customizations Kubuntu; do sudo mkdir /media/$i; done
```

Do they belong to you?
If not, make yourself the owner of the mount points:
```
for i in WindowsVista Media WindowsXP Windows7 Common Beta Customizations Kubuntu; do sudo chown $USER: /media/$i ; done
```

Let's try using labels in fstab. 
After the swap line, copy the following. I've left the two working mounts (
WindowsVista and Custom) as is.


```

/dev/sdd1              /media/WindowsVista    ntfs  nls=iso8859-1,users,umask=000,user  0  0  
#/dev/sdd2             /media/Media  	      ntfs  nls=iso8859-1,users,umask=000,user  0  0  
#/dev/sdc1             /media/WindowsXP       ntfs  nls=iso8859-1,users,umask=000,user  0  0  
#/dev/sdb2             /media/Windows7        ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb3              /media/Common          ntfs  defaults                            0  0  
#/dev/sda6             /media/Beta            ext4  defaults                            0  0  
#/dev/sda3             /media/Customizations  ntfs  nls=iso8859-1,users,umask=000,user  0  0
#/dev/sda1             /media/Kubuntu         ext4  defaults
 
LABEL=Media             /media/Media          ntfs  auto,users,uid=1000,gid=100,utf8,umask=027 0 0  
LABEL=WindowsXP         /media/WindowsXP      ntfs  auto,users,uid=1000,gid=100,utf8,umask=027 0 0 
LABEL=Windows7          /media/Windows7       ntfs  uuto,users,uid=1000,gid=100,utf8,umask=027 0 0 
LABEL=Beta              /media/Beta           ext4  defaults 0  0  
LABEL=Customizations    /media/Customizations ntfs  auto,users,uid=1000,gid=100,utf8,umask=027 0 0 
LABEL=Kubuntu           /media/Kubuntu        ext4  defaults
```

Save fstab. Then run the following commands to see if the partitions all mount. If they do, you will get no error messages and they are now mounted (and should mount on boot). If you don't want them to mount on booting, change "auto" to "noauto".
```
sudo mount -a
```

Make sure you keep the /etc/fstab.bak file in case you need to restore it.

---

### Post by qaissi on 2011-10-14
Thank you very much drs305 for your assistance with this.  However I have resolved the issue and I will try to mark this solved if I can figure that one out.

I will certainly be looking at your last post for ideas in the future.

However I resolved the issue after reading a couple of other posts.  Yes Google is my friend lol.

Anyway the first issue turns out to be that the software I downloaded from the ubuntu software center (Storage Device Manager) which is what I found when I was trying to get PySDM simply is not working properly.  I had that confirmed by a couple of sites. (sorry I lost those links)

My normal method of dealing with this stuff in the past was to install the NTFS Configuration Tool from the software center.  I had done this earlier but it simply was not doing anything.  However after some more searching I found the following link explaining how to fix the problem.  Works in both 11.04 and 11.10.

[http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html]("http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html")

The end result of all of that was that the NTFS Configuration Tool wrote what I needed in the fstab and using that as a template of sorts along with all the other information you and others gave me I came up with this fstab.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#Entry for /dev/sdd6 :
UUID=225ccfa9-0faf-44a6-9f43-6340759456f7	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=525868745868592D	/media/Common	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdd3 :
UUID=623FE7E44584BA86	/media/Customizations	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdc2 :
UUID=50CA7503CA74E69E	/media/Media	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=6846E44046E4111C	/media/Windows7	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=D834C35D34C33CEE	/media/WindowsVista	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=84FCAB64FCAB4F6C	/media/WindowsXP	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdd7 :
UUID=ba6b8b96-e51e-4920-8afc-b8305d80acba	none	swap	sw	0	0
#Entry for /dev/sba1 : Kubuntu
UUID=efb01fcd-1506-4cd3-bbe3-74c9b1df0348    /media/Kubuntu    ext4   errors=remount-ro	0	1
#Entry for /dev/sba1 : Beta
UUID=225ccfa9-0faf-44a6-9f43-6340759456f7    /media/Beta    ext4   errors=remount-ro	0	1

```

I am sure that I will probably have some fine tuning to do in the future but I would like to thank everybody who passed ideas on to me to explore.

---

### Post by drs305 on 2011-10-14
> **qaissi said:**
> Thank you very much drs305 for your assistance with this.  However I have resolved the issue and I will try to mark this solved if I can figure that one out.


You can mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

One of my first tutorials on these forums was how to use PySDM. It was a bit outdated then and that was five or more years ago I think; so congratulations on your success!

---

