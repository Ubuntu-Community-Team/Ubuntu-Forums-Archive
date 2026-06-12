---
title: "Rescuing GRUB"
date: 2011-04-19
forum: General Help
---

### Post by trisztan94 on 2011-04-19
Hi there,

I recentely installed ubuntu to my second hard disk (on the first i had windows 7 and data), but the hard disk that i installed ubuntu on broke, so i had to trash it. The problem is that i have an external disk reader that is only bootable after i booted at least once into windows. So basically i can't boot using either Windows or Linux disks, nor can i boot into the os itself. When i start the computer i get something like device not fount and a long code, then a prompt shows up (Rescue GRUB). What do i need to type here to remove grub and be able to boot into windows? 

Thanks in advance,
Trisztán

---

### Post by dragonfly41 on 2011-04-19
I've been through a similar problem where my internal CD-drive couldn't be used for booting LiveCD.

Firstly check if your bios allows booting from USB device.

If yes .. then you can download a copy of LiveCD into a USB disk which has been formatted and has boot flag set.

Parted Magic is another useful rescue disk which can be burned into a bootable CD or USB device.

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

To boot from USB device you will need to select F12 (or equivalent) to choose USB as the bootable source.

I also have an external CD disk reader which runs on USB port (in fact two ports, one for power the other for data) so check if you can load CD's from this via USB as another method of booting.

---

