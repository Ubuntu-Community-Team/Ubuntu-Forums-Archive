---
title: "Writing to external media is slow to finalize"
date: 2010-05-21
forum: General Help
---

### Post by Keith_Beef on 2010-05-21
I have a USB hub on my desk, and also a multi-card reader in the front-panel of the computer (connected to a USB PCI card).

I have found that when I write files to a USB "thumb" drive plugged into the USB hub, or to a card in the multi-card reader (I have tried SD, SDHC, CompactFlash and MMC) the file is written quickly. The progress bar that appears on the screen goes to almost 100%, but then stops...

If I try to unmount the filesystem (either umount on the command line, or MB3 and eject or unmount option) I get a message that the device is busy. Sometimes, this stays busy for three minutes.

The filesystems on these cards are almost always FAT32; they are for digital cameras, media players, or are for exchanging files between home and office (where I use WinXP).

How can I find out what is causing this long pause at the end of writing a file?

K.

---

### Post by dcstar on 2010-05-22
> **Keith_Beef said:**
> I have a USB hub on my desk, and also a multi-card reader in the front-panel of the computer (connected to a USB PCI card).

I have found that when I write files to a USB "thumb" drive plugged into the USB hub, or to a card in the multi-card reader (I have tried SD, SDHC, CompactFlash and MMC) the file is written quickly. The progress bar that appears on the screen goes to almost 100%, but then stops...

If I try to unmount the filesystem (either umount on the command line, or MB3 and eject or unmount option) I get a message that the device is busy. Sometimes, this stays busy for three minutes.

The filesystems on these cards are almost always FAT32; they are for digital cameras, media players, or are for exchanging files between home and office (where I use WinXP).

How can I find out what is causing this long pause at the end of writing a file?

K.

Files are written to a memory cache which then physically writes to the device in the background. This means that the app believes that the file write is complete even though it really isn't.

You have to wait for the actual file write operations to the device to finish and this is dependant on the device/cable speed.

---

### Post by Keith_Beef on 2010-05-22
> **dcstar said:**
> Files are written to a memory cache which then physically writes to the device in the background. This means that the app believes that the file write is complete even though it really isn't.

You have to wait for the actual file write operations to the device to finish and this is dependant on the device/cable speed.

I know about buffer cache, and the sync command to flush the cache to disc, and I suspected that this was the USB that was slowing down the transfer. Writing to my NAS over the wireless network is sometimes slow like this, too, and I've noticed that writing to the SATA discs does not have this lag.

My question is not so much "why is my device slow?", but rather "how can I find out where the bottleneck is?". 

I've been looking around for some kind of benchmarking tool that can show how long it takes for data to get from the SATA disc to the Compact Flash in the card reader.

K.

---

