---
title: "setting GRUB to see more than one linux OS"
date: 2012-09-17
forum: General Help
---

### Post by rawlins02 on 2012-09-17
I've just installed an older version of Ubuntu (Hardy) on a new partition on a hard drive that previously had a dual boot Windows and Precise Penguin. Before this new install I had Windows on a primary partition, then an extended partition with logical partitions for /, /home, /usr, and swap. Precise is installed on the root of that extended. I just now used the partitioner in Hardy live cd to set a new primary partition /dev/sda3 where I installed Hardy. Now when I start the machine a newer looking (older?) GRUB appears, and there are no entries in it for Precise, just the kernels for Hardy and the Windows boot option. 

How do I set up a correct GRUB to give me the option of booting Windows, Precise or Hardy?

---

### Post by critin on 2012-09-17
> **rawlins02 said:**
> I've just installed an older version of Ubuntu (Hardy) on a new partition on a hard drive that** previously had a dual boot Windows** and Precise Penguin. Before this new install I had Windows on a primary partition, then an extended partition with logical partitions for /, /home, /usr, and swap. Precise is installed on the root of that extended. I just now used the partitioner in Hardy live cd to set a new primary partition /dev/sda3 where I installed Hardy. Now when I start the machine a newer looking (older?) GRUB appears, and there are no entries in it for Precise, just the kernels for Hardy and the Windows boot option. 

How do I set up a correct GRUB to give me the option of booting Windows, Precise or Hardy?

I always let my extended partitions take the entire  empty/unallocated space left after the first primary partition.  That way I can add and delete logical partitions as I choose.

How can the new partition be dev/sda3 if there are other partitions already on the disk?  Did you change the numbers?

Do you still have windows installed?  The description of how **it previously was** set up confuses me as to how it is** now**.

edited to add:  Download boot repair and run the info.  Paste the results here.
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rawlins02 on 2012-09-17
> **critin said:**
> I always let my extended partitions take the entire  empty/unallocated space left after the first primary partition.  That way I can add and delete logical partitions as I choose.

That was my intention. But when I tried to set the new partition type, logical was unselectable. So I clicked primary and hoped that would work.

> **critin said:**
> How can the new partition be dev/sda3 if there are other partitions already on the disk?  Did you change the numbers? 

 sda1 is the Windows primary and sda2 is the linux primary containing the logical partitions containing Precise (/) and /home and /usr

> **critin said:**
> Do you still have windows installed?  The description of how **it previously was** set up confuses me as to how it is** now**.

Yes, sda1 and sda2 appear unchanged after my installation of Hardy to sda3.

> **critin said:**
> 
edited to add:  Download boot repair and run the info.  Paste the results here.
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

Please confirm this is needed before I proceed. Thanks.

---

### Post by rawlins02 on 2012-09-17
> **critin said:**
> Download boot repair and run the info.  Paste the results here.
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

