---
title: "I think I bricked my Ubuntu install -- again...."
date: 2011-04-27
forum: General Help
---

### Post by Sim-I-Am :} on 2011-04-27
Ok, so about 3 weeks ago I got a 100GB SATA HD from a friend's computer and thought I'd throw it into the second bay in my laptop (Gateway P-6860FX) and install the Natty/11.04 beta on it.

So I did.

It was a good idea too!

I seriously did not think I'd like the Unity interface, but after a little reorientation I got used to it, and I think I'm actually starting to like it!

So it's been working fine for the last few weeks, until today. I was going back and forth between my two installs of Ubuntu (10.10 and the 11.04 beta), just messing around with stuff like CompizConfig and VirtualBox, and testing/comparing general performance between the two versions. I was using Ubuntu-tweak to clean up old packages and kernels etc on both versions of Ubuntu and it seemed to be working fine for both (except for the fact that the compiz plugin for ubuntu-tweak crashes on load); however, I had just used the kernel cleanup tool in ubuntu-tweak while in 10.10, then I rebooted to go back into 11.04 to do some more stuff on that side. I proceeded to select the second HD from my BIOS boot menu, GRUB loaded fine, I selected the 11.04 beta image/kernel/installation and hit enter. The screen went blank with only a blinking terminal cursor in the top left corner. #-o

I've seen this before....

I've tried adjusting settings in my BIOS, tried fsck, tried adjusting settings from 10.10 with Storage Device Manager (pysdm) and Disk Utility, but nothing seems to work.
I can mount the HD from 10.10 and browse the contents with no error, but it won't boot.

NOTE: In regards to the first part of this post (about what happened before this problem occurred), that is all I can remember doing before it stopped working.

Any ideas?

---

### Post by idoitprone on 2011-04-27
Well that story looks confusing

run this script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Sim-I-Am :} on 2011-04-27
From 10.10? or a Live CD?

---

### Post by idoitprone on 2011-04-27
> **Sim-I-Am :} said:**
> From 10.10? or a Live CD?

yea any linux distro that has all the proper tools. Post it here with code tags.

---

### Post by Sim-I-Am :} on 2011-04-27
Ok, here goes.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,925,124    30,925,062   7 HPFS/NTFS
/dev/sda2    *     30,925,125   536,105,114   505,179,990   7 HPFS/NTFS
/dev/sda3         556,107,774   625,137,344    69,029,571   5 Extended
/dev/sda5         621,137,223   625,137,344     4,000,122  82 Linux swap / Solaris
/dev/sda6         556,107,776   621,137,072    65,029,297  83 Linux
/dev/sda4         536,107,008   556,105,727    19,998,720  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   195,368,959   195,366,912  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50CC1B45CC1B24AE                       ntfs       Recovery                      
/dev/sda2        02E6DDC1E6DDB4DF                       ntfs       localdisk                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        be87e2f6-364e-4160-96e0-7f2ea7611cdc   ext4                                     
/dev/sda5        19a36810-fed3-4b5f-8bdb-e20abf62a13d   swap                                     
/dev/sda6        cb977962-89bb-4e4a-88d1-0b38b11eefd5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ff26f11b-7b18-45c4-ac35-0b8561d4f36f   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda1        /media/Recovery          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/localdisk         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/sdb1              ext4       (rw)
/dev/sr0         /media/Ubuntu 11.04 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 50cc1b45cc1b24ae
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ff26f11b-7b18-45c4-ac35-0b8561d4f36f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ff26f11b-7b18-45c4-ac35-0b8561d4f36f ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows 7" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 76484BEE484BABA5
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc     nodev,noexec,nosuid                       0  0  
#Entry for /dev/sda4 :
UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc  /                 ext4     errors=remount-ro                         0  1  
#Entry for /dev/sda6 :
UUID=cb977962-89bb-4e4a-88d1-0b38b11eefd5  /home             ext4     defaults                                  0  2  
#Entry for /dev/sda1 :
UUID=50CC1B45CC1B24AE                      /media/Recovery   ntfs-3g  defaults,locale=en_US.UTF-8               0  0  
#Entry for /dev/sda2 :
UUID=02E6DDC1E6DDB4DF                      /media/localdisk  ntfs-3g  defaults,nosuid,nodev,locale=en_US.UTF-8  0  0  
UUID=62728D7B728D5527                      /media/sdb1       ntfs-3g  defaults,locale=en_US.UTF-8               0  0  
#Entry for /dev/sda5 :
UUID=19a36810-fed3-4b5f-8bdb-e20abf62a13d  none              swap     sw                                        0  0  


/dev/sdb1                                  /media/sdb1       ext4     defaults                                  0  0  

