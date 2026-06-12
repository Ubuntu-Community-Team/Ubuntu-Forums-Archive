---
title: "Ubuntu 10.4 gone!"
date: 2011-10-03
forum: General Help
---

### Post by astro4travel on 2011-10-03
I recently installed Pardis Linux on my second hard drive. My Ubuntu 10.4 was on /dev/sda5 (first hard drive) which was being duel booted with Window's XP.When I installed Pardis Linux on the second hard drive it had the legacy Grub menu which only showed Windows XP and Pardis. Ubuntu 10.4 was not there. How can I recover the Ubuntu 10.4 partion that Grub 2 was on. Thanks for any help on this.

---

### Post by drs305 on 2011-10-03
If your Ubuntu is a non-Wubi installation, you could probably regain Grub 2 control of things by booting a Live CD and reinstalling Grub 2. It will point the sda MBR back to your Ubuntu installation, as long as the Ubuntu drive is the one that the MBR boots first.

Note: If your Ubuntu installation is within Windows (not on it's own partition), do not run these commands.
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If it boots to the normal Ubuntu Desktop, run the following so it can find your other Linux OS:
```
sudo update-grub
```

If this doesn't work, please download and run the boot info script and post the contents of RESULTS.txt. You can go to the script page by clicking the "BIS" link in my signature line.

---

### Post by astro4travel on 2011-10-04
I used the "Grub Rescue disk" to get into 10.4. Here are my results. Thanks.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [0;33;01;37mPardus GNU/Linux 
                       [0;33;00;32m[0;33;01;37m[0;33;00;36m[0;33;01;36m([
                       0;33;01;32m [0;33;01;36m) [0;37;40m
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   215,545,855   215,545,793   7 NTFS / exFAT / HPFS
/dev/sda2         215,547,902   312,578,047    97,030,146   5 Extended
/dev/sda5         215,547,904   308,514,815    92,966,912  83 Linux
/dev/sda6         308,516,864   312,578,047     4,061,184  82 Linux swap / Solaris
/dev/sda4         312,578,048   312,580,095         2,048   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63     6,293,503     6,293,441   7 NTFS / exFAT / HPFS
/dev/sdb2           6,293,504   487,757,823   481,464,320   7 NTFS / exFAT / HPFS
/dev/sdb3    *    487,757,824   625,141,759   137,383,936  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        78654F614A3A0763                       ntfs       
/dev/sda5        c2b412a4-3000-4b83-b793-9838faf41e54   ext4       
/dev/sda6        1da8720a-630c-4c19-ae35-7e921eb5164d   swap       
/dev/sdb1        10B057BB24AA88D4                       ntfs       
/dev/sdb2        73742CB41375DDA1                       ntfs       
/dev/sdb3        949f1644-0015-4dc8-ac88-4f7cb147314a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c2b412a4-3000-4b83-b793-9838faf41e54 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c2b412a4-3000-4b83-b793-9838faf41e54 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 78654F614A3A0763
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Pardus 2011.2 Cervus elaphus (on /dev/sdb3)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 949f1644-0015-4dc8-ac88-4f7cb147314a
	linux /boot/kernel-2.6.37.6 root=UUID=949f1644-0015-4dc8-ac88-4f7cb147314a resume=/dev/sda6 splash quiet
	initrd /boot/initramfs-2.6.37.6
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c2b412a4-3000-4b83-b793-9838faf41e54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1da8720a-630c-4c19-ae35-7e921eb5164d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 118.915992737 = 127.685074944  boot/grub/core.img                             1
 118.920864105 = 127.690305536  boot/grub/grub.cfg                             1
 119.038661957 = 127.816790016  boot/initrd.img-2.6.32-24-generic              1
 118.997150421 = 127.772217344  boot/vmlinuz-2.6.32-24-generic                 1
 119.038661957 = 127.816790016  initrd.img                                     1
 118.997150421 = 127.772217344  vmlinuz                                        1

============================= sdb1/grub/grub.cfg: ==============================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c2b412a4-3000-4b83-b793-9838faf41e54
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
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 10B057BB24AA88D4
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 78654F614A3A0763
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1

========================== sdb3/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
default 1
gfxmenu /boot/grub/message
background 10333C
timeout 10

title Pardus 2011.2 Cervus elaphus
uuid 949f1644-0015-4dc8-ac88-4f7cb147314a
kernel /boot/kernel-2.6.37.6 root=UUID=949f1644-0015-4dc8-ac88-4f7cb147314a resume=/dev/sda6 splash quiet
initrd /boot/initramfs-2.6.37.6

title Windows on /dev/sda1
map (hd0) (hd1,0)
map (hd1,0) (hd0)
rootnoverify (hd1,0)
makeactive 
chainloader +1
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# Created by YALI on Sun Oct  2 20:38:50 2011
#
UUID=949f1644-0015-4dc8-ac88-4f7cb147314a /                       ext4    defaults        1 1
UUID=1da8720a-630c-4c19-ae35-7e921eb5164d swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   nodev,nosuid,noexec 0 0
debugfs                 /sys/kernel/debug       debugfs debugfs,defaults 0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 294.813438416 = 316.553519104  boot/grub/grub.conf                            1
 294.813438416 = 316.553519104  boot/grub/menu.lst                             1
 256.709831238 = 275.640082432  boot/grub/stage2                               1
 233.276657104 = 250.478903296  boot/initramfs-2.6.37.6                        2


```

---

### Post by WorMzy on 2011-10-04
You have two options. You can either

[LIST=A]
[*]Configure grub legacy to be able to boot into Ubuntu (easiest), or
[*]Re-install grub2 and update it so it can boot into Pardis
[/LIST]

drs has already told you have to do option B, so I'll tell you what you need for option A.

From Pardis, open up /boot/grub/menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

and add the following to the file, wherever you want the menu item to appear (e.g. between Pardis's entry, and Window's entry):

```
title        kernel 2.6.32-24-generic
root         (hd1,4)
kernel       /boot/vmlinuz-2.6.32-24-generic root=UUID=c2b412a4-3000-4b83-b793-9838faf41e54 ro quiet splash
initrd       /boot/initrd.img-2.6.32-24-generic
```

Save the file, and voila.

---

### Post by astro4travel on 2011-10-04
Thanks I'll give the Legacy one a shot tonight and let you know how it goes.

---

### Post by astro4travel on 2011-10-04
Did option A and success! The Ubuntu kernel is now in the Pardis boot menu. Thanks for the help.):P

---

