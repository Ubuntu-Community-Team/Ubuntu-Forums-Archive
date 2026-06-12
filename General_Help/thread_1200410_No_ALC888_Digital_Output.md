---
title: "No ALC888 Digital Output"
date: 2009-06-30
forum: General Help
---

### Post by SedaliaSteve on 2009-06-30
I have a Shuttle Prima XPC SP35 P2 barebones that I've installed 9.04 alternate on (for RAID1).

I've gotten the analog sound working but no luck with the digital SPDIF outputs. I borrowed some equipment from work to check them out and they are dead.

I used the **HOWTO: PulseAudio Fixes & System-Wide Equalizer Support** and that hasn't helped. In the Pulseaudio volume control I only see the HDA Intel - ALC888 Analog. There is no sign of a digital device.

Checking, I see:
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Steve

---

### Post by SedaliaSteve on 2009-06-30
Looking at my devices, I get:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3116
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I'm not sure if I should see two devices. I'm rather confused by some of the advice I'm finding on search. Lot's of people are getting no sound. I'm getting fine analog sound and nothing out of digital.

Steve

---

### Post by dvinothkumar on 2010-10-05
I am in the same situation. Were you able to resolve this?

---

