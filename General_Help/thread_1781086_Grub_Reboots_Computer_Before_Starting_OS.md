---
title: "Grub Reboots Computer Before Starting OS"
date: 2011-06-12
forum: General Help
---

### Post by vraicovi on 2011-06-12
This is a strange one.  Ever since upgrading to 11.04 64-bit, I've had this problem and I've just been dealing with it...

After the machine posts, grub presents itself.  Before upgrading, it would timeout after 5 seconds and boot the first/default entry.  Since the upgrade, it no longer automatically boots the first entry.  In addition, it reboots the computer after selecting the first entry.  After it comes back up to grub, you select the first option and this time it boots.

I'm pulling my hair out on this one.  I'm by no means a Linux expert, but I've been running Ubuntu for a few years now and this is one of the first issues that I've been unable to work through.

I don't know what information you need to see to help diagnose this, but just ask and I'll post it.

Thanks!

---

### Post by oldfred on 2011-06-12
This script tells just about all in one handy tool:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by vraicovi on 2011-07-04
Thanks for responding Fred.  A couple of real busy weeks at work and school kept me from responding more timely to your response.

Here is the RESULTS.txt file from the script you asked that I run.  I see that it might have ended with an error, so if there's anything else you need, please let me know.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1279.9 GB, 1279900254208 bytes
255 heads, 63 sectors/track, 155605 cylinders, total 2499805184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 2,499,794,324 2,499,794,262  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   601,361,144   601,361,082  83 Linux
/dev/sdb2         601,361,145   625,137,344    23,776,200   5 Extended
/dev/sdb5         601,361,208   625,137,344    23,776,137  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        00748d1d-fd88-4dc4-84b6-193890bd2d56   ext4       Data
/dev/sdb1        bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b   ext4       
/dev/sdb5        a1434d67-c311-4904-8397-9e51d74abce7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Data              ext4       (rw,noatime,errors=remount-ro,commit=0)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200x24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 00748d1d-fd88-4dc4-84b6-193890bd2d56
insmod jpeg
if background_image /AV/Wallpapers/bg-lespaul-black.jpg; then
  set color_normal=light-gray/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-server
}
menuentry 'Ubuntu, with Linux 2.6.38-8-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	echo	'Loading Linux 2.6.38-8-server ...'
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-server
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.31-20-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry 'Ubuntu, with Linux 2.6.31-20-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	echo	'Loading Linux 2.6.31-20-server ...'
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-server
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda0 during installation

UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b /               ext4    errors=remount-ro 0       1
UUID=a1434d67-c311-4904-8397-9e51d74abce7 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 	/media/Data 	ext4 defaults,noatime,norelatime,errors=remount-ro 0 1

-------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.274260998 = 0.294485504    boot/grub/core.img                             1
   4.880988598 = 5.240921600    boot/grub/grub.cfg                             1
  60.054072857 = 64.482569728   boot/initrd.img-2.6.31-20-server               1
  72.902804852 = 78.278790656   boot/initrd.img-2.6.38-8-server                2
   1.812293530 = 1.945935360    boot/vmlinuz-2.6.31-20-server                  2
 111.488673687 = 119.710051840  boot/vmlinuz-2.6.38-8-server                   1
  72.902804852 = 78.278790656   initrd.img                                     2
 111.488673687 = 119.710051840  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by drs305 on 2011-07-04
I've been interested in users who can't boot the first time but can after rebooting. I've never walked through all the scripts involved in booting the OS, but one thing that affects what happens is the status of 'recordfail'. The recordfail setting *could* change after a failed boot. I say 'could' because it _should_ change after a failed boot, but if your OS is hanging even on the first boot, it may be 'stuck' on the 'failed' status.

Anyway, one thing the 'recordfail' status sets is the *linux_gfx_mode* setting, which in turn is incorporated into the *gfxpayload* variable.

I'm wondering if this setting is what is causing the first boot to fail. You could check by booting into your installation, then editing grub.cfg. While this file is not normally edited, it's a good place to test because you can remove the change merely by running "sudo update-grub".

