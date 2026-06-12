---
title: "boot: out of partition message"
date: 2012-05-10
forum: General Help
---

### Post by Gingalone on 2012-05-10
Just before upgrading to 12.04, I made a bit of cleaning in my hard disk and, after restoring (with fsarchiver) my boot (main) partition, at boot time I get the message: 
error: out of partition 
press any key
and when I press a key the system starts correctly with everything working as before...

What about? And what if I upgrade my system with a not perfectly working grub?

---

### Post by oldfred on 2012-05-10
Do you have in fstab the mounting of some partition that you housecleaned? 

Or did partition table get messed up. Post this:
```

sudo fdisk -lu
```

---

### Post by Gingalone on 2012-05-11
Thank you oldfred.
Argh. This morning the grub stuck: no error message, nothing. Just stuck.
Even if I did no modifications of any kind yesterday (at least AFAIK!).
So, now I booted from a knoppix CD and here the output of the suggested command:
root@Microknoppix:/home/knoppix# fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b094e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480153599   240075776   83  Linux
/dev/sda2       480155646   488396799     4120577    5  Extended
/dev/sda5       480155648   488396799     4120576   82  Linux swap / Solaris

what about?
Thanks for help!

---

### Post by oldfred on 2012-05-11
I wanted to compare partitions to fstab, but if you now have grub issues, it also may be UUIDs from the restored data.

Run this. I have not run it from Knoppix, so it may complain about some standard tools it needs. Not sure how you run the sudo apt-get coammands in Knoppix.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Gingalone on 2012-05-14
OK, done, but the output of bootinfoscript is 413 lines long: do I have to post all of it?
Thanks!

---

### Post by Gingalone on 2012-05-14
Just seen in the results.txt file:
the two last lines:

