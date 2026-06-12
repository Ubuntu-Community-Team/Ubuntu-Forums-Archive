---
title: "Network inferfaces all jacked up"
date: 2011-12-26
forum: General Help
---

### Post by KamrynB on 2011-12-26
Hello and thanks in advance for reading.

I am a Linux newbie and have only been using it for a few months now. I recently upgraded to 11.10 from 11.04 on my HP Mini 100 netbook. It works great except for annoyances I am experiencing with my network interfaces.

First of all, my wired interface doesn't always show up. Sometimes I boot and its there (checked via ifconfig -a) and other times its not. Its really annoying since I use that port for ICS to my wifi pineapple. 

Second, my wireless interface shows up as eth0 (when my wired isnt showing up) or eth1 (when my wired IS showing up). I would really like it to be wlan1 at all times, like it was when my netbook was running BackTrack 5 or Ubuntu 11.04.

I have tried solving this on my own. I ran into this page which looks promising:

[http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html]("http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html")

When I went to etc/network/interfaces this was the content of the txt file:

```


auto lo
iface lo inet loopback


```

How do I add eth0 and wlan0 to this file so those interfaces are automatically recognized? I would experiment with it myself but I don't want my interfaces to go from "annoying" to "not working at all" and have to reinstall Ubuntu.

Thanks in advance
Kamryn

---

### Post by Bobhuber on 2011-12-26
> **KamrynB said:**
> Hello and thanks in advance for reading.

I am a Linux newbie and have only been using it for a few months now. I recently upgraded to 11.10 from 11.04 on my HP Mini 100 netbook. It works great except for annoyances I am experiencing with my network interfaces.

First of all, my wired interface doesn't always show up. Sometimes I boot and its there (checked via ifconfig -a) and other times its not. Its really annoying since I use that port for ICS to my wifi pineapple. 

Second, my wireless interface shows up as eth0 (when my wired isnt showing up) or eth1 (when my wired IS showing up). I would really like it to be wlan1 at all times, like it was when my netbook was running BackTrack 5 or Ubuntu 11.04.

I have tried solving this on my own. I ran into this page which looks promising:

[http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html)

When I went to etc/network/interfaces this was the content of the txt file:

```


auto lo
iface lo inet loopback


```How do I add eth0 and wlan0 to this file so those interfaces are automatically recognized? I would experiment with it myself but I don't want my interfaces to go from "annoying" to "not working at all" and have to reinstall Ubuntu.

Thanks in advance
Kamryn
I had the same problem and this is what I found.
Under 11.10  use the network manager (click on top bar icon)for all your configuration instead of modifying the /etc/network/interfaces file. I'm not using wireless but had to set up static IP that way and it did not change the 
 /etc/network/interfaces file after I made the changes. There is a post somewhere but I'll be darned if I can find it explaining why and where the changes are made.

---

### Post by KamrynB on 2011-12-26
So I should set up a static IP profile for my wired connection, just so my computer boots up with my wired connection recognized by the system?

---

### Post by KamrynB on 2011-12-26
Interesting note: 

If my computer is plugged in to the power when I first turn it on, the wired connection is recognized.

If I'm running on the battery when the computer turns on, it only recognized wireless.

Is it some kind of power saving feature? Can I disable that?

---

### Post by Bobhuber on 2011-12-26
> **KamrynB said:**
> So I should set up a static IP profile for my wired connection, just so my computer boots up with my wired connection recognized by the system?
That's not necessary unless you need a static IP. The network manager will assign the address automatically for you.
IMHO You will gain much more speed and reliability with a wired connection. You can specify thru the network manager whether or not you want the wireless to connect automatically or not. As far as the netbook is concerned if its like the few that I have messed with you can disable the wireless entirely if desired.Something you would have much more knowledge of as the owner

---

### Post by supremedalek on 2011-12-26
Is it possible you are running Network Manager?

---

### Post by KamrynB on 2011-12-27
If network manager is the utility that comes with 11.10 then yes I am running network manager. I have tried setting up a wired profile called "auto" which is set for DHCP. I restarted the computer and the wired connection still did not show up. I am running on battery. I'm just going to post the output of 'lshw -C network', 'ifconfig -a' and 'lspci'

```


kamryn@kamryn-netbook:~$ sudo lshw -C network
[sudo] password for kamryn: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: (intentionally removed)
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.11.139 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff

```

```

kamryn@kamryn-netbook:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr (intentionally removed)  
          inet addr:192.168.11.139  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe0b:4ffe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2454 errors:0 dropped:0 overruns:0 frame:2238
          TX packets:2075 errors:37 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1069532 (1.0 MB)  TX bytes:344402 (344.4 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```

kamryn@kamryn-netbook:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

It doesn't seem to find my wired connection at all.

---

### Post by KamrynB on 2011-12-27
This is 'sudo lspci -v'

```


kamryn@kamryn-netbook:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at dc80 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, fast devsel, latency 0
	Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 000000007fa00000-000000007fbfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 361a
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 000000007f800000-000000007f9fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 361a
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe937c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 361a

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 361a
	Flags: medium devsel, IRQ 15
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Hewlett-Packard Company Device 1507
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number (removed)
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

---

### Post by KamrynB on 2011-12-27
My "NetworkManager.conf" file says

```

[ifupdown]
managed=false

```

So does that mean I'm not using network manager?

---

### Post by KamrynB on 2011-12-27
Ok based on my own testing Ive determined the wired interface ONLY comes on when the netbook is plugged in to power during boot up. How do I change that so it is on all the time?

---

### Post by KamrynB on 2011-12-28
Well I kinda fixed my own problem. After scouring the Internets for what feels like days I finally ran into this site which explains multiple workarounds. Every HP Mini 1000 owner needs to see this. Apparently this is a well known bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297263]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297263")

Thanks for fixing my problem KamrynB!

---

