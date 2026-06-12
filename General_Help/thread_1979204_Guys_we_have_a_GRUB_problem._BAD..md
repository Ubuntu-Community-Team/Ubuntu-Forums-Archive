---
title: "Guys we have a GRUB problem. BAD."
date: 2012-05-13
forum: General Help
---

### Post by pepsifx357 on 2012-05-13
I tried installing 12.04 today from a USB flash drive, via unetbootin, to a USB external hard drive.  At the end of the installation there is a fatal grub install error.  It gave me the option to try again and it acted like it was finished.  However grub did not work.  Black screen with the flashy prompt just sat there.

I tried the tutorial on the "boot-recovery" software from yannu, but it didn't work.  If I remember correctly, this is why I did not install the Beta 2 or 1 or the alpha.  Now, I'm a little confused when it comes to the correct partition for grub to be installed to.  My options were /dev/sda and /dev/sda1.  sda did not work, and sda1 came up with the same fatal error when manually installing grub from the live CD.  I tried all of the tutorials I could find on this.

I'm currently downloading another ISO copy to try again.  If this doesn't work, I will try the 64 bit ISO.  If that doesn't work, I will boot into a live environment, download the ISO and use "Startup Disk Creator" and try again.  This is really annoying, it's the key piece of software for the OS to be able to work, so why does it not simply work?

If these options do not work, I will file a bug report, or contribute to any existing bug report on this issue, unless someone knows something I don't.

---

