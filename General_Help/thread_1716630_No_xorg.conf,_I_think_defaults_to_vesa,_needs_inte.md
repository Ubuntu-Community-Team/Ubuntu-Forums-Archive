---
title: "No xorg.conf, I think defaults to vesa, needs intel"
date: 2011-03-28
forum: General Help
---

### Post by Lolpanda on 2011-03-28
Alright setting up a friends netbook, display has b een a litte iffy (slow. glxgears is giving like 100fps). 

Couple issues: xorg.conf doesn't exist (i know thats typically not an issue) and "sudo xorg -configure" and "sudo xorg --configure" both return "xorg command not found."

glxinfo say that its using Mesa for the software rasterizer and that the driver is from mesa. 

lspci says the VGA controller is from Intel. 

I'm thinking xorg is defaulting to vesa for drivers, but I need to know how to change that to the open source intel driver

---

### Post by bodhi.zazen on 2011-03-28
What intel card is it exactly ?

The open source driver is xserver-xorg-video-intel

[http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel](http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel)

The package is almost certainly installed already, and you likely have one of those difficult intel cards (such as the gma500).

---

### Post by Lolpanda on 2011-03-28
Yeah the package is installed, I knew it was, its just a matter of making xorg USE it. And I'm honestly not sure what the actual card is. 

lspci | grep VGA

says "Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)"  and glxinfo just says Mesa one after another, which strikes me as odd because when I do mine it says ATI Radeon HD 3200 (granted I have the catalyst driver)

Incase its a sandy bridge (style) processor where its combo'd. Its an Intel Atom Z530

---

### Post by Krytarik on 2011-03-28
First, the FPS is usually capped by the set refresh rate of the monitor. It doesn't make sense to compute a higher FPS than the monitor eventually can display.
[http://en.wikipedia.org/wiki/Frame_rate](http://en.wikipedia.org/wiki/Frame_rate)

Then, please check with
```
lshw -c video
```
what driver is actually running.

---

### Post by Lolpanda on 2011-03-28
Portions of the output  (Im on a diff computer than the netbook)

*-display UNCLAIMED

product: System Controlller Hub (SCH Poulsbo) Graphics Controller

vendor: Intel Corporation

clock: 33Mhz

configuration: latency=0


The clock speed seems REALLY low. And if I go to Preferrences > Monitor. Monitor says Unknown in pink, resolution is 800 x 576 (the screen seems like it could do better) and the refresh rate says 0 Hz with no other options. So SOMEWHERE, SOMETHING doesn't appear to be working right.

---

### Post by wojox on 2011-03-28
Should be

```
sudo Xorg -configure
```

---

### Post by Lolpanda on 2011-03-28
Thanks wojox, gotta hate cap sensative stuff sometimes lol

After a try or two it correctly configured. did a cat on xorg.conf and noticed under Section Device, the driver is "fbdev"  isnt that even lower than vesa? Working off the built in linux frame buffer

---

### Post by Krytarik on 2011-03-28
It's indeed the case that this is a chip which apparently needs special attention, like bodhi said, it's a GMA500 / Poulsbo.

You may try the driver provided by this PPA:
[https://launchpad.net/~gma500/+archive/ppa](https://launchpad.net/~gma500/+archive/ppa)

See here about how to install it:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

