---
title: "Screen going black"
date: 2010-09-07
forum: General Help
---

### Post by kleinebre on 2010-09-07
Hello all, 

On my ubuntu 10.4 desktop PC, occasionally after boot-up the (LCD) screen goes black. When I switch off the monitor and back on again, I'll get image for about a second, after which the screen goes dark again. When switching to a text console and back, I will have a login prompt on the text console which remains visible, but after switching back, after about a second- you guessed it- the screen goes black again. Pressing keys does 
not restore the image (i.e. it's not a screensaver issue); however, disconnecting and reconnecting the VGA cable invariably restores the image.

I've tried different VGA cables, so I know it's not a problem with the cable either. I've got an on-board ATI Radeon 1200x series and am running the open source drivers. Any idea what could be causing this? Unfortunately the behaviour isn't very consistent (apart from the image restoring when re-connecting the VGA cable). This issue also occurred on Ubuntu Studio 8.04, by the way. The monitor does not complain that there is no signal- apparently there is an in-range signal but black.

On a related note, when actually logging in the screen flickers immensly for a few seconds (erratically switching on/off by the looks of it, irregularly) before coming stable. This is with a 1280x1024 resolution. When starting up X from a console, however, the image is rock solid from the start, no flickering whatsoever. I've tried the common solutions (adding nomodeset and i915.powersave=0 to my kernel parameters) but this  does not make a difference. This is much less of a big deal as it is  merely cosmetic, but I'm thinking it might be related- although this is an issue new to 10.04 (or perhaps 9?) which I haven't seen in 8.04.

I've spent many hours reading forums trying to find a solution or a real answer, but after about 90 restarts I've still not got one, so any suggestions would be much appreciated! 

Best,
Marc

---

### Post by kleinebre on 2010-09-07
Additional info: Here's a video of the screen flicker on login:

[http://ringbreak.dnd.utwente.nl/~mrjb/blog/flicker.avi](http://ringbreak.dnd.utwente.nl/~mrjb/blog/flicker.avi)
(13 megabytes).

It looks less serious here due to the low frame rate of my 
camera, but each blink on the video is actually a burst of
blinks. Still, as mentioned, this is just a temporary cosmetic
problem- I'm more interested in figuring out why the screen
goes black unless I unplug/replug the VGA cable. That said,
if you know how to solve the screen blinks on login I'd be 
glad to find out.

---

### Post by kleinebre on 2010-09-09
> **kleinebre said:**
> I'm more interested in figuring out why the screen
goes black unless I unplug/replug the VGA cable.

It turns out this problem is not ubuntu-related. I recently started experiencing the same blackouts when just in Power-on-self-test (POST). Connecting another monitor gave a pristine image, so it looks like it is simply a hardware problem with my monitor.

---

