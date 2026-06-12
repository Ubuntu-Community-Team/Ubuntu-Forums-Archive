---
title: "Can't boot to Windows 7 after installing Ubuntu 10.10"
date: 2011-01-18
forum: General Help
---

### Post by AN@S on 2011-01-18
Hello, 

Yesterday I've got my brand new Vaio with Windows 7 pre-installed. I've previously installed Ubuntu alongside Windows many times before without any issue, but I have no idea what happened yesterday :(

On the boot menu I have three options: Ubuntu, which loads just fine and "Windows 7 (loader) (on /dev/sda2)" in addition to a weird third option "Windows Vista (loader) (on /dev/sda1)" which I have no idea where did it come from, which I guess is some misconfiguration from Sony or something.

When I try to boot on "Windows 7 (loader)", windows seems booting but then some window appear saying that Windows is trying to repair something but it fails saying:"Startup Repair cannot repair this computer automatically"

When trying to boot on "Windows Vista" option -which is not an actual Windows Vista installation but some mistake from Sony- a recovery (Vaio branded) software appear gives me some options to recover Windows but it then says:"OS not detected on the C: drive. Cannot boot into Windows".

Now here is the interesting part of my grub.cfg

```

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b94cd233-4cbf-419e-afac-6a23ff9d8aaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b94cd233-4cbf-419e-afac-6a23ff9d8aaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b94cd233-4cbf-419e-afac-6a23ff9d8aaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b94cd233-4cbf-419e-afac-6a23ff9d8aaa ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set b94cd233-4cbf-419e-afac-6a23ff9d8aaa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ec2a24fd2a24c704
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7efa4ef8fa4eac69
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

And here is my fdisk -l:


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4ff3ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1370    11002880   27  Unknown
/dev/sda2   *        1370        1383      102400    7  HPFS/NTFS
/dev/sda3            1383       60802   477278209    5  Extended
/dev/sda5            1383       25698   195311616    b  W95 FAT32
/dev/sda6           25699       26671     7811072   82  Linux swap / Solaris
/dev/sda7           26671       60802   274153472   83  Linux

```

Can anyone help? Thanks :)

---

### Post by oj0kksn5 on 2011-01-18
looks like windows 7 think it isn't booting up correctly and if that happens it will auto boot into recovery mode and the vista thing is obvs a sony thing. If you have just got ur new sony and have no data etc on it just wipe the hdd and start over probs easier or try going through the win7 recovery as sometimes it fixes itself.

---

### Post by Mark Phelps on 2011-01-18
Yesterday, huh.  Looks like you wasted no time "breaking" your brand new PC!

You should have first used the Backup feature to create and burn a Win7 Repair CD.  You could be using that now to restore the Win7 Boot Loader and get your machine back.

IF you don't have that CD, go to the link below, download and burn the proper Win7 Repair CD, boot from it, and run Startup Repair three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

IF that claims it can't find a Win7 to repair, there's the possibility that you simply ovewrwrote it in your hurry to install Ubuntu.  To check that, open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions and at least show if the Win7 partition is still there.

---

### Post by oldfred on 2011-01-18
If it is a standard new win7 install the sda1 is a vendor recovery, sda2 is the small windows boot partition and sda3 is the main windows install. Often then sda4 is a utilities partition just to make sure they have used all 4 primary partitions and make it difficult to install anything else.

But sda3 is now the extended partition.

---

### Post by AN@S on 2011-01-19
> **Mark Phelps said:**
> Yesterday, huh.  Looks like you wasted no time "breaking" your brand new PC!

You should have first used the Backup feature to create and burn a Win7 Repair CD.  You could be using that now to restore the Win7 Boot Loader and get your machine back.

IF you don't have that CD, go to the link below, download and burn the proper Win7 Repair CD, boot from it, and run Startup Repair three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

IF that claims it can't find a Win7 to repair, there's the possibility that you simply ovewrwrote it in your hurry to install Ubuntu.  To check that, open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions and at least show if the Win7 partition is still there.

Thanks, I'll download and try the recovery CD method and report back :)

---

### Post by Quackers on 2011-01-19
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by king123440 on 2011-08-10
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   154,957,313   154,955,266  83 Linux
/dev/sda2         154,957,822   312,580,095   157,622,274   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris
/dev/sda6         154,957,824   300,300,287   145,342,464  83 Linux
/dev/sda7         300,302,336   306,440,191     6,137,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8d8d5145-be6b-4a5e-a49a-58ae479132d6   ext4       
/dev/sda5        fa069917-5363-43f3-8dc9-583d8f5b52e1   swap       
/dev/sda6        89c41c39-7b2a-4570-9300-4756945b854a   ext4       
/dev/sda7        64d8d2bb-6ff3-41e5-9cfa-a714be4fb760   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.382537842 = 0.410746880    boot/vmlinuz-2.6.35-22-generic                 2
   0.382537842 = 0.410746880    vmlinuz                                        2

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=89c41c39-7b2a-4570-9300-4756945b854a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=89c41c39-7b2a-4570-9300-4756945b854a ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 89c41c39-7b2a-4570-9300-4756945b854a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8d8d5145-be6b-4a5e-a49a-58ae479132d6
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=89c41c39-7b2a-4570-9300-4756945b854a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=64d8d2bb-6ff3-41e5-9cfa-a714be4fb760 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 132.095127106 = 141.836062720  boot/grub/core.img                             1
  94.038440704 = 100.973006848  boot/grub/grub.cfg                             1
  94.157478333 = 101.100822528  boot/initrd.img-2.6.35-22-generic              1
 132.093597412 = 141.834420224  boot/vmlinuz-2.6.35-22-generic                 1
  94.157478333 = 101.100822528  initrd.img                                     1
 132.093597412 = 141.834420224  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 
```

---

### Post by Basher101 on 2011-08-10
Shouldn't it output some NTFS partitions with windows? Thats certainly odd

---

### Post by Mark Phelps on 2011-08-10
king123440: Did you hijack this 6-month-old thread because you have a similar problem?  If so, please do NOT do that.

Instead, start your own thread -- and how about adding some descriptive text as well -- instead of expecting us to read your post and GUESS at what your problem happens to be.

---

