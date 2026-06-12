---
title: "Won't recognize resolution"
date: 2012-02-26
forum: General Help
---

### Post by Wildfire1 on 2012-02-26
I have Ubuntu 11.10, on a new-ish dell, alongside win 7. Monitor is a 42" Panasonic plasma telly, connected via hdmi cable.

Ubuntu installs fine every time, except that the resolution is always off, off to the point where my menu on the left is mostly cut off (I can barely see the edge of the icons), and the top menu isn't visible at all. On going to systems>display, it says my telly is 32" instead of 42", and only gives me 2 resolution options, the first is as above, the other is much more zoomed in (I forget the numbers, sorry, on windows while I type this or I'd check).

I assume the problem is that Ubuntu won't recognize the last 10" of my screen, but I'm fairly new to linux in general, so who knows? I hope someone can help.

---

### Post by papibe on 2012-02-26
It looks like an [overscan]("http://en.wikipedia.org/wiki/Overscan") problem. The simplest way to solve it would be to look for other scanning options on your TV. Use your remote and play with the settings.

A couple examples: 
[LIST]
[*]In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area.
[*]In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).
[/LIST]
If that don't work, you would have another solution if you have an Nvidia card and the proprietary drivers installed (read [here]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/")).

Hope it helps, and tell us how it goes.
Regards.

---

### Post by Wildfire1 on 2012-02-26
Thanks for responding!

Okay, update: I pressed every button on the remote and telly itself and gone through every menu I can find, even the ones that seemed unlikely (just in case), and found nothing that fixes the problem. There are formats available through the menu option, but none solve it (a few make it worse!).

Thinking more about it, I have more info that hopefully will help. Sorry for writing in haste before, this is truly frustrating me.

Telly is a month old, and screen resolution is just fine when I log into windows.

Resolution options in ubuntu are: 1920 by 1280, or_ 1280 by 720_, only.

Tried arandr and "monitor resolution" programs, and none help. Arandr won't even open.

video card is an AMD Radeon HD 6450 (shoulda said that before)

I dug out my user's guide and read that front to back, no help at all.

Thanks again for helping.

> **papibe said:**
> It looks like an [overscan]("http://en.wikipedia.org/wiki/Overscan") problem. The simplest way to solve it would be to look for other scanning options on your TV. Use your remote and play with the settings.

A couple examples: 
[LIST]
[*]In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area.
[*]In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).
[/LIST]
If that don't work, you would have another solution if you have an Nvidia card and the proprietary drivers installed (read [here]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/")).

Hope it helps, and tell us how it goes.
Regards.

---

### Post by papibe on 2012-02-26
Unfortunately I don't have much experience with AMD cards. Hopefully someone else will pitch in.

Anyway, are you using the AMD/ATI proprietary driver? Maybe there are some tools there to fix the problem on the computer side.

I know people can solve those kind of problems using the command xrandr, for instance (from [here]("https://wiki.archlinux.org/index.php/ATI")):
```
xrandr --output HDMI-0 --set underscan off
```
(replace HDMI-0 with the actual name of your connection).

Just some ideas.
Regards.

---

