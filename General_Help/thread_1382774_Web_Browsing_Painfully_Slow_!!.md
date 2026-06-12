---
title: "Web Browsing Painfully Slow !!"
date: 2010-01-16
forum: General Help
---

### Post by dazza1412 on 2010-01-16
I have just installed Ubuntu 9.10 on an old laptop to give it a try prior to loading up my main machine with it. I was expecting a little slowness performance wise as the laptop is an old Toshia Eqium (you know the old celeron cheapy from PC World). In general Ubuntu itself runs far better than Windows ever did however..................
 
What is the matter with the speed of internet browsing? Some pages load OK in Firefox whereas others take an age to load, if at all. In most cases the tab remains at loading even for Google. Installed the Ubuntu version of Google Chrome and got the same issues and worse!!
 
Any ideas folks? :confused:

---

### Post by n0dix on 2010-01-16
What is your graphics card?? Your configuration of xorg.conf? Give some details of hardware.

---

### Post by puzzler995 on 2010-01-16
how is it connected to the internet. If you are using Wi-Fi the card may be only Wireless G

---

### Post by dazza1412 on 2010-01-16
The only xorg.conf I could find having searched the file system was in /usr/share/man/man5 but is was a compressed archive called xorg.conf.5.gz.  What should I be looking for in this file? Also how does this file impact on web browsing?

---

### Post by wojox on 2010-01-16
Try disabling IPv6 and see if that makes a difference. 
[http://wojox.homelinux.net/?p=1](http://wojox.homelinux.net/?p=1)

---

### Post by dazza1412 on 2010-01-16
As for the graphics chipset, this I have no idea.   The laptop is a Toshiba Equium L100-186 and the Toshiba website gives little detail of this.  The WiFi is integrated 802.11 b/g

---

### Post by llama320 on 2010-01-16
> **dazza1412 said:**
> The only xorg.conf I could find having searched the file system was in /usr/share/man/man5 but is was a compressed archive called xorg.conf.5.gz.  What should I be looking for in this file? Also how does this file impact on web browsing?

The file you're looking for is /etc/X11/xorg.conf -- post is so we can have a look

---

### Post by efflandt on 2010-01-16
Unless the OP installed something non-standard for video, 9.10 does not even have xorg.conf unless he upgraded from 9.04 or created one.  So he may not even find that.

Not sure why puzzler995 mentioned Wireless G.  That is much faster than most home internet connections.  Even wireless B with a decent signal easily matches the 5000+ kbps test speeds of my DSL.  So that should not be in issue unless wireless is weak or intermittent (interference?).

There is a setting in Firefox to ignore ipv6, but I don't know if that makes any difference if Network Connections remains at its default to ignore ipv6.

What does **sudo lspci -v** in a terminal show for video and wireless if using that (or **sudo lsusb -v** if USB wireless)?

Have you pinged or run any speed tests on the internet from your ISP or [http://www.speedtest.net/](http://www.speedtest.net/) ?

One suggestion I saw somewhere suggested installing libadns1 which does asynchronous, non-blocking gethostbyname, etc. (which may help for multiple ads all over web pages).  But I don't know what 9.10 uses normally and have not done any benchmarking with/without it.

---

### Post by dazza1412 on 2010-01-17
wojox: A slight improvement but hanging on loading some sites remain (even this forum!!)

efflandt: The contents copied from the terminal are:-
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d4000000-d7ffffff
	Capabilities: [b0] Subsystem: ATI Technologies Inc RS480 PCI Bridge
	Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at d0004000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 14000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: 66MHz, medium devsel
	I/O ports at 8040 [size=16]
	Memory at d0004400 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 88 [Master SecP])
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0200000-d02fffff
	Prefetchable memory behind bridge: 10000000-13ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at d0004800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at d0004c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ATI IXP MC97 controller
	Kernel modules: snd-atiixp-modem

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at 9000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: radeon, radeonfb

09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at d0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 18000000-1bfff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at a000 [size=256]
	Memory at d0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp

09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 22
	Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath5k
	Kernel modules: ath5k

---