```
=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

is that the problem?

---

### Post by westie457 on 2012-05-14
Hi, not sure if that is the problem or not.

Us being able to see the whole file would be better and give more information.
Could you post here the whole thing between [ code] [ /code] tags by following oldfred's instructions.

Thank you

---

### Post by Gingalone on 2012-05-14
OK, here we are: RESULTS.txt from bootinfoscript:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   488,396,799     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        720a6858-59ff-46f7-831c-1b067b8e0483   ext4       
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
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
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.134288788 = 234.219909120  boot/grub/core.img                             1
 218.134578705 = 234.220220416  boot/grub/grub.cfg                             1
 124.740219116 = 133.938790400  boot/initrd.img-3.0.0-12-generic               1
 124.805664062 = 134.009061376  boot/initrd.img-3.0.0-13-generic               2
 124.774414062 = 133.975506944  boot/initrd.img-3.0.0-14-generic               2
 124.761322021 = 133.961449472  boot/initrd.img-3.0.0-15-generic               1
 124.792575836 = 133.995008000  boot/initrd.img-3.0.0-16-generic               1
 124.844726562 = 134.051004416  boot/initrd.img-3.0.0-17-generic               2
 124.823822021 = 134.028558336  boot/initrd.img-3.0.0-19-generic               1
 218.156574249 = 234.243837952  boot/vmlinuz-3.0.0-12-generic                  1
 218.203422546 = 234.294140928  boot/vmlinuz-3.0.0-13-generic                  1
 218.199104309 = 234.289504256  boot/vmlinuz-3.0.0-14-generic                  1
 218.131839752 = 234.217279488  boot/vmlinuz-3.0.0-15-generic                  1
 218.209518433 = 234.300686336  boot/vmlinuz-3.0.0-16-generic                  1
 218.192798615 = 234.282733568  boot/vmlinuz-3.0.0-17-generic                  1
 218.152091980 = 234.239025152  boot/vmlinuz-3.0.0-19-generic                  1
 220.126117706 = 236.358619136  grub/stage2                                    1
 218.152091980 = 234.239025152  vmlinuz                                        1
 218.192798615 = 234.282733568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   488,396,799     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        720a6858-59ff-46f7-831c-1b067b8e0483   ext4       
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
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
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.134288788 = 234.219909120  boot/grub/core.img                             1
 218.134578705 = 234.220220416  boot/grub/grub.cfg                             1
 124.740219116 = 133.938790400  boot/initrd.img-3.0.0-12-generic               1
 124.805664062 = 134.009061376  boot/initrd.img-3.0.0-13-generic               2
 124.774414062 = 133.975506944  boot/initrd.img-3.0.0-14-generic               2
 124.761322021 = 133.961449472  boot/initrd.img-3.0.0-15-generic               1
 124.792575836 = 133.995008000  boot/initrd.img-3.0.0-16-generic               1
 124.844726562 = 134.051004416  boot/initrd.img-3.0.0-17-generic               2
 124.823822021 = 134.028558336  boot/initrd.img-3.0.0-19-generic               1
 218.156574249 = 234.243837952  boot/vmlinuz-3.0.0-12-generic                  1
 218.203422546 = 234.294140928  boot/vmlinuz-3.0.0-13-generic                  1
 218.199104309 = 234.289504256  boot/vmlinuz-3.0.0-14-generic                  1
 218.131839752 = 234.217279488  boot/vmlinuz-3.0.0-15-generic                  1
 218.209518433 = 234.300686336  boot/vmlinuz-3.0.0-16-generic                  1
 218.192798615 = 234.282733568  boot/vmlinuz-3.0.0-17-generic                  1
 218.152091980 = 234.239025152  boot/vmlinuz-3.0.0-19-generic                  1
 220.126117706 = 236.358619136  grub/stage2                                    1
 218.152091980 = 234.239025152  vmlinuz                                        1
 218.192798615 = 234.282733568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   488,396,799     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        720a6858-59ff-46f7-831c-1b067b8e0483   ext4       
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
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
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.134288788 = 234.219909120  boot/grub/core.img                             1
 218.134578705 = 234.220220416  boot/grub/grub.cfg                             1
 124.740219116 = 133.938790400  boot/initrd.img-3.0.0-12-generic               1
 124.805664062 = 134.009061376  boot/initrd.img-3.0.0-13-generic               2
 124.774414062 = 133.975506944  boot/initrd.img-3.0.0-14-generic               2
 124.761322021 = 133.961449472  boot/initrd.img-3.0.0-15-generic               1
 124.792575836 = 133.995008000  boot/initrd.img-3.0.0-16-generic               1
 124.844726562 = 134.051004416  boot/initrd.img-3.0.0-17-generic               2
 124.823822021 = 134.028558336  boot/initrd.img-3.0.0-19-generic               1
 218.156574249 = 234.243837952  boot/vmlinuz-3.0.0-12-generic                  1
 218.203422546 = 234.294140928  boot/vmlinuz-3.0.0-13-generic                  1
 218.199104309 = 234.289504256  boot/vmlinuz-3.0.0-14-generic                  1
 218.131839752 = 234.217279488  boot/vmlinuz-3.0.0-15-generic                  1
 218.209518433 = 234.300686336  boot/vmlinuz-3.0.0-16-generic                  1
 218.192798615 = 234.282733568  boot/vmlinuz-3.0.0-17-generic                  1
 218.152091980 = 234.239025152  boot/vmlinuz-3.0.0-19-generic                  1
 220.126117706 = 236.358619136  grub/stage2                                    1
 218.152091980 = 234.239025152  vmlinuz                                        1
 218.192798615 = 234.282733568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   488,396,799     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        720a6858-59ff-46f7-831c-1b067b8e0483   ext4       
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
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
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.134288788 = 234.219909120  boot/grub/core.img                             1
 218.134578705 = 234.220220416  boot/grub/grub.cfg                             1
 124.740219116 = 133.938790400  boot/initrd.img-3.0.0-12-generic               1
 124.805664062 = 134.009061376  boot/initrd.img-3.0.0-13-generic               2
 124.774414062 = 133.975506944  boot/initrd.img-3.0.0-14-generic               2
 124.761322021 = 133.961449472  boot/initrd.img-3.0.0-15-generic               1
 124.792575836 = 133.995008000  boot/initrd.img-3.0.0-16-generic               1
 124.844726562 = 134.051004416  boot/initrd.img-3.0.0-17-generic               2
 124.823822021 = 134.028558336  boot/initrd.img-3.0.0-19-generic               1
 218.156574249 = 234.243837952  boot/vmlinuz-3.0.0-12-generic                  1
 218.203422546 = 234.294140928  boot/vmlinuz-3.0.0-13-generic                  1
 218.199104309 = 234.289504256  boot/vmlinuz-3.0.0-14-generic                  1
 218.131839752 = 234.217279488  boot/vmlinuz-3.0.0-15-generic                  1
 218.209518433 = 234.300686336  boot/vmlinuz-3.0.0-16-generic                  1
 218.192798615 = 234.282733568  boot/vmlinuz-3.0.0-17-generic                  1
 218.152091980 = 234.239025152  boot/vmlinuz-3.0.0-19-generic                  1
 220.126117706 = 236.358619136  grub/stage2                                    1
 218.152091980 = 234.239025152  vmlinuz                                        1
 218.192798615 = 234.282733568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   488,396,799     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        720a6858-59ff-46f7-831c-1b067b8e0483   ext4       
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=720a6858-59ff-46f7-831c-1b067b8e0483 ro recovery nomodeset 
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
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 720a6858-59ff-46f7-831c-1b067b8e0483
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.134288788 = 234.219909120  boot/grub/core.img                             1
 218.134578705 = 234.220220416  boot/grub/grub.cfg                             1
 124.740219116 = 133.938790400  boot/initrd.img-3.0.0-12-generic               1
 124.805664062 = 134.009061376  boot/initrd.img-3.0.0-13-generic               2
 124.774414062 = 133.975506944  boot/initrd.img-3.0.0-14-generic               2
 124.761322021 = 133.961449472  boot/initrd.img-3.0.0-15-generic               1
 124.792575836 = 133.995008000  boot/initrd.img-3.0.0-16-generic               1
 124.844726562 = 134.051004416  boot/initrd.img-3.0.0-17-generic               2
 124.823822021 = 134.028558336  boot/initrd.img-3.0.0-19-generic               1
 218.156574249 = 234.243837952  boot/vmlinuz-3.0.0-12-generic                  1
 218.203422546 = 234.294140928  boot/vmlinuz-3.0.0-13-generic                  1
 218.199104309 = 234.289504256  boot/vmlinuz-3.0.0-14-generic                  1
 218.131839752 = 234.217279488  boot/vmlinuz-3.0.0-15-generic                  1
 218.209518433 = 234.300686336  boot/vmlinuz-3.0.0-16-generic                  1
 218.192798615 = 234.282733568  boot/vmlinuz-3.0.0-17-generic                  1
 218.152091980 = 234.239025152  boot/vmlinuz-3.0.0-19-generic                  1
 220.126117706 = 236.358619136  grub/stage2                                    1
 218.152091980 = 234.239025152  vmlinuz                                        1
 218.192798615 = 234.282733568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
```

