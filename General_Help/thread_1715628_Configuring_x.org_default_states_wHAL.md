---
title: "Configuring x.org default states w/HAL"
date: 2011-03-27
forum: General Help
---

### Post by hgernhardt on 2011-03-27
Folks—

This question may very well have been answered elsewhere, but my Google-fu seems to have failed me yet again.  Here's the situation:

My primary work machine is a laptop.  When I am at work, I'm usually plugged into a portrait-oriented 4x3 monitor and use the following xrandr line (atoffice):
```
xrandr --output VGA-0 --auto --rotate left --pos 1280x0 --output LVDS --auto --pos 0x290
```If I'm not at the office, obviously I won't have the second monitor (onroad):
```
xrandr --output VGA-0 --off --output LVDS --auto --pos 0x0
```Every so often I may need to plug into a projector, but I'm not as concerned about that as I can start at the onroad setting and either use GUI tools or the xrandr command line (which I prefer) to handle setting up the projector.  Where I need help, though, is with the initial detection and configuration of X by way of HAL:

[LIST]
[*]Is there a way that I gan get a UUID (or something similar) from the monitor plugged into the VGA or HDMI port?
[*]If so, can I provide configuration hints to X, or to HAL, such that it will utilize preferred graphics modes based upon what is plugged in at any given time?
[*]If not, what is the minimum x.org configuration I would need to specify that **only** the LCD be utilized at X start, and that xrandr be enabled (I'm using the open-source ATI drivers)?
[/LIST]
Obviously, my preference is the second line item if at all possible.

Thanks,

Henry

---

