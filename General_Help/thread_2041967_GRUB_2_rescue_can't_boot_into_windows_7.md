---
title: "GRUB 2 rescue can't boot into windows 7"
date: 2012-08-13
forum: General Help
---

### Post by patw on 2012-08-13
I tried to delete old ubuntu on dual-boot via win7 to get more win space (partition had non-ajacent NTFS free disk partitions and woldn't allow me to move in either gparted or win) and reinstalled ubuntu with alongside windows selected. I left about 1/2 NTFS and 1/2 ext3 before reinstalling ubuntu. Somehow it seemed to make all sda1 and sda2 to NTFS.
Now I have grub rescue and it is fubar.

I got this info from boot-repair and use SSD drive 128Gig as primary which had dual WIn7/ubuntu 11.04 boot and J: 1T is for data storage only.

Any help is greatly appreciated! Tried boot-repair default but it asked if 128G SSD was detacheable (I said no) and kept saying grub 2 was still installed and it would not overwrite.

I have no win install disk, it was preinstalled on HP>

Log from boot -repair:
--------------------------------
```


    

   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   162,339,391   162,132,544   7 NTFS / exFAT / HPFS
/dev/sda3         162,340,862   250,068,991    87,728,130   5 Extended
/dev/sda5         162,340,864   216,553,471    54,212,608  83 Linux
/dev/sda6         216,555,520   250,068,991    33,513,472  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,871,874,047 1,871,872,000   7 NTFS / exFAT / HPFS
/dev/sdb2       1,917,685,760 1,953,521,663    35,835,904   7 NTFS / exFAT / HPFS
/dev/sdb3       1,871,876,094 1,917,683,711    45,807,618   5 Extended
/dev/sdb5       1,871,876,096 1,917,683,711    45,807,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        901459AA14599456                       ntfs       SYSTEM
/dev/sda2        1034FE1434FDFD12                       ntfs       OS
/dev/sda5        ded7b77f-439b-464f-bff1-70335793a0b2   ext4       
/dev/sda6        b381988d-2cd0-4aa2-825c-2339d3cc1289   swap       
/dev/sdb1        5210A59E10A58995                       ntfs       DataDrive
/dev/sdb2        281CED651CED2E8E                       ntfs       HP_RECOVERY
/dev/sdb5        9224694e-d6c2-4968-ad1e-361ebf8f6f6e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ded7b77f-439b-464f-bff1-70335793a0b2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/DataDrive         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ded7b77f-439b-464f-bff1-70335793a0b2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ded7b77f-439b-464f-bff1-70335793a0b2 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 901459AA14599456
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 281CED651CED2E8E
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ded7b77f-439b-464f-bff1-70335793a0b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b381988d-2cd0-4aa2-825c-2339d3cc1289 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 101.615489960 = 109.108801536  boot/grub/grub.cfg                             1
  83.074218750 = 89.200263168   boot/initrd.img-3.0.0-12-generic               2
  98.231060028 = 105.474797568  boot/vmlinuz-3.0.0-12-generic                  1
  83.074218750 = 89.200263168   initrd.img                                     2
  98.231060028 = 105.474797568  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-13__21h49 ===================
boot-repair version : 3.18-0ppa46~oneiric
boot-sav version : 3.192-0ppa4~oneiric
glade2script version : 0.3.2.1-0ppa7~oneiric
boot-sav-nonfree version : 3.18-0ppa12~oneiric
boot-repair is executed in live-session (Ubuntu 11.10, oneiric, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda5:Ubuntu 11.10 (11.10):Ubuntu:linux
/dev/sdb2:Windows Recovery Environment (loader):Windows2:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="901459AA14599456" TYPE="ntfs"
/dev/sda2: LABEL="OS" UUID="1034FE1434FDFD12" TYPE="ntfs"
/dev/sda5: UUID="ded7b77f-439b-464f-bff1-70335793a0b2" TYPE="ext4"
/dev/sda6: UUID="b381988d-2cd0-4aa2-825c-2339d3cc1289" TYPE="swap"
/dev/sdb1: LABEL="DataDrive" UUID="5210A59E10A58995" TYPE="ntfs"
/dev/sdb2: LABEL="HP_RECOVERY" UUID="281CED651CED2E8E" TYPE="ntfs"
/dev/sdb5: UUID="9224694e-d6c2-4968-ad1e-361ebf8f6f6e" TYPE="swap"


2 disks with OS, 4 OS : 1 Linux, 0 MacOS, 3 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /media/ded7b77f-439b-464f-bff1-70335793a0b2/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440
``` 1"

---

### Post by oldfred on 2012-08-13
It looks like you grub did not reinstall as the grub in the MBR is trying to boot from sda3 which is now the extended partition.

Boot-Repair should be able to correctly install grub2's boot loader to the MBR of sda. If it will not overwrite it post any details.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Once booted into Ubuntu run this:

sudo update-grub

You need to have a repairCD or liveCD/usb for the current version of every operating system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Manual ways to reinstall the grub2 boot loader. But Boot-Repair has worked for just about everyone, so we need to know errors if it is not working. Did you change any BIOS settings that would lock MBR. Some BIOS do have settings to prevent overwriting MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by patw on 2012-08-13
Thank You,
I did not save link, but entire boot-repair text is enclosed in blocks below (ran from live CD).
No changes were set in BIOS.
I tried the default repair, but as mentioned earlier:
1) It asked if 128G drive was detachable. My reply was no (as it is the primary
Solid State Drive-- sda1 I believe with both OS on it Win7/Ubuntu 11.04 and sdab=J: which is only data files).
2) It requested to overwrite grub2, to which I said Yes (as the default) to which it kept replying, grub is still active and made no changes before closing.

