---
title: "Dual Monitor setup - Mouse pointer misplaced and other bugs"
date: 2011-03-23
forum: General Help
---

### Post by GTMoraes on 2011-03-23
Hello.

I love ubuntu, but sometimes it just drives me crazy.

Right now, I need to use a dual-monitor setup. Be it for my casual desktop usage, or to my projects and programs presentations with a slideshow. The latter is critical and that's why I'm here.

So, after some Intel Drivers update, some programs started to work nicely, faster and beautifully. But it corrupted my Dual-Monitor Setup.
I don't know what to say, I'm totally desperate. I had to show one of my programs to my teacher using a projector, but with the dual monitor corruption, I called in sick today. I need to use the netbook screen to make changes on the program and the second monitor/projector to show the program working.

I'll show some pictures, but I'm without a camera right now, so I'll use one china-phone that's hanging around here to take a picture. Sorry for the quality.
[IMG]http://i56.tinypic.com/2822qn5.jpg[/IMG]
Both Monitors, you can see on the right of the bigger one the corruption I'm talking about.

[IMG]http://i53.tinypic.com/2yuekk3.jpg[/IMG]
Mouse pointer misplacement

[IMG]http://i54.tinypic.com/287m0c7.jpg[/IMG]
Part of the primary monitor (LVDS) and an 'accessible' black area. 

It gets corrected when I disable Compiz, but I would like to use the Compiz with the dual-monitor setup, like I could before

It wasn't like this before updating the graphics. It was plug-and-play, tottally working, with or without Compiz enabled. What might be the cause? Do I need to create a Xorg.conf file? Update something?

Please help me =( Thanks

----------
Intel 4500 Mobile HD. Projector and my Monitor are connected thru HDMI. Doesn't matter if I change the resolution, stays the same.

-----------------------------------------

I tested something here. I've set up the netbook (LVDS) monitor as the right one
[IMG]http://i53.tinypic.com/wikcxv.jpg[/IMG]
This way, he's the one that becomes bugged, and the big one (now primary) works beautifully.
Basically, the left monitor will always work. The right monitor will have the bug
Placing monitors on top of another renders a black screen on one of them. Mouse cursor is still visible moving around even though the screen is black

I'm lost here =(

-------------------------------------------

I've tried deleting my xorg.conf. No luck, stays the same thing.

---

### Post by GTMoraes on 2011-03-23
Fixed. It was the Kernel version (2.6.35). Updating to the latest one available on Kernel.org (2.6.38 ) solves this.

---

