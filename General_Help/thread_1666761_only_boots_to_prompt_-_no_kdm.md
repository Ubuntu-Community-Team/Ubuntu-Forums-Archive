---
title: "only boots to prompt - no kdm"
date: 2011-01-14
forum: General Help
---

### Post by tjk on 2011-01-14
I cannot boot (k)ubuntu (version 10.04 - 64-bit).  I get to the prompt and that's it.  I've tried all kinds of things:
  tried booting through recovery
  tried using sudo /etc/init.d/kdm start
    and sudo kdm start
    and startx
I've verified that all the partitions are there and no files seem to be missing.
I've removed and then reinstalled kdm
I've tried sudo apt-get install kubuntu-desktop
I can't think of what else to try.  

Help please!!

---

### Post by tjk on 2011-01-14
Anyone?

---

### Post by tjk on 2011-01-14
Okay... here's some additional information about my setup.  Can anyone see something that may be causing the problem from this?
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.9 GB, 250999111168 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490232639 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       401,624       401,562  83 Linux
/dev/sda2             401,686   174,465,899   174,064,214   5 Extended
/dev/sda5             401,688    61,834,184    61,432,497  83 Linux
/dev/sda6          61,834,248   113,033,339    51,199,092  83 Linux
/dev/sda7         113,033,403   174,465,899    61,432,497  83 Linux
/dev/sda3         486,126,900   490,223,474     4,096,575  82 Linux swap / Solaris
/dev/sda4         174,465,900   486,126,899   311,661,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a6d67867-7652-4a47-9329-746a11547151   ext2                                     
/dev/sda1        e616bf97-4a4e-4717-8a24-560651d8689f   ext4                                     
/dev/sda3                                               swap                                     
/dev/sda4        5adb1c20-13cf-4858-9e47-0d0223a6ef66   ext2       DATA                          
/dev/sda5        3148f80f-f16a-4e53-af6f-0afd3195d06a   ext4                                     
/dev/sda6        45da3721-5860-401f-8034-58988f21576c   ext4       homepart                      
/dev/sda7        d424024d-9432-4c63-9f19-73c68a6b252e   ext2       OTHER                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=7a884342)
/dev/sda4        /initrd/mnt/dev_save     ext2       (rw,noatime,errors=continue)
/dev/loop1       /initrd/pup_rw           ext2       (rw,noatime,errors=continue)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 3148f80f-f16a-4e53-af6f-0afd3195d06a
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux	/vmlinuz-2.6.32-27-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro   quiet splash
	initrd	/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/vmlinuz-2.6.32-27-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux	/vmlinuz-2.6.32-26-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro   quiet splash
	initrd	/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/vmlinuz-2.6.32-26-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux	/vmlinuz-2.6.32-25-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro   quiet splash
	initrd	/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/vmlinuz-2.6.32-25-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux	/vmlinuz-2.6.32-24-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro   quiet splash
	initrd	/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/vmlinuz-2.6.32-24-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux	/vmlinuz-2.6.32-21-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e616bf97-4a4e-4717-8a24-560651d8689f
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: initrd.img-2.6.32-25-generic
    .1GB: initrd.img-2.6.32-26-generic
    .1GB: initrd.img-2.6.32-27-generic
    .0GB: vmlinuz-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-25-generic
    .0GB: vmlinuz-2.6.32-26-generic
    .0GB: vmlinuz-2.6.32-27-generic

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
UUID=3148f80f-f16a-4e53-af6f-0afd3195d06a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e616bf97-4a4e-4717-8a24-560651d8689f /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=45da3721-5860-401f-8034-58988f21576c /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 81 00 00 d5 26 01 00  8f 2a 46 4c 8e 2a 46 4c  |.....&...*FL.*FL|
00000010  16 ca 0c 4c 00 00 00 00  00 00 01 00 98 00 00 00  |...L............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  13 00 00 00 c8 8d 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 e9 79 59 89  00 00 00 00 00 00 00 00  |.....yY.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 f4 08 4a a8  00 00 00 00 9c 67 f9 d7  |......J......g..|
00000090  63 2a 46 4c 88 06 70 ce  00 00 00 00 00 00 00 00  |c*FL..p.........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ed 81 00 00 30 05 00 00  8f 2a 46 4c 8e 2a 46 4c  |....0....*FL.*FL|
00000110  18 ca 0c 4c 00 00 00 00  00 00 01 00 08 00 00 00  |...L............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 bf 85 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 ea 79 59 89  00 00 00 00 00 00 00 00  |.....yY.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 f4 08 4a a8  00 00 00 00 3c 6a 39 a6  |......J.....<j9.|
00000190  63 2a 46 4c 88 06 70 ce  00 00 00 00 00 00 00 00  |c*FL..p.........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  01 19 83 fe ff ff 02 00  00 00 b1 62 a9 03 00 fe  |...........b....|
000001d0  ff ff 05 fe ff ff b3 62  a9 03 b3 3c 0d 03 00 00  |.......b...<....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdb sdc sdd sde sdf sdg sdh sdi 

```

---

### Post by tjk on 2011-01-14
***Anyone can jump in and help out... I still haven't solved the problem.***

Here's the latest:
  I was able to install the LXDE desktop manager (login screen) and the window does appear when booting, but it does not accept my password(or user name).  So I tried installing KDM again, but it was the same old thing -- ended boot with prompt. (However, I did notice that the graphic mouse cursor did appear briefly before I was sent to the prompt.)
  I wanted to add something to this situation... the last thing I remember doing before this problem started was: I renamed /tmp to /tmp.bak so that I could install a Windows program under wine.  When I was done I renamed the backup folder to /tmp again. All this was done with root permissions.  (Although in all of this hacking the last couple of days I renamed it to /tmp.bak again and then tried rebooting (k)ubuntu, so that a new /tmp folder was created during the boot process... but this didn't help either.  If I recall correctly I've messed around with the /tmp folder before without any problems, that's why I didn't think it would have contributed to my current situation.
  Hopefully someone will help out soon... this has got me very frustrated and confused.

---

### Post by tjk on 2011-01-14
bump

---

### Post by tjk on 2011-01-15
I hate having to bump, but I really need some help with this...

---

