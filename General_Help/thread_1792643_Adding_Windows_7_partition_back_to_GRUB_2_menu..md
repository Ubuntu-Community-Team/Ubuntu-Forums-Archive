---
title: "Adding Windows 7 partition back to GRUB 2 menu."
date: 2011-06-28
forum: General Help
---

### Post by elsewares on 2011-06-28
For whatever reason, upgrading to Natty on my dual-boot machine removed the option to boot into my Windows 7 partition.  The partition is still there, and I hope otherwise unaffected.  After several searches, I haven't found instructions on how to add the partition back into the GRUB menu - just how to repair GRUB after installing Windows (the inverse problem).

To further complicate things, I've checked to make sure that I have GRUB2 (grub-pc is installed), but I have no /boot/grub/menu.lst file to edit.

Both partitions are on the same hard drive (HD 0,0) - and Windows is on /dev/sda5.   I can provide whatever outputs are necessary to help diagnose.

Thanks!

---

### Post by Elfy on 2011-06-28
menu.lst is for grub1

Have you tried updating grub from a terminal?

```
sudo update-grub
```

---

### Post by elsewares on 2011-06-28
> **forestpiskie said:**
> menu.lst is for grub1

Have you tried updating grub from a terminal?

```
sudo update-grub
```

I have - and it just returns the following:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

I fear this means that the MBR has been altered and I'm screwed.

---

### Post by Elfy on 2011-06-28
Can you go here and follow the instructions please.


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by elsewares on 2011-06-28
> **forestpiskie said:**
> Can you go here and follow the instructions please.


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *        206,848   365,810,476   365,603,629   7 NTFS / exFAT / HPFS
/dev/sda3         490,921,984   625,137,663   134,215,680  83 Linux
/dev/sda4         365,811,710   490,921,983   125,110,274   5 Extended
/dev/sda5         365,811,712   485,725,774   119,914,063  83 Linux
/dev/sda6         485,726,208   490,921,983     5,195,776  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,468,415 1,953,466,368   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        78F83C99F83C5798                       ntfs       
/dev/sda3        2d045930-922e-4715-831c-a4e51585ad0c   ext4       
/dev/sda5        585fcbed-8df3-492b-9d15-78cd977165cc   ext4       
/dev/sda6        fd890e63-2b5a-4ad9-bd66-cd1be4145c9a   swap       
/dev/sdb1        B0560558560520A8                       ntfs       Winston Smith

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /home                    ext4       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Winston Smith     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=585fcbed-8df3-492b-9d15-78cd977165cc ro  splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=585fcbed-8df3-492b-9d15-78cd977165cc ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=585fcbed-8df3-492b-9d15-78cd977165cc ro  splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=585fcbed-8df3-492b-9d15-78cd977165cc ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 585fcbed-8df3-492b-9d15-78cd977165cc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
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
UUID=585fcbed-8df3-492b-9d15-78cd977165cc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=2d045930-922e-4715-831c-a4e51585ad0c /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=fd890e63-2b5a-4ad9-bd66-cd1be4145c9a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 188.603507996 = 202.511474688  boot/grub/core.img                             1
 178.622570038 = 191.794524160  boot/grub/grub.cfg                             1
 175.563720703 = 188.510109696  boot/initrd.img-2.6.35-28-generic-pae          2
 178.489906311 = 191.652077568  boot/initrd.img-2.6.38-8-generic-pae           2
 188.628242493 = 202.538033152  boot/vmlinuz-2.6.35-28-generic-pae             1
 175.741638184 = 188.701147136  boot/vmlinuz-2.6.38-8-generic-pae              1
 178.489906311 = 191.652077568  initrd.img                                     2
 175.563720703 = 188.510109696  initrd.img.old                                 2
 175.741638184 = 188.701147136  vmlinuz                                        1
 188.628242493 = 202.538033152  vmlinuz.old                                    1
```

---

### Post by oldfred on 2011-06-28
Somehow you deleted sda1 which is with win7 the boot/recovery partition and has these two boot files. But you have moved boot flag to sda2 and then can use a windows repairCD to fix the boot.

Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Your are missing bootmgr & BCD. If you have copies you can copy them back in and repair the BCD or just run the windows repairs. If you run autorepairs it will reinstall windows boot loader to the MBR and then you will have to reinstall grub2's boot loader.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #[COLOR=DarkRed]updates MBR master boot record  do not run if you still want grub[/COLOR]
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

