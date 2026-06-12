---
title: "No sound - was fine yesterday 12.04"
date: 2012-08-11
forum: General Help
---

### Post by tydfil on 2012-08-11
Sound worked fine yesterday.  Updated last thing last night.  Today I have no sound.  All applications trying to pay sound hang.  Volume control cannot be altered and icon is changed to a speaker followed by three dashes.

I have tried to follow troublshooting guides found by google but all look old and I don't fully understand guides which tell me how to start my driver when I don't know the driver name!

**sudo aplay -l**
[sudo] password for loveden: 
**** List of PLAYBACK Hardware Devices ****
Home directory /home/loveden not ours.
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**find /lib/modules/`uname -r` | grep snd**
Gives a long list of modules, codecs and drivers

 **lspci -v | grep -A7 -i "audio"**
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
	Subsystem: NVIDIA Corporation Device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fbf78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

 I also note youtube is blue but this is likely to be unrelated and I'm not sure I care enough to sort it!

Thanks to all who who respond.  Your help is greatly appreciated.

---

### Post by tydfil on 2012-08-11
Problem sorted.  Decided to remove all nvidia drivers to sort my flash issues.  Solved the sound problems to.  Don't know why.

Thanks to all who read my post.

---

