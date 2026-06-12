---
title: "Possible problems ahead"
date: 2011-06-17
forum: General Help
---

### Post by Yepi on 2011-06-17
Hi,  recently installed Ubuntu on my laptop 'alongside' win7 and basically its on the same partition. I had created a separate partition but in the Ubuntu installer it wouldnt let me use it(I had formatted it and I think Ubuntu needs it as unallocated if I am correct?)

I have uploaded a screenshot of my disk manager in win7, the 'storage' use to be called ubuntu because that's were I wanted it to be installed, the 3.79Gb is swap disk as my laptop has 3.8GB ram and the 61.4GB seems to be the Ubuntu disk, the 16Gb is win7 recovery and the 200mb I think is the built in ms office files on preloaded pc's, strangely this adds up to roughly 300Gb but my hard drive is 250Gb and this is only possible if the swap and ubuntu partitions are actually in the C: partition as shown in the 'my computer' screenshot.

Well what I want to know is if any changes in my win7 will mess up my ubuntu and vice versa as they are on the same partition according to 'my computer' and sees it as 'free' space or will it be fine as they are separate according to disk management. As you can probably tell this is confusing me abit :???:

As a side note is there anyway to move Ubuntu+swap to the storage partition and remove the old ones without a complete system re-installation

Your feedback will be very useful for an Ubuntu rookie like me

---

### Post by idoitprone on 2011-06-17
If windows can read it fine, then you did not partition it for linux. Parition means a segment of the whole disk, so if linux is on the same partition, you installed wubi. btw it little confusing to read, since there there are 6 slots, but there can only be 4 primary partition for mbr and the window util somehow says they are basic partitions. GPT parition table?

Go live boot ubuntu, use gparted and use a file system such as, ext2-4, and brtfs. 
And then install ubuntu.
Remember to select the option that allows ubuntu to be install along side other oses

---

### Post by wildmanne39 on 2011-06-18
> **Yepi said:**
> Hi,  recently installed Ubuntu on my laptop 'alongside' win7 and basically its on the same partition. I had created a separate partition but in the Ubuntu installer it wouldnt let me use it(I had formatted it and I think Ubuntu needs it as unallocated if I am correct?)

I have uploaded a screenshot of my disk manager in win7, the 'storage' use to be called ubuntu because that's were I wanted it to be installed, the 3.79Gb is swap disk as my laptop has 3.8GB ram and the 61.4GB seems to be the Ubuntu disk, the 16Gb is win7 recovery and the 200mb I think is the built in ms office files on preloaded pc's, strangely this adds up to roughly 300Gb but my hard drive is 250Gb and this is only possible if the swap and ubuntu partitions are actually in the C: partition as shown in the 'my computer' screenshot.

Well what I want to know is if any changes in my win7 will mess up my ubuntu and vice versa as they are on the same partition according to 'my computer' and sees it as 'free' space or will it be fine as they are separate according to disk management. As you can probably tell this is confusing me abit :???:

As a side note is there anyway to move Ubuntu+swap to the storage partition and remove the old ones without a complete system re-installation

Your feedback will be very useful for an Ubuntu rookie like meHi, the only way it would be on the same partition is if you did a wubi install, then you do not have to worry about partitions.

---

### Post by Yepi on 2011-06-18
Hi, I don't think I used the wubi installer because I loaded from the Ubuntu live CD and selected the 'Install alongside Win7' option unless that is wubi.

My bad its 320GB hdd, windows 'my computer' only shows up as 250GB, probably due to hidden partitions for recovery.

---

### Post by Rubi1200 on 2011-06-18
To get a better overview regarding what is where on the drive, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Yepi on 2011-06-18
Here is the summary of the RESULTS file

```
               
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 358660552 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
#
```

I have also added  screenshot of ubuntu disk utility

---

### Post by Rubi1200 on 2011-06-18
Can you please post the output from the whole file since it contains additional information that can help us to help you.

Thanks.

---

### Post by Yepi on 2011-06-18
Ok sorry, here is the whole thing

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 358660552 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    33,556,479    33,554,432  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,556,480    33,966,079       409,600   7 NTFS / exFAT / HPFS
/dev/sda3          33,966,080   320,630,279   286,664,200   7 NTFS / exFAT / HPFS
/dev/sda4         320,630,782   625,139,711   304,508,930   f W95 Extended (LBA)
/dev/sda5         457,367,552   625,139,711   167,772,160   7 NTFS / exFAT / HPFS
/dev/sda6         320,630,784   449,396,735   128,765,952  83 Linux
/dev/sda7         449,398,784   457,355,263     7,956,480  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FC0C46E80C469D90                       ntfs       
/dev/sda2        5ECA4962CA493813                       ntfs       
/dev/sda3        664605F84605C9AF                       ntfs       
/dev/sda5        7CF223E6F223A37E                       ntfs       Storage
/dev/sda6        d17a31c4-52b0-432a-96e5-439e80a2797f   ext4       
/dev/sda7        4e89d513-5ca5-4b75-967b-9e5727dd67e0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=600)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d17a31c4-52b0-432a-96e5-439e80a2797f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d17a31c4-52b0-432a-96e5-439e80a2797f ro single 
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root FC0C46E80C469D90
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5ECA4962CA493813
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
UUID=d17a31c4-52b0-432a-96e5-439e80a2797f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4e89d513-5ca5-4b75-967b-9e5727dd67e0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 171.021957397 = 183.633428480  boot/grub/core.img                             1
 197.573318481 = 212.142735360  boot/grub/grub.cfg                             1
 155.269496918 = 166.719352832  boot/initrd.img-2.6.38-8-generic               2
 171.020977020 = 183.632375808  boot/vmlinuz-2.6.38-8-generic                  1
 155.269496918 = 166.719352832  initrd.img                                     2
 171.020977020 = 183.632375808  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by wildmanne39 on 2011-06-18
