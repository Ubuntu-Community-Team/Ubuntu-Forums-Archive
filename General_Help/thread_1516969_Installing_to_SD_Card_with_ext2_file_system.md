---
title: "Installing to SD Card with ext2 file system"
date: 2010-06-24
forum: General Help
---

### Post by thricebedamned on 2010-06-24
Hi.  I've got an old EEEPC 701 kicking around, and I want to install Ubuntu 10.04 NBR to a 16gb SD flash card in order to avoid using the internal drive.

The trouble is it won't install how I want it to.

I want to format the card as ext2 as it's non-journaled and therefore faster to respond.  I also do not want to use any swap space.

I can use the defaults of ext4 and swap, and it boots and runs. However I do not want ext4 or swap.

I can also install Ubuntu NBR to the internal 4gb flash drive, as ext2 and without swap. Boots and runs fine.  I want to use this with the SD card tho.

So I know it can be done, I'm just missing a step.

Maybe I'm just picky.

---

### Post by dabl on 2010-06-24
Yep, I have one of those 701s also.  Running sidux/Xfce, it is my wife's favorite computer in the house.

The problem you are encountering is that the sdhc drive is really a USB drive internally.  So you have to (every time) tell it through the BIOS settings to boot from the USB device first.  Kind of clunky, unfortunately.

But yes, ext2 will work. However, you really do need a swap space or a swap file -- I don't think *buntu is going to very happy without one or the other.

---

### Post by thricebedamned on 2010-06-24
Runs fine without swap when it's installed to the internal flash drive.  I can set the BIOS to boot to the card by default as long as I don't remove the card, which I don't plan to.  Neither of these are issues.

In fact it boots to Puppy Linux installed to a card just fine. It boots to a ext4 formatted SD card with a swap partition just fine as well.

But it won't boot from an install from an ext2 formatted SD card.

---

### Post by dabl on 2010-06-24
> **thricebedamned said:**
> 

But it won't boot from an install from an ext2 formatted SD card.

Hmmm -- that almost smacks of a Grub bug.

I definitely did format a SDHC card ext2 and boot Linux from it, on my EeePC 701, but it was several years ago and I don't remember which distro it was.  But I don't see why the filesystem type would matter -- I agree ext2 would be the best choice for that situation.

---

