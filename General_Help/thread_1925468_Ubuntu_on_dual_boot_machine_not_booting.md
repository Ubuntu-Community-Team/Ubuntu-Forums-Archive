---
title: "Ubuntu on dual boot machine not booting"
date: 2012-02-14
forum: General Help
---

### Post by linuxpingu on 2012-02-14
Last night, I upgraded various things on my Ubuntu installation including the headers and kernel and have accidentally managed to brick it. Ironically it was the same night I was trying to make a backup image, but I never succeeded with doing that either.
I can boot into the boot loader, but that's basically all. Any Ubuntu version I try to boot into (including recovery versions) gives me the following error: 
```
mount: mounting /proc on /root/proc failed: no such file or directory
init: unable to mount /proc filesystem: no such file or directory
/bin/sh: can't open /proc/self/fd/9
```

The versions that are avaliable on my machine to try are:
3.0.0-16-generic (and recovery)
3.0.0-15-generic (and recovery)
3.0.0-12-generic (and recovery)

I'm running 11.10 64bit and it's a fairly new install.

I don't want to have to reinstall if I can help it - I was just getting everything how I liked it ](*,)

Thanks in advance for all the help you can give :)

---

### Post by kc1di on 2012-02-14
These references may be of help.


[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by linuxpingu on 2012-02-15
> **kc1di said:**
> These references may be of help.
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")


Hiya I've tried both methods you've given me, but unfortunately they've both failed. The method described in the link above though did give me a '[pastebin]("http://paste.ubuntu.com/842557/")', so, if anyone can look at it and find what's wrong I'd be grateful :)

Many thanks

---

### Post by darkod on 2012-02-15
OK, first follow the link in my signature, download and run the boot info script. Post the results here as explained there.

Lets see what it shows.

---

### Post by linuxpingu on 2012-02-15
Okay, sorry for the wait, but here it is: 
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  64        96,389        96,326   7 NTFS / exFAT / HPFS
/dev/sda2              98,304   111,587,327   111,489,024  af HFS / HFS+
/dev/sda3    *    111,587,488   443,683,169   332,095,682   7 NTFS / exFAT / HPFS
/dev/sda4         443,684,862   579,371,007   135,686,146   f W95 Extended (LBA)
/dev/sda5         443,684,864   571,287,551   127,602,688  83 Linux
/dev/sda6         571,289,600   579,371,007     8,081,408  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7998 MB, 7998537728 bytes
35 heads, 35 sectors/track, 12752 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    15,622,143    15,614,080   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7A36465336461115                       ntfs       SYSTEM RESERVED
/dev/sda2        2f80520c-9272-38d1-ac0d-5839678eddc2   hfsplus    OS X Lion
/dev/sda3        8CA24748A24735CC                       ntfs       Acer
/dev/sda5        80ed58d0-20b5-46f6-a37e-3545573a4f94   ext4       
/dev/sda6        635543a4-f6ba-48cd-bc26-9b7e2ebae01f   swap       
/dev/sdc1        B1AF-6562                              vfat       FLASH DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 ro recovery nomodeset 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {
	insmod part_msdos
	insmod hfsplus
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root baa269fb4fce3f53
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid baa269fb4fce3f53 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {
	insmod part_msdos
	insmod hfsplus
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root baa269fb4fce3f53
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid baa269fb4fce3f53 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 8CA24748A24735CC
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=2924dd81-0b84-41bd-8e29-94acd6a8960d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=2924dd81-0b84-41bd-8e29-94acd6a8960d ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=2924dd81-0b84-41bd-8e29-94acd6a8960d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 80ed58d0-20b5-46f6-a37e-3545573a4f94
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=2924dd81-0b84-41bd-8e29-94acd6a8960d ro recovery nomodeset
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=635543a4-f6ba-48cd-bc26-9b7e2ebae01f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              88
               =                boot/initrd.img-3.0.0-15-generic              77
               =                boot/initrd.img-3.0.0-16-generic              192
               =                boot/vmlinuz-3.0.0-12-generic                 20
               =                boot/vmlinuz-3.0.0-15-generic                 139
               =                boot/vmlinuz-3.0.0-16-generic                 70
               =                vmlinuz                                       70
               =                vmlinuz.old                                   139

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.img                                     1
            ?? = ??             initrd.img.old                                 1
            ?? = ??             vmlinuz                                        1
            ?? = ??             vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf ed  e1 e8 6a 00 8a 16 04 e6  |.|h.N.....j.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5b 00 f4 eb fd 66 60  |.... ....[....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 52 31 d2 66 c1 ea 04  |.fa.f`...R1.f...|
000000f0  8e c2 5b 1e 1e 66 03 0e  00 e6 66 51 06 53 30 e4  |..[..f....fQ.S0.|
00000100  50 68 10 00 8a 16 04 e6  89 e6 b4 42 cd 13 72 a5  |Ph.........B..r.|
00000110  89 ec 07 66 61 c3 66 60  57 be dd e3 e8 07 00 5e  |...fa.f`W......^|
00000120  e8 03 00 66 61 c3 bb 01  00 ac 3c 00 74 06 b4 0e  |...fa.....<.t...|
00000130  cd 10 eb f5 c3 66 60 ad  86 e0 ab 3c 00 74 23 89  |.....f`....<.t#.|
00000140  c1 ad 86 e0 80 3e 01 e4  58 74 14 09 c0 75 01 48  |.....>..Xt...u.H|
00000150  80 fc 00 77 0a 3c 41 72  06 3c 5a 77 02 04 20 ab  |...w.<Ar.<Zw.. .|
00000160  e2 df 66 61 c3 66 60 b2  00 66 8b 44 02 66 3b 45  |..fa.f`..f.D.f;E|
00000170  02 75 0f 80 3c 00 75 0a  66 8b 44 06 66 3b 45 06  |.u..<.u.f.D.f;E.|
00000180  74 48 77 44 72 3d 66 60  31 d2 87 f7 66 ad 66 89  |tHwDr=f`1...f.f.|
00000190  c1 87 f7 66 ad 66 39 c8  77 2e 72 27 87 f7 ad 89  |...f.f9.w.r'....|
000001a0  c1 87 f7 ad 80 f9 00 74  1f 39 c8 74 0b 77 07 fe  |.......t.9.t.w..|
000001b0  ce 89 c1 e9 02 00 fe c6  f3 a7 77 0c 72 05 88 f2  |..........w.r...|
000001c0  e9 07 00 fe ca e9 02 00  fe c2 88 96 14 00 80 fa  |................|
000001d0  00 66 61 c3 50 57 8b 3e  0a e6 57 47 47 49 49 b0  |.fa.PW.>..WGGII.|
000001e0  00 f3 aa 89 3e 0a e6 5d  89 2d 5f 58 c3 2f 62 6f  |....>..].-_X./bo|
000001f0  6f 74 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |ot............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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

I got a message at the beginning though:
'"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.'
(I used a live disk to produce this)

FYI: I've just realised that 'sdc1' could be a memory stick.

---

### Post by darkod on 2012-02-15
Looks fine, except the fact that you seem to have OS X also on /dev/sda2. I didn't know grub2 can boot OS X.

From live mode, I would run a check on the ubuntu root partition, /dev/sda5. Don't mount it, it needs to be unmounted. Simply boot into live mode and run:
sudo fsck /dev/sda5

Let it finish.

By the way, only ubuntu has problems booting? Win7 boots fine? OS X?

---

### Post by linuxpingu on 2012-02-15
When I took the steps in reply 2 it became the first boot manager to come up and added entries for everything - It used to be that I had to chose an entry off the windows bootmgr and it would direct me to grub. Although that was because I had to reinstall windows after my old OS X experiments went wrong.
OS X is only experimental at the moment, and no, grub doesn't boot it properly. To be honest I've only just reinstalled it, so I'm still working on that.
Windows 7 boots fine, there's not really that much I can say on that.
I'll run that command now.

---

### Post by linuxpingu on 2012-02-15
> **darkod said:**
>  Simply boot into live mode and run:
sudo fsck /dev/sda5

Let it finish.


I've run it, and it didn't take much time at all.
```
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda5: clean, 317189/3989504 files, 13190515/15950336 blocks
```

---

### Post by darkod on 2012-02-15
OK, and if you try to mount it and list the files on it:

```
sudo mount /dev/sda5 /mnt
ls /mnt
```

Does it show any files and folders?

---

### Post by linuxpingu on 2012-02-15
Here's what it shows:
[IMG]http://farm8.staticflickr.com/7057/6883459895_53010b5bd9_b.jpg[/IMG]

---

### Post by darkod on 2012-02-15
Looks fine.

I would try to enter the installation with chroot and maybe even reinstall the latest kernel.

Mounting it for chroot takes few steps. The first group of commands mounts the needed parts:

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
```

If that works without any errors, enter the chroot, remove the latest kernel completely and reinstall it, update the grub config after that:

```
sudo chroot /mnt
apt-get remove --purge linux-image-3.0.0-16-generic
apt-get install linux-image-3.0.0-16-generic
update-grub
grub-install /dev/sda
```

Hopefully that worked. Exit the chroot and unmount everything.

```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /
```

Restart and cross your fingers. :) Select to boot -16- and see how it goes.

---

### Post by linuxpingu on 2012-02-15
I've only just started, but I've already got an error message about proc:
```
mount: mount point /mnt/proc does not exist
```
The other two are fine.

---

### Post by linuxpingu on 2012-02-15
Nope, it hasn't worked. It kept giving me proc related errors throughout and has just brought up the same error I started with.
This /proc whatever it is seems to be missing, which is why it can't boot.
Why does technology have to be so annoying at times? :(

---

### Post by darkod on 2012-02-16
I found something that might help in one spanish forum. If my Spanish is any good, it said they had similar problem and what helped was:
1. Boot with the ubuntu cd.
2. Open the Disk Utility (I think it was called like that).
3. Select the root partition, /dev/sda5.
4. Click on Edit Partition and there should be some Repair option. Use that option.

After it finishes, restart and see if it boots fine. It helped other people in the same situation.

---

### Post by linuxpingu on 2012-02-16
I tried doing that with GParted before I posted this thread :/ I've just tried it again and I tried doing fsck (I think it's called) manually in terminal a couple of times last night, but it passes everything.

---

### Post by linuxpingu on 2012-02-16
This is what it comes back as:
```
GParted 0.8.1 --enable-libparted-dmraid

Libparted 2.3

Check and repair file system (ext4) on /dev/sda5  00:00:16    ( SUCCESS )
    	
calibrate /dev/sda5  00:00:00    ( SUCCESS )
    	
path: /dev/sda5
start: 443684864
end: 571287551
size: 127602688 (60.85 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:16    ( SUCCESS )
    	
e2fsck -f -y -v /dev/sda5
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

317180 inodes used (7.95%)
8732 non-contiguous files (2.8%)
374 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 18/5/1
Extent depth histogram: 273107/494/1
13190504 blocks used (82.70%)
0 bad blocks
9 large files

226187 regular files
32539 directories
57 character device files
25 block device files
0 fifos
707 links
58360 symbolic links (43450 fast symbolic links)
3 sockets
--------
317878 files
e2fsck 1.41.14 (22-Dec-2010)
grow file system to fill the partition  00:00:00    ( SUCCESS )
    	
resize2fs /dev/sda5
    	
resize2fs 1.41.14 (22-Dec-2010)
The filesystem is already 15950336 blocks long. Nothing to do!

========================================
```

---

### Post by darkod on 2012-02-16
Gparted is not the same as the Disk Utility. The Disk Utility is inclosed in ubuntu, Gparted is installed additionally (but it's included in live mode).

I would try with the Disk Utility because the post said that worked. There is no guarantee it will work for you too, but at least you can try with the same tool.

---

### Post by linuxpingu on 2012-02-16
Well, straight after that post I did try it in disk utility, although it was slightly different than you described. On the version on the live CD that I've got there's two different buttons for edit and repair. I tried them both, and that in truth seemed to do less than GParted.
Juts out of wonder, should my fstab file say
```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

```
I thought it was meant to say 'defaults' and not 'nodev,noexec,nosuid'. Do you know why this might be and how I could fix it?

---

### Post by darkod on 2012-02-16
No, it shouldn't. As far as I know there is no separate entry in fstab for proc. It has entry for the / partition and proc is a part of it. Seems like you located your problem.

Please post the output of:
cat /etc/fstab

---

### Post by linuxpingu on 2012-02-16
> **darkod said:**
> 
Please post the output of:
cat /etc/fstab

I've just tried to run this is in terminal on my live CD, but it's given me the message: cat: etc/fstab: No such file or directory

The file does exist however on my main filesystem.

---

### Post by darkod on 2012-02-16
Sorry, didn't specify that. You need to open the /etc/fstab from the hdd partition and post the content here so we can take a look.

---

### Post by linuxpingu on 2012-02-16
I wondered why there wasn't any reference to a drive or anything in that command - that'd be why :P
Anyway, here it is:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=80ed58d0-20b5-46f6-a37e-3545573a4f94 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=635543a4-f6ba-48cd-bc26-9b7e2ebae01f none            swap    sw              0       0
```

---

### Post by darkod on 2012-02-16
What happens if you try to comment out the proc line?
Just open the file and put a # at the beginning of the line where proc is. That makes it ignore the rest of the line.
Save the changes and reboot. See if it boots from the hdd.

---

### Post by linuxpingu on 2012-02-16
No, it's still coming up with the same error that's at the start of this thread. What other files would affect the proc filesystem and how it boots/mounts?

---

### Post by linuxpingu on 2012-02-16
Would it do me any good to do what it says here? [http://tldp.org/LDP/nag2/x-087-2-iface.procfs.html](http://tldp.org/LDP/nag2/x-087-2-iface.procfs.html)
Add the line and then reinstall/compile the kernel again, as I did earlier in this thread?

---

### Post by darkod on 2012-02-16
You can try, but that looks like very old advice, and for different OS.

Sorry, this is beyond my knowledge. It doesn't seem I can help you save this install.

---

### Post by linuxpingu on 2012-02-16
Fair enough, thanks for trying.
 Just one more question that you might know the answer to: If I make a new install on another partition, is there a way to transfer settings/programs over from this mucked up one?

---

### Post by darkod on 2012-02-16
> **linuxpingu said:**
> Fair enough, thanks for trying.
 Just one more question that you might know the answer to: If I make a new install on another partition, is there a way to transfer settings/programs over from this mucked up one?

I've never tried that. You can try googling for something like "transfer program settings to new ubuntu" or similar. If you find some tutorial and don't understand a part of it, post your questions on the forum, someone should be able to help.

Very often for manu programs it is enough to copy the folder which is inside your Home folder. Since your new install will have a new Home folder (even better if you make it a separate /home partition), you should be able to copy folders with settings from the old to the new install.

---