> **Yepi said:**
> Ok sorry, here is the whole thing

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 358660552 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    33,556,479    33,554,432  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,556,480    33,966,079       409,600   7 NTFS / exFAT / HPFS
/dev/sda3          33,966,080   320,630,279   286,664,200   7 NTFS / exFAT / HPFS
/dev/sda4         320,630,782   625,139,711   304,508,930   f W95 Extended (LBA)
/dev/sda5         457,367,552   625,139,711   167,772,160   7 NTFS / exFAT / HPFS
/dev/sda6         320,630,784   449,396,735   128,765,952  83 Linux
/dev/sda7         449,398,784   457,355,263     7,956,480  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FC0C46E80C469D90                       ntfs       
/dev/sda2        5ECA4962CA493813                       ntfs       
/dev/sda3        664605F84605C9AF                       ntfs       
/dev/sda5        7CF223E6F223A37E                       ntfs       Storage
/dev/sda6        d17a31c4-52b0-432a-96e5-439e80a2797f   ext4       
/dev/sda7        4e89d513-5ca5-4b75-967b-9e5727dd67e0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=600)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d17a31c4-52b0-432a-96e5-439e80a2797f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d17a31c4-52b0-432a-96e5-439e80a2797f ro single 
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root d17a31c4-52b0-432a-96e5-439e80a2797f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root FC0C46E80C469D90
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5ECA4962CA493813
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
UUID=d17a31c4-52b0-432a-96e5-439e80a2797f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4e89d513-5ca5-4b75-967b-9e5727dd67e0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 171.021957397 = 183.633428480  boot/grub/core.img                             1
 197.573318481 = 212.142735360  boot/grub/grub.cfg                             1
 155.269496918 = 166.719352832  boot/initrd.img-2.6.38-8-generic               2
 171.020977020 = 183.632375808  boot/vmlinuz-2.6.38-8-generic                  1
 155.269496918 = 166.719352832  initrd.img                                     2
 171.020977020 = 183.632375808  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```Hi, from what I can tell everything looks good, you have ubuntu on partition sda6, and you have a swap partition, you should not have any problems. I am not an expert, you can leave this thread open a little while and let Rubi1200 take a look she is much more experienced reading the boot information then I am.

---

### Post by Rubi1200 on 2011-06-19
Rubi1200 does not see any issues with the results except for possibly this:
> Grub2 (v1.99) is installed in the boot sector of sda5

sda5 appears to be a data partition; is this correct?

If both Ubuntu and Windows are booting normally, I would leave well alone.

And for the record Rubi1200 is a he not a she ;)

---

### Post by Yepi on 2011-06-19
Hi, yes sda5 is an empty partition just for storage and both win7 and ubuntu boot normally. I was planning to reformat sda5 'storage' into FAT32 so that I could share files directly rather than have to use a usb but that would destroy grub meaning cant load pc.

Is there anyway to move it to sda6, if not then ill just stick to using the usb drive.

Thanks for all the advice guys.

---

### Post by idoitprone on 2011-06-19
> Hi, yes sda5 is an empty partition just for storage and both win7 and ubuntu boot normally. I was planning to reformat sda5 'storage' into FAT32 so that I could share files directly rather than have to use a usb but that would destroy grub meaning cant load pc.

Is there anyway to move it to sda6, if not then ill just stick to using the usb drive.

sure why not, from the looks of it grub2 is installed in the mbr. It points to sda6, which means it bypass sda5 entirely. All the boot files such as fstab and grub.cfg are inside sda6. the worse thing you can do is mess up grub and you have to boot a live cd to re-install it. Just keep a live cd on hand that is all I can say

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2)

---

### Post by Yepi on 2011-06-20
Hey, I reformatted that drive, got the grub rescue error so used boot-repair program from live CD and its up and running.
Booted into win7 and Ubuntu just to check and its all fine.

Thanks for the link, it helped a lot and sure does make grub re-install a lot easier.

---

### Post by Rubi1200 on 2011-06-20
Glad you got things sorted out in the end :-)

If all issues are resolved, please mark this thread Solved using the Thread Tools near the top of the page.

Thanks.

---

