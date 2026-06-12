---
title: "Trying to move to larger hard disk"
date: 2011-10-08
forum: General Help
---

### Post by AlexBooton on 2011-10-08
Hi,

I can't boot from the larger drive.  It says "No such disk.  You need to load the kernel first".

Here's what I've done so far.

1. Installed U11.04 on the new drive and made sure it's bootable.

2. Attached both drives and booted from the old.

3. Did a full backup of the old drive.  (I used Retrospect for this).

4. Restored everything to the new drive deleting all old files.

5. Removed the old drive and attempted to boot from the now.

That's when I hit the wall.

This is something I wanted to be able to do for the future.  IOW, keep a full backup in case the system died; and do a "bare metal" restore.

Any ideas?

Thanks

---

### Post by dcstar on 2011-10-08
> **AlexBooton said:**
> Hi,

I can't boot from the larger drive.  It says "No such disk.  You need to load the kernel first".

Here's what I've done so far.

1. Installed U11.04 on the new drive and made sure it's bootable.

2. Attached both drives and booted from the old.

3. Did a full backup of the old drive.  (I used Retrospect for this).

4. Restored everything to the new drive deleting all old files.

5. Removed the old drive and attempted to boot from the now.

That's when I hit the wall.

This is something I wanted to be able to do for the future.  IOW, keep a full backup in case the system died; and do a "bare metal" restore.

Any ideas?

Thanks

[LIST=1]
[*]Boot from old drive with new one connected.
[*]Do "sudo update-grub" in terminal.
[*]Reboot and select new drive from Grub menu
[*]Do "sudo dpkg-reconfigure grub-pc" and select option to install boot loader on new drive
[*]Shut down, remove old drive and reboot.
[/LIST]

---

### Post by AlexBooton on 2011-10-09
> **dcstar said:**
> [LIST=1]
[*]Boot from old drive with new one connected.
[*]Do "sudo update-grub" in terminal.
[*]Reboot and select new drive from Grub menu
[*]Do "sudo dpkg-reconfigure grub-pc" and select option to install boot loader on new drive
[*]Shut down, remove old drive and reboot.
[/LIST]

Thank you for the feedback.  I think I'm close!  But so far, no joy.

At your 3rd step: "Reboot and select new drive from Grub menu"

I do not get a boot time option.  It goes directly to booting from the old drive. (see the screen resolution issue below) 

I've tried several ways to get it to boot from the new drive.  This includes selecting the new drive from the BIOS boot priority menu; simply switching SATA cables so that the new drive becomes SATA1 in the BIOS; and physically removing the old drive from the system.  Nothing works.

With the old drive removed I get the same message as I got before trying your method.  The BIOS just says there is no bootable drive.  With the old drive as SATA1 or 2 in the BIOS it always boots from the old drive without any choice.

On the fourth step:  "sudo dpkg-reconfigure grub-pc"  

I probably shouldn't have gone to the fourth step; but I couldn't resist.  I booted from the old drive (seemingly the only option) and tried the fourth step.

I get three pages of text.  I hit <enter> on the first two and it freezes on the third.

Here's what's on the screen when it freezes:
" â The grub-pc package is being upgraded. This menu allows you to select
 â which devices you'd like grub-install to be automatically run for, if
 â any.
 â
 â Running grub-install automatically is recommended in most situations, to
 â prevent the installed GRUB core image from getting out of sync with GRUB
 â modules or grub.cfg.
 â
 â If you're unsure which drive is designated as boot drive by your BIOS,
 â it is often a good idea to install GRUB to all of them.
 â
 â Note: it is possible to install GRUB to partition boot records as well,
 â and some app"

At that point I don't seem to be able to continue.  Hitting enter does nothing.  Even <ctrl>C does nothing.

Am I missing something?

Screen resolution:
Here's a potential glitch; although I think not.  I'm working with an old monitor.  When the system boots, the monitor says "Out of range".  But after a successful boot Ubuntu comes up and is fully visible.

With the new drive as SATA1, it never gets past that "Out of range message". It just freezes there.

So, is it remotely possible that the boot option to select a drive is being blocked by the low screen resolution?  If so, can I adjust Ubuntu to NOT try to start at too high a resolution?

Thanks

---

### Post by oldfred on 2011-10-09
With both drives plugged in run this either from your working install or the liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by AlexBooton on 2011-10-09
Phew.  It's a long file.  Here goes.

Hope you can make some sense of it :)

