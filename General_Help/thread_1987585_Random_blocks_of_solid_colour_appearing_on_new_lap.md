---
title: "Random blocks of solid colour appearing on new laptop"
date: 2012-05-26
forum: General Help
---

### Post by demonboy on 2012-05-26
Yesterday we bought my wife an Acer 4752 and installed 11.10 64bit.

Completely randomly in both Chromium and Libre strange blocks of lines appear. I assume this is a graphics card compatibility issue issue since this does not happen to her in Windows. The lines are random and their appearance is random. They only appear in the window that is on top but if a window is opened on top of it, it doesn't show (that is, it only affects the current window). In Chromium they will appear in one tab and won't go away even when navigating in that tab, but they won't show in another tab. They go only after closing the app.

Here's a screen shot of what happens: [https://dl.dropbox.com/u/47314650/Screenshot%20at%202012-05-26%2015%3A40%3A07.png](https://dl.dropbox.com/u/47314650/Screenshot%20at%202012-05-26%2015%3A40%3A07.png) 

And here is a print out of her lspci:

> 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
03:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
03:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) 


Any help appreciated.

---

### Post by demonboy on 2012-06-07
C'mon, people, are you telling me I'm on my own here? 

So far I have found others who have other issues with the same laptop but their issues are completely different, like Unity 3D not loading up or stuff freezing. That's not happening with my wife's laptop though so I am loath to install the recommended xorg-edgers recommendation as outlined [here]("http://askubuntu.com/questions/87090/how-do-i-install-drivers-for-an-intel-hd-graphics-3000-on-an-acer-aspire-4750") as it appears to be a last resort and one that can mess with the computer.

Another recommendation was the [IntelLinuxGraphics ]("http://intellinuxgraphics.org/download.html")website but the download page gives warnings about compiling stuff, which I know nothing about, so it recommends getting the driver from pre-compiled sources. Where do I find these?

Our problems, then, are that we are not convinced the problems we are having are the same as other more serious problems other users are having. We're not comfortable downloading this xorg-edgers thing because it comes with loads of warnings and we are not happy compiling stuff ourselves. 

So what do we do? Any pointers? Please, we're about to lose my wife to Windows and even she doesn't want to do that!

---

