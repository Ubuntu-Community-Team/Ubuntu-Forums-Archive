---
title: "No Sound in Lucid"
date: 2010-09-21
forum: General Help
---

### Post by spivee69 on 2010-09-21
Hoping somebody might be able to assist here.  I've gone through many different threads about sound problems with Lucid, but so far, nothing I've done has helped.  I get absolutely no sound in this installation.  Everything was working until I upgraded from Karmic. 

For a while, I thought it might be my sound card, so I put in a new Sound Blaster card, but was still unable to get sound.  I have since removed it, but still available if I need to re-install.

System particulars:

uname -a
Linux odin 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

lspci -v
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7250
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9ff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC883

aplay -l
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

If I try to launch System->Preferences->Sound, I get a popup with "waiting for sound system to respond".

I've tried a number of things (including deleting the pulseaudio files, upgrading alsa etc) from my user but cannot get sound to work. correctly.  

Any help would be appreciated.  Really stumped..

---

### Post by lkjoel on 2010-09-24
> **spivee69 said:**
> Hoping somebody might be able to assist here.  I've gone through many different threads about sound problems with Lucid, but so far, nothing I've done has helped.  I get absolutely no sound in this installation.  Everything was working until I upgraded from Karmic. 

For a while, I thought it might be my sound card, so I put in a new Sound Blaster card, but was still unable to get sound.  I have since removed it, but still available if I need to re-install.

System particulars:

uname -a
Linux odin 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

lspci -v
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7250
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9ff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC883

aplay -l
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

If I try to launch System->Preferences->Sound, I get a popup with "waiting for sound system to respond".

I've tried a number of things (including deleting the pulseaudio files, upgrading alsa etc) from my user but cannot get sound to work. correctly.  

Any help would be appreciated.  Really stumped..
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

