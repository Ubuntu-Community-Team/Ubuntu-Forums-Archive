---
title: "Not able to set order of ALSA playback devices"
date: 2012-05-14
forum: General Help
---

### Post by fritz222 on 2012-05-14
Hi guys

I use XBMCbuntu Eden.

Alsa changes the order of my playback devices on nearly every bootup. I want to set my Xonar DG as default.
 I tried to set the order of my playback devices with one of this entries at the end of /etc/modprobe.d/alsa-base.conf:

[LIST]
[*]options snd-cmi8786 index=0
[*]options snd-xonar_dg index=0
[*]options snd-dg index=0
[/LIST]
I tried the above entries also in CAPS.


The ouput of cat /proc/asound/cards is the follwing:



 ```
xbmc@HTPC:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfbff4000 irq 43
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfaffc000 irq 17
 2 [DG             ]: CMI8786 - Xonar DG
                      C-Media Oxygen HD Audio at 0xde00, irq 18
```I'm at a loss right now. :confused:

Would be great if somebody is able to help me.
Thanks in advance.
Regards, fritz222

---