---

### Post by westie457 on 2012-05-14
Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR="Red"]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   480,153,599   480,151,552  83 Linux
/dev/sda2         480,155,646   [COLOR="Red"]488,396,799[/COLOR]     8,241,154   5 Extended
/dev/sda5         480,155,648   488,396,799     8,241,152  82 Linux swap / Solaris

I have highlighted the problem. The extended partition has been mis-reported and is beyond the physical size of the hard drive.

IMHO there is a choice of fixes for this issue.
Fix number one is 'Fixparts' available here.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fix number two is 'Testdisk' available here.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Both links have full instructions. Read both links it will not hurt to research while waiting for oldfred to offer the best solution. He might even have a better idea than either of the ones suggested by me.

Hope this helps.

---

### Post by oldfred on 2012-05-14
Actually sectors look ok. 

It looks like you posted script twice? Script is supposed to create results1 results2 etc every time you run it.  Did script combine two or did you just include two copies?

This looks like the issue. In moving partitions, you must have deleted & recreated swap. So you need the new UUID in fstab. All the others have the correct UUID even though the notes still refer to the old partition number.

> From UUID list
/dev/sda5        9924de52-646a-4038-9f88-faaea97a6d9b   swap 

from fstab
# swap was on /dev/sda8 during installation
UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0

Just change the UUID in fstab to the one from your blkid.

# Find your UUID (also shown above from script):
sudo blkid -o list

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by Gingalone on 2012-05-15
```
gksudo gedit /etc/fstab
```

