---
title: "Grub problems"
date: 2011-08-03
forum: General Help
---

### Post by sonicj on 2011-08-03
Hey guys, I have a bit of a problem. I had Ubuntu 10.10 and windows 7 dual booting and it simply worked. Now I recently installed fedora 15 and that's when trouble arose. Initially, after the installation turning on the computer would only boot Fedora 15. So I used super grub disk 2 to boot into Ubuntu 10.10 and I tried to restore my original grub I used 
> 
grub-mkconfig
grub-install /dev/sda
update-grub

And I had grub 2 back t the way it was previously, except now I couldn't boot Fedora 15. Fedora 15 did not show up in Grub disk 2 either, just windows and ubuntu.

Some where down the line I messed up my current grub again, now I'm booting into grub rescue. I have super grub disk 2 and that's how I boot into ubuntu or windows (or another flavor on my usb). My question is, how can I boot into Fedora 15 again? I wanted a triple boot, but I can't seem to manage to get it working :(

Here is my fdisk -l output:
> sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6bcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       34367   275944448    7  HPFS/NTFS
/dev/sda3           34367       38914    36521985    5  Extended
/dev/sda5           35724       38914    25621504   83  Linux
/dev/sda6           34367       34431      512000   83  Linux
/dev/sda7           34431       35723    10380288   8e  Linux LVM

Partition table entries are not in disk order


sda 1 & 2 are both windows partitions, Sda 5 is ubuntu 10, and 6 & 7 both showed up after I installed fedora 15, so I assume they are both related to that.

---

### Post by sonicj on 2011-08-03
Bumping.

---

