---
title: "Fresh Ubuntu install won't boot"
date: 2012-05-21
forum: General Help
---

### Post by Jolladay on 2012-05-21
Hi there,

I just did a fresh Ubuntu 11.10 minimal CLI install from a USB stick to an external HDD connected through ESATA-P. The installation seemed to go fine.

When I boot up to the external hdd, it hangs on a screen with just a cursor flashing. If I choose recovery console in grub and run fsck, then select resume boot it will boot just fine. This happens every time.

Any help is greatly appreciated!

-Jolladay

---

### Post by wilee-nilee on 2012-05-21
> **Jolladay said:**
> Hi there,

I just did a fresh Ubuntu 11.10 minimal CLI install from a USB stick to an external HDD connected through ESATA-P. The installation seemed to go fine.

When I boot up to the external hdd, it hangs on a screen with just a cursor flashing. If I choose recovery console in grub and run fsck, then select resume boot it will boot just fine. This happens every time.

Any help is greatly appreciated!

-Jolladay

Have you run in the booted ubuntu.

```
sudo update-grub
```

---

### Post by Jolladay on 2012-05-22
Hi,

I tried both sudo update-grub and sudo update-grub2, both of which spit out:


```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found memtest86+ image: /boot/memtest96+.bin
done
```

I then do sudo reboot, select the default in grub and it still goes to the blank/flashing cursor screen and hangs. If I then hit ctrl+alt+del to restart the system and run fsck -> resume boot, it goes in fine. So I still have to run fsck every time. :(

---

### Post by wilee-nilee on 2012-05-22
Hmm to really know what your set up is the bootscript might help, here is a link and a command to run it if you extract it to the ubuntu  desktop, just extra info really post the results.txt if you want.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by Jolladay on 2012-05-22
That's a nifty script, here's the output (sdb is just a flash drive that is not there when I am trying to boot normally)

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    76,087,295    76,085,248  83 Linux
/dev/sda2          76,089,342    78,163,967     2,074,626   5 Extended
/dev/sda5          76,089,344    78,163,967     2,074,624  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 254     1,952,767     1,952,514   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        586c0e22-47f0-4f93-b46c-75e43509b1d3   ext4       
/dev/sda5        0aef5df4-3be4-4ef4-9ba6-ac6d835eea11   swap       
/dev/sdb1        8006-A0A3                              vfat       DRIVERTECH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/external          vfat       (rw,uid=1000,gid=1000,utf8,dmask=027,fmask=137)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=586c0e22-47f0-4f93-b46c-75e43509b1d3 ro   splash quiet vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=586c0e22-47f0-4f93-b46c-75e43509b1d3 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 586c0e22-47f0-4f93-b46c-75e43509b1d3
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=586c0e22-47f0-4f93-b46c-75e43509b1d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0aef5df4-3be4-4ef4-9ba6-ac6d835eea11 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-19-generic               2
               =                boot/vmlinuz-3.0.0-19-generic                  2
               =                initrd.img                                     2
               =                vmlinuz                                        2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by wilee-nilee on 2012-05-22
So the ESATA-P is just the plugin type to the computer is this correct? Not sure of any effect this can have on booting.

Is the external your only HD? 

I see a sda HD that looks like it should boot in, not sure why it does not just go straight in.

---

### Post by Jolladay on 2012-05-22
Yep, it's just a type of connection. The external HDD also has USB, which I have tried with the same results. I do have other hard drives and have tried it on various drives, all with the same results.

---

### Post by Jolladay on 2012-05-22
This thread can be marked as solved. 

To fix the problem I had to modify /etc/default/grub.

I had to add the line GRUB_GFXPAYLOAD_LINUX=text and voila, it works great! I also set GRUB_CMDLINE_LINUX=text instead of quiet splash. I think vt.handoff=7 was also causing problems. I'm thinking that this was necessary because the distro I'm using is "limited" or whatever it's called, command line only. Thus, maybe it was getting confused looking for a gfx driver or something.

Thanks for the help everyone!

-Jolladay

---

