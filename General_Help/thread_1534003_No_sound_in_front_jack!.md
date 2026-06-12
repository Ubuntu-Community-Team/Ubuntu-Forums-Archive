---
title: "No sound in front jack!"
date: 2010-07-18
forum: General Help
---

### Post by pedrosurf on 2010-07-18
Hello everybody,
I've just installed Ubuntu 10.04, the sound works great but only in the back jack. The front jack, that I use my headset, is completely mute. The problem is not in the headset because it works fine in windows. I also tried alsamixer and all the channels are at the maximum level.
This link([http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+jack](http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+jack)) also didn't solve my problem.

My motherboard is M2N68 and the output from lspci -v (only the audio part) is:

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8345
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at dbff8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Any idea on how to solve my problem??
Cheers

---

### Post by oustiti on 2010-07-20
If you're using 10.04 have a look in Sound Preferences (can also be accessed from the Notification Area if you have the Volume icon there) and have a look at the output tab, particularly the output devices and connector settings.

---

### Post by smullins on 2010-07-30
I too am having this problem. Sound works from rear jack and microphone works from front jack but headphones through front jack are not working (works in Windows).

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I went through each option in the sound preferences hardware profiles and none of them enabled sound through the headphones. I've checked the levels in alsamixer and every level (including "headphones") is at full.

I can post my alsa-info as well if that helps (its over 1k lines).

Help would be greatly appreciated.

---

