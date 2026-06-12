---
title: "Black screen / hang at boot with ATI Radeon HD 4350"
date: 2010-12-01
forum: General Help
---

### Post by FoH on 2010-12-01
I need help troubleshooting this. I know that problems with ATi cards is fairly common, but this is somewhat different than the threads I've been looking at here.

**Background:**
I have a small form factor (SFF) desktop computer from Fujitsu Siemens. It's based around the Intel Q43 chipset with an internal Intel GMA card (which I've disabled in the BIOS). It has ONE extension, which is a regular PCI (NOT PCIe/Express) with room for a low-profile PCI-card.

Looking to increase the performance of my system, graphic-vise, I bought an HIS ATI Radeon HD 4350 PCI-version, low-profile compatible. The card has a DVI, HDMI and optional VGA connector (which I've removed to have the card as LP). However, when installing the proprietary drivers with "Additional drivers" / jockey-gtk, the computer get stuck on an black screen (although still "backlit", ie a signal goes out on the DVI-connector) and becomes completely unresponsive. I cannot switch to another VT etc. The logs does not give any clues, as far as I can tell (will post later if needed), so my theory is that it hangs completely. Sometimes when I move the mouse before the pointer is visible, I can see corrupted mouse pointer pop up and it moves around a bit before the system locks up. It looks like the corruption of graphics back in the old days when you set your CRT monitor's resolution to high, but it's in no way possible to tell that it is the mouse arrow, it's just like a lot of green lines, that's how bad it is.

**lspci | grep ATI:**
[FONT="Courier New"]05:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV710 [Radeon HD 4350] [1002:954f][/FONT]

**What I have tried:**
[LIST]
[*]My system is a Ubuntu 10.10 64-bit upgraded from 10.04. At first I thought that was the problem, so I've made a clean install on a different partition. I've tried both 32-bit and 64-bit. I've also tried the latest proprietary drivers downloaded from AMDs site. I've tried different workarounds listed here: [https://wiki.archlinux.org/index.php/ATI_Catalyst](https://wiki.archlinux.org/index.php/ATI_Catalyst)
[*]I've also updated the BIOS of the chipset.
[*]I've tried uninstalling radeon, ati, and other packages to see if there's a conflict.
[*]I've tried diffrent settings to gfxpayload when booting.
[*]I've tried inactivating splash when booting.
[/LIST]

**What works and what I want:**
The card works in full 1920x1200 resolution with the Radeon-driver. But I do not wish to use the Radeon-driver, the integrated Intel-card gives better performance.

I'm running out of ideas, but a couple of things I'm thinking of:
[LIST]
[*]Installing Vista on the computer and try the card with prop. drivers there just to see that it works in full load etc. Is it even possible that a card can work with the radeon driver but not the proprietary driver, if there's a hardware fault?
[*]Looking into options for the prop. driver for using in xorg.conf. a link to a list of these options would be appreciated.
[*]Looking into EDID problems, pointers to workarounds or troubleshooting this would be appreciated.
[*]According to log file of Xorg.0.log the card is identified as a PCIE card with both radeon and fglrx. For instance:
[/LIST]
[INDENT][FONT="Courier New"][   266.963] (II) RADEON(0): PCIE card detected[/FONT]
Is that a problem? I believe the PCI Express kernel module is loaded when fglrx is modprobed, but it's not loaded with radeon driver. Instead a intel_agp module is loaded (not used by any other modules though). Since my chipset has a regular PCI and not AGP nor PCIE, I'm wondering if this could be a source of trouble.[/INDENT]

[FONT="Courier New"]**lspci | grep PCI:**
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e11] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 [8086:3a70] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 5 [8086:3a78] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a2)
04:05.0 PCI bridge [0604]: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge [10b5:8112] (rev aa)[/FONT]