```

   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    45,223,919    45,223,857   7 NTFS / exFAT / HPFS
/dev/sda2          45,239,040   304,994,024   259,754,985   5 Extended
/dev/sda5          45,239,103    68,661,809    23,422,707  83 Linux
/dev/sda6          68,661,873   273,747,599   205,085,727  83 Linux
/dev/sda7         273,747,663   293,282,639    19,534,977  83 Linux
/dev/sda8         293,282,703   304,994,024    11,711,322  82 Linux swap / Solaris
/dev/sda3         304,994,025   312,576,704     7,582,680  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4058CDF058CDE52E                       ntfs       Preload
/dev/sda3        5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b   ext3       
/dev/sda5        bb7d1d88-0139-4319-86d3-bdd3ec70018b   ext4       
/dev/sda6        6da7978d-81c3-4629-b25a-e977eb247ede   ext3       
/dev/sda7        ceca24a3-38e3-4782-8fca-7206b24cb788   ext4       
/dev/sda8        34199f98-173c-47f0-a184-a490f722d88f   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ceca24a3-38e3-4782-8fca-7206b24cb788
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
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
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=bb7d1d88-0139-4319-86d3-bdd3ec70018b ro reboot=efi  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	echo	'Loading Linux 3.2.0-30-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=bb7d1d88-0139-4319-86d3-bdd3ec70018b ro recovery nomodeset reboot=efi
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb7d1d88-0139-4319-86d3-bdd3ec70018b ro reboot=efi  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb7d1d88-0139-4319-86d3-bdd3ec70018b ro recovery nomodeset reboot=efi
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
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
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root bb7d1d88-0139-4319-86d3-bdd3ec70018b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 4058CDF058CDE52E
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
UUID=bb7d1d88-0139-4319-86d3-bdd3ec70018b /               ext4    errors=remount-ro 0       1
# /usr was on /dev/sda7 during installation
UUID=ceca24a3-38e3-4782-8fca-7206b24cb788 /usr            ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=34199f98-173c-47f0-a184-a490f722d88f none            swap    sw              0       0
# /home was on /dev/sda6 during installation
UUID=6da7978d-81c3-4629-b25a-e977eb247ede /home            ext3    defaults        0       2--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.736217022 = 31.929019904   boot/grub/core.img                             1
  29.782363415 = 31.978569216   boot/grub/grub.cfg                             1
  22.108302593 = 23.738609152   boot/initrd.img-3.2.0-29-generic-pae           1
  22.141997814 = 23.774789120   boot/initrd.img-3.2.0-30-generic-pae           2
  29.734488964 = 31.927164416   boot/vmlinuz-3.2.0-29-generic-pae              1
  21.943542004 = 23.561698816   boot/vmlinuz-3.2.0-30-generic-pae              1
  22.108302593 = 23.738609152   initrd.img.old                                 1
  21.943542004 = 23.561698816   vmlinuz                                        1
  29.734488964 = 31.927164416   vmlinuz.old                                    1

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-32-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-32-generic root=UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-32-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-32-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-32-generic root=UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b ro single
initrd		/boot/initrd.img-2.6.24-32-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=34199f98-173c-47f0-a184-a490f722d88f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 146.937199116 = 157.772616192  boot/grub/menu.lst                             1
 146.631760120 = 157.444653568  boot/grub/stage2                               2
 146.189411640 = 156.969685504  boot/initrd.img-2.6.24-26-generic              6
 145.842403889 = 156.597088768  boot/initrd.img-2.6.24-32-generic             13
 145.903988361 = 156.663214592  boot/initrd.img-2.6.24-32-generic.bak          5
 145.693535328 = 156.437242368  boot/vmlinuz-2.6.24-26-generic                 2
 145.876556873 = 156.633760256  boot/vmlinuz-2.6.24-32-generic                11
 145.842403889 = 156.597088768  initrd.img                                    13
 146.189411640 = 156.969685504  initrd.img.old                                 6
 145.876556873 = 156.633760256  vmlinuz                                       11
 145.693535328 = 156.437242368  vmlinuz.old                                    2


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-09-17__09h46 ===================
boot-repair version : 3.193-0ppa6~precise
boot-sav version : 3.193-0ppa19~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa20~precise
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 62 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
boot-repair is executed in live-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda3:Ubuntu 8.04.4 LTS (8.04):Ubuntu:linux
/dev/sda5:Ubuntu 12.04.1 LTS (12.04):Ubuntu1:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Preload" UUID="4058CDF058CDE52E" TYPE="ntfs"
/dev/sda3: UUID="5d1ed3b1-e7d4-4644-b2cb-274c9f33ce9b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="bb7d1d88-0139-4319-86d3-bdd3ec70018b" TYPE="ext4"
/dev/sda6: UUID="6da7978d-81c3-4629-b25a-e977eb247ede" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda7: UUID="ceca24a3-38e3-4782-8fca-7206b24cb788" TYPE="ext4"
/dev/sda8: UUID="34199f98-173c-47f0-a184-a490f722d88f" TYPE="swap"
/dev/sr0: LABEL="Ubuntu 12.04.1 LTS i386" TYPE="iso9660"


1 disks with OS, 3 OS : 2 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Jan 21  2010 grub.d
total 4
-rwxr-xr-x 1 root root 219 Sep 28  2007 20_memtest86+


No sda3/etc/default/grub
/mnt/boot-sav/sda3/boot/grub/menu.lst detected


=================== sda5/etc/default/grub :

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
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="reboot=efi"

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




=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug 17 22:08 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17 07:22 00_header
-rwxr-xr-x 1 root root 5522 May 17 07:07 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 07:22 10_linux
-rwxr-xr-x 1 root root 6335 May 17 07:22 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17 07:22 30_os-prober
-rwxr-xr-x 1 root root  214 May 17 07:22 40_custom
-rwxr-xr-x 1 root root   95 May 17 07:22 41_custom
-rw-r--r-- 1 root root  483 May 17 07:22 README


/usr detected in the fstab of sda5: UUID=ceca24a3-38e3-4782-8fca-7206b24cb788 (sda7)

=================== dmesg | grep EFI :
This live-session is not EFI-compatible.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	NTLDR,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	not-sepboot,	no-grubenv	grub1,	no-docgrub,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.
sda5	: sda,	not-sepboot,	grubenv-ok	nogrub,	no-docgrub,	no-update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	emptyusr,	fstab-has-goodUSR,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda5.
sda6	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.
sda7	: sda,	maybesepboot,	no-grubenv	grub2,	grub-pc,	update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	no---usr,	part-has-no-fstab,	is-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda7.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	63 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MK1652GS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  23.2GB  23.2GB  primary   ntfs            boot
2      23.2GB  156GB   133GB   extended
5      23.2GB  35.2GB  12.0GB  logical   ext4
6      35.2GB  140GB   105GB   logical   ext3
7      140GB   150GB   10.0GB  logical   ext4
8      150GB   156GB   5996MB  logical   linux-swap(v1)
3      156GB   160GB   3882MB  primary   ext3



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:msdos:ATA TOSHIBA MK1652GS;
1:32.3kB:23.2GB:23.2GB:ntfs::boot;
2:23.2GB:156GB:133GB:::;
5:23.2GB:35.2GB:12.0GB:ext4::;
6:35.2GB:140GB:105GB:ext3::;
7:140GB:150GB:10.0GB:ext4::;
8:150GB:156GB:5996MB:linux-swap(v1)::;
3:156GB:160GB:3882MB:ext3::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext3 (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda6 on /mnt/boot-sav/sda6 type ext3 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sda8 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout tpm0 uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1: WINDOWS VALUEADD Information Volume System syslevel.lgl SWTOOLS SWSHARE SUPPORT RRbackups RECYCLER Files Program Photos NTLDR NTDETECT.COM MSOCache MSDOS.SYS IO.SYS install.log Icons I386 hiberfil.sys drivez.log drivers Settings and Documents cygwin CONFIG.SYS boot-sav boot.ini AUTOEXEC.BAT 9f6c3fea75991151b1780773c64350b4 441f2edaa2370352ae9cc8013e

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1007M  100M  907M  10% /
udev           devtmpfs   999M   12K  999M   1% /dev
tmpfs          tmpfs      403M  836K  402M   1% /run
/dev/sr0       iso9660    696M  696M     0 100% /cdrom
/dev/loop0     squashfs   667M  667M     0 100% /rofs
tmpfs          tmpfs     1007M   32K 1006M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1007M   76K 1006M   1% /run/shm
/dev/sda1      fuseblk     22G   19G  3.0G  87% /mnt/boot-sav/sda1
/dev/sda3      ext3       3.6G  2.6G  849M  76% /mnt/boot-sav/sda3
/dev/sda5      ext4        12G  2.4G  8.3G  23% /mnt/boot-sav/sda5
/dev/sda6      ext3        97G   64G   29G  70% /mnt/boot-sav/sda6
/dev/sda7      ext4       9.3G  4.6G  4.3G  52% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    45223919    22611928+   7  HPFS/NTFS/exFAT
/dev/sda2        45239040   304994024   129877492+   5  Extended
/dev/sda3       304994025   312576704     3791340   83  Linux
/dev/sda5        45239103    68661809    11711353+  83  Linux
/dev/sda6        68661873   273747599   102542863+  83  Linux
/dev/sda7       273747663   293282639     9767488+  83  Linux
/dev/sda8       293282703   304994024     5855661   82  Linux swap / Solaris


Partition outside the disk detected.
=================== Final advice in case of recommended repair


The boot files of [Ubuntu 8.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages fix legacy files) and reinstall the grub2 of sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
pastebinit  packages needed
dpkg-preconfigure: unable to re-open stdin: No such file or directory
cp: cannot create regular file ` /var/log/boot-sav/log/2012-09-17__09h46boot-repair41/sources_': No such file or directory

