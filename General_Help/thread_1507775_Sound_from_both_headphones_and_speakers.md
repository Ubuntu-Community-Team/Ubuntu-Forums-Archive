---
title: "Sound from both headphones and speakers"
date: 2010-06-12
forum: General Help
---

### Post by wksmeditate on 2010-06-12
[LEFT]I am receiving sound from both my headphones and speakers at the same  time. I have an alienware laptop running Ubuntu 10.04 32Bit. I have  tried muting and unmuting various options within alsamixer, but every  option which muted my speakers also muted my headphones. When I uncheck  the speaker option I receive no sound in both my speakers and  headphones. I receive the same outcome when I uncheck the headphone  option.

$ uname -a
Linux Debian 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC  2010 i686 GNU/Linux

$ lspci -v|grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition  Audio Controller (rev 02)

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC889A

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

[/LEFT]

---

