---
title: "External Monitor: Wallpaper and Mouse limit"
date: 2010-04-19
forum: General Help
---

### Post by Fabrik on 2010-04-19
I'm using Ubuntu 9.10 (With Nvidia driver) in a Laptop, with an external monitor.

I'm current using the Twinview to set up both monitors, but there is some issues:

1) My second monitor has a higher resolution. So the height of the laptop monitor (The "internal") follows the height of the external one, so there is an area where the mouse can go, but there is nothing over there, which just annoys me to click in the programs opened at the taskbar.

Screenshot to explain better: [http://i43.tinypic.com/1r98k5.png](http://i43.tinypic.com/1r98k5.png)

2) As you can see in the screenshot above, my wallpaper gets cut in half between the monitors. I would like to know if there is a way to make the wallpaper fit perfectly each screen, without splitting it.

Thanks in advance.

---

### Post by Fabrik on 2010-04-20
bump

---

### Post by Fabrik on 2010-04-22
Bump.

---

### Post by P4man on 2010-04-22
confirmed. I believe there are bug reports about this on launchpad, but it cant be fixed (easily) due to the way how X works. Dont have the links, but I remember searching for it as i have the same issue using 2 different size monitors.

You can alleviate the issue somewhat by dragging your monitors in nvidia-settings so they align at the bottom. Obviously you get the same issue at the top then, but especially if you use something like docky with autohide, its a lot less problematic.

If there is a fix for this that I overlooked, Id love to hear it too.

---

### Post by Fabrik on 2010-04-24
What I did was removing the bottom panel of Gnome and adding some of that funcionalities to the top panel.

But still, I would like to have those 2 problems solved. I guess I should post somewhere else, since this section gets tons of new topics every day.

---

### Post by Fabrik on 2010-04-24
bump (?)

---

### Post by P4man on 2010-04-25
I looked a bit further in to this, and found this:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html)

scroll down to the MetaModes section. and read about panning domains:
> 
A panning domain is the area in which a display device's viewport will be panned to follow the mouse. Panning actually happens on two levels with TwinView: first, an individual display device's viewport will be panned within its panning domain, as long as the viewport is contained by the bounding box of the MetaMode. Once the mouse leaves the bounding box of the MetaMode, the entire MetaMode (i.e. all display devices) will be panned to follow the mouse within the virtual screen. Note that individual display devices' panning domains default to being clamped to the position of the display devices' viewports, thus the default behavior is just that viewports remain "locked" together and only perform the second type of panning.
[B]
The most beneficial use of panning domains is probably to eliminate dead areas -- regions of the virtual screen that are inaccessible due to display devices with different resolutions.[/B] For example:

    "1600x1200, 1024x768"

produces an inaccessible region below the 1024x768 display. Specifying a panning domain for the second display device:

    "1600x1200, 1024x768 @1024x1200"

provides access to that dead area by allowing you to pan the 1024x768 viewport up and down in the 1024x1200 panning domain.


 Looks like its possible to configure X in a way to alleviate this problem, but I have yet to try. Ill see if I can test this later.

---