Download as text


```

---

### Post by rawlins02 on 2012-09-17
Here's GParted's view of my hard drive partitions. If there are major drawbacks to having this second Ubuntu distro (Hardy) in /dev/sda3, please suggest how to fix. I assume it would be easy to delete that partition, fold the space back into the extended partition, and try again with a different place/setup for that distro.

---

### Post by oldfred on 2012-09-17
Only grub legacy with 9.04 was updated to work with ext4 partitions. So with grub 0.97 in the MBR and booting, it will never see the ext4 partition with 12.04. Old grub installed to partitions really well. I did that a lot and used chainloading to boot multiple installs. When you installed the old version you could have just installed to its partition and left the MBR with grub2's boot loader.

You should be able to reinstall grub2 from 12.04 and its os-prober should find the old install.

You will have to use a 12.04 liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

OR:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by rawlins02 on 2012-09-17
> **oldfred said:**
> 

You should be able to reinstall grub2 from 12.04 and its os-prober should find the old install.




Thanks oldfred.  I've looked through the grub pages you suggest. Is this the procedure to install grub2 as you suggest?

```

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

/dev/sda5 has 12.04 install. But I'm unsure what the boot directory should be. I do not have a separate boot partition. Is there a way to determine what it i,s or is it obvious to those in the know?

