---
title: "SD card will no longer mount"
date: 2010-03-20
forum: General Help
---

### Post by rmetzger on 2010-03-20
During the approximately 1 week since I last mounted my SD card with my laptop (Compaq cq60-420)  I've lost thha ability to mount or even find the SD card reader built into the PC.  Up to today it has worked fin but somehow its either stopped functioning or the operating system has lost the ability to communicate with it.

I ran the following in the terminal: sudo fdisk -l and it was unable to find anything other than my partitions.  If I plug in a memory card reader in the USB it works fine and automounts the reader and finds the card.  Also, one of my cards can be plugged into a usb connection and it is not found either.

any suggestions to troubleshoot?

---

### Post by dcstar on 2010-03-21
> **rmetzger said:**
> During the approximately 1 week since I last mounted my SD card with my laptop (Compaq cq60-420)  I've lost thha ability to mount or even find the SD card reader built into the PC.  Up to today it has worked fin but somehow its either stopped functioning or the operating system has lost the ability to communicate with it.

I ran the following in the terminal: sudo fdisk -l and it was unable to find anything other than my partitions.  If I plug in a memory card reader in the USB it works fine and automounts the reader and finds the card.  Also, one of my cards can be plugged into a usb connection and it is not found either.

any suggestions to troubleshoot?

Boot previous kernel version and see if things change.

---

