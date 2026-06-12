---
title: "USB boot, older BIOS (USB-ZIP option only)"
date: 2010-09-24
forum: General Help
---

### Post by gstilma on 2010-09-24
This is my second post (I think), though I've been an Ubuntu convert since January. My question is not about Ubuntu per se, but thought I'd get an answer from one of you more readily than on another forum.

My machine was built for me 6 years ago, so the hardware, BIOS, etc. is at least that old. I'm preparing to build my own system, but for now all I can afford is a few upgrades, one of which is a new hdd. I want to clone the old one using Clonezilla live, preferably from a flash drive. My BIOS doesn't support booting from USB, just USB-ZIP and USB-FDD, but I found [[COLOR="Red"]this article[/COLOR]]("http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/") that explains how to fake a USB-ZIP drive.

Problem is: still doesn't work. When I get to the last step ```
syslinux /dev/sdb4
``` I get an error stating that sdb4 isn't recognized as a device. Running ```
fdisk -l
``` shows that the system is still seeing this partition as sdb1. Disk Utility, GParted, etc. see it correctly.

My specs:
System board: AOpen MX4B
BIOS: Phoenix Award v. 6.00PG
Processor: P4 2.4 GHz

The flash drive is SanDisk Cruzer Micro and I deleted the U3 stuff.

Any ideas on how to run syslinux successfully?

---

### Post by sikander3786 on 2010-09-24
This link will definitely help you.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by 7h3d4rk0n3 on 2010-09-24
When you go into the BIOS, check to see if your USB drive is listed as a disk drive, rather than a removable drive. That is how my USB drive is when I use it for booting Ubuntu 10.04.

---

### Post by gstilma on 2010-09-25
> **sikander3786 said:**
> This link will definitely help you.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
This is isn't a great workaround, IMO. I can just as easily burn a Clonezilla live CD.

> **berwald.derik@gmail.com said:**
> When you go into the BIOS, check to see if your USB drive is listed as a disk drive, rather than a removable drive. That is how my USB drive is when I use it for booting Ubuntu 10.04.
Nope -- it's just not listed, period. I'm given options of drive letters A-F, USB-ZIP, USB-FDD, CD-ROM, LAN, and a few others. Right now I have it set to primary USB-ZIP, secondary CD-ROM, third hard drive.

The link in my original post is instruction on how to mimic a USB-ZIP boot, which seems to be my best option, but I can't get it to work in my BIOS. I might give up and burn a live CD, just thought USB might make the cloning process go faster.

Any other thoughts?

---

### Post by 7h3d4rk0n3 on 2010-09-25
It seems that the LiveCD option would be your best bet, unless you can get the mimic to work.

---

### Post by universe-traveller on 2010-11-22
this may help you
[http://syslinux.zytor.com/doc/usbkey.txt](http://syslinux.zytor.com/doc/usbkey.txt)

---

### Post by gstilma on 2010-11-22
Thanks for responding to my 2-month-old question; I had given up. I appreciate the effort, but that txt file is linked in the [article]("http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/") in my original post.

---

