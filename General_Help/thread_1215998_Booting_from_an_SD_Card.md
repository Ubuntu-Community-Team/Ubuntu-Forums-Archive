---
title: "Booting from an SD Card"
date: 2009-07-17
forum: General Help
---

### Post by cooper77z on 2009-07-17
My hard drive is kind of slow. I was wondering how I could go about saving the image to an SD Card and just booting from the SD Card to save time.

---

### Post by az on 2009-07-17
> **cooper77z said:**
> My hard drive is kind of slow. I was wondering how I could go about saving the image to an SD Card and just booting from the SD Card to save time.

What image?  Do you want to copy your whole drive to an SD card?  If your Ubuntu partition fits on an SD card, then you should be able to do it.  You need to partition the card so that you can install GRUB as the bootloader.  You probably will also need to edit the grub menu.list file to point to the correct partition.

---

### Post by cooper77z on 2009-07-17
Do you think my 2.2 ghz celeron bios will have a problem booting from a 16 gig sd card instead of the internal hard drive?

Also, I don't want to install the entire hard drive onto the sd card, just the os and a few important files. How stable is an sd card to shock? Is it worth buying a pcmcia memory device to try to boot from?

---