### Post by oldfred on 2011-08-03
Several similar threads:
[http://ubuntuforums.org/showthread.php?t=1815724&highlight=fedora](http://ubuntuforums.org/showthread.php?t=1815724&highlight=fedora)
[http://ubuntuforums.org/showthread.php?t=1816088&highlight=fedora](http://ubuntuforums.org/showthread.php?t=1816088&highlight=fedora)
[http://ubuntuforums.org/showthread.php?t=1736692&highlight=fedora](http://ubuntuforums.org/showthread.php?t=1736692&highlight=fedora)

Post boot script:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You may need this also for boot script to search LVM:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install mawk


HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by sonicj on 2011-08-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

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
    Boot files:        /grub/menu.lst /grub/grub.conf

sda7: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

vg_fedeorajose-lv_swap': _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg_fedeorajose-lv_root': _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   552,095,743   551,888,896   7 NTFS / exFAT / HPFS
/dev/sda3         552,097,790   625,141,759    73,043,970   5 Extended
/dev/sda5         573,898,752   625,141,759    51,243,008  83 Linux
/dev/sda6         552,101,888   553,125,887     1,024,000  83 Linux
/dev/sda7         553,127,936   573,888,511    20,760,576  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CCEA3222EA3208EA                       ntfs       System Reserved
/dev/sda2        C8DC3A40DC3A2958                       ntfs       
/dev/sda5        2b8983e9-5757-4b56-90e0-04f1b505427e   ext4       
/dev/sda6        3019bbb5-4dfb-4cf4-b7c6-36251bb913d3   ext4       
/dev/sda7        bMiAW7-ddIv-1pUo-mEqp-hYwN-Vvly-7RB8yN LVM2_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


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
search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-30-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 2b8983e9-5757-4b56-90e0-04f1b505427e
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=2b8983e9-5757-4b56-90e0-04f1b505427e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set CCEA3222EA3208EA
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 ( (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set CCEA3222EA3208EA
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
UUID=2b8983e9-5757-4b56-90e0-04f1b505427e	/	ext4	errors=remount-ro	0	1

--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 286.246311188 = 307.354636288  boot/grub/core.img                             1
 284.056148529 = 305.002967040  boot/grub/grub.cfg                             1
 275.703250885 = 296.034111488  boot/initrd.img-2.6.35-22-generic              2
 275.924312592 = 296.271474688  boot/initrd.img-2.6.35-24-generic              1
 280.549312592 = 301.237530624  boot/initrd.img-2.6.35-25-generic              2
 287.117187500 = 308.289732608  boot/initrd.img-2.6.35-27-generic              2
 287.490764618 = 308.690857984  boot/initrd.img-2.6.35-28-generic              2
 287.192008972 = 308.370071552  boot/initrd.img-2.6.35-30-generic              2
 286.285289764 = 307.396489216  boot/vmlinuz-2.6.35-22-generic                 1
 286.347793579 = 307.463602176  boot/vmlinuz-2.6.35-24-generic                 1
 286.410293579 = 307.530711040  boot/vmlinuz-2.6.35-25-generic                 1
 286.863422394 = 308.017254400  boot/vmlinuz-2.6.35-27-generic                 1
 286.878906250 = 308.033880064  boot/vmlinuz-2.6.35-28-generic                 2
 286.969303131 = 308.130942976  boot/vmlinuz-2.6.35-30-generic                 1
 287.192008972 = 308.370071552  initrd.img                                     2
 287.490764618 = 308.690857984  initrd.img.old                                 2
 286.969303131 = 308.130942976  vmlinuz                                        1
 286.878906250 = 308.033880064  vmlinuz.old                                    2

============================= sda6/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,5)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_fedeorajose-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
	root (hd0,5)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=/dev/mapper/vg_fedeorajose-lv_root rd_LVM_LV=vg_fedeorajose/lv_root rd_LVM_LV=vg_fedeorajose/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Other
	rootnoverify (hd0,0)
	chainloader +1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 263.277293205 = 282.691841024  grub/grub.conf                                 1
 263.277293205 = 282.691841024  grub/menu.lst                                  1
 263.277410507 = 282.691966976  grub/stage2                                    1
 263.293881416 = 282.709652480  initramfs-2.6.38.6-26.rc1.fc15.x86_64.img      2
 263.270977974 = 282.685060096  initrd-plymouth.img                            1
 263.274854660 = 282.689222656  vmlinuz-2.6.38.6-26.rc1.fc15.x86_64            1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  59 32 46 5b b7 b9 c1 19  f7 3f 8e 0d 74 ed a9 52  |Y2F[.....?..t..R|
00000010  6d c1 b4 f7 68 9e 47 cc  81 62 e1 64 3c 86 ea bc  |m...h.G..b.d<...|
00000020  1f eb 51 0d f9 65 0e c2  4c 71 93 8c e3 ff 00 af  |..Q..e..Lq......|
00000030  5a a6 be cb e9 dc cd a7  74 a4 ee 93 b1 59 a3 b8  |Z.......t....Y..|
00000040  79 c9 f9 98 30 f9 4a 91  cf 27 df fc ff 00 36 bc  |y...0.J..'....6.|
00000050  73 12 54 46 3c b7 db 22  95 c6 47 ad 4c 6a 46 2d  |s.TF<.."..G.LjF-|
00000060  ea d3 b2 33 87 2c 94 9b  b3 4a f6 29 e2 2c 11 b8  |...3.,...J.).,..|
00000070  b4 91 4d 92 32 41 18 cf  f4 ac d9 e4 9a 02 d2 2f  |..M.2A........./|
00000080  ef c0 76 2c 0a 83 eb fe  7f cf 1d 34 a6 aa 46 57  |..v,.......4..FW|
00000090  ef 7b dc e3 e5 7c ce 3a  25 29 6b e5 b9 ce 6a b2  |.{...|.:%)k...j.|
000000a0  df 1b 17 b8 d3 f4 b9 f5  09 76 e1 34 db 69 16 37  |.........v.4.i.7|
000000b0  90 e4 67 69 63 8c e0 93  f8 11 f5 41 0a b4 58 68  |..gic......A..Xh|
000000c0  f6 cf b0 86 57 20 ec 38  3c 1f 7a d1 54 95 9a 6f  |....W .8<.z.T..o|
000000d0  76 ba 1b 46 33 84 9a 4d  25 65 d4 e2 5a f5 92 c1  |v..F3..M%e..Z...|
000000e0  23 86 18 cc c3 c9 8e 58  c0 00 29 20 83 d0 74 1d  |#......X..) ..t.|
000000f0  bf fa f5 d4 68 ef 06 97  a6 19 a4 fb 38 96 53 e5  |....h.......8.S.|
00000100  b6 41 07 2c a7 8e 9c f3  9c 57 85 39 c2 29 28 ea  |.A.,.....W.9.)(.|
00000110  bb 9f 2d 1b 46 13 4d 34  e4 8c 97 75 d4 77 df 49  |..-.F.M4...u.w.I|
00000120  24 f0 59 47 be 08 ec c8  01 59 49 ea dd ff 00 fa  |$.YG.....YI.....|
00000130  d5 ca e8 da 45 ad fd fc  d7 b3 e8 f6 fa 46 1e 4b  |....E........F.K|
00000140  eb 9b 4b 18 7c b3 73 b8  92 92 1c 37 2e f9 07 07  |..K.|.s....7....|
00000150  07 af 19 aa 82 8f bd 77  79 34 ac 6d 09 2a 52 49  |.......wy4.m.*RI|
00000160  3d 1c 76 b7 91 d1 5e 79  97 ab 14 c4 dd db b4 33  |=.v...^y.......3|
00000170  47 32 5d 5b a9 56 40 8c  0e 39 ee 71 8c 53 96 79  |G2][.V@..9.q.S.y|
00000180  ee ed 2d ad 64 92 db ec  9e 6b bd c4 53 5b 05 92  |..-.d....k..S[..|
00000190  32 fc 12 cd 8d c4 e0 0f  94 f0 33 91 cd 67 cf 3a  |2.........3..g.:|
000001a0  72 b3 77 4d db 6d 8a 95  27 36 b5 b3 ba 37 6c 25  |r.wM.m..'6...7l%|
000001b0  d3 f4 f3 70 b6 37 f1 b4  9c 29 59 18 36 58 00 fe  |...p.7...)Y.6X..|
000001c0  ff ff 83 fe ff ff 02 a8  4c 01 00 e8 0d 03 00 fe  |........L.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 b0 0f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on vg_fedeorajose-lv_swap'


Unknown BootLoader on vg_fedeorajose-lv_root'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_fedeorajose-lv_swap': No such file or directory
hexdump: /dev/mapper/vg_fedeorajose-lv_swap': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_fedeorajose-lv_root': No such file or directory
hexdump: /dev/mapper/vg_fedeorajose-lv_root': No such file or directory
mdadm: No arrays found in config file or automatically

```

Thanks for the help/links.

---

### Post by sonicj on 2011-08-03
Well, somehow I got it working. Fedora 15 randomly showed up when I used Grub customiser, thanks for the help!

---

### Post by oldfred on 2011-08-03
Grub customizer would run sudo update-grub to implement changes, so that may be all that was required.

Glad its working.

---

