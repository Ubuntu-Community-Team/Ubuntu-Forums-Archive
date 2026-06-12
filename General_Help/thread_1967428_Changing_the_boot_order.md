---
title: "Changing the boot order?"
date: 2012-04-28
forum: General Help
---

### Post by Jaxke on 2012-04-28
Hey!

Having problems with Grub2 boot orders, here's the story:

I decided to try Win7 again, and I downloaded *Grub-customizer* program, I then changed the boot order to 

Ubuntu 11.10
Windows 7

After a day of use, I started regretting of even trying Windows(what a crappy piece of software :mad: ), and wanted to get back to Ubuntu. Next time I booted up, I selected Ubuntu 11.10 from Grub, and noticed that it was my second Ubuntu partition(kind of a secondary partition for worst-case-scenario), that only has about 10gigs(so it's not the Ubuntu partition I've used before).

Now I want my old Ubuntu partition to be in the Grub boot list. I downloaded Grub-custmizer again, I applied the settings I want to have. But it's not working. It still has only two options(Win7 and the second Ubuntu). I ran the program again and again, but no difference. 

I'm sorry if I sound stupid. All help appreciated! :P

---

### Post by jerome1232 on 2012-04-28
I would suggest you download and run the bootinfo script will give us all the information we need to troubleshoot the issue at hand. Instructions for use can be found at the linked site as well as the script. When you paste the results here, be sure to go into advanced mode, highlight all of the output, and click the # symbol to wrap it in code tags for readability.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Jaxke on 2012-04-28
Cool. 

```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

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

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     37,955,584   793,619,646   755,664,063   7 NTFS / exFAT / HPFS
/dev/sda2         793,620,478 1,250,263,039   456,642,562   5 Extended
/dev/sda5         793,620,480 1,237,966,847   444,346,368  83 Linux
/dev/sda6       1,237,985,280 1,250,263,039    12,277,760  82 Linux swap / Solaris
/dev/sda3               2,048    25,675,775    25,673,728  83 Linux
/dev/sda4          25,675,776    37,955,583    12,279,808  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        06F8944BF8943B3F                       ntfs       Acer
/dev/sda3        6c0a495e-7115-4b93-8638-5063c06c7b43   ext4       
/dev/sda4        1b40cd1b-5cac-4d86-a984-8704bdde4db4   swap       
/dev/sda5        19691af6-2e81-44e1-9f2c-945ec96c49d7   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/24_SEASON4_DISC6  udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 06F8944BF8943B3F
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux_proxy ###
### END /etc/grub.d/20_linux_proxy ###

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
UUID=19691af6-2e81-44e1-9f2c-945ec96c49d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=1b40cd1b-5cac-4d86-a984-8704bdde4db4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-17-generic               9
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu 11.10 (11.10) (on /dev/sda5)"
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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x8
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
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

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img.old
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img.old
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img.old
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz.old root=/dev/sda5
    initrd /initrd.img.old
}
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 06F8944BF8943B3F
    chainloader +1
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sda5
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /boot/vmlinuz-3.0.0-17-generic root=/dev/sda5
    initrd /boot/initrd.img-3.0.0-17-generic
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux ###
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
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 ro vga=792  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    echo    'Loading Linux 3.0.0-17-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 ro recovery nomodeset vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 ro vga=792  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 ro recovery nomodeset vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/20_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6c0a495e-7115-4b93-8638-5063c06c7b43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/30_memtest86+ ###

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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=6c0a495e-7115-4b93-8638-5063c06c7b43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=1b40cd1b-5cac-4d86-a984-8704bdde4db4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             2
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-17-generic-pae           1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic-pae              1
               =                initrd.img                                     3
               =                initrd.img.old                                 3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

The partition that has Ubuntu(the one I wanna use) is /dev/sda5/

---

### Post by oldfred on 2012-04-28
It almost looks like you copied the grub.cfg from sda3 into sda5 and the grub.cfg from sda5 into sda3, so the grub actually boots the wrong install?

You can manually edit the grub entry that comes up to boot sda5.

At the grub menu press e to edit and update entry to this,cntrl x to boot:

```
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}

