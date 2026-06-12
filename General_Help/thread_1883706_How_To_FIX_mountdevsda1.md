---
title: "How To FIX mount/dev/sda1"
date: 2011-11-19
forum: General Help
---

### Post by esg10 on 2011-11-19
Hi, I'm currently using UBUNTU 11.10 with Lubuntu installed you know, the desktops....

I have a problem when I boot or re boot. 

"error mounting mount/dev/sda1"  its what I see on my screen right after I get passed bios. 
 Any help kindly appreciated thanks.:(:(

---

### Post by Bobhuber on 2011-11-19
> **esg10 said:**
> Hi, I'm currently using UBUNTU 11.10 with Lubuntu installed you know, the desktops....

I have a problem when I boot or re boot. 

"error mounting mount/dev/sda1"  its what I see on my screen right after I get passed bios. 
 Any help kindly appreciated thanks.:(:(
It looks like your trying to mount sda1 thru fstab entry. If mount is the directory you are using for a mount point  .
/mount /dev/sda1
You should really be using device by UUID entries instead of /dev/sda1 as sda1 will magically change its name occasionally.
Here's one of mine as an example only  >  /dev/disk/by-uuid/676425de-eb34-47b6-b66d-ad27a1167d89 /media/natty    ext4     user     0     2
blkid    from a terminal will give you the correct UUID for your partitions.

You can use Google for more info.

---

### Post by JC Cheloven on 2011-11-19
Please post the output od these commands at terminal:
```
cat /etc/fstab
``` ```
sudo blkid
```
Thank you.

---

### Post by esg10 on 2011-11-19
This is what I got:

steve@Steve:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
sudo mount/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3a3cf7ea-95b7-48a0-a213-47b8a7133843 none            swap    sw              0       0
steve@Steve:~$ sudo blkid
[sudo] password for steve: 
/dev/sda1: UUID="eda79df6-f1e7-472c-b4d9-94dcc82fba37" TYPE="ext4" 
/dev/sda5: UUID="3a3cf7ea-95b7-48a0-a213-47b8a7133843" TYPE="swap" 
/dev/sdb1: UUID="0C78-E3AD" TYPE="vfat" 
steve@Steve:~$

---

### Post by JC Cheloven on 2011-11-19
For future ocasions: If you put the output beteen code tags (using the # symbol in the mini bar tools at the top ot the writing area), it looks clearer:
```
steve@Steve:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
sudo mount/dev/sda1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=3a3cf7ea-95b7-48a0-a213-47b8a7133843 none swap sw 0 0 
```

```
steve@Steve:~$ sudo blkid
[sudo] password for steve:
/dev/sda1: UUID="eda79df6-f1e7-472c-b4d9-94dcc82fba37" TYPE="ext4"
/dev/sda5: UUID="3a3cf7ea-95b7-48a0-a213-47b8a7133843" TYPE="swap"
/dev/sdb1: UUID="0C78-E3AD" TYPE="vfat"
steve@Steve:~$
```

So, to the matter: your /etc/fstab file contains a command intended to be run from  terminal (well, kind of), not proper for this file. Please edit the file (gksudo gedit /etc/fstab) and replace this line
```
sudo mount/dev/sda1 / ext4 errors=remount-ro 0 1
```
with this one:
```
UUID=eda79df6-f1e7-472c-b4d9-94dcc82fba37 / ext4 errors=remount-ro 0 1
```

It should fix it.

---

### Post by esg10 on 2011-11-20
wow, THank you JC CHELOVEN! you seem like you really know how to get stuff done!

now, I have one more problem,... how do I get my computer to read my music and dvd cd?  Whenever I put in a blank cd... it recognizes it and asks what to do with it, but when I put music in... it just spins for a few seconds then stays in there like nothing...

---

### Post by JC Cheloven on 2011-11-22
Sorry, I was away yesterday. So as for your new question:
> **esg10 said:**
> now, I have one more problem,... how do I get my computer to read my music and dvd cd?  Whenever I put in a blank cd... it recognizes it and asks what to do with it, but when I put music in... it just spins for a few seconds then stays in there like nothing...

It depends on the file manager you're using, which in turn depends on what environment you're on. If you're using regular Ubuntu, you're using the nautilus file manager. In that case open it, go to edit->preferences, click on the devices tab (or something similar, I don't have a nautilus at hand right now), and you can choose from that the action the system should perform when you insert a media of each category (cd, dvd, usb stick, etc).

I don't use gnome myself (so no nautilus), but lxde, which has the pcmanfm file manager. Here we have a similar option.

Enjoy!

---

### Post by morningsunshine on 2011-12-04
Facing a similar issue. Don't mean to hijack this thread. But seems the OP got the answer.

I've updated the kernet to .36 today. And upon reboot, it gives a UUID not found error, & drops to busybox.

I looked in the forums & edited in the boot entry, the UUID to /dev/sda1.

I can boot now but this change is not permanent.

I've run the boot info script. Can someone help me understand what's wrong with the boot config?
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 579083392 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 1 for /boot/grub.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   953,374,719   953,372,672  83 Linux
/dev/sda2         953,376,766   976,773,119    23,396,354   5 Extended
/dev/sda5         953,376,768   976,773,119    23,396,352  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        b22454a2-33c9-45b0-96d9-4f67c3de3a31   ext4       
/dev/sda5        a75f54d9-444c-4d03-999f-8b9b07ad192a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-36-generic ...'
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b22454a2-33c9-45b0-96d9-4f67c3de3a31
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b22454a2-33c9-45b0-96d9-4f67c3de3a31 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=a75f54d9-444c-4d03-999f-8b9b07ad192a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 276.128505707 = 296.490725376  boot/grub/core.img                             1
 108.735588074 = 116.753948672  boot/grub/grub.cfg                             1
 276.266422272 = 296.638812160  boot/initrd.img-2.6.32-24-generic              1
  44.040409088 = 47.288029184   boot/initrd.img-2.6.32-25-generic              2
 124.638504028 = 133.829574656  boot/initrd.img-2.6.32-26-generic              2
 133.764972687 = 143.629045760  boot/initrd.img-2.6.32-32-generic              2
 130.051261902 = 139.641479168  boot/initrd.img-2.6.32-33-generic              2
 348.508182526 = 374.207811584  boot/initrd.img-2.6.32-36-generic              2
 276.258655548 = 296.630472704  boot/vmlinuz-2.6.32-24-generic                 1
 276.274215698 = 296.647180288  boot/vmlinuz-2.6.32-25-generic                 1
 276.277988434 = 296.651231232  boot/vmlinuz-2.6.32-26-generic                 1
 276.254749298 = 296.626278400  boot/vmlinuz-2.6.32-32-generic                 1
 276.445960999 = 296.831590400  boot/vmlinuz-2.6.32-33-generic                 1
 347.524284363 = 373.151358976  boot/vmlinuz-2.6.32-36-generic                 1
 348.508182526 = 374.207811584  initrd.img                                     2
 130.051261902 = 139.641479168  initrd.img.old                                 2
 347.524284363 = 373.151358976  vmlinuz                                        1
 276.445960999 = 296.831590400  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

```

Thanks.

---