=================== sda4: Location of files loaded by Grub: ===================


 281.0GB: boot/grub/core.img
 276.7GB: boot/grub/grub.cfg
 276.5GB: boot/initrd.img-2.6.35-27-generic
 275.8GB: boot/initrd.img-2.6.35-28-generic
 282.7GB: boot/vmlinuz-2.6.35-27-generic
 282.6GB: boot/vmlinuz-2.6.35-28-generic
 275.8GB: initrd.img
 282.6GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff26f11b-7b18-45c4-ac35-0b8561d4f36f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff26f11b-7b18-45c4-ac35-0b8561d4f36f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ff26f11b-7b18-45c4-ac35-0b8561d4f36f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 50CC1B45CC1B24AE
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root be87e2f6-364e-4160-96e0-7f2ea7611cdc
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=be87e2f6-364e-4160-96e0-7f2ea7611cdc ro single
	initrd /boot/initrd.img-2.6.35-27-generic
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc     nodev,noexec,nosuid                       0  0  
#Entry for /dev/sdb1 :
UUID=ff26f11b-7b18-45c4-ac35-0b8561d4f36f  /                 ext4     users                                     0  1  
#Entry for /dev/sda2 :
UUID=02E6DDC1E6DDB4DF                      /media/localdisk  ntfs-3g  defaults,nosuid,nodev,locale=en_US.UTF-8  0  0  
#Entry for /dev/sda5 :
UUID=19a36810-fed3-4b5f-8bdb-e20abf62a13d  none              swap     sw                                        0  0  



=================== sdb1: Location of files loaded by Grub: ===================


  81.7GB: boot/grub/core.img
  90.4GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.38-8-generic
   2.0GB: boot/vmlinuz-2.6.38-8-generic
   2.6GB: initrd.img
   2.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  41 63 41 41 41 41 51 41  41 41 41 42 2f 2f 2f 2f  |AcAAAAQAAAAB////|
00000010  2f 38 41 41 41 41 48 2f  2f 2f 2f 2f 77 41 41 41  |/8AAAAH/////wAAA|
00000020  41 63 41 41 41 41 51 41  41 41 41 46 77 41 41 41  |AcAAAAQAAAAFwAAA|
00000030  41 6f 41 41 41 41 58 41  41 41 41 43 67 41 41 41  |AoAAAAXAAAACgAAA|
00000040  42 63 41 41 41 41 42 41  41 41 41 47 41 41 41 41  |BcAAAABAAAAGAAAA|
00000050  41 6b 41 41 41 41 59 2f  2f 2f 2f 2f 77 41 41 41  |AkAAAAY/////wAAA|
00000060  42 66 2f 2f 2f 2f 2f 41  41 41 41 46 2f 2f 2f 2f  |Bf/////AAAAF////|
00000070  2f 38 41 41 41 41 58 2f  2f 2f 2f 2f 77 45 41 41  |/8AAAAX/////wEAA|
00000080  41 41 41 41 41 41 41 41  41 41 42 41 64 36 55 63  |AAAAAAAAAABAd6Uc|
00000090  74 43 41 4e 42 48 54 6b  35 6b 41 45 45 75 67 2f  |tCANBHTk5kAEEug/|
000000a0  55 41 48 6f 69 7a 41 44  4f 55 52 30 35 4d 78 41  |UAHoizADOUR05MxA|
000000b0  42 42 4c 6f 50 31 41 41  41 41 41 41 76 2f 2f 2f  |BBLoP1AAAAAAv///|
000000c0  2f 38 41 41 41 42 51 41  51 41 41 41 42 31 6f 64  |/8AAABQAQAAAB1od|
000000d0  48 52 77 4f 69 38 76 5a  6d 46 6a 5a 57 4a 76 62  |HRwOi8vZmFjZWJvb|
000000e0  32 73 75 59 32 39 74 4c  32 4a 79 61 57 52 6e 5a  |2suY29tL2JyaWRnZ|
000000f0  58 4a 6f 4d 51 41 41 41  41 41 41 41 41 41 45 41  |XJoMQAAAAAAAAAEA|
00000100  41 41 41 42 77 41 41 41  41 77 41 41 41 41 48 2f  |AAABwAAAAwAAAAH/|
00000110  2f 2f 2f 2f 77 41 41 41  41 66 2f 2f 2f 2f 2f 41  |////wAAAAf/////A|
00000120  41 41 41 42 77 41 41 41  41 77 41 41 41 41 54 41  |AAABwAAAAwAAAATA|
00000130  41 41 41 43 67 41 41 41  42 4d 41 41 41 41 4b 41  |AAACgAAABMAAAAKA|
00000140  41 41 41 45 77 41 41 41  41 45 41 41 41 41 55 41  |AAAEwAAAAEAAAAUA|
00000150  41 41 41 43 51 41 41 41  42 54 2f 2f 2f 2f 2f 41  |AAACQAAABT/////A|
00000160  41 41 41 45 2f 2f 2f 2f  2f 38 41 41 41 41 54 2f  |AAAE/////8AAAAT/|
00000170  2f 2f 2f 2f 77 41 41 41  42 50 2f 2f 2f 2f 2f 41  |////wAAABP/////A|
00000180  51 41 41 41 41 41 41 41  41 41 41 41 41 45 41 22  |QAAAAAAAAAAAAEA"|
00000190  2c 22 73 63 72 6f 6c 6c  22 3a 22 30 2c 30 22 7d  |,"scroll":"0,0"}|
000001a0  5d 2c 22 66 6f 72 6d 64  61 74 61 22 3a 7b 22 2f  |],"formdata":{"/|
000001b0  2f 78 68 74 6d 6c 3a 64  69 76 5b 40 69 64 00 fe  |/xhtml:div[@id..|
000001c0  ff ff 82 fe ff ff 49 45  e0 03 7a 09 3d 00 00 fe  |......IE..z.=...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 b2 44 e0 03 00 00  |...........D....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by idoitprone on 2011-04-27
Can you check the bios on the boot order? Which drive get booted first? try to make it so your sda drive or the one that has windows 7 get booted first, then try the other one

---

### Post by idoitprone on 2011-04-27
double post

---

### Post by Sim-I-Am :} on 2011-04-27
Yup, it's like this:
1) CD/DVD Drive
2) Win7/Ubuntu 10.10 HD (Ubuntu 10.10 is on separate partition)
3) Ubuntu 11.04 HD (the new one, sdb I think)

