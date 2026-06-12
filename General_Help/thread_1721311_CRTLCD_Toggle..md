---
title: "CRT/LCD Toggle."
date: 2011-04-04
forum: General Help
---

### Post by Skunkle on 2011-04-04
Hey, appologies if this has been brought up before but I cant find any related stuff to help me. I'm also a huge newbie on ubuntu so please be very basic with any info, I'm not no expert or nottin.I have connected my laptop to a crt tv via s-video adapter. It works on my other laptop and my desktop. But on this particular laptop I need to be able toggle the lcd/crt switch. My FN key to do this doesnt work. I seen something about i810switch on another thread and installed it. But like I said I'm a noob of the highest degree so havent a clue how to use it.

---

### Post by 3Miro on 2011-04-04
I suggest you use the display menu from System -> Prefs -> Display. If you want a shortcut to switch between them, you can take a look at the xrandr command:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

You can make shortcuts with commands like:

```
xrandr --output VGA1 --auto && xrandr --output LVDS1 --off 
```
and

```
xrandr --output VGA1 --off && xrandr --output LVDS1 --auto 
```

You can test them in terminal (Apps -> Access -> Terminal).

LVDS1 and VGA might be different for you. Use 
```
xrand -q
```
to see all monitors.

---

### Post by Skunkle on 2011-04-04
Thanks for the reply. I dont see a Display in the pref, I do have Monitors though which I'll assume is the same. I'm on Ubuntu 10.1 if its different. In the Monitor menu its only showing an unknown monitor which is the laptop screen I think. 

When I use xrandr -q I get : xrandr: 

Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0 



When I attempted the re-configure on thinkwiki page I got :

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log



Laptop must not be picking up the monitor. When on windows it didnt pick up other monitors until I switched the display with the toggle keys. Is there a way to bypass the fn keys and toggle it through the terminal ? Or would I be entering another world of headaches ?

---

### Post by 3Miro on 2011-04-04
When you plug the monitor, then xrandr -q should list it. Give us the exact model of your video card. Also, can you post the output of:

```
sudo lspci -v
```
the important section looks like this:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device d000
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at ee00 [size=256]
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: radeon
```
Yours would be different to reflect your video card.

---

### Post by Skunkle on 2011-04-04
Its an old laptop perhaps its past its usefulness, I'd imagine the video card is some integrated bit of rubbish. I cant even find the specific model of the laptop. I just connected my new samsung with ubuntu on it and its all working straight away. I might re-install windows on the other one or maybe dump it. Sorry to have wasted your time and thank you sincerely for the help. I'm just not in the mood to fight with that old thing any more lol.

---

### Post by 3Miro on 2011-04-04
> **Skunkle said:**
> Its an old laptop perhaps its past its usefulness, I'd imagine the video card is some integrated bit of rubbish. I cant even find the specific model of the laptop. I just connected my new samsung with ubuntu on it and its all working straight away. I might re-install windows on the other one or maybe dump it. Sorry to have wasted your time and thank you sincerely for the help. I'm just not in the mood to fight with that old thing any more lol.

The lspci command should give you info for the card and model. If it is too old, however, it may not have the proper driver to connect to an external monitor.

---

