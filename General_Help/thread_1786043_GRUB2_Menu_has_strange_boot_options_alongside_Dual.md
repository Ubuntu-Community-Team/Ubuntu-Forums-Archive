---
title: "GRUB2 Menu has strange boot options alongside Dual-Boot"
date: 2011-06-19
forum: General Help
---

### Post by sammya on 2011-06-19
Hey guys. So I did a dual boot of Chrome OS (FLOW, Hexxeh edition) and it works fine. However...when I boot up the PC and go into GRUB2 (automatically) it not only gives me the option to boot from Ubuntu, Ubuntu recovery and Chrome OS but also 4 other operating systems that all say the same thing in a row! 

They say:

Squeeze/sid on /dev/sda4
Squeeze/sid on /dev/sda4
Squeeze/sid on /dev/sda4
Squeeze/sid on /dev/sda4
 

Any idea what this is or more importantly how to remove them?

Cheers

---

### Post by sammya on 2011-06-19
*edit*

here is an image of the GRUB2 boot

[IMG]http://i54.tinypic.com/e02a0p.jpg[/IMG]

---

### Post by coffeecat on 2011-06-19
> **sammya said:**
> Chrome OS (FLOW, Hexxeh edition)

[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

Squeeze is the current stable version of Debian, Sid the unstable. Perhaps Chromium OS is built on a Debian base. When you boot into one of the Debian entries on your grub menu, do you get into this Chrome/Chromium thing?

* **EDIT**: my apologies to "Hexxeh" for originally doubting that this had anything to do with Google's Chrome OS. I've found this:

[http://en.wikipedia.org/wiki/Chromium_OS](http://en.wikipedia.org/wiki/Chromium_OS)

It's on wikipedia, so it must be true! :wink:

@sammya, nevertheless, what happens when you try to boot one of the Debian entries?

---

### Post by sammya on 2011-06-19
> **coffeecat said:**
> [http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

Squeeze is the current stable version of Debian, Sid the unstable. Perhaps Chromium OS is built on a Debian base. When you boot into one of the Debian entries on your grub menu, do you get into this Chrome/Chromium thing?

* **EDIT**: my apologies to "Hexxeh" for originally doubting that this had anything to do with Google's Chrome OS. I've found this:

[http://en.wikipedia.org/wiki/Chromium_OS](http://en.wikipedia.org/wiki/Chromium_OS)

It's on wikipedia, so it must be true! :wink:

@sammya, nevertheless, what happens when you try to boot one of the Debian entries?

i booted into the first one of those OS's and it brought up this screen and froze:

[IMG]http://i55.tinypic.com/2447als.jpg[/IMG]

so is there anyway to remove those options from the grub list?

---

### Post by blackmail on 2011-06-19
So how is the new chromium OS?
Sorry if I am off topic, just asking since i think your answers are already granted by coffecat, and also you can remove the entries from the GRUB menu :)

---

### Post by coffeecat on 2011-06-19
> **sammya said:**
> so is there anyway to remove those options from the grub list?

If you simply remove the entries by editing your grub.cfg, they'll reappear when you next get a kernel update in Ubuntu. The answer to how to remove them lies in knowing what is on sda4, and whether that's Chromium OS.

I was going to suggest that we look at your system by running the boot info script, but the website is down at the moment.

Boot into Ubuntu and run these commands from a terminal:

```
sudo fdisk -lu
sudo blkid
```Post the output between [noparse]```
 and 
```[/noparse] tags for legibility. **This is very important.** You can use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

Also, open /boot/grub/grub.cfg by double-clicking on it. It will open read-only so you won't be able to damage it. Post the contents of that file as well, **also posting between [noparse]```
 and 
```[/noparse] tags.**

---

### Post by sammya on 2011-06-19
> **coffeecat said:**
> If you simply remove the entries by editing your grub.cfg, they'll reappear when you next get a kernel update in Ubuntu. The answer to how to remove them lies in knowing what is on sda4, and whether that's Chromium OS.

I was going to suggest that we look at your system by running the boot info script, but the website is down at the moment.

Boot into Ubuntu and run these commands from a terminal:

```
sudo fdisk -lu
sudo blkid
```Post the output between [noparse]```
 and 
```[/noparse] tags for legibility. **This is very important.** You can use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

Also, open /boot/grub/grub.cfg by double-clicking on it. It will open read-only so you won't be able to damage it. Post the contents of that file as well, **also posting between [noparse]```
 and 
```[/noparse] tags.**

Hey man, here is what i got from the terminal commands:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002cd58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3952639     1975296   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3952640   484599807   240323584   83  Linux
/dev/sda3       484599808   485115903      258048   83  Linux
/dev/sda4       485115904   488396799     1640448   83  Linux

/dev/sda1: UUID="f82b1544-4c03-4a0a-bc5e-f2a4bbf5303b" TYPE="swap" 
/dev/sda2: UUID="41d727d0-0f06-453f-b889-65fae9cea170" TYPE="ext4" 
/dev/sda3: LABEL="C-STATE" UUID="4c8be7b1-ca78-423a-9678-8b0d641c80b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="C-ROOT" UUID="63eb221c-3a11-4e63-b059-c1901a432f39" SEC_TYPE="ext2" TYPE="ext3"
```

and this is what i copied from grub.cfg

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
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
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=41d727d0-0f06-453f-b889-65fae9cea170 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=41d727d0-0f06-453f-b889-65fae9cea170 ro single 
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
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 41d727d0-0f06-453f-b889-65fae9cea170
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 63eb221c-3a11-4e63-b059-c1901a432f39
	linux /boot/vmlinuz root=/dev/sda4
	initrd /boot/initrd.img
}
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 63eb221c-3a11-4e63-b059-c1901a432f39
	linux /boot/vmlinuz root=/dev/sda4
	initrd /boot/initrd.img
}
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 63eb221c-3a11-4e63-b059-c1901a432f39
	linux /boot/vmlinuz root=/dev/sda4
	initrd /boot/initrd.img
}
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 63eb221c-3a11-4e63-b059-c1901a432f39
	linux /boot/vmlinuz root=/dev/sda4
	initrd /boot/initrd.img
}
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 63eb221c-3a11-4e63-b059-c1901a432f39
	linux /boot/vmlinuz-2.6.31.4-intel-menlow root=/dev/sda4
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "ChromiumOS" {
	insmod ext2
	set root=(hd0,4)
	linux   /boot/vmlinuz root=LABEL=C-ROOT rw noresume noswap i915.modeset=1 loglevel=1 quiet
	initrd  /boot/initrd.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by coffeecat on 2011-06-19
Your Chromium OS grub entry is clearly one you created yourself by editing 40_custom, and your Chromium OS is on sda4, according to the entry in grub.cfg. The Debian entries in your grub menu are those created by os-prober. Since they are on sda4 as well, we can safely assume that they refer to the same OS.

Since you don't want to see those Debian entries, simply make 30_os-prober non-executable with:

```
sudo chmod -x /etc/grub.d/30_os-prober
```Then run:

```
sudo update-grub
```By the way, your sda4 partition is only 1.7GB approx. Is that large enough? Also, you have a sda3 partition of approx 260MB. What is that?

---

### Post by sammya on 2011-06-19
> **coffeecat said:**
> Your Chromium OS grub entry is clearly one you created yourself by editing 40_custom, and your Chromium OS is on sda4, according to the entry in grub.cfg. The Debian entries in your grub menu are those created by os-prober. Since they are on sda4 as well, we can safely assume that they refer to the same OS.

Since you don't want to see those Debian entries, simply make 30_os-prober non-executable with:

```
sudo chmod -x /etc/grub.d/30_os-prober
```Then run:

```
sudo update-grub
```By the way, your sda4 partition is only 1.7GB approx. Is that large enough? Also, you have a sda3 partition of approx 260MB. What is that?

did the job cheers mate. the other two partitions were requirements from the installation of chrome os that was in the tutorial for dual booting.
thanks for your help man

> **blackmail said:**
> So how is the new chromium OS?
Sorry if I am off topic, just asking since i think your answers are already granted by coffecat, and also you can remove the entries from the GRUB menu :)

yeah goes good man the only thing is that to sign into ChromeOS you need an ethernet so it can connect to the internet and allow you to sign in and save the sign in info (wireless works but not during sign in)

---

### Post by blackmail on 2011-07-22
Ok so if I understand correctly, then the chromium os needs connection to the internet to allow you to boot up to it?

I wanted to try it but hearing this i will most certainly not install that thing

---

### Post by grahammechanical on 2011-07-22
@Sammya

I am not disagreeing with anything that the others have said but you can install Grub Customizer. That utility will let you mark entries in the Grub menu as not to be shown in the menu. It does not remove what has been put on sda4 but it might stop you seeing those lines in the menu.

Regards.

---

