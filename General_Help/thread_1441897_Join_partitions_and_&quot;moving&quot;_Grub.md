---
title: "Join partitions and &quot;moving&quot; Grub"
date: 2010-03-29
forum: General Help
---

### Post by Cranio on 2010-03-29
Hi folks, here's my **fdisk -l**:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfa4dfa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            3697       14593    87530152+   5  Extended
/dev/sda5            6981       14277    58613121   83  Linux
/dev/sda6           14278       14593     2538238+  82  Linux swap / Solaris
/dev/sda7   *        3697        5624    15486597   83  Linux
/dev/sda8            5625        6980    10892038+  83  Linux
```

Now, i'd like to join partitions **sda7** and **sda8** in a single partition. However, it seems that **GRUB** is residing on sda8, where there is a Ubuntu installation I don't need anymore, while I use the Ubuntu 9.10 installation on sda7.
To make it more clear, I see two /boot/grub dirs on both partitions, but my pc seems to use the one on sda8.

What's the correct way to handle this problem?

I believe I use Grub1.97 but I don't know if the system is showing me the "wrong" grub (on sda7) instead of the one that's really used.

Hope to get some help :)

---

### Post by ajgreeny on 2010-03-29
You may be able to overcome this problem by booting to the OS who's grub you want to use, even if you are not at the moment, and then just use the command ```
sudo grub-install /dev/sda
```  That will put grub from that OS on to the MBR of your hard disk.  Having done that run ```
sudo update-grub
```to make sure the grub menu is updated fully to current system settings.

Once you know that is working OK, you can use gparted to remove the unwanted partitions and amalgamate them if you need to.

It would also be worth running the boot-info-script which you can get from here after carrying out my instructions, and posting the info vack here, if you have further problems.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by theozzlives on 2010-03-29
> **Cranio said:**
> Hi folks, here's my **fdisk -l**:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfa4dfa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            3697       14593    87530152+   5  Extended
/dev/sda5            6981       14277    58613121   83  Linux
/dev/sda6           14278       14593     2538238+  82  Linux swap / Solaris
/dev/sda7   *        3697        5624    15486597   83  Linux
/dev/sda8            5625        6980    10892038+  83  Linux
```

Looks like your boot flag is on sda7. You can't really join partitions, but delete one and grow another. I'd run the above boot info script before you do anything and post the RESULTS.TXT here. Just to be sure...

---

### Post by Cranio on 2010-03-29
> **theozzlives said:**
> Looks like your boot flag is on sda7. You can't really join partitions, but delete one and grow another. I'd run the above boot info script before you do anything and post the RESULTS.TXT here. Just to be sure...

Yes, "to join" was just a way to summarize :)

Anyway, ok, before doing anything I paste here my RESULT.TXT - no operation done yet whatsoever :)

And thank you both for your help and time.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4dfa4

Partition  Boot         Start           End          Size  Id System

/dev/sda2          59,376,240   234,436,544   175,060,305   5 Extended
/dev/sda5         112,133,763   229,360,004   117,226,242  83 Linux
/dev/sda6         229,360,068   234,436,544     5,076,477  82 Linux swap / Solaris
/dev/sda7    *     59,376,366    90,349,559    30,973,194  83 Linux
/dev/sda8          90,349,623   112,133,699    21,784,077  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        f7e786ff-9bb2-4355-994a-026fbdf2d0d3   ext3       OLD                           
/dev/sda6        2401bffe-5498-4d94-9e39-10ba8cd65b22   swap                                     
/dev/sda7        741b67dc-458b-4c10-9fcd-7e6e203d1464   ext4                                     
/dev/sda8        703cefd0-552d-4cfa-a94b-39f08525ac39   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/OLD               ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda8        /media/703cefd0-552d-4cfa-a94b-39f08525ac39 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro   
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro   
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro   
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro   
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 703cefd0-552d-4cfa-a94b-39f08525ac39
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=703cefd0-552d-4cfa-a94b-39f08525ac39 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 703cefd0-552d-4cfa-a94b-39f08525ac39
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=703cefd0-552d-4cfa-a94b-39f08525ac39 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=deca0cc2-b121-4127-bd69-ba974c00d154 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  33.7GB: boot/grub/core.img
  37.3GB: boot/grub/grub.cfg
  30.7GB: boot/grub/stage2
  33.7GB: boot/initrd.img-2.6.31-14-generic
  38.3GB: boot/initrd.img-2.6.31-19-generic
  39.8GB: boot/initrd.img-2.6.31-20-generic
  37.6GB: boot/initrd.img-2.6.31-9-rt
  32.9GB: boot/vmlinuz-2.6.31-14-generic
  33.9GB: boot/vmlinuz-2.6.31-19-generic
  38.4GB: boot/vmlinuz-2.6.31-20-generic
  32.6GB: boot/vmlinuz-2.6.31-9-rt
  39.8GB: initrd.img
  37.6GB: initrd.img.old
  38.4GB: vmlinuz
  32.6GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 703cefd0-552d-4cfa-a94b-39f08525ac39
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 703cefd0-552d-4cfa-a94b-39f08525ac39
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=703cefd0-552d-4cfa-a94b-39f08525ac39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 703cefd0-552d-4cfa-a94b-39f08525ac39
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=703cefd0-552d-4cfa-a94b-39f08525ac39 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 741b67dc-458b-4c10-9fcd-7e6e203d1464
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=741b67dc-458b-4c10-9fcd-7e6e203d1464 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=703cefd0-552d-4cfa-a94b-39f08525ac39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=3a773d37-c903-44c5-9642-2543b176e619 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  48.5GB: boot/grub/core.img
  48.5GB: boot/grub/grub.cfg
  47.1GB: boot/initrd.img-2.6.31-14-generic
  48.5GB: boot/vmlinuz-2.6.31-14-generic
  47.1GB: initrd.img
  48.5GB: vmlinuz
```

---