```

Once booted run
sudo update-grub

---

### Post by Jaxke on 2012-05-01
> **oldfred said:**
> It almost looks like you copied the grub.cfg from sda3 into sda5 and the grub.cfg from sda5 into sda3, so the grub actually boots the wrong install?

You can manually edit the grub entry that comes up to boot sda5.

At the grub menu press e to edit and update entry to this,cntrl x to boot:

```
menuentry "Ubuntu 11.10 (11.10) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 19691af6-2e81-44e1-9f2c-945ec96c49d7
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}

```Once booted run
sudo update-grub
I tried, but it didn't work & got discarded after reboot. Is that "search --nofloppy" line unique for my computer or do I use the exact same code as you wrote?

Thanks for answers again!

---

### Post by strask on 2012-05-01
It looks like he took the info from your boot info script output and customized that line just for you, so if you typed it exactly as written it should have worked. What kind of failure did you get when you tried it?

---

### Post by oldfred on 2012-05-01
If the set root line is correct, you do not even need the search line at all.

The search overides the set root in those cases where drive order has changed so UUID is the preferred final choice.  But if you type that line it has to be exact as that should be the UUID for sda5.

---

### Post by Jaxke on 2012-05-01
> **strask said:**
> It looks like he took the info from your boot info script output and customized that line just for you, so if you typed it exactly as written it should have worked. What kind of failure did you get when you tried it?
OK. I copied all of it and edited the script. After I pressed Ctrl-X, it immediately showed 
```

}

```I then copied everything again into that entry, and soon had error. I took my cell phone and tried to take a picture, but the nuisance rebooted :mad:

After it rebooted, my GRUB looked like this:
```

Windows 7
Ubuntu Generic 3.3.1.7
Ubuntu 11.10
Ubuntu 11.10
```Ubuntu Generic is the partition I've always had without any problems, but now I had two Ubuntu 11.10 entries(or whatever they are :D I suck at computer terminology). Obviously I tried to go to them, but both had the same error. "You need to load kernel first" or something like that. I've never had anything to do with computer kernels, how do I "load" it? Would it be just easier to reinstall? 

Thanks.

E: I have that other working Ubuntu partition so if there's something I can edit from there...

E2: Great, no more Ubuntu 11.10 entry. Just those two again. 
I have this GRUB2 CD burnt, and I tried to the disc, and I managed to boot my Ubuntu 11.10 up that way. Now it's working, but I still want to have that option without this disc...

---

### Post by oldfred on 2012-05-01
Are you booting into an install on your drive?

Then run this, if this is the install you want to primarily boot into.

sudo grub-install /dev/sda
# then
sudo update-grub

---

### Post by Jaxke on 2012-05-02
> **oldfred said:**
> Are you booting into an install on your drive?

Then run this, if this is the install you want to primarily boot into.

sudo grub-install /dev/sda
# then
sudo update-grub
```
jaxe@JaXXXe-Aspire:~$ sudo grub-install /dev/sda
[sudo] password for jaxe: 
Installation finished. No error reported.
jaxe@JaXXXe-Aspire:~$ update-grub
grub-mkconfig: You must run this as root
jaxe@JaXXXe-Aspire:~$ sudo update-grub
Generating grub.cfg ...
/etc/grub.d/10_os-prober_proxy: 9: /etc/grub.d/bin/grubcfg_proxy: not found
Found Windows 7 (loader) on /dev/sda1

```

Got this. Is it possible to install GRUB2 to hard drive? If the disc works, why wouldn't it work on HD?

---

### Post by oldfred on 2012-05-02
It seems that the update scripts are damaged, if you have not rebooted, I would uninstall grub & reinstall it. Make sure you have Internet connect as uninstall will work, then without Internet reinstall will not work and then you will not be able to boot.

If in the system you want to reinstall grub into, you can skip the chroot.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

