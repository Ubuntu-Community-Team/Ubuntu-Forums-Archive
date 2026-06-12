---
title: "Grub is hiding my CD drive from WinXP"
date: 2011-06-25
forum: General Help
---

### Post by Jason Spaceman on 2011-06-25
Hello.

I installed Ubuntu 11.04 on my laptop alongside WinXP.  For some reason Grub hides my CD drive from WinXP but not Ubuntu.  I can access the drive in Ubuntu, but it doesn't appear in WinXP at all.

I know there is a solution to this, but I can't remember what it is.  Something to do with modifying grub.conf or something like that.  Does anyone know how to fix this?

---

### Post by varunendra on 2011-06-25
I don't think it is even possible for Grub to do that for XP.

As far as I know, it just hands over the boot process to windows bootloader (ntldr), which then takes care of boot process, passing boot arguments as specified in "boot.ini" file.

Grub simply 'cannot' pass its own boot arguements to windows, hence cannot interfere with how windows deals with hardware (or anything else) while or after booting.

But my knowledge regarding this may be incomplete, although I strongly believe I'm absolutely right about above explanation.

While in windows, open device manager and see if your drive shows up there. It maybe disabled, or have no drive letter assigned.

I have at least once experienced the same problem, but it had nothing to do with grub or linux. It was a 'windows only' machine. As far as I can remember, it was some registry error - deliberately created by a CD based game - "Downtown Run" (or maybe by some virus in it).

---

### Post by Joris Donders on 2011-06-25
Try sudo update-grub ; maybe it solves that issue. 

But the explanation in the previous post is absolutely correct.

---

### Post by Jason Spaceman on 2011-07-11
sudo update-grub didn't fix it.

Here is my CD drive info, from dmesg:

```
[2.426761] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-K16  1.44 PQ: 0 ANSI: 5
[2.438913] cdrom: Uniform CD-ROM driver Revision: 3.20
[2.439134] sr 1:0:1:0: Attached scsi CD-ROM sr0
```

It lists my CD drive as being scsi.  I know there was some issue with Grub and drives like this.  There is some parameter that you need to give to Grub so that it passes it along to Windows when it boots.

---

### Post by wildmanne39 on 2011-07-12
Hi, I am pretty sure grub is not the problem,if you can not use it in windows maybe you need to reinstall the windows driver for it, have you opened device manager in windows and see what it tells you about the cd drive? The two system are separate of each other.

---

### Post by Jason Spaceman on 2011-07-27
I tried reinstalling Ubuntu the other night using the Alternate CD with Expert Mode enabled.  Before I began the reinstall I booted into my WinXP install disk and ran 'fixmbr', which replaced GRUB.  I then booted into WinXP and low and behold my CD drive reappears in Windows Explorer.

I reinstalled Ubuntu and selected GRUB as my bootloader.  I then booted back into WinXP and the CD drive has disappeared again. :(  

There is no listing for the CD drive under the WinXP device manager either, but it still appears and works fine in Ubuntu.

I then ran 'fixmbr' again, from the WinXP install disk, and my CD drive reappeared in WinXP.  I then reinstalled GRUB, following [these instructions](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows), and the CD drive has disappeared from WinXP (but is still visible in Ubuntu).  

So GRUB certainly seems to be the problem.  It's not letting WinXP know that there is a CD drive.

---

### Post by varunendra on 2011-07-28
> **Jason Spaceman said:**
> I tried reinstalling Ubuntu the other night using the Alternate CD with Expert Mode enabled.  Before I began the reinstall I booted into my WinXP install disk and ran 'fixmbr', which replaced GRUB.  I then booted into WinXP and low and behold my CD drive reappears in Windows Explorer.

I reinstalled Ubuntu and selected GRUB as my bootloader.  I then booted back into WinXP and the CD drive has disappeared again. :(  

There is no listing for the CD drive under the WinXP device manager either, but it still appears and works fine in Ubuntu.

I then ran 'fixmbr' again, from the WinXP install disk, and my CD drive reappeared in WinXP.  I then reinstalled GRUB, following [these instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), and the CD drive has disappeared from WinXP (but is still visible in Ubuntu).  

So GRUB certainly seems to be the problem.  It's not letting WinXP know that there is a CD drive.
Hmm.. it's getting more than interesting now. I think we'd require some extensive info about your system. Please provide these:

[LIST]
[*]contents of /boot/grub/grub.cfg
[*]Laptop's model
[*]CD drive's connection mode in XP (SATA/USB)
[*]SATA connection mode in BIOS (if there's a choice available in BIOS like- Enhanced/Combined/IDE/...etc)
[/LIST]
 Let's see if we are missing something here.

---

### Post by decrepit on 2011-07-28
I think "more than interesting" is a slight understatement!

Is it possible XP needs something from the windows MBR to see the drive? (so when grub is installed it doesn't get it)
Doesn't seem very likely, but to me that's a more resonable explanation than grub blocking XP's ability to see it.

If this proves unsolvable, you may have to consider booting ubuntu from windows. I've seen posts on how to dual boot that way.

---

### Post by Jason Spaceman on 2011-08-01
My laptop is a Sager NP5760, also known as a Clevo M570U.

Here are the contents of my grub.cfg:

```
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
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 4c8f2e7e-a01e-43ee-95d2-33ae7bbe6d85
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0E3C074F3C0730EF
	drivemap -s (hd0) ${root}
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
```

The CD/DVD drive itself is a Pioneer DVR-K16, that slides into the side of the laptop and connects that way.  I'm not sure about its connection mode in the BIOS.  I checked the BIOS and couldn't find anything about that.

---

### Post by dcstar on 2011-08-03
> **Jason Spaceman said:**
> 
.........
The CD/DVD drive itself is a Pioneer DVR-K16, that slides into the side of the laptop and connects that way.  I'm not sure about its connection mode in the BIOS.  I checked the BIOS and couldn't find anything about that.

I believe that GRUB does a basic hardware probe before loading whatever OS is selected, so it is possible that that step of the process is setting something that XP does not like and does not happen when the Windows bootloader is used.

It may well be a BIOS setting that fixes this, or if you have a USB CD drive available check if XP can use that after boot.

---