---

### Post by oldfred on 2012-09-17
Yes and if you do not have a separate /boot partition it is really just two lines. If older version does not work for any reason then try the newer version. If /boot partition is in the / (root), I do not think it matters which version you use. 

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=DarkRed]sudo mount /dev/sda5 /mnt[/COLOR]
[COLOR=DarkRed]sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by rawlins02 on 2012-09-17
Thanks again. Problem solved. Loaded grub now has all needed entries. :)

---

### Post by critin on 2012-09-18
Are you just trying out Hardy, partition 3?  With only 1gb of space left you won't be able to install much.  Of course you can still run it and enjoy it for awhile.

Glad you got the help you needed.

---

### Post by rawlins02 on 2012-09-18
I installed Hardy for use when generating display to external projector, a few hours each week. I have an old, unsupported ATI Radeon card that I could not get to work with the open source driver in Precise. In Hardy I installed the proprietary fglrx driver which gives me the functionality I need for the external display. I don't intend to install much in Hardy. At the moment a functioning Flash Player so I can show some animations is all that is missing.

If there was a fix (xrandr ?) to display issues within Precise, I could not identify it.

Interestingly, I see no issues with the function of Unity, display, resolution, etc in Precise when using just the laptop screen.

---

### Post by oldfred on 2012-09-18
Best to start new thread on the video out issue. 

I have not had to manually edit a /etc/X11/xorg.conf for ages, but you might want to compare the old version and your new one (if one). I thought they were doing away with xorg.conf, but I think it still is used for some things?

---

