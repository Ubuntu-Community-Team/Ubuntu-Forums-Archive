---
title: "Dual boot problem Ubuntu 11.04 - Windows 7"
date: 2011-06-30
forum: General Help
---

### Post by kold92 on 2011-06-30
Hey mates! I've got an HP G-61 laptop with Windows 7 Home Edition. Today I needed to install Ubuntu 11.04.

I created an bootable pen, installed and everything was alright by then.

When I rebooted, this message showed up on my display:

> Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:[INDENT]1. Insert your Windows installation disc and restart your computer.
[/INDENT][INDENT]2. Choose your language settings, and the click "Next."
[/INDENT][INDENT]3. Click "Repair your computer."
[/INDENT]If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
Status: 0xc000000f
Info: The boot selection failed because a required device is inaccessible.By then, I got the HP Recovery disc and made the *fixmbr* thing on Windows command prompt. Windows got working but then... my boot loader had gone.

I ran up the bootable pen, used a live version of Ubuntu and executed *Boot Repair*. Now, my Ubuntu is working and I have grub's bootloader, but I'm getting that error when trying to inicialize Windows.

May I have some suggestions?

Thanks!

---

### Post by drs305 on 2011-06-30
Get Windows booting. Once that is working corrrectly, reinstall Grub2 to the MBR. Do that by identifying your Ubuntu partition. For this thread, I will assume it is sd**a5**. Change as necessary. If you don't know which partition is your Linux partition, run "sudo fdisk -l" (lowercase L).


Boot the LiveCD/USB, then mount your Ubuntu partition:
```
sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```
Do not include the partition number in the second command.

Reboot. If Windows wasn't an option in the Grub menu, after rebooting into Ubuntu (without the CD), run:```

sudo update-grub
```

---

### Post by kold92 on 2011-06-30
Hey drs305, when you say "**Once that is working corrrectly, reinstall Grub2 to the MBR.**", is it doing this?

> sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**

Or is it something else?

I did that "sudo fdisk -l" and I had

sda5 - Linux
sda6 - Linux swap / Solaris

What's my partition? I guess it's sda5.

Sorry, but I'm a noob!

---

### Post by drs305 on 2011-06-30
I meant getting Windows to boot on it's own using the recovery disk as you originally did, then running those two commands. Those two commands will 'reinstall' G2 to the MBR.

Yes, your Ubuntu partition appears to be sda5, so you can run the commands as I posted them after you get Windows working.

Generally speaking, if Windows is booting via it's own bootloader and Grub 2 worked at some point, it's merely a matter of 'reintroducing' G2 to the MBR and pointing to the Ubuntu partition's grub files. That's one of the things mounting your Ubuntu partition and running grub-install does.

---

### Post by kold92 on 2011-06-30
Already did everything unless the "sudo update-grub".

When I put that command in the terminal, it starts "Generating grub.cfg ..."

But then, when everything looks going fine, it says

ls: cannot access /var/lib/os-prober/mount/boot
Boot: non existing file or directory
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
done

(i'm not sure the messages are 100% equal to that because I'm translating from portuguese).

---

### Post by drs305 on 2011-06-30
Did you run "sudo update-grub" *after* you rebooted into Ubuntu? You can't do it while running the LiveCD.

I believe you can also get that error if you have grub folders in your Windows partition. You should not have any Grub folders such as /boot/grub in your Windows partition. 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows")

If you still can't get it working, at this point it might be best just to download, extract and run the 'boot info script'. Do this from the LiveCD, and then post the contents of RESULTS.txt

The contents will show us the status of all your boot files and allow us to give you specific directions on how to get things set up.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by kold92 on 2011-06-30
I wasn't able to boot Windows. I got the same error.

Gonna do that.

---

### Post by kold92 on 2011-06-30
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

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

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   925,849,053   925,439,454   7 NTFS / exFAT / HPFS
/dev/sda3         925,849,598   950,263,807    24,414,210   5 Extended
/dev/sda5         925,849,600   941,942,783    16,093,184  83 Linux
/dev/sda6         941,944,832   950,263,807     8,318,976  82 Linux swap / Solaris
/dev/sda4         950,263,808   976,771,071    26,507,264   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8115 MB, 8115978240 bytes
199 heads, 32 sectors/track, 2489 cylinders, total 15851520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,851,519    15,851,488   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       ef504939-e7d2-7d4e-8a32-41b6c636ea9b   ext2       casper-rw
/dev/sda1        0A44B3D544B3C1AD                       ntfs       SYSTEM
/dev/sda2        2E56642A5663F0CF                       ntfs       
/dev/sda4        42DAA5A6DAA596A7                       ntfs       RECOVERY
/dev/sda5        1c05d708-be9f-42f0-a18d-abc49a3d42db   ext4       
/dev/sda6        0ec4f6e3-51fd-40c3-9589-4cbeaca9f5b5   swap       
/dev/sdb1        DA47-BCC0                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

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
search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
set locale_dir=($root)/boot/grub/locale
set lang=pt_PT
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
menuentry 'Ubuntu, com Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1c05d708-be9f-42f0-a18d-abc49a3d42db ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, com Linux 2.6.38-8-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1c05d708-be9f-42f0-a18d-abc49a3d42db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 1c05d708-be9f-42f0-a18d-abc49a3d42db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2E56642A5663F0CF
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 42DAA5A6DAA596A7
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
UUID=1c05d708-be9f-42f0-a18d-abc49a3d42db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0ec4f6e3-51fd-40c3-9589-4cbeaca9f5b5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.759014130 = 474.335129600  boot/grub/core.img                             1
 445.737430573 = 478.606921728  boot/grub/grub.cfg                             1
 447.368488312 = 480.358256640  boot/initrd.img-2.6.38-8-generic               2
 442.210269928 = 474.819661824  boot/vmlinuz-2.6.38-8-generic                  1
 447.368488312 = 480.358256640  initrd.img                                     2
 442.210269928 = 474.819661824  vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

Here is the RESULTS.txt

---

### Post by kold92 on 2011-06-30
Went to Computer and noticed I had there 3 "500 GB Hard Disk". I only have one, so, I assume these are the partitions.

One of them is called "500 GB Hard Disk: 8.2 GB Filesystem".
Other, called, "500 GB Hard Disk: 474 GB Filesystem".
The last one is called "500 GB Hard Disk: SYSTEM".

This last one has in it two folders called "boot" and "Boot". boot has grub inside, Boot has BCD.

Can this help?

---

### Post by meduffie on 2011-06-30
Well what I imagine happened is the ubuntu partition got set inactive, so just set it as the active partition, there are PLENTY of guides online showing how to do this... Just google it!

---

### Post by kold92 on 2011-06-30
Hey meduffie, now I have Ubuntu starting up, so I guess this partition is active. The problem is that when I go to the bootloader and select to initialize Windows, that erros keps happening

---

### Post by kold92 on 2011-06-30
Solved. Just gone to the partition of Windows and renamed "boot" to "Boot", and then, typed the "sudo update-grub" in terminal.

Thank you all!

---

