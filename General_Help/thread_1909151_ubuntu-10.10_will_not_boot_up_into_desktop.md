---
title: "ubuntu-10.10 will not boot up into desktop"
date: 2012-01-14
forum: General Help
---

### Post by dragonfly41 on 2012-01-14
I need a refresher course .. I've not been using ubuntu-10.10 for a few months.

I have dual boot configuration.   GRUB menu.
Vista in one partition
Ubuntu-10.10 installed in two separate partitions "/" and "/home" in an extended partition.

Having been working on Vista for some months I returned to boot into ubuntu-10.10 but it would not startup into desktop.   The "/" root partition was too full (nearly 10 GB) and preventing startup.

I've just gone through the exercise of resizing and moving the two ext4 partitions (using GParted in ubuntu Live CD) to release more disk space for "/" root partition (/dev/sda7) .. but I still can't get ubuntu to startup .. it just shows ubuntu loading on the screen and does not get to launch desktop.  I've tried two separate kernels listed in GRUB menu.

What terminal commands can I use when in Live CD to restore ubuntu-10.10 installed in /dev/sda7 and /dev/sda8 ext4 partitions to working order to launch into desktop?

Or should I reinstall "/" root partition only from Live CD?
  

The CD's I keep to hand for troubleshooting include:
Live CD ubuntu-10.10
Live CD GParted
PartedMagic
Boot Repair