Thanks!

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
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

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   773,296,127   773,294,080  83 Linux
/dev/sda2         773,298,174   781,422,591     8,124,418   5 Extended
/dev/sda5         773,298,176   781,422,591     8,124,416  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34         1,987         1,954 BIOS Boot partition
/dev/sdb2           1,988 3,898,902,378 3,898,900,391 Data partition (Windows/Linux)
/dev/sdb3   3,898,902,379 3,907,029,118     8,126,740 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        465e9e03-3dcc-4109-bddc-d324a9a94b36   ext4       
/dev/sda5        030e2ecb-9ba9-442e-8606-82e1958063c0   swap       
/dev/sdb2        d157dbc4-9fb7-4188-9bd0-e67ed4c993b2   ext4       
/dev/sdb3        f84f2ec2-89e7-4e25-b848-5c774ce020de   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary. Linux command line: _________________________________________________________________________  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro single The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary. Linux command line: _________________________________________________________________________
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt2)'
	search --no-floppy --fs-uuid --set=root d157dbc4-9fb7-4188-9bd0-e67ed4c993b2
	linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt2)'
	search --no-floppy --fs-uuid --set=root d157dbc4-9fb7-4188-9bd0-e67ed4c993b2
	linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro single
	initrd /boot/initrd.img-2.6.38-11-generic-pae
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=030e2ecb-9ba9-442e-8606-82e1958063c0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 200.127956390 = 214.885756928  boot/grub/core.img                             1
 118.655460358 = 127.405330432  boot/grub/grub.cfg                             1
 118.930664062 = 127.700828160  boot/initrd.img-2.6.38-11-generic-pae          2
   0.942813873 = 1.012338688    boot/vmlinuz-2.6.38-11-generic-pae             2
 118.930664062 = 127.700828160  initrd.img                                     2
   0.942813873 = 1.012338688    vmlinuz                                        2

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 465e9e03-3dcc-4109-bddc-d324a9a94b36
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

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=465e9e03-3dcc-4109-bddc-d324a9a94b36 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=030e2ecb-9ba9-442e-8606-82e1958063c0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1536.133626938 = 1649.410922496 boot/grub/core.img                             1
1536.134126663 = 1649.411459072 boot/grub/grub.cfg                             1
   0.149385452 = 0.160401408    boot/initrd.img-2.6.38-11-generic-pae          2
1536.133420944 = 1649.410701312 boot/vmlinuz-2.6.38-11-generic-pae             1
   0.149385452 = 0.160401408    initrd.img                                     2
1536.133420944 = 1649.410701312 vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by oldfred on 2011-10-10
Several issues that I know prevent booting and one that may be an issue(large / partition). Your old drive was MBR(msdos) partitioning where the new large drive is gpt. GPT is a newer partitioning scheme that has internal backups and other minor improvements (no logical partitions). But if you are thinking of ever installing Windows you may want to revert to MBR.

You copied the grub & fstab files from your old install that refer to the UUIDs of the partitions on the old drive. The new drive has different UUIDs. You have to manually edit fstab and may be able to manually boot (in effect by-passing the wrong UUIDs in grub.cfg. Then when you boot you can run sudo update-grub to get to automatically correct itself. Or in may be better just to totally reinstall grub.

You should have only copied /home from your old install to your new. Reviewed any special system wide settings you had in /etc and manually added them again and exported a list of installed apps and reinstalled those. Installing and then moving from old system copied the older data from you old install and all the history, log files etc that you do want to houseclean with a new install. The /home has all your user settings & your files so it copies what you really want. Best to have a separate /home especially with very large drives.

From liveCD or your old install:
sudo blkid
# you should see these UUIDs which is from the script:
```
/dev/sdb2        d157dbc4-9fb7-4188-9bd0-e67ed4c993b2   ext4       
/dev/sdb3        f84f2ec2-89e7-4e25-b848-5c774ce020de   swap 

```sudo mkdir /mnt/sdb2
sudo mount /dev/sdb2 /mnt/sdb2
gksudo gedit /mnt/sdb2/etc/fstab

#you should see this:
```
# / was on /dev/sdb1 during installation
UUID=[COLOR=Red]465e9e03-3dcc-4109-bddc-d324a9a94b36[/COLOR] /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=[COLOR=Red]030e2ecb-9ba9-442e-8606-82e1958063c0[/COLOR] none            swap    sw              0       0

```Copy & replace the red entries in fstab that are from your 400GB drive with the one's in your 2TB drive.

Do you get a grub boot menu with your 2TB drive booting from BIOS? If so you can manually boot using device and the linkes in / to the newest kernel. Drive letter will change if you unplug your 400GB drive.

At grub menu go to command line and type these in.

Adjust drive, partition to your install sdb is hd1:

```
set prefix=(hd1,2)/grub
set root=(hd1,2)
linux (hd1,2)/vmlinuz root=/dev/sdb2
initrd (hd1,2)/initrd.img
boot

```There was a bug that grub would not boot from very large drives and one / (root) partition. If you still cannot boot use gparted to shrink your / partition a lot. I normally suggest separate / & /home and then / can be 10 to 20GB. I use 20 to 25GB root partitions and use only 7GB with many programs. But all my data is in other partitions. You may need bigger, but if you separate /home then 20 or 25GB would be good. Smaller root partition is slightly more efficent as all the system files that are used the most are closer on the hard drive and the hard drive does not have to move heads across entire 2TB to load system.

---

### Post by AlexBooton on 2011-10-11
Thanks oldfred (btw, I'm 71.  Do I have you beat? ;) )

I've tried but just can't get the new drive to boot.  

I'm about to give up on this.  

I was trying to find a way to do a bare metal recovery but from what I've seen so far it just isn't that easy.

It's a shame though that Linux doesn't seem to have that capability.

---

