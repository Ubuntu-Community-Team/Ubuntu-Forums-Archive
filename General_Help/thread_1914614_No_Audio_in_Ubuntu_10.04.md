---
title: "No Audio in Ubuntu 10.04"
date: 2012-01-24
forum: General Help
---

### Post by JohnnyPolite on 2012-01-24
Hello everyone,

I recently got a new desktop and installed Ubuntu on it. Unfortunately, I have yet to get the sound working. I've gone looking for fixes, and tried a number of them that I could find by looking through old threads and things, but so far no luck. 

If it helps, here's the output from aplay -l


**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And here is output from lspci -v


00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Also, I can't run alsamixer. when I try, I get the message "cannot load mixer controls: Invalid argument". So I downloaded the gnome alsamixer from the Software Centre, and while it downloaded no problem, it never actually launches.

Any ideas? Thanks for the help.

---