To test the above, open /boot/grub/grub.cfg. Go to line 105 and change
> set gfxpayload=**$linux_gfx_mode**
[I]to
[/I]set gfxpayload=**text**

Save the file, do NOT update-grub, and power off and reboot to see what happens. If that doesn't work, you might also try changing the value from **text** to **keep**

Note: There is a line just before the menu entries which uses the $linux_gfx_mode setting to determine whether video is loaded, but I don't think this is part of the issue. If it is, this test won't determine that.

If manually changing the value for *gfxpayload* doesn't work, after booting just run "sudo update-grub" to change things back to the way they were when you started.

---

### Post by vraicovi on 2011-07-04
Thanks for the response drs305.  I have tried the changes you suggested, but the condition remains the same.  I noticed no difference when changing setting gfxpayload=text.  However, when I changed gfxpayload=keep, I noticed the screen did not flip back to text upon selecting what to boot in grub, it stayed graphical the second time through to the login screen.

Just to clarify, the computer never freezes or doesn't boot.  From a cold start, it boots to grub, auto-selects the default, reboots itself and starts grub again.  At this point, it does not auto-select the default.  After pressing Enter, the computer boots fine.

---

### Post by drs305 on 2011-07-04
Sorry the manual edit didn't work. 

The only thing I know different between your first and second boots is that 'recordfail' is not 1 for the first boot and is equal to 1 on the reboot. The 'recordfail' conditional occurs just prior to Grub2 displaying the menu and affects the value of 'linux_gfx_mode' and whether the 'load_video' subroutine is executed. Perhaps someone else will have an idea.

---

### Post by vraicovi on 2011-07-04
No need to be sorry, I appreciate the effort and the attempt.  As my machine is somewhat stable, I really don't run into this issue oftern, except for when I need to restart.  The real issue here is that I can't get it to auto-select the default entry, which is particularly a problem if I need to restart the machine remotely.

drs305, I even tried a complete reload of grub, using your instructions from the following thread, also with no luck:
[http://ubuntuforums.org/showpost.php?p=10874105&postcount=12](http://ubuntuforums.org/showpost.php?p=10874105&postcount=12)

So, here's a fresh output from boot_info_script, after the grub reinstall:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 29624815 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1279.9 GB, 1279900254208 bytes
255 heads, 63 sectors/track, 155605 cylinders, total 2499805184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 2,499,794,324 2,499,794,262  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   601,361,144   601,361,082  83 Linux
/dev/sdb2         601,361,145   625,137,344    23,776,200   5 Extended
/dev/sdb5         601,361,208   625,137,344    23,776,137  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        00748d1d-fd88-4dc4-84b6-193890bd2d56   ext4       Data
/dev/sdb1        bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b   ext4       
/dev/sdb5        a1434d67-c311-4904-8397-9e51d74abce7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Data              ext4       (rw,noatime,errors=remount-ro,commit=0)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
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
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-server
}
menuentry 'Ubuntu, with Linux 2.6.38-8-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	echo	'Loading Linux 2.6.38-8-server ...'
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-server
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.31-20-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry 'Ubuntu, with Linux 2.6.31-20-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	echo	'Loading Linux 2.6.31-20-server ...'
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-server
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda0 during installation

UUID=bb2fa1a2-6b14-43d3-8324-e86c42d5fc9b /               ext4    errors=remount-ro 0       1
UUID=a1434d67-c311-4904-8397-9e51d74abce7 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 	/media/Data 	ext4 defaults,noatime,norelatime,errors=remount-ro 0 1

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.126239300 = 15.167933952   boot/grub/core.img                             1
  38.647334576 = 41.497259520   boot/grub/grub.cfg                             1
  60.054072857 = 64.482569728   boot/initrd.img-2.6.31-20-server               1
  72.902804852 = 78.278790656   boot/initrd.img-2.6.38-8-server                2
   1.812293530 = 1.945935360    boot/vmlinuz-2.6.31-20-server                  2
 111.488673687 = 119.710051840  boot/vmlinuz-2.6.38-8-server                   1
  72.902804852 = 78.278790656   initrd.img                                     2
 111.488673687 = 119.710051840  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

