---
title: "Error booting with GParted from USB drive"
date: 2010-04-09
forum: General Help
---

### Post by krige on 2010-04-09
Hello,

I have installed gparted-live-0.5.2-1.iso on a USB drive using UNetbootin.

When I try booting from it I get the blinking message "Initial menu has no label entries!" for a few seconds, then the message "Could not find kernel image: vesamenu.c32" is displayed continuously, filling up the screen indefinitely.

Any idea why it's happening and how to fix this?

---

### Post by C.S.Cameron on 2010-04-09
I don't think gparted works with UNetbootin.
Parted Magic does though.
You might be able to get gparted working on usb using grub2 or syslinux,
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by krige on 2010-04-10
Thank you C.S.Cameron. Parted Magic didn't work either with UNetbootin.

I have tried following Choice 1 (Manually) instructions in:
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)
but didn't work either: now it doesn't even boot from the USB drive at all (I have ensured the USB is the first entry in the BIOS boot priority list).

---

### Post by C.S.Cameron on 2010-04-10
In some bios you need to make the flash drive the first HDD to boot from it.
Another alternative for booting iso's from USB is BootMyISO.
there is a write up on it here:
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)
I have tried it with gparted and it did not work but parted magic and Partition Wizard are suppose to.

---

### Post by krige on 2010-04-11
> **C.S.Cameron said:**
> In some bios you need to make the flash drive the first HDD to boot from it.

Yes, I knew that, that's what I meant with "I have ensured the USB is the first entry in the BIOS boot priority list".


> **C.S.Cameron said:**
> Another alternative for booting iso's from USB is BootMyISO.
there is a write up on it here:
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

Thanks, but that procedure requires a Windows XP/Vista/7 host to create the Bootable USB and I would rather not use Windows if possible (I am trying to detoxify myself from it).

I have found though another procedure to do the same thing using Linux only:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

I followed those instructions but still can't boot from USB.

I am start thinking there may be something wrong with the USB drive or in the procedure to make it bootable.

---

### Post by C.S.Cameron on 2010-04-23
I tried the panticz method and could not get it to work.
I got the one here to work:

[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

as long as I typed in the script by hand and did not copy and paste.

Replys 18 - 21 on this thread:
[http://ubuntuforums.org/showthread.php?t=1451184&page=3](http://ubuntuforums.org/showthread.php?t=1451184&page=3)
got gparted working for me.

---

### Post by wilee-nilee on 2010-04-23
If you have a ubuntu ISO use it, gparted is on the live cd. This also gives you the power of really messing with all the other partitions or at least access to them generally.

---

### Post by oldfred on 2010-04-24
I followed a combination of panticz & ky forum and got a bunch of ISOs booting.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

Another thread with discussion & examples
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

---

### Post by stvdel on 2010-04-24
Maybe you can try the Linux live USB creator to install it to your USB? [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

