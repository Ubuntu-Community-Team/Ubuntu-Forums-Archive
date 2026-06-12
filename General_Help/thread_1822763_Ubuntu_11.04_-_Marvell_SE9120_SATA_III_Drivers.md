---
title: "Ubuntu 11.04 - Marvell SE9120 SATA III Drivers"
date: 2011-08-11
forum: General Help
---

### Post by Kissell on 2011-08-11
I upgraded an Ubuntu box with new hardware, bought an [_**ASrock 890FX Deluxe4**_]("http://www.asrock.com/mb/overview.asp?Model=890FX%20Deluxe4&cat=Specifications") mobo not just because it was cheap, but also because it was the only board I could find which could run an AMD six-core processor and had eight SATA III ports.  All Asus and Gigabyte products only have six SATA III ports, if they have a 7th and 8th port they are only SATA II speed.

Anyway, _**the box is up and running with Natty Narwhal 64-bit kernel version 2.6.38-8-generic.  **_

Unfortunately, I can't see all of my hard disk drives.  The BIOS sees them, they show up in the POST, but linux can't see them.  After further investigation I found out that the mobo uses two onboard SATA chips...  and guess what, _**the two ports that use the Marvell SE9120 chip are the two ports linux can't see**_.

> 
SATA3	- 6 x SATA3 6.0 Gb/s connectors by AMD SB850, support RAID (RAID 0, RAID 1, RAID 10 and RAID 5), NCQ, AHCI and "Hot Plug" functions
- 2 x SATA3 6.0 Gb/s connectors by Marvell SE9120, support NCQ, AHCI and "Hot Plug" functions


I would really appreciate some help on this...  I'm stuck..  ASrock doesn't provide linux drivers, and I haven't been able to Google-Fu a generic marvell driver for linux...  my only remaining thought is maybe I can somehow upgrade to a newer kernel that might have the drivers I need prepackaged in it...

---

### Post by Kissell on 2011-08-11
It's working :)

The fix appears to have been a BIOS modification.  I went to upgrade to the latest BIOS but it was already flashed with the latest, so I poked around the settings.
[U][B]
The BIOS setting for > SATA3_7,8 Operation was set to > IDE and I changed it to > AHCI[/B][/U] then when I booted up into Ubuntu I was able to see those drives in linux.  :)

NOTE1: The other onboard SATA controller is set to IDE mode and it works just fine, so I left it that way.

NOTE2: I also tried something I found in a similar old post with "sata_mv" and updating initramfs, but it didn't appear to work for me.  Just thought I'd mention it in case someone else tries the BIOS thing alone and it doesn't work.

---

