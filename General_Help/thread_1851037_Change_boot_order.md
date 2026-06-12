---
title: "Change boot order"
date: 2011-09-27
forum: General Help
---

### Post by Alaza on 2011-09-27
Hi guys,

How can I the simplest way change boot order to ensure that I boot into Windows per default instead of Ubuntu. My setup is like this:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 567b39d7-627f-42a6-bdcc-85191b024e35 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
16 heads, 63 sectors/track, 290721 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   293,044,719   293,044,657  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   117,225,471   117,018,624   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    51,591,167    51,589,120  83 Linux
/dev/sdd2          51,593,214    72,302,591    20,709,378   5 Extended
/dev/sdd5          68,362,240    72,302,591     3,940,352  82 Linux swap / Solaris
/dev/sdd6          59,977,728    68,362,239     8,384,512  82 Linux swap / Solaris
/dev/sdd7          51,593,216    59,975,679     8,382,464  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   234,436,544   234,436,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        64F01914F018EDD4                       ntfs       1337 Raptor
/dev/sdb1        426036CE6036C905                       ntfs       Kæmpe lager
/dev/sdc1        9A4886DF4886B991                       ntfs       System Reserved
/dev/sdc2        44809068809061EA                       ntfs       OS
/dev/sdd1        567b39d7-627f-42a6-bdcc-85191b024e35   ext4       
/dev/sdd5        72c63c76-8099-4bd9-8442-41f922b7cd13   swap       
/dev/sdd6        679f0142-2a0e-4863-a628-345260477568   swap       
/dev/sdd7        cd6e27b9-d02f-414a-b860-2c715264d946   swap       
/dev/sde1        F64072D040729759                       ntfs       Lager

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=567b39d7-627f-42a6-bdcc-85191b024e35 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root 567b39d7-627f-42a6-bdcc-85191b024e35
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 9A4886DF4886B991
	chainloader +1
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

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=567b39d7-627f-42a6-bdcc-85191b024e35 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sdd7 during installation
UUID=cd6e27b9-d02f-414a-b860-2c715264d946 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.245296478 = 23.885705216   boot/grub/core.img                             1
   8.249370575 = 8.857694208    boot/grub/grub.cfg                             1
   3.075435638 = 3.302223872    boot/initrd.img-2.6.38-10-generic-pae          1
  20.505119324 = 22.017204224   boot/initrd.img-2.6.38-11-generic-pae          2
   1.255088806 = 1.347641344    boot/initrd.img-2.6.38-8-generic-pae           2
  18.856876373 = 20.247416832   boot/vmlinuz-2.6.38-10-generic-pae             1
  19.653751373 = 21.103054848   boot/vmlinuz-2.6.38-11-generic-pae             1
   0.786560059 = 0.844562432    boot/vmlinuz-2.6.38-8-generic-pae              2
  20.505119324 = 22.017204224   initrd.img                                     2
   3.075435638 = 3.302223872    initrd.img.old                                 1
  19.653751373 = 21.103054848   vmlinuz                                        1
  18.856876373 = 20.247416832   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by collisionystm on 2011-09-27
Just install startup-manager from the software center.

---

### Post by Basher101 on 2011-09-27
Thats very easy. Before i can write down the correct commands, do you have any "older version of ubuntu" option on startup? You will have to delete the older kernels through synaptic, otherwise the bootentries will change from kernel update to update.

edit: or just use the startup manager..

---

### Post by collisionystm on 2011-09-27
Keep in mind that everytime your system installs a new kernel, you will need to update your default OS option in startup manager. The software is not smart enough to recognize the specific OS you want, it just goes by what line you have chosen in the code.

---

### Post by Mark Phelps on 2011-09-28
> Just install startup-manager from the software center. 
Except ... that startup-manager does not work well with recent GRUB2 versions.  Should switch to GRUB-Customizer, instead.

> **collisionystm said:**
> Keep in mind that everytime your system installs a new kernel, you will need to update your default OS option in startup manager. 

If, instead of chang the stanza number in the DEFAULT line, you place the full text of the boot stanza, surrounded by double-quotes (as in DEFAULT="Windows 7 Boot Loader on (xxxx)" ), the addition of more kernel entries will not affect the default boot anymore.

---

### Post by Alaza on 2011-10-12
Sorry I haven't replied earlier.

I just tried to install the startup-manager and set the 10 second timer down to 2. And furthermore I set the default OS to Win7. It changes the time, but the default OS is still Ubuntu. How do I solve that?

Thank you

---

### Post by Mark Phelps on 2011-10-12
Try reading my post ... where I told you that startupmanager doesn't work well anymore ...

---

