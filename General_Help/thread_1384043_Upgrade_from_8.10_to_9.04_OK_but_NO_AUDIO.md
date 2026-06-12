---
title: "Upgrade from 8.10 to 9.04 OK but NO AUDIO ???"
date: 2010-01-17
forum: General Help
---

### Post by ozark_hillbilly on 2010-01-17
Just jumped from intrepid to jaunty (9.04) and it went OK but
I have NO AUDIO (Desktop or Browser).

I am not experienced in Linux troubleshooting.

Here is a partial listing of lspci -v : 

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Attached is a file of other terminal command results for 
lshw -c
lspci
lspci -v
cat /etc/X11/xorg.conf
aplay -l

Any directions like a thread to use for troubleshooting or 
configuration settings to check for would really be appreciated!

Ed

---