I can re-run if you need link and I'm in the process of trying supergrub, which says:
Booting 'Super Grub Disk'

usbshift 
configfile (cd)/boot/sgd/sgd.lst
Error 25: Disk read error
Press any key to continue:

It only shows SuperGrub Disk as OS choice
update: restarted machine and mbr & win were successful from supergrub--
so I can manually get to win via supergrub repair disk, but doesn't solve grub problem yet...

update 2: supergrub fixed windows boot .. I could just use from here and reformat or reinstall ubuntu maybe.. no more multiple OS choice on bootup.
But not sure why installation messed up with pre-windows installed. I selected install alongside windows from liveCD and that is where the problems started.
Should I maybe delete extra drive partition and reformat to ext3 and just re-run live cd alongside windows again? Or is there better solution.

Also, if I do make changes as suggested in boot-repair (like make Ubuntu partition near start of disk)... I still desire to have windows boot first as that was a hassle before, because I used windows most of the time and had to manually select on each bootup. I also don't feel too comfortable risking etching out area where windows is now successfully working and stable to make space for ubuntu in front of it.


    ```


   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   162,339,391   162,132,544   7 NTFS / exFAT / HPFS
/dev/sda3         162,340,862   250,068,991    87,728,130   5 Extended
/dev/sda5         162,340,864   216,553,471    54,212,608  83 Linux
/dev/sda6         216,555,520   250,068,991    33,513,472  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,871,874,047 1,871,872,000   7 NTFS / exFAT / HPFS
/dev/sdb2       1,917,685,760 1,953,521,663    35,835,904   7 NTFS / exFAT / HPFS
/dev/sdb3       1,871,876,094 1,917,683,711    45,807,618   5 Extended
/dev/sdb5       1,871,876,096 1,917,683,711    45,807,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        901459AA14599456                       ntfs       SYSTEM
/dev/sda2        1034FE1434FDFD12                       ntfs       OS
/dev/sda5        ded7b77f-439b-464f-bff1-70335793a0b2   ext4       
/dev/sda6        b381988d-2cd0-4aa2-825c-2339d3cc1289   swap       
/dev/sdb1        5210A59E10A58995                       ntfs       DataDrive
/dev/sdb2        281CED651CED2E8E                       ntfs       HP_RECOVERY
/dev/sdb5        9224694e-d6c2-4968-ad1e-361ebf8f6f6e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ded7b77f-439b-464f-bff1-70335793a0b2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/DataDrive         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ded7b77f-439b-464f-bff1-70335793a0b2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ded7b77f-439b-464f-bff1-70335793a0b2 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ded7b77f-439b-464f-bff1-70335793a0b2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 901459AA14599456
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 281CED651CED2E8E
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ded7b77f-439b-464f-bff1-70335793a0b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b381988d-2cd0-4aa2-825c-2339d3cc1289 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 101.615489960 = 109.108801536  boot/grub/grub.cfg                             1
  83.074218750 = 89.200263168   boot/initrd.img-3.0.0-12-generic               2
  98.231060028 = 105.474797568  boot/vmlinuz-3.0.0-12-generic                  1
  83.074218750 = 89.200263168   initrd.img                                     2
  98.231060028 = 105.474797568  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-13__21h49 ===================
boot-repair version : 3.18-0ppa46~oneiric
boot-sav version : 3.192-0ppa4~oneiric
glade2script version : 0.3.2.1-0ppa7~oneiric
boot-sav-nonfree version : 3.18-0ppa12~oneiric
boot-repair is executed in live-session (Ubuntu 11.10, oneiric, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda5:Ubuntu 11.10 (11.10):Ubuntu:linux
/dev/sdb2:Windows Recovery Environment (loader):Windows2:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="901459AA14599456" TYPE="ntfs"
/dev/sda2: LABEL="OS" UUID="1034FE1434FDFD12" TYPE="ntfs"
/dev/sda5: UUID="ded7b77f-439b-464f-bff1-70335793a0b2" TYPE="ext4"
/dev/sda6: UUID="b381988d-2cd0-4aa2-825c-2339d3cc1289" TYPE="swap"
/dev/sdb1: LABEL="DataDrive" UUID="5210A59E10A58995" TYPE="ntfs"
/dev/sdb2: LABEL="HP_RECOVERY" UUID="281CED651CED2E8E" TYPE="ntfs"
/dev/sdb5: UUID="9224694e-d6c2-4968-ad1e-361ebf8f6f6e" TYPE="swap"


2 disks with OS, 4 OS : 1 Linux, 0 MacOS, 3 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /media/ded7b77f-439b-464f-bff1-70335793a0b2/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /media/ded7b77f-439b-464f-bff1-70335793a0b2/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 2011-10-12 14:29 grub.d
total 56
-rwxr-xr-x 1 root root 6698 2011-10-01 12:40 00_header
-rwxr-xr-x 1 root root 5522 2011-10-01 12:19 05_debian_theme
-rwxr-xr-x 1 root root 7269 2011-10-01 12:40 10_linux
-rwxr-xr-x 1 root root 6344 2011-10-01 12:40 20_linux_xen
-rwxr-xr-x 1 root root 1588 2011-05-02 23:07 20_memtest86+
-rwxr-xr-x 1 root root 7545 2011-10-01 12:40 30_os-prober
-rwxr-xr-x 1 root root  214 2011-10-01 12:40 40_custom
-rwxr-xr-x 1 root root   95 2011-10-01 12:40 41_custom
-rw-r--r-- 1 root root  483 2011-10-01 12:40 README




=================== dmesg | grep EFI :
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
[    0.000000] EFI v2.10 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000077000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000077000-0x0000000000078000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000078000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000056d000) (4MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000056d000-0x0000000001000000) (10MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] EFI: mem07: type=4, attr=0xf, range=[0x0000000001100000-0x000000000151a000) (4MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[0x000000000151a000-0x000000000151e000) (0MB)
[    0.000000] EFI: mem09: type=4, attr=0xf, range=[0x000000000151e000-0x000000000154c000) (0MB)
[    0.000000] EFI: mem10: type=3, attr=0xf, range=[0x000000000154c000-0x000000000154f000) (0MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x000000000154f000-0x0000000001554000) (0MB)
[    0.000000] EFI: mem12: type=3, attr=0xf, range=[0x0000000001554000-0x000000000155d000) (0MB)
[    0.000000] EFI: mem13: type=4, attr=0xf, range=[0x000000000155d000-0x000000000155f000) (0MB)
[    0.000000] EFI: mem14: type=3, attr=0xf, range=[0x000000000155f000-0x0000000001562000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x0000000001562000-0x0000000001571000) (0MB)
[    0.000000] EFI: mem16: type=3, attr=0xf, range=[0x0000000001571000-0x0000000001573000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x0000000001573000-0x0000000001589000) (0MB)
[    0.000000] EFI: mem18: type=3, attr=0xf, range=[0x0000000001589000-0x0000000001595000) (0MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x0000000001595000-0x00000000015ad000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x00000000015ad000-0x00000000015af000) (0MB)
[    0.000000] EFI: mem21: type=4, attr=0xf, range=[0x00000000015af000-0x00000000015b1000) (0MB)
[    0.000000] EFI: mem22: type=3, attr=0xf, range=[0x00000000015b1000-0x00000000015bc000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x00000000015bc000-0x00000000015ca000) (0MB)
[    0.000000] EFI: mem24: type=3, attr=0xf, range=[0x00000000015ca000-0x00000000015d1000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x00000000015d1000-0x00000000015e9000) (0MB)
[    0.000000] EFI: mem26: type=3, attr=0xf, range=[0x00000000015e9000-0x00000000015ec000) (0MB)
[    0.000000] EFI: mem27: type=4, attr=0xf, range=[0x00000000015ec000-0x00000000015f5000) (0MB)
[    0.000000] EFI: mem28: type=3, attr=0xf, range=[0x00000000015f5000-0x000000000160b000) (0MB)
[    0.000000] EFI: mem29: type=4, attr=0xf, range=[0x000000000160b000-0x000000000160e000) (0MB)
[    0.000000] EFI: mem30: type=3, attr=0xf, range=[0x000000000160e000-0x0000000001617000) (0MB)
[    0.000000] EFI: mem31: type=4, attr=0xf, range=[0x0000000001617000-0x000000000161d000) (0MB)
[    0.000000] EFI: mem32: type=3, attr=0xf, range=[0x000000000161d000-0x0000000001620000) (0MB)
[    0.000000] EFI: mem33: type=4, attr=0xf, range=[0x0000000001620000-0x0000000001628000) (0MB)
[    0.000000] EFI: mem34: type=3, attr=0xf, range=[0x0000000001628000-0x000000000162d000) (0MB)
[    0.000000] EFI: mem35: type=4, attr=0xf, range=[0x000000000162d000-0x0000000001644000) (0MB)
[    0.000000] EFI: mem36: type=3, attr=0xf, range=[0x0000000001644000-0x0000000001652000) (0MB)
[    0.000000] EFI: mem37: type=4, attr=0xf, range=[0x0000000001652000-0x0000000001653000) (0MB)
[    0.000000] EFI: mem38: type=3, attr=0xf, range=[0x0000000001653000-0x0000000001659000) (0MB)
[    0.000000] EFI: mem39: type=4, attr=0xf, range=[0x0000000001659000-0x000000000165f000) (0MB)
[    0.000000] EFI: mem40: type=3, attr=0xf, range=[0x000000000165f000-0x0000000001665000) (0MB)
[    0.000000] EFI: mem41: type=4, attr=0xf, range=[0x0000000001665000-0x000000000166a000) (0MB)
[    0.000000] EFI: mem42: type=3, attr=0xf, range=[0x000000000166a000-0x000000000167f000) (0MB)
[    0.000000] EFI: mem43: type=4, attr=0xf, range=[0x000000000167f000-0x0000000001685000) (0MB)
[    0.000000] EFI: mem44: type=3, attr=0xf, range=[0x0000000001685000-0x000000000168c000) (0MB)
[    0.000000] EFI: mem45: type=4, attr=0xf, range=[0x000000000168c000-0x000000000168f000) (0MB)
[    0.000000] EFI: mem46: type=3, attr=0xf, range=[0x000000000168f000-0x00000000016a0000) (0MB)
[    0.000000] EFI: mem47: type=4, attr=0xf, range=[0x00000000016a0000-0x00000000016a8000) (0MB)
[    0.000000] EFI: mem48: type=3, attr=0xf, range=[0x00000000016a8000-0x00000000016a9000) (0MB)
[    0.000000] EFI: mem49: type=4, attr=0xf, range=[0x00000000016a9000-0x00000000016ab000) (0MB)
[    0.000000] EFI: mem50: type=3, attr=0xf, range=[0x00000000016ab000-0x00000000016ae000) (0MB)
[    0.000000] EFI: mem51: type=4, attr=0xf, range=[0x00000000016ae000-0x00000000016b3000) (0MB)
[    0.000000] EFI: mem52: type=3, attr=0xf, range=[0x00000000016b3000-0x00000000016b8000) (0MB)
[    0.000000] EFI: mem53: type=4, attr=0xf, range=[0x00000000016b8000-0x000000000173d000) (0MB)
[    0.000000] EFI: mem54: type=3, attr=0xf, range=[0x000000000173d000-0x000000000174b000) (0MB)
[    0.000000] EFI: mem55: type=4, attr=0xf, range=[0x000000000174b000-0x0000000001756000) (0MB)
[    0.000000] EFI: mem56: type=3, attr=0xf, range=[0x0000000001756000-0x0000000001757000) (0MB)
[    0.000000] EFI: mem57: type=4, attr=0xf, range=[0x0000000001757000-0x000000000175a000) (0MB)
[    0.000000] EFI: mem58: type=3, attr=0xf, range=[0x000000000175a000-0x000000000175c000) (0MB)
[    0.000000] EFI: mem59: type=4, attr=0xf, range=[0x000000000175c000-0x0000000001760000) (0MB)
[    0.000000] EFI: mem60: type=3, attr=0xf, range=[0x0000000001760000-0x0000000001762000) (0MB)
[    0.000000] EFI: mem61: type=4, attr=0xf, range=[0x0000000001762000-0x0000000001c2e000) (4MB)
[    0.000000] EFI: mem62: type=3, attr=0xf, range=[0x0000000001c2e000-0x0000000001c34000) (0MB)
[    0.000000] EFI: mem63: type=4, attr=0xf, range=[0x0000000001c34000-0x0000000001c3c000) (0MB)
[    0.000000] EFI: mem64: type=3, attr=0xf, range=[0x0000000001c3c000-0x0000000001c41000) (0MB)
[    0.000000] EFI: mem65: type=4, attr=0xf, range=[0x0000000001c41000-0x0000000001c5a000) (0MB)
[    0.000000] EFI: mem66: type=3, attr=0xf, range=[0x0000000001c5a000-0x0000000001ca9000) (0MB)
[    0.000000] EFI: mem67: type=4, attr=0xf, range=[0x0000000001ca9000-0x0000000001cc5000) (0MB)
[    0.000000] EFI: mem68: type=3, attr=0xf, range=[0x0000000001cc5000-0x0000000001ccd000) (0MB)
[    0.000000] EFI: mem69: type=4, attr=0xf, range=[0x0000000001ccd000-0x0000000001cd3000) (0MB)
[    0.000000] EFI: mem70: type=3, attr=0xf, range=[0x0000000001cd3000-0x0000000001cd6000) (0MB)
[    0.000000] EFI: mem71: type=4, attr=0xf, range=[0x0000000001cd6000-0x0000000001d31000) (0MB)
[    0.000000] EFI: mem72: type=3, attr=0xf, range=[0x0000000001d31000-0x0000000001d3a000) (0MB)
[    0.000000] EFI: mem73: type=4, attr=0xf, range=[0x0000000001d3a000-0x0000000001d42000) (0MB)
[    0.000000] EFI: mem74: type=3, attr=0xf, range=[0x0000000001d42000-0x0000000001d46000) (0MB)
[    0.000000] EFI: mem75: type=4, attr=0xf, range=[0x0000000001d46000-0x0000000001d4b000) (0MB)
[    0.000000] EFI: mem76: type=3, attr=0xf, range=[0x0000000001d4b000-0x0000000001d4d000) (0MB)
[    0.000000] EFI: mem77: type=4, attr=0xf, range=[0x0000000001d4d000-0x0000000001d50000) (0MB)
[    0.000000] EFI: mem78: type=3, attr=0xf, range=[0x0000000001d50000-0x0000000001d55000) (0MB)
[    0.000000] EFI: mem79: type=4, attr=0xf, range=[0x0000000001d55000-0x0000000001d58000) (0MB)
[    0.000000] EFI: mem80: type=3, attr=0xf, range=[0x0000000001d58000-0x0000000001d5d000) (0MB)
[    0.000000] EFI: mem81: type=4, attr=0xf, range=[0x0000000001d5d000-0x0000000001d65000) (0MB)
[    0.000000] EFI: mem82: type=3, attr=0xf, range=[0x0000000001d65000-0x0000000001d69000) (0MB)
[    0.000000] EFI: mem83: type=4, attr=0xf, range=[0x0000000001d69000-0x0000000001d76000) (0MB)
[    0.000000] EFI: mem84: type=3, attr=0xf, range=[0x0000000001d76000-0x0000000001d7c000) (0MB)
[    0.000000] EFI: mem85: type=4, attr=0xf, range=[0x0000000001d7c000-0x0000000001d7d000) (0MB)
[    0.000000] EFI: mem86: type=3, attr=0xf, range=[0x0000000001d7d000-0x0000000001d80000) (0MB)
[    0.000000] EFI: mem87: type=4, attr=0xf, range=[0x0000000001d80000-0x0000000001d93000) (0MB)
[    0.000000] EFI: mem88: type=3, attr=0xf, range=[0x0000000001d93000-0x0000000001d95000) (0MB)
[    0.000000] EFI: mem89: type=4, attr=0xf, range=[0x0000000001d95000-0x0000000001d96000) (0MB)
[    0.000000] EFI: mem90: type=3, attr=0xf, range=[0x0000000001d96000-0x0000000001da1000) (0MB)
[    0.000000] EFI: mem91: type=4, attr=0xf, range=[0x0000000001da1000-0x0000000001da5000) (0MB)
[    0.000000] EFI: mem92: type=3, attr=0xf, range=[0x0000000001da5000-0x0000000001da7000) (0MB)
[    0.000000] EFI: mem93: type=4, attr=0xf, range=[0x0000000001da7000-0x0000000001dad000) (0MB)
[    0.000000] EFI: mem94: type=3, attr=0xf, range=[0x0000000001dad000-0x0000000001db2000) (0MB)
[    0.000000] EFI: mem95: type=4, attr=0xf, range=[0x0000000001db2000-0x0000000001dc7000) (0MB)
[    0.000000] EFI: mem96: type=3, attr=0xf, range=[0x0000000001dc7000-0x0000000001dcb000) (0MB)
[    0.000000] EFI: mem97: type=4, attr=0xf, range=[0x0000000001dcb000-0x0000000001dcd000) (0MB)
[    0.000000] EFI: mem98: type=3, attr=0xf, range=[0x0000000001dcd000-0x0000000001ddb000) (0MB)
[    0.000000] EFI: mem99: type=4, attr=0xf, range=[0x0000000001ddb000-0x0000000001ddd000) (0MB)
[    0.000000] EFI: mem100: type=3, attr=0xf, range=[0x0000000001ddd000-0x0000000001de0000) (0MB)
[    0.000000] EFI: mem101: type=4, attr=0xf, range=[0x0000000001de0000-0x0000000001df4000) (0MB)
[    0.000000] EFI: mem102: type=3, attr=0xf, range=[0x0000000001df4000-0x0000000001df6000) (0MB)
[    0.000000] EFI: mem103: type=4, attr=0xf, range=[0x0000000001df6000-0x0000000001e04000) (0MB)
[    0.000000] EFI: mem104: type=3, attr=0xf, range=[0x0000000001e04000-0x0000000001e14000) (0MB)
[    0.000000] EFI: mem105: type=4, attr=0xf, range=[0x0000000001e14000-0x0000000001eb2000) (0MB)
[    0.000000] EFI: mem106: type=3, attr=0xf, range=[0x0000000001eb2000-0x0000000001ebf000) (0MB)
[    0.000000] EFI: mem107: type=4, attr=0xf, range=[0x0000000001ebf000-0x0000000001f1c000) (0MB)
[    0.000000] EFI: mem108: type=7, attr=0xf, range=[0x0000000001f1c000-0x0000000001f8f000) (0MB)
[    0.000000] EFI: mem109: type=1, attr=0xf, range=[0x0000000001f8f000-0x0000000002005000) (0MB)
[    0.000000] EFI: mem110: type=7, attr=0xf, range=[0x0000000002005000-0x0000000002014000) (0MB)
[    0.000000] EFI: mem111: type=4, attr=0xf, range=[0x0000000002014000-0x0000000002018000) (0MB)
[    0.000000] EFI: mem112: type=7, attr=0xf, range=[0x0000000002018000-0x0000000002027000) (0MB)
[    0.000000] EFI: mem113: type=4, attr=0xf, range=[0x0000000002027000-0x00000000023d0000) (3MB)
[    0.000000] EFI: mem114: type=7, attr=0xf, range=[0x00000000023d0000-0x000000000270b000) (3MB)
[    0.000000] EFI: mem115: type=4, attr=0xf, range=[0x000000000270b000-0x0000000002a0c000) (3MB)
[    0.000000] EFI: mem116: type=7, attr=0xf, range=[0x0000000002a0c000-0x000000003642a000) (826MB)
[    0.000000] EFI: mem117: type=2, attr=0xf, range=[0x000000003642a000-0x000000003720d000) (13MB)
[    0.000000] EFI: mem118: type=7, attr=0xf, range=[0x000000003720d000-0x000000008fa5d000) (1416MB)
[    0.000000] EFI: mem119: type=2, attr=0xf, range=[0x000000008fa5d000-0x00000000bf0ba000) (758MB)
[    0.000000] EFI: mem120: type=10, attr=0xf, range=[0x00000000bf0ba000-0x00000000bf10f000) (0MB)
[    0.000000] EFI: mem121: type=6, attr=0x800000000000000f, range=[0x00000000bf10f000-0x00000000bf112000) (0MB)
[    0.000000] EFI: mem122: type=0, attr=0xf, range=[0x00000000bf112000-0x00000000bf346000) (2MB)
[    0.000000] EFI: mem123: type=5, attr=0x800000000000000f, range=[0x00000000bf346000-0x00000000bf347000) (0MB)
[    0.000000] EFI: mem124: type=0, attr=0xf, range=[0x00000000bf347000-0x00000000bf359000) (0MB)
[    0.000000] EFI: mem125: type=5, attr=0x800000000000000f, range=[0x00000000bf359000-0x00000000bf35a000) (0MB)
[    0.000000] EFI: mem126: type=6, attr=0x800000000000000f, range=[0x00000000bf35a000-0x00000000bf35c000) (0MB)
[    0.000000] EFI: mem127: type=7, attr=0xf, range=[0x00000000bf35c000-0x00000000bf35e000) (0MB)
[    0.000000] EFI: mem128: type=0, attr=0xf, range=[0x00000000bf35e000-0x00000000bf35f000) (0MB)
[    0.000000] EFI: mem129: type=10, attr=0xf, range=[0x00000000bf35f000-0x00000000bf369000) (0MB)
[    0.000000] EFI: mem130: type=5, attr=0x800000000000000f, range=[0x00000000bf369000-0x00000000bf36c000) (0MB)
[    0.000000] EFI: mem131: type=6, attr=0x800000000000000f, range=[0x00000000bf36c000-0x00000000bf3b1000) (0MB)
[    0.000000] EFI: mem132: type=5, attr=0x800000000000000f, range=[0x00000000bf3b1000-0x00000000bf3bf000) (0MB)
[    0.000000] EFI: mem133: type=6, attr=0x800000000000000f, range=[0x00000000bf3bf000-0x00000000bf3c2000) (0MB)
[    0.000000] EFI: mem134: type=10, attr=0xf, range=[0x00000000bf3c2000-0x00000000bf405000) (0MB)
[    0.000000] EFI: mem135: type=3, attr=0xf, range=[0x00000000bf405000-0x00000000bf7e8000) (3MB)
[    0.000000] EFI: mem136: type=4, attr=0xf, range=[0x00000000bf7e8000-0x00000000bf7ef000) (0MB)
[    0.000000] EFI: mem137: type=3, attr=0xf, range=[0x00000000bf7ef000-0x00000000bf800000) (0MB)
[    0.000000] EFI: mem138: type=7, attr=0xf, range=[0x0000000100000000-0x000000043f800000) (13304MB)
[    0.000000] EFI: mem139: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] EFI: mem140: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    3.295296] fb0: EFI VGA frame buffer device
[    4.120343] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/ded7b77f-439b-464f-bff1-70335793a0b2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/DataDrive.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    no-grldr,    boot/bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    2048 sectors * 512 bytes
sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    2048 sectors * 512 bytes

=================== parted -l:

Model: ATA PLEXTOR PX-128M3 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  106MB   105MB   primary   ntfs            boot
2      106MB   83.1GB  83.0GB  primary   ntfs
3      83.1GB  128GB   44.9GB  extended
5      83.1GB  111GB   27.8GB  logical   ext4
6      111GB   128GB   17.2GB  logical   linux-swap(v1)


Model: ATA ST31000524AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  958GB   958GB   primary   ntfs            boot
3      958GB   982GB   23.5GB  extended
5      958GB   982GB   23.5GB  logical   linux-swap(v1)
2      982GB   1000GB  18.3GB  primary   ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/DataDrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /media/ded7b77f-439b-464f-bff1-70335793a0b2 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw10 hidraw11 hidraw12 hidraw13 hidraw14 hidraw15 hidraw2 hidraw3 hidraw4 hidraw5 hidraw6 hidraw7 hidraw8 hidraw9 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sdb2 sdb3 sdb5 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda2: Windows Users Information Volume System SYSTEM.SAV SWSETUP $RECYCLE.BIN Recovery Python27 (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys OS newpart Folder New MSOCache Intel hp hiberfil.sys Settings and Documents BOOTSECT.BAK boot-sav bootmgr Boot

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    7.9G  237M  7.7G   3% /
udev      devtmpfs    7.9G   12K  7.9G   1% /dev
tmpfs        tmpfs    3.2G  1.0M  3.2G   1% /run
/dev/sr0   iso9660    698M  698M     0 100% /cdrom
/dev/loop0
squashfs    663M  663M     0 100% /rofs
tmpfs        tmpfs    7.9G  628K  7.9G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    7.9G  100K  7.9G   1% /run/shm
/dev/sdb1  fuseblk    893G   12G  882G   2% /media/DataDrive
/dev/sda5     ext4     26G  2.8G   22G  12% /media/ded7b77f-439b-464f-bff1-70335793a0b2
/dev/sda1  fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2  fuseblk     78G   60G   18G  78% /mnt/boot-sav/sda2
/dev/sdb2  fuseblk     18G   15G  2.2G  88% /mnt/boot-sav/sdb2

=================== fdisk -l:

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c9eb1f4

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   162339391    81066272    7  HPFS/NTFS/exFAT
/dev/sda3       162340862   250068991    43864065    5  Extended
/dev/sda5       162340864   216553471    27106304   83  Linux
/dev/sda6       216555520   250068991    16756736   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0dfd733c

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1871874047   935936000    7  HPFS/NTFS/exFAT
/dev/sdb2      1917685760  1953521663    17917952    7  HPFS/NTFS/exFAT
/dev/sdb3      1871876094  1917683711    22903809    5  Extended
/dev/sdb5      1871876096  1917683711    22903808   82  Linux swap / Solaris

Partition table entries are not in disk order


User choice: Is sda (128GB) a removable disk? no
Partition outside the disk detected.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda (128GB) disk!


The boot files of [Ubuntu 11.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
```Download as text

