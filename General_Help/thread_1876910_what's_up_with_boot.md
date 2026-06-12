---
title: "what's up with boot?"
date: 2011-11-07
forum: General Help
---

### Post by debd on 2011-11-07
I have a dual boot machine with Ubuntu 10.10 and WinXP
Recently I installed backtrack linux, which had the mbr rewritten and for some reason grub didn't find the ubuntu partition. So I purged and reinstalled grub using a live 10.10 CD which gave me back grub with all menu entries but when trying to boot into Ubuntu, the loading process starts up, but after a while it stops. HD lamp becomes idle and nothing happens. Its stuck at the boot up screen. Neither do recovery modes work.
I can however boot into backtrack and windows.
Here is my partition list from fdisk:
```
fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe714e714

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       60800   457659689+   f  W95 Ext'd (LBA)
/dev/sda5            3825        5722    15244904+   7  HPFS/NTFS
/dev/sda6            7649       15297    61440561    7  HPFS/NTFS
/dev/sda7           15298       22946    61440561    7  HPFS/NTFS
/dev/sda8           22947       30595    61440561    7  HPFS/NTFS
/dev/sda9           30596       38244    61440561    7  HPFS/NTFS
/dev/sda10          38245       38731     3905536   83  Linux
/dev/sda11          38731       39339     4881408   83  Linux
/dev/sda12          39339       39582     1951744   82  Linux swap / Solaris
/dev/sda13          39582       45893    50697216   83  Linux
/dev/sda14          45894       60800   119740446    7  HPFS/NTFS
/dev/sda15           5723        6087     2928640   83  Linux
/dev/sda16           6087        7648    12539904   83  Linux

Partition table entries are not in disk order

```/dev/sda10 is the boot partition for my ubuntu installation.
/dev/sda13 is the / of the ubuntu installation. /dev/sda11 is the home partition.

/dev/sda15 and /dev/sda16 is home and / of the backtrack installation.

Here's the current grub.cfg

```
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set b3d060a1-750a-4e5c-90eb-1193c0ab072d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
set locale_dir=($root)/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    linux    /vmlinuz-2.6.35-28-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro   quiet splash
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /vmlinuz-2.6.35-28-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    linux    /vmlinuz-2.6.35-27-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro   quiet splash
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /vmlinuz-2.6.35-27-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 621406221405F9B5
    drivemap -s (hd0) ${root}
    chainloader +1
}
##this is actually the backtrack installation    based on ubuntu :p
menuentry "Ubuntu, with Linux 2.6.39.4 (on /dev/sda16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos16)'
    search --no-floppy --fs-uuid --set 3b492feb-5afd-4f53-b737-333c021ed973
    linux /boot/vmlinuz-2.6.39.4 root=UUID=3b492feb-5afd-4f53-b737-333c021ed973 ro text splash vga=791
    initrd /boot/initrd.img-2.6.39.4
}
menuentry "Ubuntu, with Linux 2.6.39.4 (recovery mode) (on /dev/sda16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos16)'
    search --no-floppy --fs-uuid --set 3b492feb-5afd-4f53-b737-333c021ed973
    linux /boot/vmlinuz-2.6.39.4 root=UUID=3b492feb-5afd-4f53-b737-333c021ed973 ro single
    initrd /boot/initrd.img-2.6.39.4
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
```I had some custom options in the cfg file which are gone and as far as I remember I changed a script sequence. probably that has affected..
I'll check out on that. Still, please look @ the cfg and tell me if somethings wrong.

Thanks.

---

### Post by debd on 2011-11-08
okey.. I solved it.
coz I resized a partition the partition numbers shifted, so I needed to update fstab .

---