### Post by wilee-nilee on 2012-05-13
Post the bootscript that can be generated from the boot-repair tool. Or download it, and extract it to your desktop, and run this command and post the results.txt in this thread.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by pepsifx357 on 2012-05-13
Thanks for the reply. The hard drive in question has changed from sda to sdc. sda is obviously my ssd drive.  The 3 500GB hard drive are my "dormant" linux raid that are waiting to see linux again. sdc is my external hard drive I'm trying to install to.
```

	

            Boot Info Script 0.61-git-patched      [23 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

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

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdc1 
                       and looks at sector 605175472 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......#'.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1505808 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 63.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdf1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

md/HMS: ________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848    78,161,919    77,955,072   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   615,233,535   615,231,488  83 Linux
/dev/sdc2         615,233,536   625,141,759     9,908,224  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sde _____________________________________________________________________

Disk /dev/sde: 16.1 GB, 16137584128 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31518719 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63    31,503,464    31,503,402   b W95 FAT32


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             63   976,768,064   976,768,002  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md/HMS      21f34a6f-053c-4cad-b2ed-0a44b3accff7   ext4       HMS
/dev/md127       21f34a6f-053c-4cad-b2ed-0a44b3accff7   ext4       HMS
/dev/sda1        D4001DF2001DDBF4                       ntfs       System Reserved
/dev/sda2        C26C27CD6C27BB55                       ntfs       
/dev/sdb1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS
/dev/sdc1        bd3147e7-1207-4676-89ff-208bb5d4d32b   ext4       
/dev/sdc2        609e1583-c828-4104-8c16-f6f9bfa37538   swap       
/dev/sdd1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS
/dev/sde1        BAB6-EE4F                              vfat       
/dev/sdf1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/CDROM             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root bd3147e7-1207-4676-89ff-208bb5d4d32b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root bd3147e7-1207-4676-89ff-208bb5d4d32b
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root bd3147e7-1207-4676-89ff-208bb5d4d32b
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=bd3147e7-1207-4676-89ff-208bb5d4d32b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root bd3147e7-1207-4676-89ff-208bb5d4d32b
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=bd3147e7-1207-4676-89ff-208bb5d4d32b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root D4001DF2001DDBF4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos2)'
	search --no-floppy --fs-uuid --set=root C26C27CD6C27BB55
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bd3147e7-1207-4676-89ff-208bb5d4d32b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=609e1583-c828-4104-8c16-f6f9bfa37538 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 288.570178986 = 309.849870336  boot/grub/core.img                             1
 116.152503967 = 124.717801472  boot/grub/grub.cfg                             1
   1.243164062 = 1.334837248    boot/initrd.img-3.2.0-23-generic-pae           2
 140.134029388 = 150.467768320  boot/vmlinuz-3.2.0-23-generic-pae              1
   1.243164062 = 1.334837248    initrd.img                                     2
 140.134029388 = 150.467768320  vmlinuz                                        1

============================== sde1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-05-13__05h29 ===================
boot-repair version : 3.18-0ppa12~precise
boot-sav version : 3.18-0ppa28~precise
glade2script version : 0.3.2.1-0ppa7~precise
internet: connected

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="D4001DF2001DDBF4" TYPE="ntfs"
/dev/sda2: UUID="C26C27CD6C27BB55" TYPE="ntfs"
/dev/sdb1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="7ea76d38-a0b8-1d12-469b-e2f3333447b7" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sdc1: UUID="bd3147e7-1207-4676-89ff-208bb5d4d32b" TYPE="ext4"
/dev/sdc2: UUID="609e1583-c828-4104-8c16-f6f9bfa37538" TYPE="swap"
/dev/sdd1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="0021d0c7-f40a-81cb-3fff-2e9f6fd07f7c" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sde1: UUID="BAB6-EE4F" TYPE="vfat"
/dev/sdf1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="9eb9f0a2-e649-8581-e3d0-920cb23951ed" LABEL=":HMS" TYPE="linux_raid_member"
/dev/md127: LABEL="HMS" UUID="21f34a6f-053c-4cad-b2ed-0a44b3accff7" TYPE="ext4"
/dev/md/HMS: LABEL="HMS" UUID="21f34a6f-053c-4cad-b2ed-0a44b3accff7" TYPE="ext4"
Scanning MDraid Partitions
mdadm --detail --scan: ARRAY /dev/md/HMS metadata=1.2 name=:HMS UUID=8958905f:704e6fad:0bbd660c:1f14f74a
dmraid packages needed
User refused to install dmraid
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686)
md/HMS has unknown type. Please report this message to yannubuntu@gmail.com
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
Disk /dev/md127 doesn't contain a valid partition table

=================== OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sdc1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="D4001DF2001DDBF4" TYPE="ntfs"
/dev/sda2: UUID="C26C27CD6C27BB55" TYPE="ntfs"
/dev/sdb1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="7ea76d38-a0b8-1d12-469b-e2f3333447b7" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sdc1: UUID="bd3147e7-1207-4676-89ff-208bb5d4d32b" TYPE="ext4"
/dev/sdc2: UUID="609e1583-c828-4104-8c16-f6f9bfa37538" TYPE="swap"
/dev/sdd1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="0021d0c7-f40a-81cb-3fff-2e9f6fd07f7c" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sde1: UUID="BAB6-EE4F" TYPE="vfat"
/dev/sdf1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="9eb9f0a2-e649-8581-e3d0-920cb23951ed" LABEL=":HMS" TYPE="linux_raid_member"
/dev/md127: LABEL="HMS" UUID="21f34a6f-053c-4cad-b2ed-0a44b3accff7" TYPE="ext4"
/dev/md/HMS: LABEL="HMS" UUID="21f34a6f-053c-4cad-b2ed-0a44b3accff7" TYPE="ext4"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: /dev/md127 already mounted or /mnt/boot-sav/md/HMS busy
mount: according to mtab, /dev/md127 is already mounted on /mnt/boot-sav/md/HMS


=================== /media/CDROM/etc/default/grub :

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
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sda2.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdb1.
sdc1	: sdc,	not-sepboot,	grubenv-ok	grub2,	grub-pc,	update-grub,	32,	with-boot,	is-os,	not-on-gpt-disk,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	/media/CDROM.
sdd1	: sdd,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdd1.
sdf1	: sdf,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdf1.
md127	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/md127.
md/HMS	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/md/HMS.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes
sdc	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdd	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes
sdf	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes

=================== PARTED:

Model: ATA INTEL SSDSA2M040 (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs
2      106MB   40.0GB  39.9GB  primary  ntfs         boot


Model: ATA ST500DM002-1BC14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               raid


Model: ST932032 5AS (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
1      1049kB  315GB  315GB   primary  ext4
2      315GB   320GB  5073MB  primary  linux-swap(v1)


Model: ATA ST500DM002-1BC14 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               raid


Model: SanDisk Cruzer (scsi)
Disk /dev/sde: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  16.1GB  16.1GB  primary  fat32        boot


Model: ATA ST3500320AS (scsi)
Disk /dev/sdf: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               boot, raid


Model: Linux Software RAID Array (md)
Disk /dev/md127: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  1000GB  1000GB  ext4


=================== MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sde1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/CDROM type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/md127 on /mnt/boot-sav/md127 type ext4 (rw)
/dev/md127 on /mnt/boot-sav/md/HMS type ext4 (rw)


/sys/block/md127:  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdf1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  admmidi amidi autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dmmidi dmmidi1 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg log mapper mcelog md md127 mem midi midi1 net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdc1 sdc2 sdd sdd1 sde sde1 sdf sdf1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 vga_arbiter zero
/dev/mapper:  control
Disk /dev/md127 doesn't contain a valid partition table

=================== DF:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1007M  190M  817M  19% /
udev           devtmpfs   999M   12K  999M   1% /dev
tmpfs          tmpfs      403M  908K  402M   1% /run
/dev/sde1      vfat        16G  721M   15G   5% /cdrom
/dev/loop0     squashfs   673M  673M     0 100% /rofs
tmpfs          tmpfs     1007M  648K 1006M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1007M   76K 1007M   1% /run/shm
/dev/sdc1      ext4       294G  6.8G  272G   3% /media/CDROM
/dev/sda1      fuseblk    100M   34M   67M  34% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     38G   37G  754M  99% /mnt/boot-sav/sda2
/dev/md127     ext4       931G   87G  798G  10% /mnt/boot-sav/md127
/dev/md127     ext4       931G   87G  798G  10% /mnt/boot-sav/md/HMS

=================== FDISK:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001638b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848    78161919    38977536    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033918

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000870f8

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   615233535   307615744   83  Linux
/dev/sdc2       615233536   625141759     4954112   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d00d2

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sde: 16.1 GB, 16137584128 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31518719 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066f51

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63    31503464    15751701    b  W95 FAT32

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062845

Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/md127: 1000.2 GB, 1000210104320 bytes
2 heads, 4 sectors/track, 244191920 cylinders, total 1953535360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 32768 bytes / 65536 bytes
Disk identifier: 0x00000000


User choice: Is sdc a removable disk? yes

=================== Before mainwindow
FSCK no PASTEBIN yes WUBI no WINBOOT no
recommendedrepair, reinstall, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION yes (10s), noflag (sda2)
PART_TO_REINSTALL_GRUB sdc1, FORCE_GRUB all (sdc) REMOVABLEDISK yes
USE_SEPARATEBOOTPART no (sdb1) grub2 (0, 0 , )
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )
/usr/share/boot-sav/gui-init.sh: line 57: kill: (20172) - No such process

=================== Actions
FSCK no PASTEBIN yes WUBI no WINBOOT no
bootinfo, nombraction, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION no (10s), noflag (sda2)
PART_TO_REINSTALL_GRUB sdc1, FORCE_GRUB all (sdc) REMOVABLEDISK yes
USE_SEPARATEBOOTPART no (sdb1) grub2 (0, 0 , )
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )
No change has been performed on your computer. See you soon!
internet: connected

Download as text

```

