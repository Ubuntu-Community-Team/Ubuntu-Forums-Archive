---
title: "Delete older Ubuntu Installations from HDD"
date: 2010-12-30
forum: General Help
---

### Post by SNYP40A1 on 2010-12-30
I have 1 Windows XP and 3 different installations of Ubuntu on my system.  I want to remove the older installations of Ubuntu.  How do I do this without damaging the current Ubuntu and  XP installation?  I boot through GRUB so I assume there's more to it than simply deleting the corresponding partitions.

---

### Post by dcstar on 2010-12-30
> **SNYP40A1 said:**
> I have 1 Windows XP and 3 different installations of Ubuntu on my system.  I want to remove the older installations of Ubuntu.  How do I do this without damaging the current Ubuntu and  XP installation?  I boot through GRUB so I assume there's more to it than simply deleting the corresponding partitions.

Grub should be on the last Ubuntu system you installed, so just deleting the other old partitions with **gparted** and then running the following should clear them up:

```
sudo update-grub
```

---

### Post by SNYP40A1 on 2010-12-30
> **dcstar said:**
> Grub should be on the last Ubuntu system you installed, so just deleting the other old partitions with **gparted** and then running the following should clear them up:

```
sudo update-grub
```

Here's what my gparted screen looks like.  Which partitions should I delete?  

