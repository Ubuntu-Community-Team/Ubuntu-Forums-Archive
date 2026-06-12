---
title: "Wireless network - finding access points"
date: 2006-02-04
forum: General Help
---

### Post by omeg on 2006-02-04
Hi everybody. I've got Breezy set up on an old laptop, and it's got a Sitecom 802.11g WL-112 PCMCIA card. It has the Ralink chipset and the rt2x00 driver. 

Breezy supports my card out of the box, but I can't seem to be able to scan for wireless access points. I remember that Windows XP allowed me to see all available access points and then connect to one of them. Do I need to input the specific data where wireless points can be found in Ubuntu, or is there a similar method? I haven't set up my own wireless network yet, which will be coming in a while when my new ISP sends me a notification that I'm online, but I have been able to use my neighbor's wireless access point without problem before (albeit with a slightly low signal strength).

It would be great if there's a simple solution to this. Thanks in advance.

EDIT: some more information.
[font=monospace]
0000:01:00.0 Network controller: Ralink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
	Subsystem: Unknown device 182d:9070
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at 10800000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <available only to root>[/font]

---

### Post by zenwhen on 2006-02-04
See if wifi-radar works for you.

---

### Post by omeg on 2006-02-04
Wifi-radar seems to allow scanning for a connection, but also only if I give the network key. And it seems to give me problems just running it...

I first ran it without having the "ra0" network interface activated. Then I activated that interface (since I assume that it wouldn't work without it) and then all of a sudden I'm unable to run it anymore.

It gives me this output:
[font=monospace]
Traceback (most recent call last):
File "/usr/sbin/wifi-radar", line 1273, in ?
auto_profile_order = auto_profile_order.split ( ',' )
AttributeError: 'list' object has no attribute 'split'[/font]

---

