---
title: "Processor to 90% when restore Connectwise Window in ICA Session"
date: 2010-07-16
forum: General Help
---

### Post by charon79m on 2010-07-16
I'm running the Citrix XenApp Linux Client Version 11.100 to connect to my company's Citrix farm.  The connection works great until I fire up one particular application in my Citrix session, Connectwise.

When the Connectwise window is on the screen, the X process spikes to 90% and my entire Ubuntu desktop experience crawls.  When I minimize the Connectwise window in the ICA session, processor utilization drops to a reasonable level and all is well.

Yeah, read it a few time and shake you head... it doesn't make any sense, but that's what happens.

Remember, this is an ICA session to a Citrix farm (read terminal server) and the processor that is spiking is my local one.  It's a window inside the terminal session that is being minimized and restored that triggers the odd local processor utilization issue.

This is 100% predictable and I can replicate it at will.

Here's what I've got so far:
1:  There is no change in bandwidth usage.
2:  I've only found this to happen with the ConnectWise application.
3:  There is no change in utilization on the host server of my ICA Session.
4:  It is the X process itself that is pegging to 90%.
5:  It affects only a single core, it is not multi-threaded.
6:  It only one of my Ubuntu boxes. (I'd have listed this first, but I just now thought to try it.)

Ok... suggestions on troubleshooting this?  Now that I know it's just this one box, I'm considering a wipe an reload just for the fun of it.  Thoughts?

Here's some machine specific info:
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
01:05.1 Display controller: ATI Technologies Inc Radeon Xpress Series (RS482)
07:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)
```

---

