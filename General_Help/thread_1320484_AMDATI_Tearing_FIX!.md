---
title: "AMD/ATI Tearing FIX!"
date: 2009-11-09
forum: General Help
---

### Post by vhozard on 2009-11-09
I have found it impossible to watch videos without noticeable tearing, with my ATI videocard.

The solution is a (new) different window manager: **[COLOR="DarkRed"][SIZE="3"]MUTTER[/SIZE][/COLOR]**

Just install it via Synaptic or execute:
> sudo apt-get install mutter

You will also need to enable V-Sync in the Catalyst Control Center:
> amdcccle
Go to _3D_ --> _More Setting_ --> _Wait for vertical refresh_ --> Every setting is good, [COLOR="Red"]except[/COLOR] "Always off"

To replace it with your current window manager:
> mutter --replace

(I hope this is the right category, please tell me if it isn't)

---

### Post by iameffendi on 2009-11-09
Thank you. This is a simple fix to a very annoying problem. I didn't realize the window manager would make such a significant impact.

---

### Post by kreggz on 2009-11-17
How did you work this out? If this works it means I can finally use HDMI :D

---

### Post by vhozard on 2009-12-14
Fix this out?
Just follow the exact same steps as I described at the top.

---

### Post by ChrisNiemy on 2010-11-29
This is so great! I'm using ubuntu for quite 5 years. And the last thing, my last BIG problem was vsync. It never really worked.

With compiz flash was ok, but fullscreen flickering. Games were slow and flickering. Without compiz flash was flickering, fullscreen flash ok. Videos ok. Some games ok. But WorldofGoo flickering. And so on...

Especially with compiz Firefox 4 with little hardware acceleration seems extremely sluggish. Without compiz, the whole UI (Gnome, nautilus etc.) seems sluggish. Moving windows, always flickering (tearing).

With mutter/gnome-shell, I have NOT ANY Problems! :) :) Since 5 years - for the first time! Welcome to 2010.

Btw, I'm using Nvidia propietary drivers for my nvidia card. No messing around with xorg.conf or nvidia-settings. I just set "mutter --replace" in the startup application dialog. Perfect. Flawlessly. I just made sure nvidia-settings is loading before mutter, so my entry in the gnome-session-properties is:
sh -c '/usr/bin/nvidia-settings --load-config-only && mutter --replace &'


I'm wondering how this works. The compiz guys often wrote, that Vsync with composite is not possible because of the drivers and old X11. But it seems to be.

With mutter, all videos, all flash (windowed or fullscreen), all GL games, and scrolling in firefox etc., moving windows: without flickering. without tearing. And blazingly fast, no slowdown through compositing.

Cons: Effects are yet not configurable and very little (but nice). Switching between viewports is very little more sluggish than usual.

I'm really happy. Too bad they are moving to compiz for unity. But as long as mutter stays in the repositories I'm fine. I like unity very much, but I don't need it. I was always looking for proper vsync.

So this works for ATI and Nvidia. Spread the word! :)

I'm wondering how the mutter devs did this. Maybe this can be implemented in compiz?

---

