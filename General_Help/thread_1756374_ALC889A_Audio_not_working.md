---
title: "ALC889A Audio not working"
date: 2011-05-12
forum: General Help
---

### Post by blinder on 2011-05-12
Hi,

I have the following mb [http://www.gigabyte.lv/products/page/mb/ga-g33-ds3r/](http://www.gigabyte.lv/products/page/mb/ga-g33-ds3r/)  
Audio isn't working. I have the speaker volume set to 100% but it fails to produce any sound. 

[I]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0



lspci -v      
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
Subsystem: Giga-byte Technology Device a002
Flags: bus master, fast devsel, latency 0, IRQ 45
Memory at f4100000 (64-bit, non-prefetchable) [size=16K]
Capabilities: access denied
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel[/I]



How could I fix it? I neither know what's wrong.

---

