---
title: "Using external monitor with different aspect ratio"
date: 2009-07-02
forum: General Help
---

### Post by lykwydchykyn on 2009-07-02
This one's a bit tricky to explain, so bear with me...

I have a Dell Latitude E5550 laptop running Kubuntu Jaunty.  The monitor is a wide screen and does a max resolution of 1280x800.

When I hook up an external monitor, it mirrors my desktop.  That's ok, except the external monitor is at a more traditional aspect ratio.  Krandr has no trouble setting the monitor to 1280x1024 and keeping the laptop display 1280x800, but the actual desktop resizes to 1280x1024 so that the bottom 224 pixels (where, of course, the plasma panel, kmenu, tray, etc are) cannot be seen on the laptop.

The other option is to just drop both monitors to 1024x768 and have nasty stone-age graphics.  Not really desirable, especially since I'm doing this for presentation purposes.

I've poked around at the options, but I am not sure the best way to approach this.  I'd be ok NOT mirroring the desktop and just treating the external monitor as a second desktop, but I don't see an option for it.

---

### Post by lykwydchykyn on 2009-07-06
bump...

---

### Post by loomsen on 2009-07-06
You gotta configure your xorg.conf for it.

Specify a device, a monitor and a screen section for each monitor, then melt them together in the server layout section.

Template:
```

Device0
  its options

Monitor0 
  its options

screen0
  device0
  monitor0
    options

Device1
  its options

Monitor1 
  its options

screen1
  device1
  monitor1
    options

serverlayout
  screen0
  screen1 <position_relative_to> screen0  ## for example rightof

```

man xorg.conf 
will tell you which options you have available, you should at least configure the resolutions you want.

---

### Post by lykwydchykyn on 2009-07-08
I figured out how to do what I need using either xrandr, grandr, or arandr (for some reason, krandr doesn't allow the functionality), but due to a bug in my video driver ([https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/394490](https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/394490)) it doesn't work.  

Oh well, at least I know HOW to do it once this bug gets rectified.

---

