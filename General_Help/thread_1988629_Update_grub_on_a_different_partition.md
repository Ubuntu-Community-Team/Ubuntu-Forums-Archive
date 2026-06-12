---
title: "Update grub on a different partition?"
date: 2012-05-27
forum: General Help
---

### Post by Bucky Ball on 2012-05-27
Hi all,

When I boot 10.04 I get '10.04' flash up on a purple screen then just a purple screen where the login should be.

My Problem:  I have 11.04 and 10.10 installed on other partitions and from either I can get to the 10.04 partition and directories ... and /etc/default/grub. 10.04 is not generating a recovery kernel and I figure if it did I'd have a better chance of fixing this (cos for the past week I've had none).

I've discovered this section in the 10.04 /etc/default/grub file:

```
# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"
```

If I can comment that out or change it to 'false' I figure I have some chance.

My question: Of course, I can make whatever changes I like to the 10.04 grub but they won't stick because I can't update-grub. So, back to the title of the thread: How do I update the 10.04 grub while I'm booted into another install? 

All I've found is some info regarding booting a LiveCD, mounting the partition and doing it that way ... but, I have three Ubuntu installs (and Win7) on this machine so I'm confused by that. 

I already have the 10.04 partition mounted when I boot one of the other installs so figuring there must be a way of update-grub on the mounted 10.04 partition (or I could unmount and mount somewhere else if required to achieve the update-grub).

Anyone know how I can update the 10.04 grub from another partition?

---

### Post by drs305 on 2012-05-27
You can get into it's recovery mode from the Grub menu. Highlight the entry you want, press 'e', then use the cursor keys to go to the end of the 'linux' line. Backspace to remove everything up to "ro". Add "single" (no quotes) so the line ends with *ro single*, then F10 or CTRL-x to boot to the recovery mode.

---

### Post by Bucky Ball on 2012-05-27
> **drs305 said:**
> You can get into it's recovery mode from the Grub menu. Highlight the entry you want, press 'e', then use the cursor keys to go to the end of the 'linux' line. Backspace to remove everything up to "ro". Add "single" (no quotes) so the line ends with *ro single*, then F10 or CTRL-x to boot to the recovery mode.

Legend. I'll try it right now and get back to you ... thanks. ;)

PS: Find attached BootInfoScript output. I have 10.10 on sda5 (which is where MBR is looking, all good as 10.10 that is running the show), 10.04 on sda8 and 11.04 on sda9. Strange things is the 'Boot Files' details seem to be different for sda5/9 than the 10.04's sda8.

When I want to make changes in 10.04 or 11.04 I generally tweak their individual /etc/default/grub, update-grub, then boot to 10.10 and update-grub there which picks up any changes in the other two.

