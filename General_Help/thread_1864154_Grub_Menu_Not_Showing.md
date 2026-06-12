---
title: "Grub Menu Not Showing"
date: 2011-10-18
forum: General Help
---

### Post by merlinus on 2011-10-18
Although I have commented out the appropriate line, the grub menu is still not showing on restart.

Here are the lines from /etc/default/grub:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by drs305 on 2011-10-18
I'm going to assume you ran update-grub after commenting out the applicable line in /etc/default/grub.

Does holding down the SHIFT key during boot display the menu?

Is there a 10 second delay before the kernel starts to boot (i.e. could the menu be waiting the default 10 seconds before booting but you just can't see it, or does it seem to boot fairly quickly)?

If you download and run the boot info script and post the contents of RESULTS.txt we can take a look at your files. The menu not appearing happens from time to time. I can offer a workaround, but would like to see the RESULTS.txt first.

You can get to the boot info script by clicking the "BIS" link in my signature line.

---

### Post by d.atanasov on 2011-10-18
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```


And this is mine. What do you use laptop or standard PC?

regards

---

### Post by merlinus on 2011-10-18
Holding down the Shift key whilst booting does display the menu, albeit in the upper-left-hand corner of the screen in very small type.

Same problem with desktop and laptop.

---

### Post by merlinus on 2011-10-18
Results.txt:

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,101   976,768,064   957,232,964   5 Extended
/dev/sda5          19,535,103    48,837,599    29,302,497  83 Linux
/dev/sda6          48,837,663    87,907,679    39,070,017  83 Linux
/dev/sda7          87,907,743   973,844,234   885,936,492  83 Linux
/dev/sda8         973,844,298   976,768,064     2,923,767  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        43c7c02b-23b5-4e6e-8779-28d9b25f6c2b   ext4       
/dev/sda5        34065451-70cd-4c9d-8cf2-781d18610d28   ext4       
/dev/sda6        bf66b37a-baa5-4b01-825a-075aeaabfdfd   ext4       
/dev/sda7        645de342-f83a-40aa-8e22-84f7bcf96332   ext4       
/dev/sda8        c4b0743c-017c-4ce6-b362-ecf2c7213824   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /data                    ext4       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda7        /art                     ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=34065451-70cd-4c9d-8cf2-781d18610d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
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
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 34065451-70cd-4c9d-8cf2-781d18610d28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=34065451-70cd-4c9d-8cf2-781d18610d28 /               ext4    errors=remount-ro 0       1
# /art was on /dev/sda7 during installation
UUID=645de342-f83a-40aa-8e22-84f7bcf96332 /art            ext4    defaults        0       2
# /data was on /dev/sda1 during installation
UUID=43c7c02b-23b5-4e6e-8779-28d9b25f6c2b /data           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=bf66b37a-baa5-4b01-825a-075aeaabfdfd /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=c4b0743c-017c-4ce6-b362-ecf2c7213824 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-28-generic              2
               =                boot/initrd.img-2.6.35-30-generic              2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.35-28-generic                 2
               =                boot/vmlinuz-2.6.35-30-generic                 1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  fd fd fd fd fd fd fd fd  fd fd fd fd fd fd fd fd  |................|
*
000001b0  fd fd fd fd fd fd fd fd  fd fd fd fd fd fd 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 e1 1e bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff e3 1e  bf 01 80 29 54 02 00 00  |...........)T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
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

---

### Post by drs305 on 2011-10-18
> **merlinus said:**
> Holding down the Shift key whilst booting does display the menu, albeit in the upper-left-hand corner of the screen in very small type.

Same problem with desktop and laptop.

EDIT:  [s]Ok. I'd still like to see the RESULTS.txt[/s]  Looking at it.

... but you might try changing the setting in /etc/default/grub for "GRUB_GFXMODE=auto" to "GRUB_GFXMODE=640x480". Save the file and update grub.

---

### Post by d.atanasov on 2011-10-18
... but you might try changing the setting in /etc/default/grub for "GRUB_GFXMODE=auto" to "GRUB_GFXMODE=640x480". Save the file and update grub.[/QUOTE]

In this sense of word try also this line :

GRUB_HIDDEN_TIMEOUT_QUIET=true

---

### Post by merlinus on 2011-10-18
GRUB_GFXMODE=640x480 worked -- many thanks!

But why is it now working without having to hold down the Shift key?

---

### Post by drs305 on 2011-10-18
> **merlinus said:**
> GRUB_GFXMODE=640x480 worked -- many thanks!

But why is it now working without having to hold down the Shift key?

There have been a few problems with the *auto* feature whereby Grub determines the video resolutions. 

One of the questions I originally asked was if the system appeared to wait 10 seconds before booting. I suspect what was happening was that the Grub menu was initiated but the video was incapable of being displayed. So Grub waited 10 seconds, thinking it was giving you a chance to make a selection, and then booted. I haven't been able to test it, but my guess is that the system would respond to either the ENTER key or UP/DN keys during the delay, but I don't know for sure.

Now that we know the cause, if you would prefer a higher resolution you can probably change the 640x480 setting. At the Grub menu, press 'c' to get to the grub prompt. Type "vbeinfo" and it will show the resolutions available to the menu. You can use any of the displayed values in place of "640x480" if you wish. 

When you consider this issue SOLVED, please mark it so via the 'Thread Tools' link near the top right of the original post.

Happy Ubuntu-ing !

---

