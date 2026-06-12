---
title: "Bootable USB"
date: 2012-01-21
forum: General Help
---

### Post by nethompson on 2012-01-21
I am trying to make one of my usb drives bootable from a disk created by the company I work for. I am not trying to install any type of distribution or OS. The CD created by my company is fully bootable but after copying the files from the disk over to the usb it will not boot. I have attempted to install MBRs by using grub-install, install-mbr, and even using dd to copy the mbr from my local HDD. (Just the first 446 bytes) I have been trying to do this for a few weeks now without any luck. Any help would be greatly appreciated.

---

### Post by layers on 2012-01-21
Umm... are you talking about a linux distribution? Is it a custom cook from any of the debian derivatives? Why can't you just boot with the CD, and from there make a USB, like in all Ubuntus?

---

### Post by Double.J on 2012-01-21
Hi there, I think if we know which OS the cd uses to boot more advice could be offered?

generally if dd'ing the cd to the usb doesn't work some form of bootloader is needed.

---

### Post by nethompson on 2012-01-22
No, it is not a linux distribution. It is a custom made _bootable_ disk from the company I work for. I am trying to put the contents on a flash drive and boot from it that way but with no luck. If it boots any OS type, I would have to say it boots into a Windows-like OS.

---

### Post by sudodus on 2012-01-22
You cannot just copy or clone from the CD to a USB drive, but you can create an iso image file of the CD. Use Brasero to make the iso file (unless there is some kind of copy protection on the CD).

Then use Unetbootin to create a USB boot drive from that iso file!

---