> **drs305 said:**
> Sorry the manual edit didn't work. 

The only thing I know different between your first and second boots is that 'recordfail' is not 1 for the first boot and is equal to 1 on the reboot. The 'recordfail' conditional occurs just prior to Grub2 displaying the menu and affects the value of 'linux_gfx_mode' and whether the 'load_video' subroutine is executed. Perhaps someone else will have an idea.

---

### Post by drs305 on 2011-07-04
> As my machine is somewhat stable, I really don't run into this issue oftern, except for when I need to restart.  The real issue here is that I can't get it to auto-select the default entry, which is particularly a problem if I need to restart the machine remotely.

That I can probably help you with. If it is pausing because of the recordfail value, you can modify the 00_header file to set the recordfail value at something other than -1 (indefinite pause) so it automatically attempts another reboot. 

```
sudo nano /etc/grub.d/00_header
```

Find this section (mine is at line 229). Note I've already added the **#** symbol to the existing line:
> make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
[COLOR="Red"]#  set timeout=-1[/COLOR]
**  set timeout=10**
else
  set timeout=${2}
fi
EOF
}
Save and update-grub.

Now when a recordfail event is set, the computer will delay 10 seconds and then reboot. You are overriding the default action of pausing to await user input. If unattended and a reboot with a recordfail is accomplished, the computer will continuously attempt to reboot until successful or the user intervenes.

---

### Post by vraicovi on 2011-07-04
That did the trick... thank you drs305!  Grub loaded the first time (more on this in a second), the computer rebooted, grub loaded a second time, and Ubuntu booted up - automatically.

I should have mentioned this before, but I assumed it was a change in the way the new version of grub functions.  When it loads, the screen background changes to the purple-ish color, but I am never presented with a menu.  Is this a change in the new version or is this more screwiness on my end?

Any thoughts on tracing down the recordfail?

---

### Post by drs305 on 2011-07-04
> **vraicovi said:**
> That did the trick... thank you drs305!  Grub loaded the first time (more on this in a second), the computer rebooted, grub loaded a second time, and Ubuntu booted up - automatically.

I should have mentioned this before, but I assumed it was a change in the way the new version of grub functions.  When it loads, the screen background changes to the purple-ish color, but I am never presented with a menu.  Is this a change in the new version or is this more screwiness on my end?

Any thoughts on tracing down the recordfail?

The default purple background was a change, I think in  1.98. Since you have only one OS, Grub legacy actually never displays the menu (even with the timeout set). There was a way to display it if you wish (place a # icon before the "GRUB_HIDDEN_TIMEOUT=" in /etc/default/grub - I haven't checked to see if this technique still works in the latest versions of G2).

Grub 2 is pretty good about providing explanations of why it won't get to the menu or can't *start* the entry. After that it's a different story.

The actual 'recordfail' is pretty straightforward. It sets it to 1 at boot, and after Linux successfully boots it resets or removes it. If it fails, it remains at 1 for the next boot. So technically, if you ever boot you should not be able to find the 'recordfail' set to anything.

As far as tracking down the what *triggers* a recordfail:
I've tried tracking it down for users about half a dozen times. In each instance, I kept peeling back layers of Grub2 scripts and routines until I finally gave up. I'm just a user, not a dev or coder, so eventually I just get lost in all the possibilities.  :-(

---

### Post by oldfred on 2011-07-04
drs305 knows these type of issues a lot more than I. 

But do you have any issues when you shut the computer down after using it for a while?

---

### Post by vraicovi on 2011-07-04
drs305, I appreciated your help and your candor!

---

### Post by vraicovi on 2011-07-04
> **oldfred said:**
> drs305 knows these type of issues a lot more than I. 

But do you have any issues when you shut the computer down after using it for a while?

Not that I'm aware of.  When the system boots (after the grub oddness), it works great.  When I shut it down, it appears to shutdown properly.

---

