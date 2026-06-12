---
title: "Problems booting Ubuntu after HD crash"
date: 2010-11-13
forum: General Help
---

### Post by JCon on 2010-11-13
I've searched the forum but have not found a solution. Perhaps my searches are asking the wrong question. Anyhow...

I was experiencing issues with my Vista install. It crashed and froze me out of rebooting. I had recently downloaded and edited a bunch of photos which I had not backed up yet (I know, I know). Anyhow, when this issue had previously happened I had installed Ubuntu and was able to retrieve any lost data (about two years ago). Over time I removed Ubuntu to create more HD space. When the most recent crash happened I tried Ubuntu 10.10. I mounted it on a back-up HD and was able to recover all my 'lost' photos. Phew! It booted fine and always asked me to choose 

It turns out the reason Vista crashed, or so it seems, was that my primary HD was failing. It has subsequently failed and will not boot. Thankfully everything was backed up now. 

However, now Ubuntu won't boot. I can see the partition when I load my Ubuntu CD, so I know it still exists, but I am never given any option when booting my computer. I tried changing the BIOS to only load from the HD and even ordered it correctly. The only message I get when I try to boot is asking for the system disk. 

I have two HDs currently working. One has data and the other has my back-ups and the Ubuntu partition. Vista was only loaded on the HD that has now failed. 

Any advice I can get would be greatly appreciated.

---

### Post by Rubi1200 on 2010-11-13
Hi and welcome to the forums :)

Please use the Ubuntu LiveCD and follow the instructions in the link at the bottom of my post.

Post the results back here to the forums.

Thanks.

---

### Post by JCon on 2010-11-13
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,364,145,349 1,364,143,302   7 HPFS/NTFS
/dev/sda2       1,364,146,174 1,953,523,711   589,377,538   5 Extended
/dev/sda5       1,364,146,176 1,929,758,719   565,612,544  83 Linux
/dev/sda6       1,929,760,768 1,953,523,711    23,762,944  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0676AFA776AF9649                       ntfs       Back Up                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        dc5fea80-64a9-4aa6-ab18-61ba170a512c   ext4                                     
/dev/sda6        5366668d-c46e-4a6a-8d71-3ec369363022   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EE3447243446EF61                       ntfs       Media Storage                 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc5fea80-64a9-4aa6-ab18-61ba170a512c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc5fea80-64a9-4aa6-ab18-61ba170a512c ro single 
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set dc5fea80-64a9-4aa6-ab18-61ba170a512c
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
# / was on /dev/sdc5 during installation
UUID=dc5fea80-64a9-4aa6-ab18-61ba170a512c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=5366668d-c46e-4a6a-8d71-3ec369363022 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 971.3GB: boot/grub/core.img
 947.8GB: boot/grub/grub.cfg
 827.0GB: boot/initrd.img-2.6.35-22-generic
 971.3GB: boot/vmlinuz-2.6.35-22-generic
 827.0GB: initrd.img
 971.3GB: vmlinuz

---

### Post by Rubi1200 on 2010-11-13
If I understood your original post correctly, sdb is the failed drive with Vista and sda is the drive with Ubuntu and backups (but not a bootable Windows system); right?

To get Ubuntu up and running again, you need to use a LiveCD and follow these instructions:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Once the computer boots again, run this:

```
sudo update-grub
```

If you have any questions, please feel free to ask.

---

### Post by JCon on 2010-11-13
> **Rubi1200 said:**
> If I understood your original post correctly, sdb is the failed drive with Vista and sda is the drive with Ubuntu and backups (but not a bootable Windows system); right?

Correct. Thank-you! I will try what you've suggested and report back.

---

### Post by JCon on 2010-11-13
It worked! Thank-you so much! I really appreciate you taking time out to help me.

---

### Post by Rubi1200 on 2010-11-13
No problem, you are more than welcome :)

---

