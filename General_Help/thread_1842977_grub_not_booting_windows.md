---
title: "grub not booting windows"
date: 2011-09-12
forum: General Help
---

### Post by pk44 on 2011-09-12
i had ubuntu 11.04 installed and then installed windows. windows replaced grub and would boot fine. today i re-installed grub2 from a livecd of and then installed os-prober(it wasnt installed for some reason). after running os prober it detected windows on its correct partition (/dev/sda2) and then i updated grub and that added a windows entry to the menu. here is my grub.cfg entry for windows:

menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set C2CC6D05CC6CF4D7
    chainloader +1
}

it appears to detect something when i boot it, there is no error message, but then it just ends with a blank screen with a flashing '_' in the upper-left corner. i have no idea why its doing this, everything else seems correct. could this be something wrong with my windows installation or is it grub? thanks for any help! (i really need to get windows working for school...)

---

### Post by drs305 on 2011-09-12
Is the boot flag still set to your Windows partition? You can check with "sudo fdisk -l". If it isn't, you can use a variety of tools to move/add the boot flag (Gparted, Disk Utility, etc).

If that isn't the problem please run the boot info script and post the contents of RESULTS.txt. A link to the script page is in my signature line (BIS).

---

### Post by pk44 on 2011-09-12
the partitions is flagged as bootable, yes. i ran th bis,it used busybox awk instead of gawk (should i install gawk?), anyway, here are the results:
```


                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 1223222856 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #6 for /boot/grub/menu.lst.
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2    *      3,074,048   954,951,679   951,877,632   7 NTFS / exFAT / HPFS
/dev/sda4         976,775,166 1,250,263,039   273,487,874   f W95 Extended (LBA)
/dev/sda5         976,775,168 1,045,728,782    68,953,615   7 NTFS / exFAT / HPFS
/dev/sda6       1,045,729,280 1,111,003,135    65,273,856  83 Linux
/dev/sda7       1,111,005,184 1,111,234,297       229,114  82 Linux swap / Solaris
/dev/sda8       1,111,234,560 1,244,506,111   133,271,552  83 Linux
/dev/sda9       1,244,508,160 1,250,263,039     5,754,880  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        C2CC6D05CC6CF4D7                       ntfs       TI105322W0F
/dev/sda5        4CD64BA2D64B8AE2                       ntfs       New Volume
/dev/sda6        24f12be9-9f9a-4260-953c-7ed7f2fa1464   ext4       
/dev/sda7        fde045b6-f49a-41db-b45a-2b88a45a3d3c   swap       
/dev/sda8        64270a06-986f-4735-aada-ccc866c33d6c   ext4       
/dev/sda9        71d5eebb-da9a-458e-80cd-878edc0dbb5d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set C2CC6D05CC6CF4D7
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=fde045b6-f49a-41db-b45a-2b88a45a3d3c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)

522.794559479 = 561.346383872 boot/grub/core.img 1
523.080211639 = 561.653100544 boot/grub/grub.cfg 1
519.149845123 = 557.432901632 boot/initrd.img-2.6.35-22-generic 2
499.339935303 = 536.162172928 boot/vmlinuz-2.6.35-22-generic 2
519.149845123 = 557.432901632 initrd.img 2
499.339935303 = 536.162172928 vmlinuz 2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic-pae
}
1
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
echo 'Loading Linux 2.6.38-8-generic-pae ...'
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
echo 'Loading Linux 2.6.38-8-generic ...'
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
echo 'Loading Linux 2.6.35-28-generic ...'
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root C2CC6D05CC6CF4D7
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 9A4493F54493D1FD
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 24f12be9-9f9a-4260-953c-7ed7f2fa1464
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 24f12be9-9f9a-4260-953c-7ed7f2fa1464
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro single
initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

532.013404846 = 571.245043712 boot/grub/core.img 1
562.094299316 = 603.544158208 boot/grub/grub.cfg 1
532.010856628 = 571.242307584 boot/grub/stage2 1
563.393402100 = 604.939059200 boot/initrd.img-2.6.35-28-generic 2
567.513370514 = 609.362841600 boot/initrd.img-2.6.38-8-generic 3
567.516494751 = 609.366196224 boot/initrd.img-2.6.38-8-generic-pae 2
532.009807587 = 571.241181184 boot/vmlinuz-2.6.35-28-generic 1
565.643859863 = 607.355469824 boot/vmlinuz-2.6.38-8-generic 1
565.710388184 = 607.426904064 boot/vmlinuz-2.6.38-8-generic-pae 1
567.516494751 = 609.366196224 initrd.img 2
567.513370514 = 609.362841600 initrd.img.old 3
565.710388184 = 607.426904064 vmlinuz 1
565.643859863 = 607.355469824 vmlinuz.old

```

---

### Post by pk44 on 2011-09-12
[COLOR="darkred"](Moderator note: I've stitched this and the next post into the previous one so the entire contents are in a single post. I've left these posts intact - within their own 'code' tags - in case my 'sewing' isn't too good. Code tags are generated by pressing the **#** icon in the post's menubar while composing, and pasting the contents between the tags.)[/COLOR]

and more of it:
```

GiB - GB             File                                 Fragment(s)

 522.794559479 = 561.346383872  boot/grub/core.img                             1
 523.080211639 = 561.653100544  boot/grub/grub.cfg                             1
 519.149845123 = 557.432901632  boot/initrd.img-2.6.35-22-generic              2
 499.339935303 = 536.162172928  boot/vmlinuz-2.6.35-22-generic                 2
 519.149845123 = 557.432901632  initrd.img                                     2
 499.339935303 = 536.162172928  vmlinuz                                        2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
         1

```

---

### Post by pk44 on 2011-09-12
and the rest:
```

menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=64270a06-986f-4735-aada-ccc866c33d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 64270a06-986f-4735-aada-ccc866c33d6c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root C2CC6D05CC6CF4D7
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 9A4493F54493D1FD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 24f12be9-9f9a-4260-953c-7ed7f2fa1464
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24f12be9-9f9a-4260-953c-7ed7f2fa1464 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 532.013404846 = 571.245043712  boot/grub/core.img                             1
 562.094299316 = 603.544158208  boot/grub/grub.cfg                             1
 532.010856628 = 571.242307584  boot/grub/stage2                               1
 563.393402100 = 604.939059200  boot/initrd.img-2.6.35-28-generic              2
 567.513370514 = 609.362841600  boot/initrd.img-2.6.38-8-generic               3
 567.516494751 = 609.366196224  boot/initrd.img-2.6.38-8-generic-pae           2
 532.009807587 = 571.241181184  boot/vmlinuz-2.6.35-28-generic                 1
 565.643859863 = 607.355469824  boot/vmlinuz-2.6.38-8-generic                  1
 565.710388184 = 607.426904064  boot/vmlinuz-2.6.38-8-generic-pae              1
 567.516494751 = 609.366196224  initrd.img                                     2
 567.513370514 = 609.362841600  initrd.img.old                                 3
 565.710388184 = 607.426904064  vmlinuz                                        1
 565.643859863 = 607.355469824  vmlinuz.old

```

---

