---
title: "Problems with Audigy LS"
date: 2006-05-05
forum: General Help
---

### Post by Davidosky on 2006-05-05
Hi all,
i'm a new user of Kubuntu breezy 64bit (2.6.12-10-amd64-k8).
i am having to trouble getting sound to work on my breezy.
I have an Audigy LS... :rolleyes: 

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v:
> 0000:06:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs: Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at e400 [size=32]
        Capabilities: <available only to root>

KInfoCenter:
> Sound Driver: 3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Sengiro 2.6.12-10-amd64-k8 #1 Fri Apr 28 13:23:31 UTC 2006 x86_64
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
AudigyLS [Unknow] at 0xe400 irq 19

Audio devices:
0: CA0106 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: mixer00

modinfo soundcore:
> filename:       /lib/modules/2.6.12-10-amd64-k8/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E11490DC3F523551C4C2A6D
depends:
vermagic:       2.6.12-10-amd64-k8 gcc-3.4

Any help?

---

