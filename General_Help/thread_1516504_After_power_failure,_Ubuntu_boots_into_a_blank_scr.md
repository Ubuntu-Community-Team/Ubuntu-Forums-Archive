---
title: "After power failure, Ubuntu boots into a blank screen"
date: 2010-06-23
forum: General Help
---

### Post by toomuchjustin on 2010-06-23
My apologies if this post is redundant or in the wrong forum.  I'm new and I've done a search, but while I've found somewhat other threads discussing similar problems, I haven't seen one that quite matches mine or that I found helpful.

I'm using Ubuntu 10.04 64-bit, which is installed to a second hard drive on my desktop.  Earlier this afternoon, there were two 10 second power outages in my neighborhood.  The first caused the system to restart with no effect, but after the second outage Ubuntu no longer boots properly.

The problem is this: When I boot, I get to the grub screen.  I have tried choosing four different options (the most recent kernel, a slightly older kernel, and the recovery mode of each).  For each, kernel begins loading, but at a certain point the input to the monitor dries up, and after a few seconds the monitor enters standby mode.  When I boot into recovery mood, the last message I see before the screen goes blank includes "udev starting version 151" followed by three lines that read "assuming [something that I can't read before the screen goes blank]."  The computer itself remains on, but I have no way of knowing exactly what it is doing.

There seems to be no hardware damage as I can boat into Vista, and I can also boot into 10.04 from a USB.  I've used fsck to check the partitions on my hard drive and the test came up clean for all of them.

Since I only installed 10.04 a week ago, I could just copy the handful of useful files I have to my external drive and re-install, but I'd like to get some experience troubleshooting this problem and so would appreciate any clues.  My first assumption is some kind of problem with the video drivers or GUI, and since I'm not that knowledgable about either I'd great appreciate someone pointing me in the right direction.  Thanks!

---

### Post by mr clark25 on 2010-06-23
if you have the stuff to do it, you may want to attempt to use the "remote desktop" option...

but, if you still have the settings at default, you must confirm it...(on the computer you are trying to view)  so that may not work...

---

### Post by TRoe on 2010-06-23
It's tough to say. I have issues at work occassionnaly when we have a power strike from a storm. If the electrical surge from a lightning strike hits nearby at just the right time (say when your hard drive is accessing a critical file), it can corrupt the magnetic imprint of that file, rendering it useless (even with surge protectors and the like). I'm then forced to reinstall the OS because I can't determine the bad file... or at least that's my story... and I'm sticking to it!

You likely have no choice but to reinstall Ubuntu.

A snippet of advice... I put my "/home" directory on a separate partition. If I have to reinstall Ubuntu, I elect to not format the "home" partition and it saves all of my non-OS data... I just have to muck about a bit afterwards to set up my system again (reinstall packages from Synaptic, etc.).

---

