---
title: "No sound in ubuntu 10.04"
date: 2010-08-24
forum: General Help
---

### Post by DeathMonkey68 on 2010-08-24
i have a clean install of Ubuntu 10.04 Desktop edition and i have no sound.

i have attempted most of the fixes that i can find and nothing works.

[http://www.alsa-project.org/db/?f=78a78926ac7d4b7f7f69d46723bc8c7904d24d36](http://www.alsa-project.org/db/?f=78a78926ac7d4b7f7f69d46723bc8c7904d24d36)

[HTML]


aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


[/HTML][HTML]

dmesg | grep HDA

[    9.487881] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.487973] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[    9.488003] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.037883] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11

[/HTML][HTML]

lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 2a74
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f9bf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


[/HTML]

---

### Post by drewbub on 2010-08-24
Try using alsamixer to check the levels

alsamixer- c 0
Or something similar.

I think the m key is used go mute/unmute

---

