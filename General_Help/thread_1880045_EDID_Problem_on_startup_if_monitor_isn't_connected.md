---
title: "EDID Problem on startup if monitor isn't connected."
date: 2011-11-12
forum: General Help
---

### Post by niietzshe on 2011-11-12
I have a Revo running Pre-Eden updated from the default XBMC-Live-Dharma install.

If I have my amp/tv turned to the correct inputs it'll have no problems starting up, but if they're on different inputs it refuses to start (don't think I've had this problem before, but might have never tried to start it without the screen being on the right channel).

I've read that if I create a custom EDID file in /etc/X11 and point the xorg.conf to it that'll it'll use that if it can't find the monitor. Has anyone got any idea of what kinda format this should be in? I've searched all over the place but can't find an example.

If I run:
```
sudo get-edid | sudo parse-edid
```

I get this (when amp is connected and XBMC Live is working):
```
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
```

How should I use that to create my own EDID to point to in xorg.conf? And is the error anything to worry about?

Thanks for any help
Christian

---

