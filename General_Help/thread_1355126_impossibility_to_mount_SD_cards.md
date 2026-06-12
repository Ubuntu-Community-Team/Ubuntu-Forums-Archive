---
title: "impossibility to mount SD cards"
date: 2009-12-14
forum: General Help
---

### Post by Gingalone on 2009-12-14
My Ubuntu Karmic (on a desktop) refuses to mount a sd card both by means of a built-in cards reader and by an external usb card reader. The sd card I am struggling with is normally read and written on a HP laptop with Ubuntu Karmic (on built-in sd slot).
The card reader is seen by Ubuntu and a green light gets on when I insert the card in it.
What about? Thanks for any help.

---

### Post by efflandt on 2009-12-14
Sometimes a laptop SD slot is a different type of block device than usb mass storage.  Although, that should not really be an issue because when it is in a USB card reader it would be seen as an sd device.

What size is the SD and is it SDHC?  2 GB or smaller should not be an issue.  Some older devices may not know how to handle SDHC, or even faster than normal 4 GB SD.

What type of filesystem is on the SD (maybe a permission issue)?  Does it auto mount on the laptop when in the external USB reader?

How does it show up in **sudo fdisk -l** in laptop card slot, or when in external USB card reader.  Does **sudo fdisk -l** show it at all in desktop internal or external reader?  Does the desktop work with any other flash memory or USB memory stick or drive?

The SD card slot in my laptop is a block device that it will not boot from, yet it will boot from the same SD (actually microSD in an SD adapter) from an old Lexar SD card reader.  My desktop internal multi-card reader is connected through USB, so it can even boot from SD there (or external USB).

---

### Post by Gingalone on 2009-12-14
Thanks efflandt for the message,

Yes, the sd card I am working with (trying to) is sdhc (4 GB)
I have just tried an older 16 MB sd card and it still doesn't work on the built-in reader, but it is correctly mounted if connected through the external usb card reader.
The mystery deepens..!

The fs on the sd card is fat. 
Never tried the card reader on laptop (since its sd slot works!) and I have not it here to try that now.

With the sd (4GB) inserted in the external usb reader the terminal command
sudo fdisk -l gives only the PC's hard disk (nothing about the sd card).
Obviously same null response if the card is in the built-in reader.

The desktop works normally with usb flash drives (pen drives).

---

### Post by benj1 on 2009-12-14
what kind of card reader do you have? post the output of lspci.

---

### Post by Gingalone on 2009-12-16
Sorry for my delay with reply.
I made a few tests and I discovered that both my external USB card reader and my PC built-in one don't support SD HC cards, which is very disappointing since the pc is only 3 years old and so the usb card reader.
Any hope to read my 4GB sd card at home or I have to buy a state-of-art card reader?
Thanks and ciao,
Gingalone

---

### Post by mfdc1969 on 2009-12-20
I am having troubles mounting SD cards - I used to be able to in 8.10 & 9.04

Computer: Acer 5610Z
Card HP 2GB Secure Digital #L1877A


The results of lspci are:> 

[INDENT]06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d0102000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 84000000-87fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 11
	Memory at d0103000 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: [80] Power Management version 2

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 17
	Memory at d0103400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 11
	Memory at d0103800 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: [80] Power Management version 2

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 17
	Memory at d0103100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
[/INDENT]

If I use 'sudo gparted' I can see and format the card - I can not mount it though. The mount option in the gparted menu is unavailable.

Any suggestions?

Mike

---

### Post by mfdc1969 on 2009-12-20
OK, I solved my problem ... after posting above I went to [HP Support site for the SD card]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01290207&tmp_task=solveCategory&lc=en&dlc=en&cc=uk&product=1839471&lang=en") on a whim.

As instructed I just shut down and upon starting it a few minutes later 9.10 now auto mounts and is fully readable.

Curious as to why a re-start solved this but none the less I'm happy it works.

---

### Post by Sianegad on 2009-12-22
[http://ohioloco.ubuntuforums.org/showthread.php?t=1318913&highlight=sd+reader+menu.lst](http://ohioloco.ubuntuforums.org/showthread.php?t=1318913&highlight=sd+reader+menu.lst)

This thread helped me fix my built-in multiformat card reader.  might help you too

---

### Post by dcstar on 2009-12-22
> **Gingalone said:**
> 
Yes, the sd card I am working with (trying to) is sdhc (4 GB)
I have just tried an older 16 MB sd card and it still doesn't work on the built-in reader, but it is correctly mounted if connected through the external usb card reader.
The mystery deepens..!
.........

All SD card reader hardware is not equal, some can not read cards over a certain capacity, some can not read SDHC.

You have to have hardware that is compatible with your media.

---

