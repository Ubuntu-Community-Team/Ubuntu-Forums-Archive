---
title: "Random Crashing in 9.04"
date: 2009-06-30
forum: General Help
---

### Post by Pox on 2009-06-30
Hey all

I'm a fairly experienced Linux user, but this issue has me stumped.

I upgraded a machine (core2 e2200, Asus P5VDC-MX with VIA P4M800 PRO chipset) to 9.04 yesterday (coming from 7.10). I nuked the whole partition and let the installer choose how to set it up.

The install went fine, but soon after first boot I noticed I had some problems - the resolution was stuck at 800x600 (no big deal, I fixed this by setting refresh/scan rates manually in xorg.conf), and the system was crashing hard (straight back to POST) anywhere from 30 seconds to 15 minutes after logging in.

I checked the logs immediately after each crash and couldn't find any error messages, suggesting it's not even a kernel panic - it's just gone.  This suggested a hardware issue, but after working fine for two years, it seems very, very unlikely that a hardware issue would arise the day I upgrade the OS.  I'm currently downloading another distribution LiveCD to test this. I'll post back with the results when I have some.

Interestingly, while GNOME crashes within 10 minutes every time, KDE lasted for an hour, and I was using a raw X session with wmii for 4 hours this morning before it finally died.  I did "narrow it down" to something graphical yesterday by leaving it in a TTY for two hours, but after today's longevity I can't be sure.

The video card is VIA integrated (model in lspci below).  It crashes with both the openchrome and vesa drivers, and with NoDRI.

The really odd thing is that we have an identical machine (other than screen,mouse,keyboard) running 9.04, and it's going smoothly - no crashes, and the widescreen resolution was automatically configured.

I've had a good google around and haven't found any leads, and I'm all out of ideas short of trying other distros and swapping bits of hardware.  Anyone got any ideas?

Thanks in advance.

Output of lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
```

---

### Post by synapsys on 2009-06-30
Run memtest from boot menu.

---

### Post by Pox on 2009-06-30
Memtest was clean after one pass (in my experience if there's an issue, a single pass is always more than sufficient to find it).  Mandriva ran for an hour last night before I had to leave and I shut it down manually.

Also, I just tried booting it with the suspiciously loud DVD drive unplugged completely, no dice.  Anyone got any other ideas?

---