---

### Post by oldfred on 2012-08-13
Boot-Repair mentions your liveCD was in UEFI/efi mode. Both Windows & Ubuntu offer to boot from the UEFI system menu in UEFI mode or BIOS mode. But both systems must be installed in the same mode.

Windows is installed in BIOS/MBR mode as you do not have the efi partition as the first partition and partitions are MBR not gpt.

But if you boot Ubuntu in efi mode it will try to install grub-efi into the first partition which should be an error. Try again but boot liveCD/USB in BIOS mode not efi mode. Then Boot-Repair should work.

If you decide to reinstall do not use side by side again as it will leave old Linux install and try to shrink something and just add another new install. Either delete existing partitions and install into free space or use Something Else or manual install and choose the same partitions for / as ext4 format and it should find swap. If you had a separate /home you would choose it, but DO NOT format it.

Arch suggests using gpt for SSDs. But Windows 7 will only boot from gpt partitioned drives if you have a UEFI enabled system.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by patw on 2012-08-13
I'm not really sure how to set everything to EFI modes vs BIOS/MBR, etc..
Those options don't really show up in the installation process. Since windows seems happy, I think I'll run for a while with old partitions (allocated to ext4/linux) just wiped  out and non-formatted. And if I build up the courage (I seemed to have a lot of problems with dual boot and SSD from the getco-- see old forum I posted on display drivers nightmare)..
I will just use liveCD booted as 1st device from BIOS and install ubuntu on the newly formatted partitions. In order to not leave this issue floating, I'll call it resolved.

If anyone else arrives here from fubar land... SuperGrub was a godsend.

@oldfred: thanks for fast response. It's very comforting to get that when we our tearing out our hair with debugging panics.

---

### Post by oldfred on 2012-08-13
If you are using the 64bit installer not the 32bit installer, you should get two choices. One will be UEFI/efi and the other BIOS/legacy/AHCI or whatever your UEFI calls the non-efi version. Which ever way you boot the liveCD/USB will be the way it installs.

---

### Post by YannBuntu on 2012-08-16
Hello

If you hadn't changed your BIOS settings before, don't touch them.

I think the problem comes from the initial move of Ubuntu: when you expanded Windows, Ubuntu was moved far from the start of the disk (currently its partition ends at 115GB from the start of the disk).
If I were you, I would either make the Ubuntu partition fit inside the first 100GB of the disk, OR create a separate /boot partition that fits inside the first 100GB of the disk.
See [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk) and [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887)

Remark: when asked if 128G drive is detachable you can reply no.

---

