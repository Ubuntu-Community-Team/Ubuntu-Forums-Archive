---
title: "How to find an empty PCI-e slot?"
date: 2010-02-01
forum: General Help
---

### Post by pYrO1v1aniac on 2010-02-01
My laptop's wireless card failed some time ago. First it began dropping connections, then it failed outright and the device ceased to be detected at all, except on the occasional reboot.

I replaced it with another differently branded wireless card which fit in the slot (Mini PCI-e), and this didn't appear to be detected either.

I'm thinking of buying a new wireless card for it, but before I do, I'd like to know if there's a way I can ascertain whether the slot, or section connecting it on the mobo has failed, or if the second card simply wasn't compatible.

Is there any way to see whether the empty socket for the card is being detected in Linux?

This is what LSPCI is giving me. The old card was a broadcom BCM94321MC but it's not currently in the laptop.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
0b:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0c:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

And lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:820f Apple, Inc. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 05ac:0230 Apple, Inc. 
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I believe the entry for Broadcom Corp. to be the bluetooth adapter.

---

### Post by t4thfavor on 2010-02-01
It looks like a MAC, perhaps the laptop will only detect Apple hardware.

I have an HP I had to replace the card in, I was told that I had to buy an HP brand card, which at the time was an intel 2200 BG, I had one of them, and popped it in. 

The pc wouldn't even boot until I took out my "Haxxor Toolzz" and changed the PCIID from the intel one, to the HP one, at this time I also took the liberty of changing it to a Japan local :) Just cause I could.

Point of the story is I would find an apple card (if that's the case) and see if it's detected.

---

### Post by pYrO1v1aniac on 2010-02-01
But the point of this is to figure out if it's the slot that's broken before I go buying a new one, otherwise if it is, I'll just have dropped a lot of money on a poor paperweight.

---

### Post by pYrO1v1aniac on 2010-02-01
Anyone else?

---

### Post by clhsharky on 2010-02-01
Hi

Try a USB wireless card. Also take your laptop to store with you, and try adaptor first.

Sharky

---

### Post by pYrO1v1aniac on 2010-02-01
I've already gone through 2 USB wireless adaptors, and both seem to break after a few months use. Nothing abusive, they just died. I'd rather replace the internal card.

---

### Post by t4thfavor on 2010-02-01
My idea was to borrow another card from a friend, or get an ebay replacement. Though sometimes you cannot replace a card with a different brand because manufacturers suck. Sorry I couldn't be of more useful help.

Find another minipcie device, and see if it works.

---

### Post by wojox on 2010-02-01
What does:

```
iwconfig
```

And 

```
ifconfig
```

Tell you?

---

### Post by pYrO1v1aniac on 2010-02-01
> **wojox said:**
> What does:

```
iwconfig
```

And 

```
ifconfig
```

Tell you?

That I don't have a wireless card. Believe me. I know it's not working. I know neither card gave an entry in either of those commands. Right now there is nothing in the empty slot.

eth0      Link encap:Ethernet  HWaddr 00:1f:5b:f3:09:5c  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:5bff:fef3:95c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1356435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:822947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1765771479 (1.7 GB)  TX bytes:144516811 (144.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2184 (2.1 KB)  TX bytes:2184 (2.1 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

vboxnet0  no wireless extensions.

---

### Post by wojox on 2010-02-01
I missed that part about it not being in there. If you feel like putting one of them in run:

```
lspci | grep Network
```

And see if it recognises it. I've got a BCM4312 in my Dell Studio, so it's not really apple related I think.

---

### Post by pYrO1v1aniac on 2010-02-01
Okay, I'll dig one out (probably the old intel one from my old inspiron 6400 as the old BroadcomBCM43xx is definitely dead at this point, after it died, I left it in a pocket and put it through the wash). 

Stinkin' apple. I've no idea whether it's just that it won't detect the intel card cause of the hardware restrictions, or whether it's because the left hand I/O board is frigged, and the only way I can find out is to buy a card which is identical to the BCM43xx card that died (?) and see will it work.

To make matters worse, I don't have Mac OS X either.

---

