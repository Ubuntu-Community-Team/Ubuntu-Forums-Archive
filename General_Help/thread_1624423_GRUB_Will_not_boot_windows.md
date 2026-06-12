---
title: "GRUB Will not boot windows"
date: 2010-11-17
forum: General Help
---

### Post by razor180 on 2010-11-17
I recently deleted a 10gb partition (it was NTFS format, and it appeared to have nothing in it) and expanded my windows partition to absorb that 10gb (I used gparted and GRUB views the hard drive I have windows on as the second hard drive while the other one is the primary because grub is on the other one). I think that grub was booting to D: (the one I deleted) and not c: (the one I expanded) and was somehow routing to the boot files on C: (not sure though). I don't know how to fix it (have not tried to configure grub before from grub or another OS)

what happens when I choose the boot into windows option, it just restarts the computer

---

### Post by drs305 on 2010-11-17
Normally if Windows is selected and the system immediately returns to the Grub menu it means it was installed on the Windows partition and not in the MBR. If you have Windows on one drive and Ubuntu on another we can set up a bootloader on each if you want.

To give us a clear view of what is where, please boot the LiveCD and run the boot info script from the following link. Paste the contents of the RESULTS.txt file it generates in a new post between 'code' tags, which you generate by pressing the # icon in the menubar.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by razor180 on 2010-11-17
well, I can still boot into ubuntu (and linux mint), but I'll do the live disc just in case

