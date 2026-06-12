---
title: "Ubuntu and Zoneminder"
date: 2010-01-04
forum: General Help
---

### Post by rompstar on 2010-01-04
Great!  I am trying to implement a 4 camera system, to look over my proprty, just incase, nothing ever happened, but you never know and I have expensive horses on my property.  I have a 8 channel card, here is how it shows when I type: sudo lshw

*-multimedia:0
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: 8
bus info: pci@0000:06:08.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:16 memory:f8500000-f85003ff
*-multimedia:1
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: 9
bus info: pci@0000:06:09.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:18 memory:f8500400-f85007ff
*-multimedia:2
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: a
bus info: pci@0000:06:0a.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:21 memory:f8500800-f8500bff
*-multimedia:3
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: b
bus info: pci@0000:06:0b.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:22 memory:f8500c00-f8500fff
*-multimedia:4
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: c
bus info: pci@0000:06:0c.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:16 memory:f8501000-f85013ff
*-multimedia:5
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: d
bus info: pci@0000:06:0d.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:18 memory:f8501400-f85017ff
*-multimedia:6
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: e
bus info: pci@0000:06:0e.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:21 memory:f8501800-f8501bff
*-multimedia:7
description: Multimedia controller
product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: f
bus info: pci@0000:06:0f.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
resources: irq:22 memory:f8501c00-f8501fff

I installed ZoneMinder and try to add the first camera, as I have 2 installed so far, under /dev/video0 & 1, but I get no video and I know there is video flowing, as my friend is a pro and he installs these for a living, so he has a mobile device that can see the cameras, you just plug them into it.

Any idea ? what I have to do ?  since the hardware is seeing the card, but I get no video ?  

What am I doing wrong ?

---

