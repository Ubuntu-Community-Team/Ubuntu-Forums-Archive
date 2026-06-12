---
title: "Making a Boot Disk"
date: 2011-07-04
forum: General Help
---

### Post by chome4 on 2011-07-04
Just downloaded: Super_OS_10.10_32_bits and extracted it to a folder. How do I cut the files onto a blank DVD to be bootable?

When I last downloaded an iso file, I just double-clicked it and it launched the DVD burner and it did the rest.

---

### Post by Habitual on 2011-07-04
try unetbootin

---

### Post by sidzen on 2011-07-04
Just burn the ISO file at no more than 8X after first checking the MD5SUM  (Tools => Burn Image), or

[COLOR=#ffff00][COLOR=Navy]1. Download your chosen ISO file, noting the path to where it was downloaded  (*i.e.* /home/username/Downloads/)

2. Insert your USB stick and learn how it is recognized by the system, To do so, enter the command:
[/COLOR][/COLOR][COLOR=Navy]
[/COLOR] [INDENT] [COLOR=Navy]    sudo ls -l /dev/disk/by-id/*usb*[/COLOR][COLOR=Navy]           
    (or eliminate "sudo" if entering as root)
[/COLOR] [/INDENT][COLOR=Navy]
   This should produce output along the lines of:

[/COLOR] [INDENT] [COLOR=Navy]    lrwxrwxrwx 1 root root  9 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0[/COLOR][COLOR=Navy]
[/COLOR] [COLOR=Navy]    -> ../../sdb[/COLOR][COLOR=Navy]
[/COLOR] [COLOR=Navy]    lrwxrwxrwx 1 root root 10 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0-
    part1 -> ../../sdb1[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]
3. Unmount the usb stick  (NOTE: replace the X in sdX with whatever was returned in the first line from command above)
[/COLOR][COLOR=Navy]
[/COLOR] [INDENT] [COLOR=Navy]    sudo umount /dev/sdX[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]
4. Use this command to write (as root) the image iso to your USB stick:

[/COLOR] [INDENT] [COLOR=Navy]    dd if=/path/to/your/distro.iso of=/dev/sdX bs=4M;sync[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]

You should now have a bootable USB stick of your chosen Operating System.[/COLOR][COLOR=Navy]
[/COLOR]

---

### Post by chome4 on 2011-07-05
Thanks for that. I'll try them both later...

---

### Post by chome4 on 2011-07-09
when I enter: sudo ls -l /dev/disk/by-id/*usb* 

I get:

lrwxrwxrwx 1 root root  9 2011-07-09 14:57 /dev/disk/by-id/usb-Kingston_DT_101_II_001372982D2AA9B0963704C0-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2011-07-09 14:57 /dev/disk/by-id/usb-Kingston_DT_101_II_001372982D2AA9B0963704C0-0:0-part1 -> ../../sdb1

When I then change [COLOR=Navy]sudo umount /dev/sdX[/COLOR][COLOR=Navy] and replace the 'X' with:

[/COLOR]lrwxrwxrwx 1 root root  9 2011-07-09 14:57 /dev/disk/by-id/usb-Kingston_DT_101_II_001372982D2AA9B0963704C0-0:0 -> ../../sdb

I get:

bash: ../../sdb: Permission denied

---

### Post by vinayaksawant on 2011-07-09
If u want to make bootable usb the best unnetbootin. Try it by using following link----------------------- " http://unetbootin.sourceforge.net/"
:)

---

### Post by chome4 on 2011-07-09
> **vinayaksawant said:**
> If u want to make bootable usb the best unnetbootin. Try it by using following link----------------------- " http://unetbootin.sourceforge.net/"
:)

What's the difference between Netinstall, HDmedia and _Live. Which one do I choose?

I'm also getting: 

p, li { white-space: pre-wrap; } 7z not found. This is required for either install mode.
 Install the "p7zip-full" package or your distribution's equivalent.
 
When I run the executable program.

---