and ext2explore in Vista to view ext4 files from Vista (but can't delete files using ext2explore)

---

### Post by bluexrider on 2012-01-14
Why would the "/root partition" grow unless Windows has been using it for spawning junk?

You have probably have tried the other methods of recovery. 
Sounds like you keep a arsenal of disks on hand, so, I would dare say since your "/home partition" is elsewhere I would freshen the install from the live cd.

---

### Post by dragonfly41 on 2012-01-15
I can rule out the possibility of Windows Vista spawning junk in ubuntu ext4 partitions.

Windows Vista doesn't even recognise the ext4 partitions (other than when I use ext2explore when in Vista to view ubuntu files).   

The growing in size of  root partition in /dev/sda7 was probably due to growing logs,.. or other such files.

This is no longer an issue since using GParted I've rebalanced the space in root and home partitions and there is now plenty of spare space in root and home partitions.

Since I have had this problem  before (ubuntu hanging at splash) I would prefer to troubleshoot the reason for ubuntu not launching into desktop rather than blindly reinstalling ubuntu-10.10.

The boot-repair disk in my arsenal didn't help much since this message came up ... >  please enable a repository for the [grub-pc] package in your software sources. then try again.No changes were made by bootrepair to the boot configuration since I had no such repository.

Since I'm currently running ubuntu in Live CD I've tried a few tests and here they are ..

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          25      200781   de  Dell Utility
/dev/sda2              26        1331    10485760    7  HPFS/NTFS
/dev/sda3   *        1331       14079   102400000    7  HPFS/NTFS
/dev/sda4           14079       30402   131109888    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6           14079       23701    77288448    7  HPFS/NTFS
[COLOR=Red]/dev/sda7           23701       27526    30716928   83  Linux
/dev/sda8           27526       30075    20480000   83  Linux[/COLOR]

Partition table entries are not in disk order


```Root and home partitions are in /dev/sda7 and /dev/sda8/   (see red above)

and finally running bootinfoscript .. a rather larger dump ...

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    [COLOR=Red]File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda7 and looks at sector 394076416 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 7 for (,msdos7)/boot/grub.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img[/COLOR]

sda8: __________________________________________________________________________

    [COLOR=Red]File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:     [/COLOR]   

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2             403,456    21,374,975    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,374,976   226,174,975   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda4         226,174,976   488,394,751   262,219,776   f W95 Extended (LBA)
/dev/sda5         483,153,920   488,394,751     5,240,832  dd Dell Media Direct
/dev/sda6         226,177,024   380,753,919   154,576,896   7 NTFS / exFAT / HPFS
/dev/sda7         380,755,968   442,189,823    61,433,856  83 Linux
/dev/sda8         442,191,872   483,151,871    40,960,000  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D8-0508                              vfat       DellUtility
/dev/sda2        5204ADEB04ADD271                       ntfs       RECOVERY
/dev/sda3        3EAF0046AEFFF3ED                       ntfs       Vista
/dev/sda5        72B4-788D                              vfat       MEDIADIRECT
/dev/sda6        742F97AC1BA01137                       ntfs       internal_data
/dev/sda7        8eeb2f0d-92c7-463e-8961-3a1241fc148a   ext4       
/dev/sda8        13f48ffa-cafb-48cd-aa6a-6d3acf4e69ee   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8eeb2f0d-92c7-463e-8961-3a1241fc148a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-30-generic
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 10.10, kernel 2.6.35-30-generic (recovery mode)
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro  single
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 10.10, kernel 2.6.35-28-generic
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro  single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        8eeb2f0d-92c7-463e-8961-3a1241fc148a
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8eeb2f0d-92c7-463e-8961-3a1241fc148a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 3eaf0046aefff3ed
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 72b4-788d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 1f80d5cb-b065-4444-a2e2-07559f7651ee
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1f80d5cb-b065-4444-a2e2-07559f7651ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 1f80d5cb-b065-4444-a2e2-07559f7651ee
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1f80d5cb-b065-4444-a2e2-07559f7651ee ro single
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
proc /proc proc nodev,noexec,nosuid 0 0
UUID=8eeb2f0d-92c7-463e-8961-3a1241fc148a / ext4 errors=remount-ro 0 1
UUID=13f48ffa-cafb-48cd-aa6a-6d3acf4e69ee /home ext4 defaults 0 2
UUID=5204ADEB04ADD271 /media/RECOVERY ntfs-3g defaults,locale=en_GB.UTF-8 0 0
UUID=3EAF0046AEFFF3ED /media/Vista ntfs-3g defaults,locale=en_GB.UTF-8 0 0
UUID=17E557D8547203F0 /media/external_data ntfs-3g defaults,nosuid,nodev,locale=en_GB.UTF-8 0 0
UUID=742F97AC1BA01137 /media/internal_data ntfs-3g defaults,locale=en_GB.UTF-8 0 0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 187.910301208 = 201.767149568  boot/grub/core.img                             1
 188.281921387 = 202.166173696  boot/grub/grub.cfg                             1
 184.791763306 = 198.418644992  boot/grub/menu.lst                             1
 191.316062927 = 205.424058368  boot/initrd.img-2.6.35-22-generic              2
 191.210674286 = 205.310898176  boot/initrd.img-2.6.35-28-generic              2
 185.169887543 = 198.824652800  boot/initrd.img-2.6.35-30-generic              4
 188.205627441 = 202.084253696  boot/vmlinuz-2.6.35-22-generic                 1
 188.338882446 = 202.227335168  boot/vmlinuz-2.6.35-28-generic                 1
 190.827720642 = 204.899704832  boot/vmlinuz-2.6.35-30-generic                38
 185.169887543 = 198.824652800  initrd.img                                     4
 191.210674286 = 205.310898176  initrd.img.old                                 2
 190.827720642 = 204.899704832  vmlinuz                                       38
 188.338882446 = 202.227335168  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  74 20 63 6f 6d 2e 63 61  75 63 68 6f 2e 75 74 69  |t com.caucho.uti|
00000010  6c 2e 41 6c 61 72 6d 2e  65 78 74 72 61 63 74 41  |l.Alarm.extractA|
00000020  6c 61 72 6d 28 41 6c 61  72 6d 2e 6a 61 76 61 3a  |larm(Alarm.java:|
00000030  34 37 39 29 0d 0a 09 61  74 20 63 6f 6d 2e 63 61  |479)...at com.ca|
00000040  75 63 68 6f 2e 75 74 69  6c 2e 41 6c 61 72 6d 24  |ucho.util.Alarm$|
00000050  43 6f 6f 72 64 69 6e 61  74 6f 72 54 68 72 65 61  |CoordinatorThrea|
00000060  64 2e 72 75 6e 28 41 6c  61 72 6d 2e 6a 61 76 61  |d.run(Alarm.java|
00000070  3a 37 34 36 29 0d 0a 30  32 2d 46 65 62 2d 32 30  |:746)..02-Feb-20|
00000080  31 30 20 32 30 3a 35 32  3a 34 32 20 63 6f 6d 2e  |10 20:52:42 com.|
00000090  63 61 75 63 68 6f 2e 75  74 69 6c 2e 41 6c 61 72  |caucho.util.Alar|
000000a0  6d 24 43 6f 6f 72 64 69  6e 61 74 6f 72 54 68 72  |m$CoordinatorThr|
000000b0  65 61 64 20 72 75 6e 0d  0a 57 41 52 4e 49 4e 47  |ead run..WARNING|
000000c0  3a 20 6a 61 76 61 2e 6c  61 6e 67 2e 4e 75 6c 6c  |: java.lang.Null|
000000d0  50 6f 69 6e 74 65 72 45  78 63 65 70 74 69 6f 6e  |PointerException|
000000e0  0d 0a 6a 61 76 61 2e 6c  61 6e 67 2e 4e 75 6c 6c  |..java.lang.Null|
000000f0  50 6f 69 6e 74 65 72 45  78 63 65 70 74 69 6f 6e  |PointerException|
00000100  0d 0a 09 61 74 20 63 6f  6d 2e 63 61 75 63 68 6f  |...at com.caucho|
00000110  2e 75 74 69 6c 2e 41 6c  61 72 6d 2e 65 78 74 72  |.util.Alarm.extr|
00000120  61 63 74 41 6c 61 72 6d  28 41 6c 61 72 6d 2e 6a  |actAlarm(Alarm.j|
00000130  61 76 61 3a 34 37 39 29  0d 0a 09 61 74 20 63 6f  |ava:479)...at co|
00000140  6d 2e 63 61 75 63 68 6f  2e 75 74 69 6c 2e 41 6c  |m.caucho.util.Al|
00000150  61 72 6d 24 43 6f 6f 72  64 69 6e 61 74 6f 72 54  |arm$CoordinatorT|
00000160  68 72 65 61 64 2e 72 75  6e 28 41 6c 61 72 6d 2e  |hread.run(Alarm.|
00000170  6a 61 76 61 3a 37 34 36  29 0d 0a 30 32 2d 46 65  |java:746)..02-Fe|
00000180  62 2d 32 30 31 30 20 32  30 3a 35 32 3a 34 32 20  |b-2010 20:52:42 |
00000190  63 6f 6d 2e 63 61 75 63  68 6f 2e 75 74 69 6c 2e  |com.caucho.util.|
000001a0  41 6c 61 72 6d 24 43 6f  6f 72 64 69 6e 61 74 6f  |Alarm$Coordinato|
000001b0  72 54 68 72 65 61 64 20  72 75 6e 0d 0a 57 00 fe  |rThread run..W..|
000001c0  ff ff dd fe ff ff 00 30  51 0f 00 f8 4f 00 00 fe  |.......0Q...O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 ff af 36 09 00 00  |............6...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 22 18  |.X.MSDOS5.0...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 cc 1c  |........?....X..|
00000020  00 f8 4f 00 ef 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 8d 78 b4 72 44  65 6c 6c 4d 44 33 70 6c  |..).x.rDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200





```

---

### Post by dragonfly41 on 2012-01-16
Not getting very far trying to recover .. 

To recap

/           partition is  /dev/sda7
/home  partition is  /dev/sda8

Reading a few forum threads and one here with separate root and home partitions ..

[http://ubuntuforums.org/showthread.php?t=1907249](http://ubuntuforums.org/showthread.php?t=1907249)

[COLOR=Blue]*Unless I have misunderstood the above thread I had not realised that from Live CD I can launch into an internal Ubuntu installation by using sudo chroot /mnt.    See post 13.   Is this correct?*[/COLOR]

I tried this from Live CD ..

```

sudo mount    /dev/sda7    /mnt
sudo mount --bind   /dev   /mnt/dev
sudo mount --bind   /proc  /mnt/proc
sudo mount --bind   /sys   /mnt/sys

sudo chroot   /mnt


```but got this error message and could not proceed:

```

/bin/bash: error while loading shared libraries: libdl.so.2:  cannot open shared object file: No such file or directory.

```So why can't I chroot into ubuntu in /dev/sda7?
Do I have the correct commands?
Perhaps I also have to mount /dev/sda8 which is the /home partition?

Any suggestions for chroot into the internal Ubuntu ?

...

I could just reinstall .. but as I have said I prefer to understand where this configuration has gone wrong and how to quickly correct .. particularly when server is eventually deployed.

...
[COLOR=Navy]
[/COLOR][COLOR=Navy][EDIT]

Keeping the post count down I'm adding this postscript.

I've got round the above error by loading library (after reading a thread discussing same error)

To load library ..

```

sudo apt-get install libc6 libc6-dev

```

and then

```

locate  libdl.so.2

found in lib/libdl.so.2

```

and then I added this line to the bindings above ..

```

 sudo mount --bind /lib      /mnt/lib

returning no errors .. but ..
root@ubuntu:/#

 
```

Now the question is where do I go from here to get into  /dev/sda7 and /dev/sda8  ??

```

root@ubuntu:/# sudo blkid
sudo: unable to resolve host ubuntu

```

Or is this all a red herring and it would be better to reinstall?[/COLOR]

---

### Post by dragonfly41 on 2012-01-16
I may have to **repair** ubuntu from Live CD since I still can't boot up into desktop.   Still stuck in splash loading and not launching into desktop.

If I now **repair** ubuntu (in two separate partitions .. root and home)
I understand that the **/home** partition must not be formatted (otherwise all data is lost).

[http://sazeit.com/articles/manually-select-partitions-ubuntu](http://sazeit.com/articles/manually-select-partitions-ubuntu)

But can the **/root** partition also be installed without formatting?

Or should the /root partition be formatted?

The reason for the question is that I seem to have extra programs and data installed in /root partition (in /dev/sda7) which I do not want to lose or reinstall (short of cloning the partitions using clonezilla).  

So .. if I don't format /root partition will the core ubuntu files be overwritten?

I can see all files in Nautilus (Live CD) when I mount /dev/sda7 and /dev/sda8.   (root and home respectively).

---

### Post by dragonfly41 on 2012-01-18
I've failed to track down why I can't launch into desktop (ubuntu stuck at splash).

So I've backed up key files and I'm about to reinstall ubuntu 10.10 into root and home partitions.

I got as far as this ..

changing partitions ...

/dev/sda7    ext4     /               no format
/dev/sda8    ext4    /home       no format

but then comes the boot loader !
Device for boot loader installation

There is a drop down menu giving various devices to select for the boot loader

/dev/sda                        this is highlighted by default in the installation process
/dev/sda1
/dev/sda2
/dev/sda3    Windows Vista loader                       (Vista partition which works)
/dev/sda6                                                                         
[COLOR=Red]/dev/sda7    Ubuntu 10.10 (10.10)                        this root partition has previously worked
/dev/sda8[/COLOR] [COLOR=Red]                                                             this home partition has previously worked[/COLOR]
/dev/sda4    Microsoft Windows XP Embedded    (Vista recovery partition - unused)

The partition usage is shown in the boot info script which I posted earlier.

My one question before installing to repair (no formatting)

[COLOR=Navy][B]Should I select /dev/sda as boot loader destination 
or select /dev/sda7  ?[/B][/COLOR]

Once I'm quite sure that I should select [COLOR=Navy]**/dev/sda7 **[/COLOR]as boot loader device I'll go ahead and repair existing ubuntu installation.

---

### Post by dragonfly41 on 2012-01-18
Well I couldn't wait around any longer for an answer .. so I chose /dev/sda7 as the target device for the boot loader in my ubuntu repair/reinstall from Live CD.

This repair added another kernel into the GRUB menu (there are now three ubuntu kernels plus the Vista boot).

Selecting this new kernel listed in dual boot menu I was back in business again with ubuntu-10.10 going into desktop.

At first look it seems that my user files are preserved and firefox bookmarks etc..  
Not sure yet if all applications are preserved since at first test localhost does not connect .. localhost:8080.   And the splash style is smaller than usual.   Seems that a few tweaks will still be needed.

I would still like to know how to recover from a stuck splash after startup without having to go through a repair of root and home partitions.   I've had this hangup hit me a few times now and there seems to be no troubleshooting tips.

---