It looks there is no device UUID in my /etc/fstab, here the entire file:
```
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

is it more serious than it looked?

Thanks again for help!

---

### Post by Gingalone on 2012-05-15
> **oldfred said:**
> 
gksudo gedit /etc/fstab


It looks there are no UUID for devices in my /etc/fstab, here the entire file:```
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Is it more serious than it looked?
Thanks again for help!

---

### Post by Gingalone on 2012-05-15
Sorry I posted the last message twice (change of page...)
And yes oldfred, I pasted the output of bootinfoscript twice, sorry^2!

---

### Post by oldfred on 2012-05-15
I think you are looking at the fstab on your liveCD. Boot script shows your fstab.

Since you are in liveCD, you can directly drill down from command line & edit, but it may be easier just to do this:

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
gksudo gedit /mnt/sda1/etc/fstab
# Then replace incorrect UUID


# /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda7 during installation UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda8 during installation UUID=c4962814-196c-4f3d-8c64-15be6bfffdd1 none            swap    sw              0       0

---

### Post by Gingalone on 2012-05-16
No luck.
Done as you said oldfred, swap partition UUID corrected in fstab, but grub still hangs. (See attached thumbnail of the boot screen (dead!)).
The sda1 new fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=720a6858-59ff-46f7-831c-1b067b8e0483 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9924de52-646a-4038-9f88-faaea97a6d9b none            swap    sw              0       0
```

---

### Post by oldfred on 2012-05-16
Did you put the Debian theme in? I have seen another post where a user got that which is not actually correct. 

If you did not add it, it think you need to chroot into your install and do the total uninstall and reinstall.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Boot-Repair also has a full removal of grub and reinstall function.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by Gingalone on 2012-05-17
> **oldfred said:**
> Did you put the Debian theme in? I have seen another post where a user got that which is not actually correct. 


I didn't. It came out after updating to Oneiric, got grub troubles that time too and at the end I got the Debian boot screen...

Now I used Boot-Repair and the system boots as before now (but always with the Debian screen). The results are here: [http://paste.ubuntu.com/991992/]("http://paste.ubuntu.com/991992/")

I want to update to Precise (and then stick to the LTS releases of Ubuntu!) what would be the best for my system? 
Format HD and clean install 12.04? 
Is there a clean way to install the new Ubuntu without the need to work a week to get my system in the previous state/conditions?

---

### Post by oldfred on 2012-05-17
Boot-Repair has some advanced modes where it will totally reinstall grub, have you tried those?

I am in the clean install preferred over upgrade group, but to make it a bit easier you need to be able to copy /home and export a list of installed applications. Possibly some other settings in /etc if you manually edited a configuration file.

My backups are to allow me to totally reinstall and then restore my configurations & setups.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

But if you cannot get into your old system then you just about have to manually recreate everything. I prefer either a separate /home or even better a separate /data partition and /home backed up often.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Gingalone on 2012-05-18
> **oldfred said:**
> Boot-Repair has some advanced modes where it will totally reinstall grub, have you tried those?


No; there are many options there (completely reinstall Grub (and purge it before reinstall?) or better to restore MBR?) and is it better to boot from a live CD before the Grub/MBR 'restoring' or OK after a normal boot from HD?

Backup and restore task: I am thinking to go toward a clean install... Some doubts on packages reinstall since there are 2107 packages in my my-packages list... I think I have a 'dirty' system...

Thank you for help Oldfred (it's a pity we can exchange only a post per day since we are 7 time zones away!)

---

### Post by oldfred on 2012-05-18
Some claim a 'dirty' install right over an existing install without formating works. I would think it would cause issues.

I had done upgrades for many versions and with 9.10 I wanted to change to ext4 and 64bit, so I had to do a clean install. Now I really like clean installs as it in effect does a houseclean (which I am not good at maintaining otherwise). But I keep old installs, so I can go back and find a setting or file if need be. I have all data in separate partitions, so my / (root) is only in 25GB partitions with about 7GB used including /home which I now do not have separate.

---

### Post by Gingalone on 2012-05-22
I followed your advice and clean installed Precise and the process of restoring my data and settings is going smoothly.

Thank you Oldfred for your competent help!

---