---

### Post by grahammechanical on 2011-04-27
Do not take me for an expert, but I say the problem lies between the Grub menu on the second hard disc and the kernel image on the second hard disc. You are using the BIOS menu to select the second hard disc and you say that Grub loads. So, things are fine up to that point. You select an OS and things fail when you select the 11.04 kernel.

Are you sure that you did not delete the 11.04 beta kernel when you were messing around with Ubuntu tweak in the 10.10 installation? Is it possible to do that? Have you tried booting into the recovery kernel.

Regards.

---

### Post by idoitprone on 2011-04-27
I was thinking the same thing about the kernel

There is also something that is bother me
```
 Grub 2 is installed in the MBR of /dev/sdb and looks for **b2d**
``` 
I wonder what do that means

that is why i tried to instruct you to change the boot order in the bios, since one of the two grubs is compromized or you messed up the kernel and have to reinstall it

If you can post the output of ```
ls /boot
``` on 10.10

since you have to mount it maybe ```
ls /media/boot or ls /mnt/boot
```

---

### Post by Sim-I-Am :} on 2011-04-27
Yes, that is what I was thinking, but I don't know how I might have deleted a kernel image from a separate hard drive.... but even if I did, I don't know how to reinstall it from 10.10.
I can see (and that previously posted readout from the boot_info script reveals) that all the correct kernels appear to be present in the /boot/ folder on the 11.04 hard drive. screenshot: [IMG]http://img815.imageshack.us/img815/8756/screenshotowg.png[/IMG]

Actually though, thank you; you reminded me of something I was going to say.
When I boot into the recovery mode of the 11.04 beta, everything starts to load, but it stops at this point, says:
ata5: Sata link down (Sstatus 0 Scontrol 0)

---

### Post by Sim-I-Am :} on 2011-04-27
Output of ls /boot

```
abi-2.6.35-27-generic         memtest86+.bin
abi-2.6.35-28-generic         memtest86+_multiboot.bin
burg                          System.map-2.6.35-27-generic
config-2.6.35-27-generic      System.map-2.6.35-28-generic
config-2.6.35-28-generic      vmcoreinfo-2.6.35-27-generic
grub                          vmcoreinfo-2.6.35-28-generic
initrd.img-2.6.35-27-generic  vmlinuz-2.6.35-27-generic
initrd.img-2.6.35-28-generic  vmlinuz-2.6.35-28-generic

```

It looks like my previous experimentations with BURG didn't get completely cleaned out... lol 
Let me know if I need to fix this.

---

### Post by idoitprone on 2011-04-27
> **Sim-I-Am :} said:**
> Output of ls /boot

```
abi-2.6.35-27-generic         memtest86+.bin
abi-2.6.35-28-generic         memtest86+_multiboot.bin
burg                          System.map-2.6.35-27-generic
config-2.6.35-27-generic      System.map-2.6.35-28-generic
config-2.6.35-28-generic      vmcoreinfo-2.6.35-27-generic
grub                          vmcoreinfo-2.6.35-28-generic
initrd.img-2.6.35-27-generic  vmlinuz-2.6.35-27-generic
initrd.img-2.6.35-28-generic  vmlinuz-2.6.35-28-generic

```

