---
title: "help with boot-repair"
date: 2012-04-14
forum: General Help
---

### Post by glilly on 2012-04-14
I'm trying to set up my system to dual boot Ubuntu and Windows, and have got to a state where all it will do is boot to grub. I ran Ubuntu from CD and tried boot-repair, and got these results. It still won't boot. What should I do next?

thanks
gpl

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /BOOTMGR /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
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
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    37,750,783    37,748,736  27 Hidden NTFS (Recovery Environment)
/dev/sda2          37,750,784    37,955,583       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          37,955,584 1,020,917,759   982,962,176   7 NTFS / exFAT / HPFS
/dev/sda4       1,020,919,806 3,907,028,991 2,886,109,186   5 Extended
/dev/sda5       2,044,921,856 3,907,028,991 1,862,107,136   7 NTFS / exFAT / HPFS
/dev/sda6       1,020,919,808 1,977,951,057   957,031,250  83 Linux
/dev/sda7       1,997,481,984 2,044,913,663    47,431,680  82 Linux swap / Solaris
/dev/sda8    *  1,977,954,304 1,997,479,935    19,525,632  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7098EC0698EBC8A4                       ntfs       PQSERVICE
/dev/sda2        5CE6ECFFE6ECDA72                       ntfs       SYSTEM RESERVED
/dev/sda3        3C9EF48B9EF43EC8                       ntfs       Acer
/dev/sda5        2E25AF9B11DFE529                       ntfs       data
/dev/sda6        69693419-f288-4aea-8a99-a7418f5a529d   ext2       
/dev/sda7        3420ebcc-8a09-4e67-972c-19ff40baf42a   swap       
/dev/sda8        755e65e4-9755-4fcf-9e5d-1ee514b338dc   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /                        ext2       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 69693419-f288-4aea-8a99-a7418f5a529d
if loadfont  ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 69693419-f288-4aea-8a99-a7418f5a529d
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 69693419-f288-4aea-8a99-a7418f5a529d
	linux16	
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 69693419-f288-4aea-8a99-a7418f5a529d
	linux16	 console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 7098EC0698EBC8A4
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5CE6ECFFE6ECDA72
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 3C9EF48B9EF43EC8
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             0

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-04-15__00h03 ===================
boot-repair version : 3.16-0ppa28~oneiric
boot-sav version : 3.17-0ppa46~oneiric
glade2script version : 0.3.2.1-0ppa7~oneiric
internet: connected
boot-repair is executed in live-session (Ubuntu 11.10 , oneiric , Ubuntu , x86_64)

=================== OSPROBER:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda3:Windows Recovery Environment (loader):Windows2:chain

=================== BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="PQSERVICE" UUID="7098EC0698EBC8A4" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="5CE6ECFFE6ECDA72" TYPE="ntfs"
/dev/sda3: LABEL="Acer" UUID="3C9EF48B9EF43EC8" TYPE="ntfs"
/dev/sda5: LABEL="data" UUID="2E25AF9B11DFE529" TYPE="ntfs"
/dev/sda6: UUID="69693419-f288-4aea-8a99-a7418f5a529d" TYPE="ext2"
/dev/sda7: UUID="3420ebcc-8a09-4e67-972c-19ff40baf42a" TYPE="swap"
/dev/sda8: UUID="755e65e4-9755-4fcf-9e5d-1ee514b338dc" TYPE="ext4"


1 disks with OS, 3 OS : 0 Linux, 0 MacOS, 3 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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




=================== PARTITIONS & DISKS:
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, not-on-GPT-disk, no-fstab, no-ntldr, no-winload, recovery-or-hidden, BOOTMGR, no-grldr, BOOT/BCD.
sda2 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, with-os, not-on-GPT-disk, no-fstab, no-ntldr, no-winload, no-recov-nor-hid, bootmgr, no-grldr, Boot/BCD.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, not-on-GPT-disk, no-fstab, no-ntldr, winload, no-recov-nor-hid, BOOTMGR, no-grldr, Boot/BCD.
sda5 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda5, no-os, not-on-GPT-disk, no-fstab, no-ntldr, no-winload, no-recov-nor-hid, no-bootmgr, no-grldr, no-BCD.
sda6 : sda, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /, with-os, not-on-GPT-disk, fstab-without-efi, no-ntldr, no-winload, no-recov-nor-hid, no-bootmgr, no-grldr, no-BCD.
sda8 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda8, no-os, not-on-GPT-disk, no-fstab, no-ntldr, no-winload, no-recov-nor-hid, no-bootmgr, no-grldr, no-BCD.

