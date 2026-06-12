---
title: "DVI and 11.10"
date: 2011-10-16
forum: General Help
---

### Post by bibble235 on 2011-10-16
Hi,

I have a nvidia 6200. This has a SVGA and a DVI-D. I only use the DVI-D.

I have installed 11.10 (32-bit) and although it did install, none of the console screens work (I get black stripes) and worst of all the VOB playback is jumpy and jerky either direct from the harddrive or from the DVD.

Googling forever and a day I have found.

- Use the nouveau
This did not solve the VOB playback but did solve the console display.

- Custom EDID
i.e. do into nvidia setting save EDID.bin  chanage X to have 
Option "ConnectedMonitor" "DFP"
Option "CustomEDID" "DFP-0:/etc/X11/dfp0.edid"
This did not solve the console or the VOB playback

- Use old NVIDIA driver 173.14.28
This did not solve the console or the VOB playback

- Use new NVIDIA driver 185
This did not solve the console or the VOB playback

It looks like to me that the video card can only operate on he highest resolution. All others do not work. I cannot confirm but I am reasonably sure that the flash plugin did not work either however it was a long day.

---