It looks like my previous experimentations with BURG didn't get completely cleaned out... lol 
Let me know if I need to fix this.

wait did you ever try to update the grub after you experimented, try to get rid of all easy possiblities

```
sudo update-grub

```

---

### Post by wilee-nilee on 2011-04-27
Put the sdb hd before the sda, in the bios first.

Boot the natty cd and in the terminal run these 3 commands.

fdisk -l
this identifies the hard drives; we are trying to confirm that the sdb is still the natty drive when you run that command, if it is run these two commands from the terminal

sudo mount /dev/sdb1 /mnt
then
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
reboot to natty and run 
sudo update-grub

The deal is that the 1.99 grub in natty has problems being read by the bootscript so it is hard to tell if it is accurate here.
```
Grub 2 is installed in the MBR of /dev/sdb and looks for b2d.
```

The grub commands above here are from this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You are just reloading the grub2 bootloader in the master boot record (MBR) of the sdb hd, where natty is.

There is also the option of a supergrub2 disc to boot you in to natty.
[http://www.bootproblems.com/](http://www.bootproblems.com/)

The only way you could remove the last installed kernel with Ubuntu tweak is if you did the removal before rebooting and looking at the kernel being removed. Once you upgrade a kernel and reboot UT should not be able to remove the last kernel there.

---

### Post by idoitprone on 2011-04-27
wilnee thank for the info. I wonder what type of changes grub1.99 has to offer

---

### Post by wilee-nilee on 2011-04-27
> **idoitprone said:**
> wilnee thank for the info. I wonder what type of changes grub1.99 has to offer

It has a new menu that has a second page drs305 the mod has some great tutorials, here one that is a bit oh info on 1.99.
[http://ubuntuforums.org/showthread.php?t=1739337](http://ubuntuforums.org/showthread.php?t=1739337)

---

### Post by idoitprone on 2011-04-27
I did not mean that. I mean new headaches like this one. After a few seconds of reading
Should this
> 
sudo grub-install --root-directory=/mnt /dev/sdb

be this
```
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

```

---

### Post by wilee-nilee on 2011-04-27
> **idoitprone said:**
> I did not mean that. I mean new headaches like this one. After a few seconds of reading
Should this

be this
```
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

```
since its a natty live cd

look at the link
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by idoitprone on 2011-04-27
thanks again, so there are alternative methods to doing the same thing

---

### Post by wilee-nilee on 2011-04-27
> **idoitprone said:**
> thanks again, so there are alternative methods to doing the same thing

Yeah, And actually you are correct for Natty I believe, per the drs305 link I posted.

> NOTE to Forum Helpers! This change is bound to create a bit of confusion in cases where the user needs to repoint the MBR to the actual partition with the Grub files. For several years we have been using the "--root-directory" switch. While the old command/switch will still work, it might be useful when/if using the new switch this change is empahsized. When using the "--boot-directory" switch, don't forget that the specified path must also contain grub's parent folder (normally 'boot').
When using the grub-install, grub-set-default, or grub-reboot commands, the new '--boot-directory' option is used to specify the target folder DIR/grub; i.e. the folder into which the grub folder will be installed. If the switch is not used, /boot/grub is assumed.
The default folder is /boot/grub if not specified.
Examples:

    To install on a currently-running Ubuntu installation located on the sda drive:
    Code:

    ```
sudo grub-install /dev/sda
```

To install from the LiveCD to an Ubuntu partition mounted on sda's /mnt:

    Code:

    ```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Thanks for noticing, I have Natty and have used the older command so I hadn't really noticed the difference.

OP I changed the command for you in my first post.

---

### Post by Sim-I-Am :} on 2011-04-27
> **idoitprone said:**
> wait did you ever try to update the grub after you experimented, try to get rid of all easy possiblities

```
sudo update-grub

```

Yup, I've done that multiple times, with different boot order configurations. Gonna try wilee-nilee's recommendation, will report back when I'm done.
Thanks for all the help so far!

---

### Post by Sim-I-Am :} on 2011-04-28
Ok, I tried doing all that, from the live CD. I tried doing it the --root-directory=/mnt /dev/sdb AND --boot-directory=/mnt/boot /dev/sdb

Neither seemed to work, natty still won't boot past the black screen with the blinking cursor, and recovery mode still stops at "ata5: Sata link down (Sstatus 0 Scontrol 0)"....

---

### Post by Sim-I-Am :} on 2011-04-29
Okay, screw this. This is the third time something like this has happened so I'm just gonna do what I've been doing -- reformat and reinstall ubuntu. Natty just went out of beta, so I may as well.... Luckily, Ubuntu works so well for me and suits my needs as far as OS's go, so I'm not to the point of complete exasperation that I would ditch Ubuntu altogether. (though it certainly is starting to wear on me after so long....)

Thanks for all the attempted help anyway :)

---

