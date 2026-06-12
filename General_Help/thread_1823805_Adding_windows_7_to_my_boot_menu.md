---
title: "Adding windows 7 to my boot menu"
date: 2011-08-12
forum: General Help
---

### Post by F1lthym0nk3y on 2011-08-12
Hi guys,

I've just installed a fresh copy of ubuntu 11.04 and want grub to display the grub menu with an option of loading into windows 7... etc..

When I run update-grub I get this message..

```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Windows7/boot
Boot: No such file or directory
done

```

I have tried using the startup manager to add it to the grub menu but there is no option to do so..

I have downloaded a script to show all my drives etc with the following results..

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 681fe9bb-52f3-4487-afc1-1867335d1892 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fa9b424b-c1c6-4d1b-8f15-09005e7d2155 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/mnt/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/BCD /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   781,420,543   781,418,496   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 2,827,872,247 2,827,870,200   7 NTFS / exFAT / HPFS
/dev/sdb2    *  2,827,872,256 2,930,272,255   102,400,000   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,519,615 1,953,517,568   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdd5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdd2           3,905,536   160,155,647   156,250,112  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        781EA2521EA208E8                       ntfs       New Downloads
/dev/sdb1        DA9C94729C944AC1                       ntfs       Downloads
/dev/sdb2       3A0897110896CB71                       ntfs       Windows7
/dev/sdc1        BCEE1DEBEE1D9EA8                       ntfs       Music>Work>Files
/dev/sdd2        fa9b424b-c1c6-4d1b-8f15-09005e7d2155   ext4       
/dev/sdd5        dcb5c1eb-7317-4f2f-9368-991eb3f61cd4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Windows7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Music>Work>Files  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd2        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdd2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdd,msdos2)'
search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos2)'
search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos2)'
	search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fa9b424b-c1c6-4d1b-8f15-09005e7d2155 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos2)'
	search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fa9b424b-c1c6-4d1b-8f15-09005e7d2155 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos2)'
	search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdd,msdos2)'
	search --no-floppy --fs-uuid --set=root fa9b424b-c1c6-4d1b-8f15-09005e7d2155
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

=============================== sdd2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc2 during installation
UUID=fa9b424b-c1c6-4d1b-8f15-09005e7d2155 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=dcb5c1eb-7317-4f2f-9368-991eb3f61cd4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.095527649 = 45.199728640   boot/grub/core.img                             1
  34.621246338 = 37.174280192   boot/grub/grub.cfg                             1
   3.293918610 = 3.536818176    boot/initrd.img-2.6.38-8-generic               2
  42.093067169 = 45.197086720   boot/vmlinuz-2.6.38-8-generic                  1
   3.293918610 = 3.536818176    initrd.img                                     2
  42.093067169 = 45.197086720   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
```

Again all I want to be able to go is add the windows 7 partition to my grub menu and for the menu to be displayed every time I boot up etc..

Thanks in advance guys ;)

---

### Post by raja.genupula on 2011-08-12
do you know at what partition you have installed your windows 
if so add this to end of your grub.cfg file in /boot/grub location 

  Windows system on the first partition of the first hard disk

```
menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

then , You should put that in /etc/grub.d/40_custom so you don't lose it every time Ubuntu has a Kernel upgrade

---

### Post by oldfred on 2011-08-12
You only want to install grub2 to the MBR especially since you have multiple drives and can have a different boot loader in 4 drives. You also should have Windows boot loader in the MBR of the windows drive.

It looks like you grub2 in sdd the 500GB drive is ok. YOu have an old copy of grub2 in sdc the 1TB drive and should install a Windows boot loader to that drive.

You have installed grub to various windows drives and that causes problems for windows.

Delete the /boot with grub in it from these partitions, but be careful not to delete the windows /Boot that has the BCD. Do not delete from any Ubuntu partition. Windows is not case sensitive like Linux so it sees two /boot file which it cannot have.

```
sda1: __________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        [COLOR=Red]/boot/grub/core.img[/COLOR]

sdb1: _________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]

sdb2: ____________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]


```

More info here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

### Post by F1lthym0nk3y on 2011-08-12
Many thanks, I have followed both your instructions and redone the update-grub command which displays this..

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb2
/etc/grub.d/40_custom: 22: function: not found
/etc/grub.d/40_custom: 26: save_env: not found
/etc/grub.d/40_custom: 27: Syntax error: "}" unexpected

```

Now all I need to be able to do is to be able choose the default OS and actually see the grub menu upon booting, at the moment it is just booting straight into ubuntu with no grub menu..:(

---

### Post by oldfred on 2011-08-12
That it found win7 it should start showing menu. But I think the update-grub does not work when you have a typo in 40_custom. I had a typo in my 40_custom for several versions and with grub 1.99 it would write the update to a backup file and not really update.

You need to see why it is complaining about an extra } in 40_custom. If it is finding your windows on its own you can delete the entry in 40_custom.

---

### Post by F1lthym0nk3y on 2011-08-22
Brilliant, thanks again oldfred :)

---