* Wouldn't attach for some reason so her 'tis in code bracks:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

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
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda3 and looks at sector 147279352 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048    86,960,127    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3    *     86,962,174   602,276,849   515,314,676   5 Extended
/dev/sda5          86,962,176   116,256,767    29,294,592  83 Linux
/dev/sda6         179,317,593   491,267,699   311,950,107  83 Linux
/dev/sda7         594,067,698   602,276,849     8,209,152  82 Linux swap / Solaris
/dev/sda8         116,262,468   147,155,399    30,892,932  83 Linux
/dev/sda9         147,155,463   179,317,529    32,162,067  83 Linux
/dev/sda10        491,267,763   594,067,634   102,799,872   7 NTFS / exFAT / HPFS
/dev/sda4         602,284,032   625,141,759    22,857,728  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E10BBBF10BB7C89                       ntfs       System
/dev/sda10       6B8E2F2A62CEE191                       ntfs       Misc
/dev/sda2        7060EA3E60EA0B24                       ntfs       S3A8406D004
/dev/sda4        8AD8245BD82447B1                       ntfs       HDDRECOVERY
/dev/sda5        93f00b46-2cf5-4b46-83be-f708cf831675   ext4       root
/dev/sda6        0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1   ext4       home
/dev/sda7        63d86782-bff4-41c1-924f-37d093fbe371   swap       
/dev/sda8        c597757f-1add-48e4-ba9f-5e167a5f938a   ext4       
/dev/sda9        5b20be62-a948-4693-b6c9-a8b11eb2d271   ext4       11.04

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /media/Misc              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda8        /media/c597757f-1add-48e4-ba9f-5e167a5f938a ext4       (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0,commit=0,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt  quiet splash acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	echo	'Loading Linux 2.6.38-020638-generic ...'
	linux	/boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-020638-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt  quiet splash acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 93f00b46-2cf5-4b46-83be-f708cf831675
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux /boot/vmlinuz-2.6.38-15-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (recovery mode) (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux /boot/vmlinuz-2.6.38-15-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single
	initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux /boot/vmlinuz-2.6.38-14-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux /boot/vmlinuz-2.6.38-14-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single
	initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-33-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7060EA3E60EA0B24
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=93f00b46-2cf5-4b46-83be-f708cf831675	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1	/home	ext4	defaults	0	2
#Entry for /dev/sda4 :
#UUID=8AD8245BD82447B1	/media/HDDRECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda11 :
UUID=6B8E2F2A62CEE191	/media/Misc	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda2 :
#UUID=7060EA3E60EA0B24	/media/S3A8406D004	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda1 :
#UUID=3E10BBBF10BB7C89	/media/System	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda7 :
UUID=63d86782-bff4-41c1-924f-37d093fbe371	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  49.778465271 = 53.449220096   boot/grub/core.img                             1
  50.804885864 = 54.551330816   boot/grub/grub.cfg                             2
  46.654296875 = 50.094669824   boot/initrd.img-2.6.32-020632-generic          2
  50.604312897 = 54.335967232   boot/initrd.img-2.6.35.11dazimage              1
  46.844238281 = 50.298617856   boot/initrd.img-2.6.35-22-generic              2
  46.602516174 = 50.039070720   boot/initrd.img-2.6.35-23-generic              2
  43.365234375 = 46.563065856   boot/initrd.img-2.6.35-24-generic              2
  46.970901489 = 50.434621440   boot/initrd.img-2.6.35-25-generic              2
  47.001510620 = 50.467487744   boot/initrd.img-2.6.35-27-generic              2
  45.178112030 = 48.509628416   boot/initrd.img-2.6.35-28-generic              2
  52.373046875 = 56.235130880   boot/initrd.img-2.6.35-30-generic              2
  48.638671875 = 52.225376256   boot/initrd.img-2.6.35-31-generic              2
  50.794921875 = 54.540632064   boot/initrd.img-2.6.35-32-generic              2
  43.399742126 = 46.600118272   boot/initrd.img-2.6.36-020636-generic          2
  46.878013611 = 50.334883840   boot/initrd.img-2.6.36-2.dmz.7-liquorix-amd64  2
  46.922962189 = 50.383147008   boot/initrd.img-2.6.36-3.dmz.1-liquorix-amd64  2
  47.094837189 = 50.567696384   boot/initrd.img-2.6.36-3.dmz.2-liquorix-amd64  2
  46.915088654 = 50.374692864   boot/initrd.img-2.6.37-020637-generic          2
  47.135364532 = 50.611212288   boot/initrd.img-2.6.37-0.dmz.4-liquorix-amd64  2
  45.240234375 = 48.576331776   boot/initrd.img-2.6.38-020638-generic          3
  45.260829926 = 48.598446080   boot/initrd.img-2.6.38-020638rc2-generic       2
  50.099678040 = 53.794119680   boot/vmlinuz-2.6.32-020632-generic             1
  50.541076660 = 54.268067840   boot/vmlinuz-2.6.35.11dazimage                 1
  49.849220276 = 53.525192704   boot/vmlinuz-2.6.35-22-generic                 1
  50.053588867 = 53.744631808   boot/vmlinuz-2.6.35-23-generic                 1
  50.002040863 = 53.689282560   boot/vmlinuz-2.6.35-24-generic                 1
  50.314590454 = 54.024880128   boot/vmlinuz-2.6.35-25-generic                 1
  50.372913361 = 54.087503872   boot/vmlinuz-2.6.35-27-generic                 1
  47.366519928 = 50.859413504   boot/vmlinuz-2.6.35-28-generic                 2
  51.152465820 = 54.924541952   boot/vmlinuz-2.6.35-30-generic                 1
  50.743373871 = 54.485282816   boot/vmlinuz-2.6.35-31-generic                 1
  50.754867554 = 54.497624064   boot/vmlinuz-2.6.35-32-generic                 1
  49.973300934 = 53.658423296   boot/vmlinuz-2.6.36-020636-generic             1
  49.963432312 = 53.647826944   boot/vmlinuz-2.6.36-2.dmz.7-liquorix-amd64     1
  50.042385101 = 53.732601856   boot/vmlinuz-2.6.36-3.dmz.1-liquorix-amd64     1
  50.164775848 = 53.864017920   boot/vmlinuz-2.6.36-3.dmz.2-liquorix-amd64     1
  50.095947266 = 53.790113792   boot/vmlinuz-2.6.37-020637-generic             1
  50.175479889 = 53.875511296   boot/vmlinuz-2.6.37-0.dmz.4-liquorix-amd64     1
  50.725345612 = 54.465925120   boot/vmlinuz-2.6.38-020638-generic             1
  50.253993988 = 53.959815168   boot/vmlinuz-2.6.38-020638rc2-generic          1
  50.794921875 = 54.540632064   initrd.img                                     2
  48.638671875 = 52.225376256   initrd.img.old                                 2
  50.754867554 = 54.497624064   vmlinuz                                        1
  50.743373871 = 54.485282816   vmlinuz.old                                    1

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=c597757f-1add-48e4-ba9f-5e167a5f938a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=63d86782-bff4-41c1-924f-37d093fbe371 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  61.946039200 = 66.514053120   boot/initrd.img-2.6.32-28-generic              1
  62.016321182 = 66.589517824   boot/initrd.img-2.6.32-32-generic              1
  62.071069717 = 66.648303616   boot/initrd.img-2.6.32-33-generic              1
  62.078874588 = 66.656684032   boot/initrd.img-2.6.32-38-generic              1
  62.086679459 = 66.665064448   boot/initrd.img-2.6.32-40-generic              1
  62.103105545 = 66.682701824   boot/initrd.img-2.6.32-41-generic              1
  56.711702347 = 60.893726720   boot/initrd.img-2.6.38-12-generic              2
  61.852334976 = 66.413438976   boot/vmlinuz-2.6.32-28-generic                 1
  61.966886520 = 66.536437760   boot/vmlinuz-2.6.32-32-generic                 1
  61.973276138 = 66.543298560   boot/vmlinuz-2.6.32-33-generic                 1
  61.977060318 = 66.547361792   boot/vmlinuz-2.6.32-38-generic                 1
  62.028711319 = 66.602821632   boot/vmlinuz-2.6.32-40-generic                 1
  62.090463638 = 66.669127680   boot/vmlinuz-2.6.32-41-generic                 1
  61.984743118 = 66.555611136   boot/vmlinuz-2.6.38-12-generic                 1
  62.103105545 = 66.682701824   initrd.img                                     1
  56.711702347 = 60.893726720   initrd.img.old                                 2
  62.090463638 = 66.669127680   vmlinuz                                        1
  61.984743118 = 66.555611136   vmlinuz.old                                    1

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
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
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-15-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-15-generic ...'
	linux	/boot/vmlinuz-2.6.38-15-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-14-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-14-generic ...'
	linux	/boot/vmlinuz-2.6.38-14-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 5b20be62-a948-4693-b6c9-a8b11eb2d271
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3E10BBBF10BB7C89
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060EA3E60EA0B24
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 8AD8245BD82447B1
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.38-020638-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.38-020638-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.38-020638-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.35-30-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.35-30-generic root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro single acpi=copy_dsdt
	initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35.11dazimage (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 93f00b46-2cf5-4b46-83be-f708cf831675
	linux /boot/vmlinuz-2.6.35.11dazimage root=UUID=93f00b46-2cf5-4b46-83be-f708cf831675 ro acpi=copy_dsdt quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-2.6.35.11dazimage
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img.old
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-33-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-38-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.32-40-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sda8
	initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz root=/dev/sda8
	initrd /initrd.img.old
}
menuentry "Ubuntu 10.04.4 LTS (10.04) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c597757f-1add-48e4-ba9f-5e167a5f938a
	linux /vmlinuz.old root=/dev/sda8
	initrd /initrd.img.old
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=5b20be62-a948-4693-b6c9-a8b11eb2d271 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=63d86782-bff4-41c1-924f-37d093fbe371 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.526061535 = 77.874265600   boot/grub/core.img                             1
  76.654479504 = 82.307120640   boot/grub/grub.cfg                             1
  72.083255291 = 77.398806016   boot/initrd.img-2.6.38-10-generic              2
  83.079905987 = 89.206369792   boot/initrd.img-2.6.38-12-generic              1
  72.814250469 = 78.183706112   boot/initrd.img-2.6.38-13-generic              1
  72.829875469 = 78.200483328   boot/initrd.img-2.6.38-14-generic              1
  73.431437969 = 78.846406144   boot/initrd.img-2.6.38-15-generic              1
  71.924716473 = 77.228576256   boot/initrd.img-2.6.38-8-generic               2
  71.837474346 = 77.134900736   boot/vmlinuz-2.6.38-10-generic                 2
  82.802318096 = 88.908312064   boot/vmlinuz-2.6.38-12-generic                 2
  71.591395855 = 76.870675968   boot/vmlinuz-2.6.38-13-generic                 1
  72.036708355 = 77.348826624   boot/vmlinuz-2.6.38-14-generic                 1
  73.228114605 = 78.628089344   boot/vmlinuz-2.6.38-15-generic                 1
  72.532783031 = 77.881482752   boot/vmlinuz-2.6.38-8-generic                  1
  73.431437969 = 78.846406144   initrd.img                                     1
  72.829875469 = 78.200483328   initrd.img.old                                 1
  73.228114605 = 78.628089344   vmlinuz                                        1
  72.036708355 = 77.348826624   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```

---

### Post by Bucky Ball on 2012-05-28
@drs305: Thankyou. That worked perfectly and has gotten me a lot further down the path to solving this. The cause of all this is I attempted to install the ATI graphics driver and updated and booting into recovery with your method and 'Fix Broken Packages' has given me plenty of errors to that effect. 

I will mark this solved, as the title issue is, and start a new thread regarding the dog's breakfast of errors I'm getting. I'll post a link back here ... 

Thanks again. ;)

---

### Post by Bucky Ball on 2012-05-28
Here is a link to a new thread regarding uninstalling fglrx so I might boot into failsafe:

[http://ubuntuforums.org/showthread.php?p=11974901#post11974901](http://ubuntuforums.org/showthread.php?p=11974901#post11974901)

;)

---

