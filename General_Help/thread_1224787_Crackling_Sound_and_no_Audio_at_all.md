---
title: "Crackling Sound and no Audio at all"
date: 2009-07-27
forum: General Help
---

### Post by jklol on 2009-07-27
I just installed ubuntu 9.04 and the sound was working perfectly before.  Then one day i booted up and I had no sound, just a crackling noise whenever there was supposed to be any sound, ie startup sounds, music etc.  Same when I go to system>preference>sound> and any of the tests.  I am getting sound in vista, so I don't think it's my sound card and it looks like ubuntu can see it, i ran "aplay -l" and "lspci -v | less" and saw my sound card come up both times:

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01f3
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I'm using a dell inspiron 1420.  Can anyone help me restore my sound??

---

### Post by Chronon on 2009-07-27
Check your mixer levels.

---

### Post by jklol on 2009-07-27
ah.  pci was turned all the way down when i ran "alsamixer" in the terminal, which is weird because it was all the way up in volume control.  i don't know, but my sound works now!

---

