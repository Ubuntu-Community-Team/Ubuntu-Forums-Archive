---
title: "PulseAudio maxes out subwoofer and peeper"
date: 2011-01-24
forum: General Help
---

### Post by SpockVulcan on 2011-01-24
When ever I adjust the audio with pulse my subwoofer and peeper get maxed out. Even if I only adjust the volume just a little bit the sound is blasted. I have confirmed this with alsamixer. 

What my question is, is there a way to have the master adjust both my peeper and subwoffer at the same time? 

I can manually adjust each with alsamixer and if i make Master, PCM (peeper) and LFE (subwoffer) all the same level the sound is fine, but if possible could Pulse adjust all 3 at the same time keeping all 3 perfectly equal?

I'm on Ubuntu 10.10 64bit

*Output of "modinfo soundcore"*
```
filename:       /lib/modules/2.6.35-24-generic/kernel/sound/soundcore.ko
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     EF16BDAFD00EF5D7A386369
depends:        
vermagic:       2.6.35-24-generic SMP mod_unload modversions
```

*Output of "lspci -v | less"*
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

If more info is needed please let me know.

---

### Post by Frogs Hair on 2011-01-24
I use the Pulse Audio equalizer , which means the system volume is set low because   the EQ  preset I ues will boost the signal .

It is possible  to make and save your own presets but it takes some time . The EQ has presets of its own also .  [http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)

---

### Post by SpockVulcan on 2011-01-24
Well that is one way but this is on a laptop and it has hardware volume up and down, and even if I just press it once the master goes up just a little (which is to be expected) but the peeper and sub-woofer get cranked all the way up. What would work is somehow keeping all 3 linked so they all go up and down together

---

