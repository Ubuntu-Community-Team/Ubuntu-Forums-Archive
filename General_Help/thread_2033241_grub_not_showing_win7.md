---
title: "grub not showing win7"
date: 2012-07-25
forum: General Help
---

### Post by fixerdave on 2012-07-25
Okay, this is a learning experience for me... no data is at risk, I'm not sweating, but I'd like to build a little more expertise in this area.

That said, I'm running a fresh install, Win7 64b (deployed via WDS, this is my work computer) and then Ubuntu 12.4 64b over-top in dual-boot mode on the same drive.  From there, I installed dmraid (I have a raid 1+0 data array, no os there), gnome-panels (cause I'm old), and vmplayer (cause I still like to play).

I'm not exactly sure when exactly grub lost track of the Win7 partition as, honestly, I don't really care about it.  I just want it there, booting as default, for when other people at work use my system.  Having it boot to -gasp- Linux kind of freaks them out. :lol:

The most likely culprit is vmplayer as I discovered that Ubuntu 12.4 is not yet an "accepted" host os.  There is, however, a patch that makes it work.  Another possibility is dmraid... might have messed with grub even though nothing is booting from the array.

here's the bootinfo script output
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

mapper/isw_bdegciegae_RAID10: __________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   528,508,800   528,506,753   7 NTFS / exFAT / HPFS
/dev/sda2         528,508,926   976,771,071   448,262,146   5 Extended
/dev/sda5         528,508,928   943,388,671   414,879,744  83 Linux
/dev/sda6         943,390,720   976,771,071    33,380,352  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_bdegciegae_RAID10 3405913a-9425-4b3a-a712-3db8a8183fcb   ext4       RAID
/dev/mapper/isw_bdegciegae_RAID10-0 3405913a-9425-4b3a-a712-3db8a8183fcb   ext4       RAID
/dev/sda1        9086303386301BE2                       ntfs       
/dev/sda5        504f8433-1477-4724-89b3-71cc6c4e19ea   ext4       
/dev/sda6        a40e8bf1-ff8d-4dd3-aea3-b5c9d4755a8f   swap       
/dev/sdb                                                isw_raid_member 
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 
/dev/sde                                                isw_raid_member 
/dev/sr0                                                udf        UDF Volume

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bdegciegae_RAID10
isw_bdegciegae_RAID10-0
isw_bdegciegae_RAID10-1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=504f8433-1477-4724-89b3-71cc6c4e19ea ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
	echo	'Loading Linux 3.2.0-27-generic ...'
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=504f8433-1477-4724-89b3-71cc6c4e19ea ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=504f8433-1477-4724-89b3-71cc6c4e19ea ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=504f8433-1477-4724-89b3-71cc6c4e19ea ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 504f8433-1477-4724-89b3-71cc6c4e19ea
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=504f8433-1477-4724-89b3-71cc6c4e19ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a40e8bf1-ff8d-4dd3-aea3-b5c9d4755a8f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-27-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-27-generic                  2
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

sudo grub-install /dev/sda just give more of the same.
sudo grub-mkconfig seems to generate the same data - no windows.
sudo os-prober says /dev/sda1:Windows 7 (loader):Windows:chain.

So, before I go the Windows repair route and possibly bork things even more, are there any other linux-side tools I should be looking at?

Like I said, not a big problem... I'm only into this for about 2 hours and it's easy to redo.  I'd just like to be able to fix these things without a re-install when I get crying, desperate people whimpering at my desk.

David...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-25
Have you tried```
$ sudo update-grub
```?

---

### Post by fixerdave on 2012-07-25
> **&#1058 said:**
> Have you tried```
$ sudo update-grub
```?

well... I thought I did... googling about gave update-grub, which I ran with -h for the help, which showed usage as "grub-mkconfig" so I ran that to generate info to stdout, and that didn't show any windows info.  

On the other hand, update-grub ran just fine and solved the problem.  Odd the usage info is so different than how it actually works.  But, work it does.

Well... that was quick.

Thank you... not sure if I learned a lot in the process, other than maybe not trying to be so smart and just run the command like google says ;)  Some days are like that.

Now, it's back to setting the default boot (I think I've got a handle on that one).

Thanks again for setting me straight,

   David...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-26
Never underestimate the power of 'update-grub' ;-) It can make or break yor day some time.

---

### Post by fixerdave on 2012-10-18
HAAA! now that's funny.  I had a crying whimpering co-worker at my desk today... no Windows boot option on the computer.  I had run an update last night and it asked about grub... completely forgot to check before I went home.

So, today, I'm off trying to figure out how to fix said grub problem... do a google search, and up pops my own post on the same problem.  I had completely forgot about it.

It's a good thing google exists because my memory is toast #-o

David...

---

