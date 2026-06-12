---
title: "Store settings for live disk"
date: 2011-07-25
forum: General Help
---

### Post by nsivin on 2011-07-25
On my desktop I am using Natty only on live disk. What I want to do is store my preference settings (for instance, rotated monitor) so that the disk will read them when it starts up. I used to do this with Knoppix, but I don’t know how Ubuntu can do it. I’d like to store the settings on a thumb drive or rewritable CD-ROM. I need to know what file to save to the drive, and how to let the CD know where to read it from. Is there some way to keep the settings file updated?

---

### Post by gordintoronto on 2011-07-25
Look for "persistence. " That's the keyword for saving your settings on a flash drive. Multisystem can make persistent flash drives. (It might have other difficulties, such as crashing during the process.)

---

### Post by nsivin on 2011-07-28
After searching for “persistence,” I found directions for making a flash drive with a persistent area using the Startup Disk Creator. I followed the very clear instructions, using the 32-bit live disk for Natty. On the first computer, a desktop with a 64-bit AMD Athlon CPU, specifying 1 GB reserved extra space, everything went fine until “creating persistence area” reached 81%, at which it stayed at 81% permanently. I had no choice but to cancel. On the second, a Thinkpad X60 with a 32-bit Intel CPU, same thing, except that it reached 100% and then went into an endless loop. It’s hard to understand why an OS would offer software so useless.

---

