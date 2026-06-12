---
title: "Win7 Will Not Boot After Upgrading From ubuntu 10.10 to 11.04"
date: 2011-08-28
forum: General Help
---

### Post by Efi Fiery on 2011-08-28
[SIZE=2]I had win7 and Ubuntu 10.10. Both booted perfectly. After upgrading to Ubuntu 11.04, Win7 no longer boots up. I tried to use the advice from several that had the same situation but their solutions did not solve my problem. 
[/SIZE]This is on my wife's Vaio laptop... [FONT=Franklin Gothic Medium]please save me.[/FONT]

```
[B]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    17,854,463    17,852,416  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     17,854,464    18,059,263       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          18,059,264   283,872,304   265,813,041   7 NTFS / exFAT / HPFS
/dev/sda4         283,873,278   488,396,799   204,523,522   5 Extended
/dev/sda5         283,873,280   482,254,847   198,381,568  83 Linux
/dev/sda6         482,256,896   488,396,799     6,139,904  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb4    *             63     2,097,151     2,097,089   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6816495D16492D7E                       ntfs       Recovery
/dev/sda2        5CAEB31EAEB2EF9E                       ntfs       System Reserved
/dev/sda3        84B2B48AB2B481EA                       ntfs       
/dev/sda5        92ca48ae-adf6-4dc1-a169-33b3141af7d1   ext4       
/dev/sda6        33737a55-6187-4a28-9c8b-25f878f03544   swap       
/dev/sdb4        2310-19D9                              vfat       Repair disc

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sdb4        /media/Repair disc       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=92ca48ae-adf6-4dc1-a169-33b3141af7d1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=92ca48ae-adf6-4dc1-a169-33b3141af7d1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92ca48ae-adf6-4dc1-a169-33b3141af7d1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92ca48ae-adf6-4dc1-a169-33b3141af7d1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 92ca48ae-adf6-4dc1-a169-33b3141af7d1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6816495D16492D7E
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5CAEB31EAEB2EF9E
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

=============================== sda5/etc/fstab: ================================

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
UUID=92ca48ae-adf6-4dc1-a169-33b3141af7d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=33737a55-6187-4a28-9c8b-25f878f03544 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 179.494529724 = 192.730783744  boot/grub/core.img                             1
 213.553215027 = 229.301018624  boot/grub/grub.cfg                             1
 137.130340576 = 147.242582016  boot/initrd.img-2.6.35-22-generic              1
 136.118412018 = 146.156032000  boot/initrd.img-2.6.38-11-generic              5
 179.493206024 = 192.729362432  boot/vmlinuz-2.6.35-22-generic                 1
 137.162418365 = 147.277025280  boot/vmlinuz-2.6.38-11-generic                 1
 136.118412018 = 146.156032000  initrd.img                                     5
 137.130340576 = 147.242582016  initrd.img.old                                 1
 137.162418365 = 147.277025280  vmlinuz                                        1
 179.493206024 = 192.729362432  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
[/B]
```

---

### Post by Mark Phelps on 2011-08-28
Did you try BOTH Win7 entries? Asking because GRUB gets confused sometimes and mislabels the Win7 entries such that they are reversed.  SO, you should try BOTH entries to confirm that neither one works.

---

### Post by oldfred on 2011-08-28
Boot script looks normal to me. Vista entries often were reversed. Your entries do seem to match labels as sda1 is the Vendor recovery and sda2 is windows boot/repair 100MB partition with your main install in sda3.

Some have tried hitting f8 as soon as they hit enter on the grub menu for Windows. As it is real quick sometime multiple tries are required. That may then get you into windows repair console and you can try chkdsk or other repairs. But it seems to be a windows issue.

---

### Post by Efi Fiery on 2011-08-29
Thanks for your quick reply! it is very much appreciated O:)

Sorry I cant reply right away. I just came back to life after getting strangled by the wife.

I  am an absolute beginner. I've been in the darkness of Micro$oft  machines all my life. Its like The Matrix movie. Now I see the light...  :)

I apologize, I should have posted this under 'Absolute Beginner'.

I've tried the F8 suggestion but no luck.

How will I be able to swap the Win7 entries?

:confused:
thanks

---

### Post by oldfred on 2011-08-29
YOu can use grub customizer or manually update grub entries.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Efi Fiery on 2011-08-31
Thanks oldfred.
The laptop is no longer in my hands.

The partition for vaio restore was used to fix it.
Backed up all the files.

It wiped out ubuntu. Cleaned out grub.

Its back in window$ 7.

the wife is not ready for ubuntu.

maybe one day.

---

### Post by oldfred on 2011-08-31
With my wife I had a long term plan. First converted to Thunderbird, then converted to Firefox. Picasa was a bit bigger issue as the Windows version had more than the Linux version, but I found I could just install the Windows version of Picasa in wine & with a few tweaks it works just as well. She had a few games she liked, but she tolerated the default Solitaire and others in Ubuntu. I am having touble with the new gui in 11.04 and 11.10, so I know that will not work.:)

---