sda : MSDos, not-GPT, BIOSboot-not-needed, no-EFI, 2048 sectors * 512 bytes

=================== PARTED:

Model: ATA WDC WD20EARX-22P (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  19.3GB  19.3GB  primary   ntfs            diag
2      19.3GB  19.4GB  105MB   primary   ntfs
3      19.4GB  523GB   503GB   primary   ntfs
4      523GB   2000GB  1478GB  extended
6      523GB   1013GB  490GB   logical   ext2
8      1013GB  1023GB  9997MB  logical   ext4            boot
7      1023GB  1047GB  24.3GB  logical   linux-swap(v1)
5      1047GB  2000GB  953GB   logical   ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== MOUNT:
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
/dev/sda6 on / type ext2 (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sdb sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
/dev/mapper:  control

=================== DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    3.9G  107M  3.8G   3% /
udev      devtmpfs    3.9G   12K  3.9G   1% /dev
tmpfs        tmpfs    1.6G  876K  1.6G   1% /run
/dev/sr0   iso9660    698M  698M     0 100% /cdrom
/dev/loop0
squashfs    663M  663M     0 100% /rofs
tmpfs        tmpfs    3.9G   32K  3.9G   1% /tmp
none         tmpfs    5.0M  4.0K  5.0M   1% /run/lock
none         tmpfs    3.9G  164K  3.9G   1% /run/shm
/dev/sda6     ext2    3.9G  107M  3.8G   3% /
/dev/sda1  fuseblk     18G   12G  6.3G  66% /mnt/boot-sav/sda1
/dev/sda2  fuseblk    100M   26M   75M  26% /mnt/boot-sav/sda2
/dev/sda3  fuseblk    469G  125G  345G  27% /mnt/boot-sav/sda3
/dev/sda5  fuseblk    888G  114M  888G   1% /mnt/boot-sav/sda5
/dev/sda8     ext4    9.2G  149M  8.6G   2% /mnt/boot-sav/sda8

=================== FDISK:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc217ca67

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    37750783    18874368   27  Hidden NTFS WinRE
/dev/sda2        37750784    37955583      102400    7  HPFS/NTFS/exFAT
/dev/sda3        37955584  1020917759   491481088    7  HPFS/NTFS/exFAT
/dev/sda4      1020919806  3907028991  1443054593    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      2044921856  3907028991   931053568    7  HPFS/NTFS/exFAT
/dev/sda6      1020919808  1977951057   478515625   83  Linux
/dev/sda7      1997481984  2044913663    23715840   82  Linux swap / Solaris
/dev/sda8   *  1977954304  1997479935     9762816   83  Linux

Partition table entries are not in disk order



=================== Before mainwindow
FSCK no PASTEBIN yes WUBI  WINBOOT no
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sda6, PART_TO_REINSTALL_GRUB_PURGE sda6, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: connected

=================== Actions
FSCK no PASTEBIN yes WUBI  WINBOOT no
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sda6, PART_TO_REINSTALL_GRUB_PURGE sda6, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda sda3)
Unhide GRUB boot menu in sda6/etc/default/grub
Reinstall the GRUB of sda6 into the MBR of sda
dpkg --configure -a sda6
grub-install (GRUB) 1.99-12ubuntu5
chroot: failed to run command `type': No such file or directory
INSTALLOUTPUT: Installation finished. No error reported.
INSTALLEXIT:0
Generating grub.cfg ...
Found memtest86+ image:
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg
internet: connected
pastebinit  packages needed
internet: connected
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Package 'pastebinit' has no installation candidate

---