---

### Post by wilee-nilee on 2012-05-13
Personally I know nothing about raid, so lets wait and see if somebody who does, takes a look. There are regulars who will comment.

---

### Post by oldfred on 2012-05-13
I do not know RAID either other than you need the drivers, to see the RAID from a Desktop install.

But you are just installing to sdc which is another drive. You should be able to just use Boot-Repair to install grub2's boot loader to sdc. You currently have it in the partition but that will not matter and not be used if correctly installed to sdc.

From a Ubuntu liveCD you can also directly install it.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
#  The above command should work but they now suggest this command for grub 1.99 with Natty or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sdc

Change BIOS to boot from sdc or use a one time boot key (f12 on my system) to choose sdc.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here

#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

---

### Post by turbos4 on 2012-05-14
Try to fix mbr windows from ubuntu live with ms-sys, windows will just create the same issu.

#sudo su

#ms-sys -m /dev/sda

and install grub manual after then grub can write to mbr boot sect. windows.

MS-SYS
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

---

### Post by pepsifx357 on 2012-05-19
Just tried a new 32 bit install(Newly downloaded ISO, newly created bootable flash).  As soon as it gets to the grub install I get this:

```
Executing 'grub-install /dev/sda' failed.
This is a fatal error.
```

Then I get a window that says:

```
Sorry, an error occurred and it was not possible to install the bootloader at the specified location.
How would you like to proceed?
```

I get three options:

```
1. Choose a different device to install the bootloader on.
2. Continue without a bootloader(Of course not).
3. Cancel the installation.
```

So I choose number 1.  /dev/sda is the USB hard drive I'm trying to install to at this point.  I'm not touching the raid, at all, and I'm not trying any dual boot with windows, just a new installation on a usb drive.

The default option under "choose a different device..." is /dev/sda, so I clicked ok.

```
Installation has finished.  You can continue testing Ubuntu now....blah blah
```

Then, it iterrupts...

```
Executing 'grub-install /dev/sda' failed.
This is a fatal error.
```

I get the same options, this time I choose /dev/sda1 instead of /dev/sda.

```
We're sorry; the installer crashed.  After you close this window, we'll allow you to file a bug report using the integrated bug reporting tool.  This will gather information about your system and your installation process.  The details will be sent to out bug tracker and a developer will attend to the problem as soon as possible.
```

Uploaded and reported.

Now I have run "boot-repair" again using the "default," "I'll fix everything" button.  Here is my info:

```
Ubuntu Pastebin
Paste from boot-repair at Sat, 19 May 2012 11:04:27 +0000
Download as text


	

                Boot Info Script 0.61-git      [12 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sde.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......c..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1507664 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdf1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   615,233,535   615,231,488  83 Linux
/dev/sda2         615,233,536   625,141,759     9,908,224  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.1 GB, 16137584128 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31518719 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    31,503,464    31,503,402   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdd2    *        206,848    78,161,919    77,955,072   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63   976,768,064   976,768,002  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        53a3bd5b-e5fe-400f-bf04-0c0e452e3b92   ext4       
/dev/sda2        609e1583-c828-4104-8c16-f6f9bfa37538   swap       
/dev/sdb1        EAF6-DB48                              vfat       
/dev/sdc1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS
/dev/sdd1        D4001DF2001DDBF4                       ntfs       System Reserved
/dev/sdd2        C26C27CD6C27BB55                       ntfs       
/dev/sde1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS
/dev/sdf1        8958905f-704e-6fad-0bbd-660c1f14f74a   linux_raid_member :HMS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /target                  ext4       (rw,errors=remount-ro)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=53a3bd5b-e5fe-400f-bf04-0c0e452e3b92 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=53a3bd5b-e5fe-400f-bf04-0c0e452e3b92 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 53a3bd5b-e5fe-400f-bf04-0c0e452e3b92
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root D4001DF2001DDBF4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos2)'
	search --no-floppy --fs-uuid --set=root C26C27CD6C27BB55
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
# / was on /dev/sda1 during installation
UUID=53a3bd5b-e5fe-400f-bf04-0c0e452e3b92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=609e1583-c828-4104-8c16-f6f9bfa37538 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  88.144847870 = 94.644809728   boot/grub/core.img                             1
 116.144897461 = 124.709634048  boot/grub/grub.cfg                             1
   1.204101562 = 1.292894208    boot/initrd.img-3.2.0-23-generic-pae           3
 116.143657684 = 124.708302848  boot/vmlinuz-3.2.0-23-generic-pae              1
   1.204101562 = 1.292894208    initrd.img                                     3
 116.143657684 = 124.708302848  vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-05-19__06h02 ===================
boot-repair version : 3.18-0ppa16~precise
boot-sav version : 3.18-0ppa44~precise
glade2script version : 0.3.2.1-0ppa7~precise
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 160 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory

BLKID BEFORE RAID ACTIVATION:
/dev/sda1: UUID="53a3bd5b-e5fe-400f-bf04-0c0e452e3b92" TYPE="ext4"
/dev/sda2: UUID="609e1583-c828-4104-8c16-f6f9bfa37538" TYPE="swap"
/dev/sdd1: LABEL="System Reserved" UUID="D4001DF2001DDBF4" TYPE="ntfs"
/dev/sdd2: UUID="C26C27CD6C27BB55" TYPE="ntfs"
/dev/sdf1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="0021d0c7-f40a-81cb-3fff-2e9f6fd07f7c" LABEL=":HMS" TYPE="linux_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="EAF6-DB48" TYPE="vfat"
/dev/sdc1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="9eb9f0a2-e649-8581-e3d0-920cb23951ed" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sde1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="7ea76d38-a0b8-1d12-469b-e2f3333447b7" LABEL=":HMS" TYPE="linux_raid_member"
dmraid -si -c: no raid disks
No DMRAID disk.
Warning: no DMRAID nor MD_ARRAY.
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686)
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'

=================== OSPROBER:
/dev/sdd1:Windows 7 (loader):Windows:chain
/dev/sdd2:Windows 7 (loader):Windows1:chain

=================== BLKID:
/dev/sda1: UUID="53a3bd5b-e5fe-400f-bf04-0c0e452e3b92" TYPE="ext4"
/dev/sda2: UUID="609e1583-c828-4104-8c16-f6f9bfa37538" TYPE="swap"
/dev/sdd1: LABEL="System Reserved" UUID="D4001DF2001DDBF4" TYPE="ntfs"
/dev/sdd2: UUID="C26C27CD6C27BB55" TYPE="ntfs"
/dev/sdf1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="0021d0c7-f40a-81cb-3fff-2e9f6fd07f7c" LABEL=":HMS" TYPE="linux_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="EAF6-DB48" TYPE="vfat"
/dev/sdc1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="9eb9f0a2-e649-8581-e3d0-920cb23951ed" LABEL=":HMS" TYPE="linux_raid_member"
/dev/sde1: UUID="8958905f-704e-6fad-0bbd-660c1f14f74a" UUID_SUB="7ea76d38-a0b8-1d12-469b-e2f3333447b7" LABEL=":HMS" TYPE="linux_raid_member"


1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'


=================== /target/etc/default/grub :

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
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc,	update-grub,	32,	with-boot,	is-os,	not-on-gpt-disk,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	/target.
sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not-on-gpt-disk,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdd1.
sdd2	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not-on-gpt-disk,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdd2.
sdf1	: sdf,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdf1.
sdc1	: sdc,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sdc1.
sde1	: sde,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sde1.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdd	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdf	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes
sdc	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes
sde	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	63 sectors * 512 bytes

=================== PARTED:

Model: ST932032 5AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
1      1049kB  315GB  315GB   primary  ext4
2      315GB   320GB  5073MB  primary  linux-swap(v1)


Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  16.1GB  16.1GB  primary  fat32        boot, lba


Model: ATA ST3500320AS (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               boot, raid


Model: ATA INTEL SSDSA2M040 (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs
2      106MB   40.0GB  39.9GB  primary  ntfs         boot


Model: ATA ST500DM002-1BC14 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               raid


Model: ATA ST500DM002-1BC14 (scsi)
Disk /dev/sdf: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary               raid


=================== MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /target type ext4 (rw,errors=remount-ro)
/dev/sdd1 on /mnt/boot-sav/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd2 on /mnt/boot-sav/sdd2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 sdd2 size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdf1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  admmidi amidi autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dmmidi dmmidi1 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg log mapper mcelog mem midi midi1 net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdc1 sdd sdd1 sdd2 sde sde1 sdf sdf1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 vga_arbiter zero
/dev/mapper:  control

=================== DF:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1007M  140M  868M  14% /
udev           devtmpfs   999M   12K  999M   1% /dev
tmpfs          tmpfs      403M  892K  402M   1% /run
/dev/sdb1      vfat        16G  721M   15G   5% /cdrom
/dev/loop0     squashfs   673M  673M     0 100% /rofs
tmpfs          tmpfs     1007M   32K 1007M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1007M   80K 1007M   1% /run/shm
/dev/sda1      ext4       294G  6.8G  272G   3% /target
/dev/sdd1      fuseblk    100M   37M   64M  37% /mnt/boot-sav/sdd1
/dev/sdd2      fuseblk     38G   35G  2.4G  94% /mnt/boot-sav/sdd2

=================== FDISK:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000870f8

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   615233535   307615744   83  Linux
/dev/sda2       615233536   625141759     4954112   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16137584128 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31518719 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066f51

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31503464    15751701    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062845

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001638b

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdd2   *      206848    78161919    38977536    7  HPFS/NTFS/exFAT

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033918

Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d00d2

Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   976768064   488384001   fd  Linux raid autodetect


User choice: Is sda (320GB) a removable disk? yes

=================== Recommended repair
recommendedrepair
This setting will reinstall the grub2 of sda1 into the MBR of sdathe MBRs of all disks (except USB without OS).
It will also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
Additional repair will be performed: unhide-bootmenu


Unhide GRUB boot menu in sda1/etc/default/grub
sda is removable, so we reinstall GRUB of the removable media only in its disk MBR
Will restore the MBR_TO_RESTORE : sdd (mbr) into sdd
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdd
0+1 records in
0+1 records out
parted /dev/sdd set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.

Will restore the MBR_TO_RESTORE : sdf (mbr) into sdf
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdf
0+1 records in
0+1 records out
parted /dev/sdd set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.

Will restore the MBR_TO_RESTORE : sdc (mbr) into sdc
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdc
0+1 records in
0+1 records out
parted /dev/sdd set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.

Will restore the MBR_TO_RESTORE : sde (mbr) into sde
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sde
0+1 records in
0+1 records out
parted /dev/sdd set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.

Reinstall the GRUB of sda1 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3
chroot: failed to run command `type': No such file or directory
/usr/sbin/grub-setup: error: hd0 appears to contain a iso9660 filesystem which isn't known to reserve space for DOS-style boot.  Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check, use at your own risk).
grub-install --recheck /dev/sda: exit code:1
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1
Found Windows 7 (loader) on /dev/sdd2
sda1/fstab unchanged for EFI
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
mount: unknown filesystem type 'linux_raid_member'
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg
Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on the removable disk!
pastebinit  packages needed
E: Package 'pastebinit' has no installation candidate
dpkg-preconfigure: unable to re-open stdin: No such file or directory