[LIST]
[*]There's a lot of repeated EDID information in Xorg.0.log, is that normal?
[*]At some point I got some mtrr errors in Xorg.0.log (I think it was), not sure with which driver, but I read somewhere that someone manually had to set the memory area for mtrr to get their card to work (different model though).
[*]I'll probably open up the computer again, and make sure that there isn't any other ports or connectors in there that could possibly be PCI Express. I'm not sure why those show up in the above, is there possible that some motherboards have PCI Express buses which components is soldered to? Because I don't see any extension ports in there (and anyways, a graphics card can't fit anywhere else in there, but in the PCI port). Here's a link to the computer: [http://ts.fujitsu.com/products/deskbound/personal_computers/esprimo_c_series.html](http://ts.fujitsu.com/products/deskbound/personal_computers/esprimo_c_series.html) (mine is a C5730 though, not sure what changed between C5730 and C5731). I need to check the PSU, too. The box recommends at least 300 W. Another reason to try the card under Vista I guess. Also, in the BIOS there's possible to chose between IGD (Internal), PEG (PCI Express), PCI and Auto for graphics. I've tried both PCI, PEG and Auto and disabled the second graphics device.
[/LIST]

Comments and pointers would be much appreciated!

---

### Post by FoH on 2010-12-01
Here's a link to an Xorg.log with the radeon driver for reference: [http://dl.dropbox.com/u/873907/xorg.radeon.log.txt](http://dl.dropbox.com/u/873907/xorg.radeon.log.txt) (was too big to attach)
Here's a link to the Xorg.0.log with fglrx driver: [http://dl.dropbox.com/u/873907/Xorg.0.log.txt](http://dl.dropbox.com/u/873907/Xorg.0.log.txt)
And here's a copy of the xorg.conf file: [http://dl.dropbox.com/u/873907/xorg.conf](http://dl.dropbox.com/u/873907/xorg.conf)

Here's the card: [http://www.hisdigital.com/un/product2-561.shtml](http://www.hisdigital.com/un/product2-561.shtml)

---

### Post by FoH on 2010-12-02
So I've installed Vista and tried ATI Catalyst drivers right away, and the systems hangs at login screen. I'm not finished trying in Windows, but there might be some hardware issues with this card (maybe in conjunction with my chipset). I'm beginning to think that PCI interface on newer cards isn't that good an idea :)

---

### Post by FoH on 2010-12-06
This is kind of embarrassing, but it seems that the problem has to do with the PSU (Power Supply Unit) in my SFF-computer. It's only 175W, and 300W is recommended for the card.
The thought didn't cross my mind that the computer had that little power. It's interesting that the card works with the radeon driver, I can only assume that a lot of heavier functions in the card isn't used with that driver, and once the proprietary drivers kick in the card doesn't get enough power anymore.

I'm gonna sell it and buy a whole new computer! :D

---

### Post by searchfgold6789 on 2010-12-06
It shouldn't be that hard to replace the power supply.
I did that a few times even before I turned geek.

---

### Post by FoH on 2010-12-06
> **searchfgold6789 said:**
> It shouldn't be that hard to replace the power supply.
I did that a few times even before I turned geek.

I've built my own computers a couple of times, and I've already looked into that. However, it's almost impossible to upgrade the PSU in this computer. As mentioned it's a Fujitsu Siemens and they seem very keen on making their own things from scratch. It's no standardized form factor on the PSU, it's practically molded to fit in this box. I looked at PSU with SFX- and TFX-form factors, and neither is small enough to fit. The computers measurement is 27x30x10 cm (BxDxH), which makes it smaller than most SFF computers sold by Dell etc. Any smaller would be the Ultra Small Form Factor.

It's not an expensive computer to begin with, so investing in the graphics card was rather "naive" in the first place, and investing in a new PSU would be even more so, IMHO :p It's very rare pieces of equipment I need, so the price/performance ratio is really bad. The reason why I bought the card in the first place is that I didn't want to change computer, since it fits nicely in my desk (due to the width of 27 cm). But I guess I'll have to move some stuff around :) And besides, with such rare pieces of equipment, I wouldn't want to be the owner once it breaks :P

I'll look into chassis and see what I can come up with, or just buy a SFF Dell computer and have it somewhere else.

---