it's just windows that's having a problem (and no, it doesn't go straight back to grub, it literally restarts my computer. Asus express gate pops up and so does the option to edit my BIOS or view the BIOS POST message. This is part of my normal computer booting process)

I know it already chainloads ubuntu and I tried an outdated method I found to try and fix it (I found it was outdated because grub didn't accept the commad map.  I tried ```
map (hd0) (hd1)
map (hd1) (hd0)
``` but it told me it couldn't recognise command 'map')

not sure why bootloader calls my windows boot option windows recovery, but it does (and has booted fine until now). This has happened once before and what I had to do was repair windows. I don't want to do that because I can't find the disc

I've run this script before

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          58,589,116   362,297,879   303,708,764   5 Extended
/dev/sda5          58,589,118    69,336,539    10,747,422  82 Linux swap / Solaris
/dev/sda6          69,339,136   315,097,087   245,757,952   7 HPFS/NTFS
/dev/sda3         370,892,655   493,773,839   122,881,185  83 Linux
/dev/sda4         362,297,880   370,892,654     8,594,775  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   488,388,607   488,386,560   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1059 MB, 1059061760 bytes
2 heads, 1 sectors/track, 1034240 cylinders, total 2068480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *          1,504     2,068,479     2,066,976   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9089b565-b0e0-4cc4-90ad-638c858cadce   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        ffe89327-eeef-4dc5-a606-39a3b002eca8   ext3                                     
/dev/sda4                                               swap                                     
/dev/sda5                                               swap                                     
/dev/sda6        7FD7779504AF72F2                       ntfs       windows backup                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E2BCCD2FBCCCFED3                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        96E1-059F                              vfat       PENDRIVE                      
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9089b565-b0e0-4cc4-90ad-638c858cadce ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9089b565-b0e0-4cc4-90ad-638c858cadce ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9089b565-b0e0-4cc4-90ad-638c858cadce
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda3) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda3) -- recovery mode (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.31-14-generic (/dev/sda3) (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 9, 2.6.31-14-generic (/dev/sda3) -- recovery mode (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9089b565-b0e0-4cc4-90ad-638c858cadce /               ext3    errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   9.1GB: boot/grub/core.img
   9.1GB: boot/grub/grub.cfg
   9.1GB: boot/initrd.img-2.6.35-22-generic
   9.2GB: boot/vmlinuz-2.6.35-22-generic
   9.1GB: initrd.img
   9.2GB: vmlinuz

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda3)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda3) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.31-14-generic (/dev/sda3)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 9, 2.6.31-14-generic (/dev/sda3) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe89327-eeef-4dc5-a606-39a3b002eca8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=ffe89327-eeef-4dc5-a606-39a3b002eca8 /               ext3    errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/sda5       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 229.8GB: boot/grub/core.img
 229.9GB: boot/grub/grub.cfg
 229.9GB: boot/initrd.img-2.6.31-14-generic
 230.0GB: boot/initrd.img-2.6.32-21-generic
 229.9GB: boot/vmlinuz-2.6.31-14-generic
 230.0GB: boot/vmlinuz-2.6.32-21-generic
 230.0GB: initrd.img
 230.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```I thought I had gotten rid of that old grub remnant

ignore G, that's a flash drive that I'm having difficulty turning into a boot drive (working on fixing that)

also, sda6 is *going* to be my backup partition until I can get an external hard drive. Ironically my attempt to create a backup partition is what created this problem (I deleted what USED to be my backup partition and expanded the normal partition and created an NTFS partition on my other drive)

---

### Post by drs305 on 2010-11-17
The menuentry for your Windows in your sda1 Grub menu is:

> 
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    [COLOR="Red"]drivemap -s (hd0) ${root}[/COLOR]
    chainloader +1
}

Disclaimer: I don't use Windows. I believe the problem is the drivemap line. It isn't really needed and I've read a few times that later versions of Windows don't like it (or being on sdb). I can't attest to either of those though.

We can see if this is what is causing the problem:
You can get rid of the drivemap line temporarily to test if this is the problem. Open /boot/grub/grub.cfg as root, delete the line, save the file and reboot. In this case, DO NOT run update-grub before rebooting.
```
gksu gedit /boot/grub/grub.cfg
```



Let us know if it now boots. I'll have more to post after the test.

---

### Post by razor180 on 2010-11-17
it didn't work

---

### Post by drs305 on 2010-11-17
Ok. You might check the device.map file in /boot/grub/ to see if it is correct. If it isn't, you can manually change it or run:

```
sudo grub-mkdevicemap
```
If it was incorrect, that might fix it.

The other thing you could try would be to switch cables so Windows is on sda, but I'm going to have to leave this to the Windows experts. If you switch cables, read the 'lilo' section below first.  I've read that Windows gets upset if it was originally on one drive and then the designation changes to another; I really don't know if it makes a difference or not. *It's something you should investigate if nobody chimes in here with a solution (if it was originally installed on sda).*

Back to things I do know a bit about:

I can give you some solutions to naming the Windows menuentry if you are interested.

My suggestion is to place your Windows menu in the 40_custom folder once you find the right menuentry to get it booting. You can make the title more accurately affect what the menu item does.

If you want to use the custom menu, you can just paste the entire Windows menuentry in grub.cfg into 40_custom below the existing lines. Change the title between the quotes to anything you like. Just remove the "drivemap" line.

If you would like it to be at the top of the menu, you can name the file 06_custom and make it executable.

Another thing I noticed in RESULTS.txt:
Both your Ubuntu and Mint /etc/fstab files list two swap partitions. That really isn't necessary - one is enough (as is one swap partition, which both distros can use).

Finally, since Grub legacy is just 'hanging around' on your Windows partition and isn't doing anything, I'd put lilo (another bootloader) there. If Grub fails, all you would have to do is go into BIOS and change the boot order to make the Windows drive primary. You would have access to Windows via lilo as soon as you do that.

To put lilo in the MBR of sdb (make sure Windows is still on sdb before running this):
```

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

```

Lilo will complain a bit that it isn't fully installed - just disregard the warnings.

Sorry I can't be more help on why Windows isn't booting.

---

### Post by oldfred on 2010-11-17
Script reports the windows install as normal but changing windows partition may have made the boot sector outdated. it just may need to be updated.

If you have windows CD/DVD you need to run fixboot.

You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:

BootRec.exe /FixBoot  #updates PBR partition boot sector

Oldfred posted a lot of windows repair & links to windows sites:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

I copied the above link from drs305, as I often just post the whole thing but it is overkill in most cases.

---

### Post by razor180 on 2010-11-17
thanks, sorry for having this problem again. 

I also tried editing 40_custom earlier, but it won't let me save the file, it says I don't have permission to add, edit, or delete files in that folder (I've run into this problem before and quite frankly I find it stupid. it's an open source OS AND I'm logged into the administrative account)

alright, this is annoying. I did what you said on the windows recovery disc and I get an error message
"*The volume does not contain a recognized file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted.*"

---

### Post by David802 on 2010-11-17
I don't know a lot about the linux and GRUB side of it, but.....

I saw oldfred suggest Fixboot, but have you tried fixmbr?

Just about every boot problem I've had that didn't involve bad hardware or having accidentally deleted the wrong partition was repaired by using fixboot and fixmbr in the windows recovery console on the windows disc. (Note: You can only run fixmbr from the recovery console of the live disc.)

> fixmbr [device_name]

Its worth a shot... If you're loading GRUB but not windows I'd think that means its on the windows side and that grub is loading fine.... (I could very easily be wrong about that LOL I'm still way new to linux, but I've been fixing windows computers for years.)

GL

---

### Post by razor180 on 2010-11-18
did that (at least I think I did it right) now it says missing operating system

---

### Post by razor180 on 2010-11-18
alright, I loaded up my ubuntu live disc. The partitions are still there, I think the data is still there too (gparted is saying that there is bytes used)

This may not be the best option, but, I'm fed up with this. I'm not going to backup what I need and completely wipe my hard drives and reinstall windows 7 and create a back up then install ubuntu and do the same(windows 7, when installing on top of another windows system, will put all of the files in windows.old, and I have few files worth saving on my linux partitions)

thanks for the help anyways

---

### Post by Mark Phelps on 2010-11-18
Don't know if you did this before -- but since you have two physical drives, I recommend doing what I always do -- install each OS to its own drive, independent of the other.

After reinstalling Win7, disconnect the Win7 drive, leaving only the other drive connected.  Then, boot from the Ubuntu CD and install to this other drive.

When that's done, reconnect the Win7 drive but continue to boot from the Ubuntu drive.  Open a terminal and enter "sudo update-grub".  That SHOULD generate a new GRUB menu with entries for Win7.

This approach prevents any problems resulting from overwriting MBRS and writing boot files to the wrong partitions.  IT also leave each drive as independently bootable.

---

### Post by razor180 on 2010-11-18
yeah, that's how I had it setup before this happened

---

