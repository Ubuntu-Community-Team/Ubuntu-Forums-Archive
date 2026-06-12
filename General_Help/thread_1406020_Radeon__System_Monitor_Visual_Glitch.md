---
title: "Radeon / System Monitor Visual Glitch"
date: 2010-02-13
forum: General Help
---

### Post by AmandaKerik on 2010-02-13
While pretty, in a plaid way, my [System Monitor screen]("http://i7.photobucket.com/albums/y268/AmandaKerik/Ubuntu/Screenshot-1.png") is less than helpful.

This started after I upgraded to 9.10 and applied more recent updates.

From what I've [read]("http://ubuntuforums.org/archive/index.php/t-1285406.html"), the glitch is Radeon based. I have a [Radeon 7000]("http://ati.amd.com/products/radeon7000/radeonve/index.html") card which itself has 32mb of ram, but I told my computer a couple years ago to think it had 128.

I've tried the suggested short term fix in the linked thread (change the driver in /etc/X11/xorg.con to "vesa") but it didn't work.

I have two related requests:
What can I try to solve the System Monitor glitch?
How do I reset my settings back to knowing my video card's real capacity?

---

### Post by AmandaKerik on 2010-02-13
Bump (I hate having to do this, but I don't want my issue to be buried)

---

### Post by AmandaKerik on 2010-02-14
I kept digging during the time I figured someone would pop in and comment, and found two short-term solutions that work - [posts 10 and 11]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582/comments/10")

Because of my forementioned artificially boosted video card (cpu does the work beyond a certain point), I opted for the more taxing EXA option.

I said short-term solution because on 3-d(ish) games like Diablo 2 I still have fluttering bits and pieces (artifacts, I think they're called), but at least now it doesn't just crash.

I hope this helps someone.

---

