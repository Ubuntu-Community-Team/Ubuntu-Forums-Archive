---
title: "resolution is huge and and cannot change it"
date: 2011-03-30
forum: General Help
---

### Post by bbpirate on 2011-03-30
so i have a acer aspire, pretty old computer... doesnt have a video card in it, and it has windows xp on it, but when i run ubuntu linux on it the resolution is huge and i cant seem to fix it cause theres no options for me to change it. (i use a 32" LCD tv for the monitor if this has anything to do with the reason...) thank you

---

### Post by deathadder on 2011-03-30
> **bbpirate said:**
> so i have a acer aspire, pretty old computer... doesnt have a video card in it, and it has windows xp on it, but when i run ubuntu linux on it the resolution is huge and i cant seem to fix it cause theres no options for me to change it. (i use a 32" LCD tv for the monitor if this has anything to do with the reason...) thank you
Can you not change it from "System/Preferences/Monitors"? 

Does "System/Administration/Additional Drivers" offer you the option to install any other drivers? If not To find out what graphics chipset the onboard is using, run the command:
```
sudo lspci -v
```
Within a terminal, and look for "VGA compatible controller:" that'll print something similiar to this:
> 
adam@adamj-VB:~$ sudo lspci -v 
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at <unassigned> [disabled]
....

This will tell you what graphics card you're using. Then you can install the correct driver by installing the "xserver-xorg-XXX" package, where XXX matches your chipset. If you're not sure what to install, post the output of the command into a reply.

---

