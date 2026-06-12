---
title: "Adding LVM volumes to GRUB2"
date: 2011-05-04
forum: General Help
---

### Post by blah... on 2011-05-04
Hello everyone. So after installing Ubuntu 11.04 with Fedora Beta 15, I decided it would be a good idea to get a *buntu based distro in case of anything. So I reinstalled it in the form of Xubuntu, and I see that Grub found my Windows 7 install, but not my Fedora install! Here is the output of fdisk -l: ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8dbd631

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       35073   280183217+   7  HPFS/NTFS
/dev/sda3           35073       59489   196117505    5  Extended
/dev/sda4           59489       60802    10548224    7  HPFS/NTFS
/dev/sda5           47310       47374      512000   83  Linux
/dev/sda6           47374       59489    97311744   8e  Linux LVM
/dev/sda7           35073       46821    94365696   83  Linux
/dev/sda8           46821       47309     3921920   82  Linux swap / Solaris

Partition table entries are not in disk order

``` My boot script:```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda6: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   563,440,482   560,366,435   7 HPFS/NTFS
/dev/sda3         563,441,662   955,676,671   392,235,010   5 Extended
/dev/sda5         760,027,136   761,051,135     1,024,000  83 Linux
/dev/sda6         761,053,184   955,676,671   194,623,488  8e Linux LVM
/dev/sda7         563,441,664   752,173,055   188,731,392  83 Linux
/dev/sda8         752,175,104   760,018,943     7,843,840  82 Linux swap / Solaris
/dev/sda4         955,676,672   976,773,119    21,096,448   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        46365E5A365E4B57                       ntfs       System                        
/dev/sda2        A05A8EFD5A8ED008                       ntfs       TI105949W0C                   
/dev/sda3: PTTYPE="dos" 
/dev/sda4        428E640C8E63F6B7                       ntfs       HDDRECOVERY                   
/dev/sda5        cc740665-72fa-4dd6-ba3f-12149c2f28e0   ext4                                     
/dev/sda6        jicgfI-U9yB-zyEO-NJh1-bcHO-eZZg-u0hYPw LVM2_member                               
/dev/sda7        d57c11a7-ebc4-430f-afb9-4c94ee47f0c6   ext4                                     
/dev/sda8        7c60be46-f4bd-4ef3-95d7-b5345f94cb34   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)


============================= sda5/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.5-22.fc15.x86_64)
	root (hd0,4)
	kernel /vmlinuz-2.6.38.5-22.fc15.x86_64 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.5-22.fc15.x86_64.img
title Fedora (2.6.38.2-9.fc15.x86_64)
	root (hd0,4)
	kernel /vmlinuz-2.6.38.2-9.fc15.x86_64 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.2-9.fc15.x86_64.img
title Other
	rootnoverify (hd0,1)
	chainloader +1

=================== sda5: Location of files loaded by Grub: ===================


 389.4GB: grub/grub.conf
 389.4GB: grub/menu.lst
 389.4GB: grub/stage2
 389.1GB: initramfs-2.6.38.2-9.fc15.x86_64.img
 389.1GB: initramfs-2.6.38.5-22.fc15.x86_64.img
 389.1GB: initrd-plymouth.img
 389.1GB: vmlinuz-2.6.38.2-9.fc15.x86_64
 389.1GB: vmlinuz-2.6.38.5-22.fc15.x86_64

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d57c11a7-ebc4-430f-afb9-4c94ee47f0c6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d57c11a7-ebc4-430f-afb9-4c94ee47f0c6 ro single 
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
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root d57c11a7-ebc4-430f-afb9-4c94ee47f0c6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 46365E5A365E4B57
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 428E640C8E63F6B7
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=d57c11a7-ebc4-430f-afb9-4c94ee47f0c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=7c60be46-f4bd-4ef3-95d7-b5345f94cb34 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 312.2GB: boot/grub/core.img
 329.4GB: boot/grub/grub.cfg
 290.2GB: boot/initrd.img-2.6.38-8-generic
 312.2GB: boot/vmlinuz-2.6.38-8-generic
 290.2GB: initrd.img
 312.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 a8  b7 0b 00 a0 0f 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 48  c7 0b 00 c0 99 0b 00 00  |.......H........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```Any suggestions are appreciated.

---

### Post by blind2314 on 2011-05-04
Have you tried ```
sudo update-grub
``` from your Ubuntu install?

---

### Post by blah... on 2011-05-04
> **blind2314 said:**
> Have you tried ```
sudo update-grub
``` from your Ubuntu install?Yes, but nothing happens.```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda4
done

```

---

### Post by blind2314 on 2011-05-04
> **blah... said:**
> Yes, but nothing happens.```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda4
done

```


I'm going to go ahead and assume that when it fails to find "Boot" is where it's actually looking for /boot from your Fedora installation. I remember GRUB used to have an issue adding logical volumes to to the loader, but I'm fairly certain that was fixed. I'll do some digging.

---

### Post by blah... on 2011-05-04
> **blind2314 said:**
> I'm going to go ahead and assume that when it fails to find "Boot" is where it's actually looking for /boot from your Fedora installation. I remember GRUB used to have an issue adding logical volumes to to the loader, but I'm fairly certain that was fixed. I'll do some digging.Thanks a lot man, keep me posted if you find something. I tried myself to google the problem but nothing too helpful came up.

---

### Post by blah... on 2011-05-05
Anyone?

---