[[IMG]http://img638.imageshack.us/img638/5595/screenshotbbo.png[/IMG]](http://img638.imageshack.us/i/screenshotbbo.png/)


I think the second largest partition is my current installation of Ubuntu.  Question is which of the swap spaces is associated with it?

---

### Post by coffeecat on 2010-12-30
> **SNYP40A1 said:**
> I think the second largest partition is my current installation of Ubuntu.  Question is which of the swap spaces is associated with it?

If you are running Gparted from the version of Ubuntu you want to keep, then you need to keep sda10 and sda11 and delete sda5, 6, 7, 8, and 9. To be 101% sure, you can go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file, not forgetting to enclose them in code tags as described in the link. 

A cautionary note. If it does turn out that you need to keep sda10 and sda11, once you have deleted the others, sda10 and sda11 may well be renumbered. In which case you **must** run 'sudo update-grub' before you reboot. Post the results file anyway and we can see what is what.

---

### Post by SNYP40A1 on 2010-12-30
> **coffeecat said:**
> If you are running Gparted from the version of Ubuntu you want to keep, then you need to keep sda10 and sda11 and delete sda5, 6, 7, 8, and 9. To be 101% sure, you can go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file, not forgetting to enclose them in code tags as described in the link. 

A cautionary note. If it does turn out that you need to keep sda10 and sda11, once you have deleted the others, sda10 and sda11 may well be renumbered. In which case you **must** run 'sudo update-grub' before you reboot. Post the results file anyway and we can see what is what.

Here it is:

[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,062,859   216,062,797   7 HPFS/NTFS
/dev/sda3         216,063,998   312,576,704    96,512,707   5 Extended
/dev/sda5         310,054,563   312,576,704     2,522,142  82 Linux swap / Solaris
/dev/sda6         297,636,381   303,524,140     5,887,760  83 Linux
/dev/sda7         309,411,963   310,054,499       642,537  82 Linux swap / Solaris
/dev/sda8         303,525,888   309,032,959     5,507,072  83 Linux
/dev/sda9         309,035,008   309,411,839       376,832  82 Linux swap / Solaris
/dev/sda10        216,064,000   294,197,247    78,133,248  83 Linux
/dev/sda11        294,199,296   297,635,839     3,436,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        04F49A6BF49A5EAC                       ntfs                                     
/dev/sda10       d78abef5-e4d2-4b25-86a9-02fd378ef484   ext4                                     
/dev/sda11       2fab5550-e873-4a4d-8b0f-970fdd1cd0db   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        14ce978c-73ba-4b1e-833b-b3cc07c36209   swap                                     
/dev/sda6        945658e3-4807-4e75-aa06-bbdd4d52b0d5   ext4                                     
/dev/sda7        422b1811-2e2b-4bc1-9e67-c084df34ab97   swap                                     
/dev/sda8        6b0ee264-db50-4a06-a7cb-0e33d154c3e4   ext4                                     
/dev/sda9        ffb4d9e2-5998-4135-941a-8c6bfc0d76e4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 04f49a6bf49a5eac
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-16-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro quiet splash
	initrd /boot/initrd.img-2.6.20-16-generic
}
menuentry "Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-16-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro single
	initrd /boot/initrd.img-2.6.20-16-generic
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-15-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro quiet splash
	initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-15-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro single
	initrd /boot/initrd.img-2.6.20-15-generic
}
menuentry "Ubuntu, kernel 2.6.20-13-generic (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-13-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro quiet splash
	initrd /boot/initrd.img-2.6.20-13-generic
}
menuentry "Ubuntu, kernel 2.6.20-13-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-13-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro single
	initrd /boot/initrd.img-2.6.20-13-generic
}
menuentry "Ubuntu, kernel 2.6.20-12-generic (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-12-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro quiet splash
	initrd /boot/initrd.img-2.6.20-12-generic
}
menuentry "Ubuntu, kernel 2.6.20-12-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/vmlinuz-2.6.20-12-generic root=UUID=d7341198-a457-4474-8d1b-fda13e0712fb ro single
	initrd /boot/initrd.img-2.6.20-12-generic
}
menuentry "Ubuntu, memtest86+ (on /dev/sda2)" {
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d7341198-a457-4474-8d1b-fda13e0712fb
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=422b1811-2e2b-4bc1-9e67-c084df34ab97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 153.1GB: boot/grub/core.img
 153.2GB: boot/grub/grub.cfg
 153.2GB: boot/initrd.img-2.6.31-14-generic
 153.1GB: boot/initrd.img-2.6.31-16-generic
 154.9GB: boot/vmlinuz-2.6.31-14-generic
 155.2GB: boot/vmlinuz-2.6.31-16-generic
 153.1GB: initrd.img
 153.2GB: initrd.img.old
 155.2GB: vmlinuz
 154.9GB: vmlinuz.old

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=6b0ee264-db50-4a06-a7cb-0e33d154c3e4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=ffb4d9e2-5998-4135-941a-8c6bfc0d76e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 157.2GB: boot/vmlinuz-2.6.35-22-generic
 157.2GB: vmlinuz

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
set locale_dir=($root)/boot/grub/locale
set lang=None.None
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 04f49a6bf49a5eac
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b0d5
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=945658e3-4807-4e75-aa06-bbdd4d52b0d5 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 6b0ee264-db50-4a06-a7cb-0e33d154c3e4
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8
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

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=2fab5550-e873-4a4d-8b0f-970fdd1cd0db none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 134.3GB: boot/grub/core.img
 123.8GB: boot/grub/grub.cfg
 111.5GB: boot/initrd.img-2.6.35-22-generic
 123.9GB: boot/initrd.img-2.6.35-24-generic
 134.3GB: boot/vmlinuz-2.6.35-22-generic
 134.3GB: boot/vmlinuz-2.6.35-24-generic
 123.9GB: initrd.img
 111.5GB: initrd.img.old
 134.3GB: vmlinuz
 134.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  cf 31 f0 e9 b8 76 6c 00  18 e0 01 38 a1 b7 58 77  |.1...vl....8..Xw|
00000010  78 08 c2 65 f3 97 5a 9d  c5 a1 53 40 ed 31 c9 0f  |x..e..Z...S@.1..|
00000020  38 8c 04 a0 6b 1c 96 3c  13 4c 83 03 20 0e 83 e1  |8...k..<.L.. ...|
00000030  80 30 25 e8 29 cc c9 e4  d0 00 ce c8 86 2f be 2d  |.0%.)......../.-|
00000040  b1 84 94 66 2e cc b6 ac  f9 97 dd 5e e6 ca 19 79  |...f.......^...y|
00000050  cb 53 1a cf 61 dc 75 54  de 83 5d cf 96 f3 30 03  |.S..a.uT..]...0.|
00000060  df 7d b0 ac b7 2b 16 1b  1e 2a d4 1c 75 7d 85 cc  |.}...+...*..u}..|
00000070  08 52 60 31 d9 66 41 c9  9d db 64 ff 26 79 3b 8b  |.R`1.fA...d.&y;.|
00000080  cb 73 0a f9 17 2b 3c cc  b6 4c ee 47 c0 8f b3 7e  |.s...+<..L.G...~|
00000090  34 01 59 b6 de 73 b6 71  67 b0 06 8d 25 8f 64 06  |4.Y..s.qg...%.d.|
000000a0  0c 42 1b 5a 4b 17 35 fc  3b c1 ea 81 2d 80 e1 07  |.B.ZK.5.;...-...|
000000b0  e7 09 ef ae c2 d5 ec 4b  8d a6 c0 51 1e 0e 9b b2  |.......K...Q....|
000000c0  35 eb dc 4f d7 67 52 a5  08 24 b1 61 08 db 06 38  |5..O.gR..$.a...8|
000000d0  34 f4 b1 fc 69 8c 65 47  5b d7 47 4c b6 b3 87 e1  |4...i.eG[.GL....|
000000e0  e4 47 60 6c 02 96 5e 6f  42 ac 85 cd c5 b0 14 cc  |.G`l..^oB.......|
000000f0  01 f3 dc 89 4d 99 d8 38  76 5b 98 b8 a4 e8 b6 2b  |....M..8v[.....+|
00000100  d8 70 72 0e c5 77 6c cf  d0 f8 a1 b2 5d 8c 23 0a  |.pr..wl.....].#.|
00000110  ce cb b1 45 62 f7 c5 0d  8c ad e8 cc 5e 99 33 68  |...Eb.......^.3h|
00000120  c2 de 65 7c f7 0e e3 38  7c 28 cc b5 80 53 6d 82  |..e|...8|(...Sm.|
00000130  00 00 40 5d 46 0b ae 68  1a 00 4e 00 83 99 00 00  |..@]F..h..N.....|
00000140  00 00 0a 9b 2d 00 00 56  74 1a 00 64 00 c1 48 a3  |....-..Vt..d..H.|
00000150  90 60 7e f2 5a 82 fc 8d  b1 7f 15 89 cf e4 4e 52  |.`~.Z.........NR|
00000160  33 05 e3 8f 06 72 8c 2b  96 a1 dd 82 22 80 98 66  |3....r.+...."..f|
00000170  5a 6e 63 71 5e 11 bc bd  12 9c d3 fb df 15 99 10  |Zncq^...........|
00000180  05 30 b3 c4 f9 2a 11 90  7d fb 6f 14 31 65 4b 40  |.0...*..}.o.1eK@|
00000190  17 1b 4d 91 68 3e b1 4d  79 07 d1 93 d6 1c 51 36  |..M.h>.My.....Q6|
000001a0  28 c1 b1 3a eb 2d a2 d2  43 82 4d 4d db 18 92 84  |(..:.-..C.MM....|
000001b0  f1 4c 22 cd 8c 12 76 4f  8b 3d cb 06 5f e6 00 fe  |.L"...vO.=.._...|
000001c0  ff ff 82 fe ff ff a5 2e  9a 05 1e 7c 26 00 00 fe  |...........|&...|
000001d0  ff ff 05 fe ff ff a1 b1  dc 04 8e d7 59 00 00 00  |............Y...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/PHP]

---

### Post by coffeecat on 2010-12-30
You have an interesting set of partitions there. The important thing is that the version of Ubuntu maverick 10.10 that you are booting into is on sda10, using sda11 as swap, so you need to retain those two partitions. Ubuntu 9.10 is on sda6 (swap sda7) and another instance of Maverick/10.10 on sda8 (swap sda9) but this has no grub installed - seemingly. There is also an unused swap partition, sda5.

So to achieve what you want, you need to boot into Maverick on sda10, open Gparted and delete sda5, 6, 7, 8 and 9. Then you must open a terminal before you reboot and:

```
sudo update-grub
```That will regenerate the grub menu for just your sda10 Maverick and for Windows.

**EDIT**: by the way - backup everything before deleting partitions. Usually everything goes OK, but once in a while manipulating partitions can lead to errors and potential data loss.

---

### Post by SNYP40A1 on 2010-12-30
There seems to be a problem...when I select /dev/sda5 in GParted and hit delete, I get a message telling me: "Unable to delete /dev/sda5! -- Please unmount any logical partitions having a number higher than 5".  Why is this necessary?  Will it try to rename the higher partitions to a lower number?  I don't think I can unmount /dev/sda10 while logged into /dev/sda10.

---

### Post by coffeecat on 2010-12-30
> **SNYP40A1 said:**
> There seems to be a problem...when I select /dev/sda5 in GParted and hit delete, I get a message telling me: "Unable to delete /dev/sda5! -- Please unmount any logical partitions having a number higher than 5".  Why is this necessary? 

That is a problem which I hadn't anticipated. What you need to do is to boot up with an Ubuntu live CD and boot into the live desktop. Open Gparted in the live CD. You'll probably find that it has mounted all four swap partitions - there will be a lock-key by any mounted ones. Right-click on each and choose swapoff. You will now be able to delete the unused partitions.

However, if sda10 and sda11 do get renumbered by this you may find that you won't be able to boot into Ubuntu from the grub menu - temporarily. Try it anyway and post back if this happens. There are two ways around this, both using the live CD, but let's see if this happens. This shouldn't affect your ability to boot into Windows.

---

### Post by OGpmpdog on 2010-12-30
> **SNYP40A1 said:**
> There seems to be a problem...when I select /dev/sda5 in GParted and hit delete, I get a message telling me: "Unable to delete /dev/sda5! -- Please unmount any logical partitions having a number higher than 5".  Why is this necessary?  Will it try to rename the higher partitions to a lower number?  I don't think I can unmount /dev/sda10 while logged into /dev/sda10.

Hi,

I dont know if you've started deleting partitions...
Start off by opening the Terminal, and typing sudo update-grub, seeing your most current partition configuration. Print our configuration.
You want to make sure all your partitions are unmounted, so:
Logout and reboot with a Live CD.
Click Try Ubuntu and boot up Gparted...you should be able to remove any partition you want. 
Remember to go to terminal and type sudo update-grub after you are finished.
Gentlemen, please include anything that I have missed.
Happy New Year to the Ubuntu Fam.
Peace.

---

### Post by SNYP40A1 on 2010-12-31
> **OGpmpdog said:**
> Hi,

I dont know if you've started deleting partitions...
Start off by opening the Terminal, and typing sudo update-grub, seeing your most current partition configuration. Print our configuration.
You want to make sure all your partitions are unmounted, so:
Logout and reboot with a Live CD.
Click Try Ubuntu and boot up Gparted...you should be able to remove any partition you want. 
Remember to go to terminal and type sudo update-grub after you are finished.
Gentlemen, please include anything that I have missed.
Happy New Year to the Ubuntu Fam.
Peace.

Will sudo-update grub work from the liveCD?  Don't I need to be logged into the Ubuntu Partition that I need to keep in order to run that?  Otherwise, won't it just update the GRUB that has been loaded into memory on the LiveCD session -- performing no persistent changes to the GRUB on the disk?

---

### Post by coffeecat on 2010-12-31
> **SNYP40A1 said:**
> Will sudo-update grub work from the liveCD? 

No.

> **SNYP40A1 said:**
>  Don't I need to be logged into the Ubuntu Partition that I need to keep in order to run that?

You would need to chroot into the Ubuntu partition in order to run update-grub so that it updates grub.cfg.

Chrooting was one of the ways I was thinking of in post #8. The other way is to edit grub.cfg directly from the live CD. That's a very quick and dirty way of dealing with things but it can work to get you booting if you need to. 

How far have you got?

---

### Post by SNYP40A1 on 2010-12-31
> **coffeecat said:**
> No.



You would need to chroot into the Ubuntu partition in order to run update-grub so that it updates grub.cfg.

Chrooting was one of the ways I was thinking of in post #8. The other way is to edit grub.cfg directly from the live CD. That's a very quick and dirty way of dealing with things but it can work to get you booting if you need to. 

How far have you got?

I haven't tried anything yet as I want to make sure I understand the whole process before I begin.  What chroot command would I issue from the live CD?  Would it be:

chroot /boot/initrd.img-2.6.35-24-generic? (taken from the results.txt log posted earlier)

---

### Post by coffeecat on 2010-12-31
> **SNYP40A1 said:**
> chroot /boot/initrd.img-2.6.35-24-generic? (taken from the results.txt log posted earlier)

No, it's a bit trickier than that. :)

Boot into the live CD and delete all the unwanted partitions. This may or may not cause sda10 and sda11 to be renumbered. It's a bit unpredictable. Open a terminal and run:

```
sudo fdisk -lu
```...to see. If they haven't been renumbered then all you have to do is to reboot and run 'sudo update-grub' in your Ubuntu installation. If they have been renumbered then sda10 has probably become sda5. Check this though. If this has happened, follow my post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=1653162](http://ubuntuforums.org/showthread.php?t=1653162)

Start at the 'sudo mount' bit, but omit 'sudo grub-install' - it's superfluous in your situation. Then follow the rest. Conveniently, those instructions refer to sda5 at the initial mount command, but change this if yours is different. If you follow that post to the end, including the 'sudo update-grub' when booted into the hard drive, that should fix everything.

---

### Post by SNYP40A1 on 2011-01-01
Something didn't go right.  I boot and there's no grub.  I see:

[PHP]
error: no such partition
grub rescue>
[/PHP]

Help!

---

### Post by SNYP40A1 on 2011-01-01
I ran that results script again and here's the RESULTS.txt file:

[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,062,859   216,062,797   7 HPFS/NTFS
/dev/sda3         216,063,998   312,580,095    96,516,098   5 Extended
/dev/sda5         216,064,000   309,137,407    93,073,408  83 Linux
/dev/sda6         309,139,456   312,578,047     3,438,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        04F49A6BF49A5EAC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d78abef5-e4d2-4b25-86a9-02fd378ef484   ext4                                     
/dev/sda6        2fab5550-e873-4a4d-8b0f-970fdd1cd0db   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d78abef5-e4d2-4b25-86a9-02fd378ef484
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=d78abef5-e4d2-4b25-86a9-02fd378ef484 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=2fab5550-e873-4a4d-8b0f-970fdd1cd0db none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.3GB: boot/grub/core.img
 134.4GB: boot/grub/grub.cfg
 111.5GB: boot/initrd.img-2.6.35-22-generic
 123.9GB: boot/initrd.img-2.6.35-24-generic
 134.3GB: boot/vmlinuz-2.6.35-22-generic
 134.3GB: boot/vmlinuz-2.6.35-24-generic
 123.9GB: initrd.img
 111.5GB: initrd.img.old
 134.3GB: vmlinuz
 134.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  cf 31 f0 e9 b8 76 6c 00  18 e0 01 38 a1 b7 58 77  |.1...vl....8..Xw|
00000010  78 08 c2 65 f3 97 5a 9d  c5 a1 53 40 ed 31 c9 0f  |x..e..Z...S@.1..|
00000020  38 8c 04 a0 6b 1c 96 3c  13 4c 83 03 20 0e 83 e1  |8...k..<.L.. ...|
00000030  80 30 25 e8 29 cc c9 e4  d0 00 ce c8 86 2f be 2d  |.0%.)......../.-|
00000040  b1 84 94 66 2e cc b6 ac  f9 97 dd 5e e6 ca 19 79  |...f.......^...y|
00000050  cb 53 1a cf 61 dc 75 54  de 83 5d cf 96 f3 30 03  |.S..a.uT..]...0.|
00000060  df 7d b0 ac b7 2b 16 1b  1e 2a d4 1c 75 7d 85 cc  |.}...+...*..u}..|
00000070  08 52 60 31 d9 66 41 c9  9d db 64 ff 26 79 3b 8b  |.R`1.fA...d.&y;.|
00000080  cb 73 0a f9 17 2b 3c cc  b6 4c ee 47 c0 8f b3 7e  |.s...+<..L.G...~|
00000090  34 01 59 b6 de 73 b6 71  67 b0 06 8d 25 8f 64 06  |4.Y..s.qg...%.d.|
000000a0  0c 42 1b 5a 4b 17 35 fc  3b c1 ea 81 2d 80 e1 07  |.B.ZK.5.;...-...|
000000b0  e7 09 ef ae c2 d5 ec 4b  8d a6 c0 51 1e 0e 9b b2  |.......K...Q....|
000000c0  35 eb dc 4f d7 67 52 a5  08 24 b1 61 08 db 06 38  |5..O.gR..$.a...8|
000000d0  34 f4 b1 fc 69 8c 65 47  5b d7 47 4c b6 b3 87 e1  |4...i.eG[.GL....|
000000e0  e4 47 60 6c 02 96 5e 6f  42 ac 85 cd c5 b0 14 cc  |.G`l..^oB.......|
000000f0  01 f3 dc 89 4d 99 d8 38  76 5b 98 b8 a4 e8 b6 2b  |....M..8v[.....+|
00000100  d8 70 72 0e c5 77 6c cf  d0 f8 a1 b2 5d 8c 23 0a  |.pr..wl.....].#.|
00000110  ce cb b1 45 62 f7 c5 0d  8c ad e8 cc 5e 99 33 68  |...Eb.......^.3h|
00000120  c2 de 65 7c f7 0e e3 38  7c 28 cc b5 80 53 6d 82  |..e|...8|(...Sm.|
00000130  00 00 40 5d 46 0b ae 68  1a 00 4e 00 83 99 00 00  |..@]F..h..N.....|
00000140  00 00 0a 9b 2d 00 00 56  74 1a 00 64 00 c1 48 a3  |....-..Vt..d..H.|
00000150  90 60 7e f2 5a 82 fc 8d  b1 7f 15 89 cf e4 4e 52  |.`~.Z.........NR|
00000160  33 05 e3 8f 06 72 8c 2b  96 a1 dd 82 22 80 98 66  |3....r.+...."..f|
00000170  5a 6e 63 71 5e 11 bc bd  12 9c d3 fb df 15 99 10  |Zncq^...........|
00000180  05 30 b3 c4 f9 2a 11 90  7d fb 6f 14 31 65 4b 40  |.0...*..}.o.1eK@|
00000190  17 1b 4d 91 68 3e b1 4d  79 07 d1 93 d6 1c 51 36  |..M.h>.My.....Q6|
000001a0  28 c1 b1 3a eb 2d a2 d2  43 82 4d 4d db 18 92 84  |(..:.-..C.MM....|
000001b0  f1 4c 22 cd 8c 12 76 4f  8b 3d cb 06 5f e6 00 fe  |.L"...vO.=.._...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 8c 05 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 6d 35  8c 05 95 7a 34 00 00 00  |......m5...z4...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/PHP]

From the top line, it looks like it's still trying to find partition 10.  I re-ran the steps from the link directly above and after grub-update, it printed:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

---

### Post by coffeecat on 2011-01-01
Fortunately, that's easily fixed. Boot up the live CD and open a terminal.

```
sudo mount /dev/sda5 /mnt
```Now:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```That will get grub in the mbr pointing to sda5.

My apologies. I was so concerned about the effect the renumbering of the partitions was going to have on the grub.cfg file that I forgot the mbr. I should not have told you to omit that command from my linked post. Sorry about that.

**EDIT**: That will get you booting into Ubuntu again. Now you must run 'sudo update-grub' again in your installed Ubuntu to get Windows back into the menu.

---

### Post by perspectoff on 2011-01-01
> **SNYP40A1 said:**
> I have 1 Windows XP and 3 different installations of Ubuntu on my system.  I want to remove the older installations of Ubuntu.  How do I do this without damaging the current Ubuntu and  XP installation?  I boot through GRUB so I assume there's more to it than simply deleting the corresponding partitions.

This is exactly the problem with Grub2. Grub2 is in the last Ubuntu OS you installed. You have to remember which one that is before deleting it.

What if you want to keep the second to last and delete the last one?

Ah well, you can always re-install Grub2 again using the LiveCD, I suppose.

Why can't they just create a way for Grub2 to live in its own boot partition so we can put it there and never have to worry about it, like we did with Grub Legacy?

---

### Post by SNYP40A1 on 2011-01-01
> **perspectoff said:**
> This is exactly the problem with Grub2. Grub2 is in the last Ubuntu OS you installed. You have to remember which one that is before deleting it.

What if you want to keep the second to last and delete the last one?

Ah well, you can always re-install Grub2 again using the LiveCD, I suppose.

Why can't they just create a way for Grub2 to live in its own boot partition so we can put it there and never have to worry about it, like we did with Grub Legacy?

Yes, fortunately, the partition that I want to keep, the one with Ubuntu 10.10 on it was the last one installed.  I wasn't actually sure where GRUB resided.  I figured it resided on the first Ubuntu partition created.  It does make sense to put it on a separate partition, I agree.

---

### Post by SNYP40A1 on 2011-01-01
Ok, that solved it!  I now have just the sda5 / sda6 linux partitions and one Windows partition on one HDD.  I really appreciate all the help.  Thanks!  

If only iTunes supported Linux my parents would have everything they need in Ubuntu.

---

