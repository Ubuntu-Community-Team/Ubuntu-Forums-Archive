---
title: "Multiple Monitors and Default Screen"
date: 2010-05-20
forum: General Help
---

### Post by osarusan on 2010-05-20
I have an ATI card using the open source drivers, Ubuntu 10.4, and 2 monitors plugged into the card.

The monitors work find and detect fine, but for some reason Ubuntu always wants to make the right monitor the "default" one rather than the left one. It's not such a major problem, but it's a nuisance. For example, the Panels are on the right monitor and I have to manually pull them over to the left one -- and since they are different resolutions the locations of the Panel widgets are all screwed up.

New windows and dialogs often open up on the right one too, though my icons are all on the left monitor like I'd like them to be.

Is there some hidden setting somewhere that will tell Ubuntu that the left monitor is the one I want to be the "main" screen? Manually dragging everything is time consuming and frustrating.

---

### Post by bodhi.zazen on 2010-05-20
I had a similar problem , and the problem existed across OS, so it is easier to physically switch the location of the montiors or switch the cables in the back.

Otherwise it tends to vary by window manager and the tool you use to set your monitors.

---

### Post by osarusan on 2010-05-20
Switching the cables is not so easy because one is VGA and one is DVI, and physical location is not so adjustable either because one is a Wacom Cintiq that I use for work and I need it to be in its primary location. At least Gnome remembers that it is the left monitor (Windows can't seem to do that), but on the other hand, Windows remembers which one is the primary monitor and Gnome doesn't...

---

### Post by osarusan on 2010-06-03
Any other ideas on this?

It's becoming a problem because the monitors are different resolution, and apps that want to use full screen are trying to force a 1680x1050 resolution into a 1600x1200 screen, resulting in some messed up graphics.

I can't switch the monitor cables, so isn't there some way to do this in Gnome?

---

### Post by bodhi.zazen on 2010-06-03
> **osarusan said:**
> Any other ideas on this?

It's becoming a problem because the monitors are different resolution, and apps that want to use full screen are trying to force a 1680x1050 resolution into a 1600x1200 screen, resulting in some messed up graphics.

I can't switch the monitor cables, so isn't there some way to do this in Gnome?

IMO gnome is not the best window manager for multiple monitors, which is one of the top reasons I use XFCE.

KDE is a bit better then gnome.

I assume it may be a setting in your ATI card configuration, but I am not sure how to do that (configure an ATI card).

---

### Post by osarusan on 2010-06-04
With KDE or XFCE is it possible to set the primary and secondary monitors?

I'll take a look through the ati driver docs for now.

---

### Post by Favux on 2010-06-04
Hi again osarusan,

You might want to look at this thread:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

---

### Post by isbura on 2010-06-04
I can't be sure of the specifics since I'm on a single-monitor system at present, but I recall editing a file, **~/.config/monitors.xml** which contained monitor descriptions used by GNOME. In this file there was a line under each monitor config similar to 
```

<primary>No</primary>

```After changing the value to **Yes** for the external monitor on my laptop and restarting X all my GNOME panels appeared on the external display rather than the internal one, something similar to what you're after I think.

edit: it may have been 1 or 0 rather than Yes or No but the same principle applies

---

### Post by osarusan on 2010-06-05
Sir, you are a hero. Thank you so much! This is EXACTLY what I was looking for. It worked perfectly!

> **isbura said:**
> I can't be sure of the specifics since I'm on a single-monitor system at present, but I recall editing a file, **~/.config/monitors.xml** which contained monitor descriptions used by GNOME. In this file there was a line under each monitor config similar to 
```

<primary>No</primary>

```After changing the value to **Yes** for the external monitor on my laptop and restarting X all my GNOME panels appeared on the external display rather than the internal one, something similar to what you're after I think.

edit: it may have been 1 or 0 rather than Yes or No but the same principle applies

---

### Post by osarusan on 2010-06-08
An update: This seems to be partially solved, but not completely.

It definitely works in the case of the Gnome Panel, and deciding which monitor windows open up on.

However, in the case of many games, for example Tremulus, Nexius, Neverputt, when I try to change the video resolution it only  gives me options fitting my 2nd monitor, not my primary monitor (my main monitor is 1600x1200 and my secondary is 1680x1050 widescreen). The games let me choose widescreen resolutions only.

Any ideas?

---

