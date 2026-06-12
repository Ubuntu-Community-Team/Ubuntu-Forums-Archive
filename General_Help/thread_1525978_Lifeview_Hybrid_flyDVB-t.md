---
title: "Lifeview Hybrid flyDVB-t"
date: 2010-07-07
forum: General Help
---

### Post by ganileni on 2010-07-07
hello to the Ubuntu community, I need some help.
please forgive my bad english, as I am not a native speaker.

I am currently trying to make a *Lifeview Hybrid flyDVB-t* tv tuner work on Ubuntu Lucid. The problem is that I can't even see it on the lspci output, here it is:
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```I've tried a lot of things, and I'm writing here as a last resort.

The last thing I tried, and the most reasonable to date, is to make the saa7134 driver work as shown here:
[http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)
(and obviously choosing the right *card* number, 94. I was uncertain about the *tuner* number, so I tried 63 and 67).
Anyways, after doing everything the post says, the output of the **dmesg | grep saa** command in bash is this:
```

$ dmesg | grep saa
[   15.665923] saa7130/34: v4l2 driver version 0.2.15 loaded
[   15.746641] saa7134 ALSA driver for DMA sound loaded
[   15.746644] saa7134 ALSA: no saa7134 cards found

```and the lspci output doesn't change.

Any ideas? I don't know what else to do, and I've been looking for a lot of time online.
Any help would be much appreciated. Thanks in advance.

---

### Post by ganileni on 2010-07-08
bump

---

### Post by ganileni on 2010-07-13
oh, come on! doesn't anyone have any ideas about why the tvtuner isn't working?

In every webpage I checked I read that the card is supported by linux  and working on every computer on earth, it seems it's not working only on mine.

By the way, I had a suspect that the tuner was just broken, so I tried looking at the hardware. It turns out that it's very difficult to reach by eye or hand, since my computer is a laptop. So, I installed windows 7, and found out that the card is correctly detected and working on that crappy OS... but still isn't on a way better OS as Ubuntu!

(...I wrote this also hoping that seeing windows working better than ubuntu on some specific issue will trigger the pride of Ubuntu fans :) )

---

