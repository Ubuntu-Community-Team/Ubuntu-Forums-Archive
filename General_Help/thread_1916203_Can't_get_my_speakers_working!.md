---
title: "Can't get my speakers working!"
date: 2012-01-27
forum: General Help
---

### Post by ofridagan on 2012-01-27
Hi,

It's a logitech usb speakers.
I ran every suggestions I could find, here are the outputs:

>>> sudo aplay -l
>>> **** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

>>> find /lib/modules/`uname -r` | grep snd
/lib/modules/3.0.0-15-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.0.0-15-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.0.0-15-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/3.0.0-15-generic/kernel/sound/isa/snd-sscape.ko
(...many more, not important right?)

>>> lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d12c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Any suggestions?

---

### Post by ofridagan on 2012-01-27
Those are the speakers, if it helps: [Logitech]("http://www.logitech.com/en-gb/for-business/products/speakers-headsets/devices/9448")

---