Download as text

```

Now I am running the "boot-repair" with advanced options.  I'm reinstalling grub,location /dev/sda.  Result?  Same as above.  Still not installing grub to the hard drive.

---

### Post by pepsifx357 on 2012-05-19
> **oldfred said:**
> 
sudo grub-install --root-directory=/mnt /dev/sdc
#  The above command should work but they now suggest this command for grub 1.99 with Natty or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sdc


```
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
/usr/sbin/grub-setup: error: hd0 appears to contain a iso9660 filesystem which isn't known to reserve space for DOS-style boot.  Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check, use at your own risk).
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: hd0 appears to contain a iso9660 filesystem which isn't known to reserve space for DOS-style boot.  Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check, use at your own risk).

```

---

### Post by oldfred on 2012-05-19
It looks like you did not mount the install partiiton, so it is trying to install to the CD rom.  
#Find linux partition, change sda1 if not correct: 
sudo fdisk -l 
#confirm that linux is sda1
 [COLOR=DarkRed]sudo mount /dev/sda1 /mnt [/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda 
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.: 
sudo grub-install --boot-directory=/mnt/boot /dev/sda  

# If no errors on previous commands reboot into working system and run this: 
sudo update-grub

---

### Post by YannBuntu on 2012-05-19
Hello
I don't know what's preventing GRUB from being installed in sda's MBR, but from the log we see that :

- grub-install --recheck /dev/sda gave no error nor warning (despite it indeed could not write in the MBR)
- grub-setup /dev/sda gave this error:
```
error: hd0 appears to contain a iso9660 filesystem which isn't known to reserve space for DOS-style boot.  Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check, use at your own risk)
```

---

### Post by pepsifx357 on 2012-06-02
Sorry guys, I gave up.  I just installed 12.04 on a SSD drive.

---

