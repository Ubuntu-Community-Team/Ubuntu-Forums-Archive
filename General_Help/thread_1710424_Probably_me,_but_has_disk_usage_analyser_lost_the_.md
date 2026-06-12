---
title: "Probably me, but has disk usage analyser lost the plot?"
date: 2011-03-19
forum: General Help
---

### Post by cjww on 2011-03-19
Hi All,

So if my files system is 5.4gb and total file system capacity 13.5gb, how come I only got 1gb free -I guess I must be reading this wrong, but I make that around 6gb free?

Please see attached screen.

Cheers

Ubuntu 10.4

---

### Post by Hedgehog1 on 2011-03-19
I think you have separate partitions for '/' and directories, and have filled the '/' one up.

If you would do the following; we can guide you in resizing the partitions to match the real data in them:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

This will tell us how system is booting and why there is an error.

***The Hedge***

:KS

p.s. Thanks for the picture; things like that do help!

---

### Post by cjww on 2011-03-19
Many thanks for your reply Hedge, below is the outcome of the script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    82,718,684    82,718,622   7 HPFS/NTFS
/dev/sda3          82,718,935   234,436,544   151,717,610   f W95 Ext d (LBA)
/dev/sda5          82,769,920   111,521,791    28,751,872  83 Linux
/dev/sda6         111,523,293   115,635,869     4,112,577  82 Linux swap / Solaris
/dev/sda7         115,635,933   234,436,544   118,800,612   7 HPFS/NTFS
/dev/sda8          82,718,937    82,766,879        47,943   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        447CAD497CAD3698                       ntfs       Programs                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4256ef1a-7648-43af-b072-177e8bc9f03e   ext4                                     
/dev/sda6        94e83ba5-0cab-424e-bd24-06f2edcd57ff   swap                                     
/dev/sda7        01C975DCE4EAD560                       ntfs       documents                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4256ef1a-7648-43af-b072-177e8bc9f03e ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4256ef1a-7648-43af-b072-177e8bc9f03e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 447cad497cad3698
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4256ef1a-7648-43af-b072-177e8bc9f03e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=94e83ba5-0cab-424e-bd24-06f2edcd57ff none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.2GB: boot/grub/core.img
  52.6GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.32-21-generic
  47.5GB: boot/initrd.img-2.6.32-24-generic
  52.0GB: boot/initrd.img-2.6.32-25-generic
  52.3GB: boot/initrd.img-2.6.32-26-generic
  56.4GB: boot/initrd.img-2.6.32-27-generic
  50.1GB: boot/initrd.img-2.6.32-28-generic
  53.9GB: boot/initrd.img-2.6.32-29-generic
  54.5GB: boot/initrd.img-2.6.32-30-generic
  51.7GB: boot/vmlinuz-2.6.32-21-generic
  46.4GB: boot/vmlinuz-2.6.32-24-generic
  43.9GB: boot/vmlinuz-2.6.32-25-generic
  53.9GB: boot/vmlinuz-2.6.32-26-generic
  55.5GB: boot/vmlinuz-2.6.32-27-generic
  56.0GB: boot/vmlinuz-2.6.32-28-generic
  52.7GB: boot/vmlinuz-2.6.32-29-generic
  54.5GB: boot/vmlinuz-2.6.32-30-generic
  54.5GB: initrd.img
  53.9GB: initrd.img.old
  54.5GB: vmlinuz
  52.7GB: vmlinuz.old

```

---

### Post by ~Plue on 2011-03-19
try running the disk usage analyzer as root. then it'll include the results of /root and other stuff  which you dont have permissions to see as a normal user
```
gksu baobab
```

---

### Post by cjww on 2011-03-19
Many thanks Verbeck and The Hedge for your help.

It turned out that root's trash was taking up the extra space-once I'd emptied it disk usage analyser reported 8gb free.

Cheers,

Carl

---

