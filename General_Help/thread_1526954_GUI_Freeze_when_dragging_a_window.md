---
title: "GUI Freeze when dragging a window"
date: 2010-07-08
forum: General Help
---

### Post by andrekp on 2010-07-08
Hi everyone - Complete Newbie alert...
 
I dug out an old Win ME box that was gathering dust to repurpose as a Linux box: PIII 800Mhz, 644M RAM, 30G IDE HD, NVidia TNT2 64 graphixs card.
 
Both Puppy Linux and DSL seemed to run fine on it, but I want to run a Ubuntu flavor since I like that better (I have Ubuntu via Wubi running on my XP box and like it). 
 
Did a dual boot install of Xubuntu, since my system is old and small, and I wanted to keep ME for the immediate moment. Partitions: sda1=windows, sda2=/ @ about 6.6G, sda3=/home @ about 6.5G, sda4=LinuxSwap @ about 1.2G.
 
So far as I can tell so far, it runs fine with one exception: Sometimes, when dragging a window (seems to be the pattern) the GUI, completely freezes. It takes a hard button reboot to get back to running again. As long as I don't grab a window and try to move it, I don't think it's ever locked up. I suspect it's just the GUI that's locking since if I do ALT+SysReq R E I S U B the system reboots (most of the time - and whatever *that* is), which would seem to mean that *something* can still get the keyboard commands. I don't know how to actually test that theory, nor how it matters (newbie).
 
My suspician, therefore, is that it is graphix card related.
 
I tried initially to get the drivers for the TNT2 off NVidia's website, but had no luck installing them, and don't really know what I am doing anyway (I think whatever's already running with Xubuntu interferes with installing the new drivers - but again, I don't know). When I ran the NVidia installer in a terminal session, it couldn't create the kernel module because some thing was interfereing with that process.
 
I do know that with the neaveau (or whatever) drivers that came with the Xubuntu install, I seem to display just fine and get 3D effects. It's just that occassional freeze that guns up the works. And it only happens if I am dragging a window around.
 
I don't know how to safely deal with the Xubuntu graphixs drivers that are running now, nor whether making a change to different one really matters anyway, since the card seems to be running fine - except for the aforementioned drag-window-freeze. 
 
So two questions emerge from all this:
 
1). Does this sound like it's a graphix card problem, or something else.
 
2). Is there a way I can tell what it is that locks things up?
 
Thanks,
Andre

---

### Post by NCLI on 2010-07-08
You could start by trying to disable Desktop Effects. If that helps, the problem is most likely driver or Compiz related.

---

### Post by andrekp on 2010-07-08
My desktop effects have been off (nothing checked in compositor tab).
 
Tried removing compiz from system, it says it's not installed.
(apt-get --purge remove compiz compiz-core)

---

