---
title: "resolution of additional displays"
date: 2012-04-23
forum: General Help
---

### Post by flipper T on 2012-04-23
hi,

have a laptop with a screen resolution of 1920x1200 & a lcd tv with a reported resolution also of 1920x1200.

the 2 are connected by a dvi-i to vga cable, if this is relevant.

lcd tv shows up in nvidia x server settings, and twinview works, but 2 questions:

1.   lcd shows up as ¨crt-0¨, i assume this stands for cathode ray tube...do i need to set this to lcd? if so how ?

2. max resolution for lcd tv shows as 1360x768 in nvidia settings. there is lots of google results for changing / adding resolutions to primary displays, but how to for attached tv ?

thx :)

---

### Post by papibe on 2012-04-23
Hi flipper T.

> **flipper T said:**
> 1.   lcd shows up as ¨crt-0¨, i assume this stands for cathode ray tube...do i need to set this to lcd? if so how ?
The LCD tech details are getting from a VGA connection (which is analog), thus the CRT name tag.

> **flipper T said:**
> 2. max resolution for lcd tv shows as 1360x768 in nvidia settings. there is lots of google results for changing / adding resolutions to primary displays, but how to for attached tv ?
First make sure about the TV resolutions available on each input. Even if the max resolution 1920x1200, it doesn't necessarily mean that is supported in all inputs.

Just a few thoughts.
Regards.

---

### Post by flipper T on 2012-04-23
> **papibe said:**
> 

First make sure about the TV resolutions available on each input. Even if the max resolution 1920x1200, it doesn't necessarily mean that is supported in all inputs.

 


hi & thx for quick response.

how do i find out the tv resolutions on each input?

---

### Post by cortman on 2012-04-23
> **flipper T said:**
> hi & thx for quick response.

how do i find out the tv resolutions on each input?

```
xrandr
```

---

### Post by papibe on 2012-04-23
Manuals, manufacture site, etc.

It also may be clues on the Xorg log file:
```
/var/log/Xorg.0.log
```
Could you paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and post back the link?

Regards.

---

### Post by flipper T on 2012-04-23
> **papibe said:**
> Manuals, manufacture site, etc.

It also may be clues on the Xorg log file:
```
/var/log/Xorg.0.log
```Could you paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and post back the link?

Regards.


[http://paste.ubuntu.com/943276/](http://paste.ubuntu.com/943276/)

i hope that is what you wanted

ps checked manual, 1920x1200 is listed as a support resolution

---

### Post by papibe on 2012-04-23
```
[    29.519] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    29.519] (WW) NVIDIA(0):     from CRT-0's EDID.
```
It looks like a common problem: you can't get the internal monitor's resolution and timings (EDID).

A few ideas:
[LIST]
[*]Try use a digital connection like DVI or HDMI. Those usually have less errros while trying to get the EDID data.
[*]If you have a Windows machine around it could be possible to get the data into a file, and then use it in  Ubuntu.
[/LIST]
Regards.

---

### Post by flipper T on 2012-04-24
¨Try use a digital connection like DVI or HDMI. Those usually have less errros while trying to get the EDID data¨

before i spend £20 on a dvi to hdmi cable, is there any way to ensure that i wont run into the same problem ? these are hard times, guys :(

ps irony of 1st world problem not lost on me.

---

### Post by cortman on 2012-04-24
> **flipper T said:**
> ¨Try use a digital connection like DVI or HDMI. Those usually have less errros while trying to get the EDID data¨

before i spend £20 on a dvi to hdmi cable, is there any way to ensure that i wont run into the same problem ? these are hard times, guys :(

ps irony of 1st world problem not lost on me.

Buy from a big retailer, keep the packaging real nice, and if it doesn't work, return it?

---

### Post by flipper T on 2012-04-24
yeah, but these cables come in those hard plastic, heat sealed, nuclear strike-proof, alcatraz tested, houdini-safe containers that you have to cut open & no matter how careful one is, it always looks like you have thrown it to a pitbull terrier to ´play´ with.

also considered stealing one, returning it if it doesn´t work, or posting them the cash if it does...

alternate plan is to target the greenest looking sales assistant & get them to promise on their mum´s life that it will work, giving me an easy return if needed.

---

### Post by cortman on 2012-04-24
> **flipper T said:**
> yeah, but these cables come in those hard plastic, heat sealed, nuclear strike-proof, alcatraz tested, houdini-safe containers that you have to cut open & no matter how careful one is, it always looks like you have thrown it to a pitbull terrier to ´play´ with.

also considered stealing one, returning it if it doesn´t work, or posting them the cash if it does...

alternate plan is to target the greenest looking sales assistant & get them to promise on their mum´s life that it will work, giving me an easy return if needed.

lol. +1.
Xrandr usually returns all available resolutions; is it limited by the VGA vs digital connection problem as well?

---

