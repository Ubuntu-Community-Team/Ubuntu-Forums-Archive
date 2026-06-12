---
title: "GRUB issue"
date: 2010-04-05
forum: General Help
---

### Post by mreyes000 on 2010-04-05
Hello, this is my first post here, I recently migrated to Ubuntu. I'm fairly new to linux. I used Unix before so I'm fairly familiar with CLI. I tried to google some options and I've tried some solutions but nothing seems to have worked so far. Anyway, great to be here, but here's my issue:

I have 2 hard drives one with Windows 7 installed, the other has my ubuntu installed. When I try to select the windows 7 option in grub, the screen goes black and I have a blinking cursor but nothing ever happens.  I don't know what to do to fix it. I can boot into Ubuntu just fine.  My fdisk shows this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028e4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58336   468581376   83  Linux
/dev/sda2           58336       60802    19803136+   5  Extended
/dev/sda5           58336       60802    19803136   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000df62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS

and my grub.cfg looks like this:

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	echo	Loading Linux 2.6.32-18-generic ...
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	echo	Loading Linux 2.6.32-17-generic ...
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=eb780349-3bff-4904-b1e9-56b94bdb56d5 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eb780349-3bff-4904-b1e9-56b94bdb56d5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 847063bd7063b498
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

This is latin to me so any help would be greatly appreciated.

---

### Post by oldfred on 2010-04-05
This is lucid which is still beta. 

First try this to rescan for other operating systems:
sudo update-grub

If that does not work post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mreyes000 on 2010-04-05
Thanks for the help. I had already tried using the update-grub command.  It didn't fix it.  I have attached the results.txt from what you gave me.

---

### Post by oldfred on 2010-04-05
You have your windows drive as sdb, usually it is sda and windows likes to the the first drive, so I do not know if that complicates things. I would like you to have the windows boot loader in the drive it is installed to and grub in the MBR of the drive Ubuntu is installed to. The advantage is each drive is stand alone and can be booted without the other. Grub is good at finding the windows install so you can boot with grub and then choose.

I would make the windows drive temporarily first to boot in BIOS and then run the windows repairs. fixboot will overwrite the grub incorrectly installed in the PBR and fixmbr should install the windows boot loader to that drive. Then change BIOS back boot Ubuntu and run sudo update-grub to find the windows install and add it to the menu.

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by mreyes000 on 2010-04-05
Thanks so much. I'll check it out when I get home tonight!

---

### Post by mreyes000 on 2010-04-08
So I followed what you said to do and I've run into an issue. Now I can't boot into Windows or Linux.  If I change the bios to boot the linux drive first it says "Missing operating system" and if i change it to boot to the windows drive i get a cursor with nothing else happening.

---

### Post by oldfred on 2010-04-08
Lets rerun the boot_info script to see what is where. You can post it in your message just highlight with the cursor and use the code tag (# ) sign in the edit panel.

---

### Post by mreyes000 on 2010-04-08
Ok so I got it going again. I ended up reinstalling windows 7, for the sheer fact that none of my data is on that partition anyway, then I went into my bios and set my ubuntu drive as primary and booted into the livecd of ubuntu and followed this how to on getting grub back in gear:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Thanks for all the help!

---

