---
title: "Totem Causes X Server Error"
date: 2010-10-28
forum: General Help
---

### Post by cfree220 on 2010-10-28
Hi guys,

I'm having a problem with X.

I have a dual monitor configuration. Monitor one is the embedded Seiko panel on my laptop (resolution = 1920X1200). Monitor two is an emachines something-or-other (resolution = 1440X900).

I am running 64-bit Ubuntu 10.10 on a Dell XPS M1530.
Graphics card is an NVidia 8600M GT.

When I log in to my account, the first thing that I do is activate the external monitor.

If I try to launch Totem (Movie Player) from the dock, I encounter an X screen error where the output on my laptop's screen reflects that of the external monitor, resolution and all. Because the external monitor is at a lower resolution, this takes up only a portion of the embedded screen; the rest of the space looks like the output has been tiled.

Here is a screenshot:[ATTACH]173792[/ATTACH]

If I close Totem and reconfigure my monitors (I usually just change the resolution on the embedded screen from Auto to 1920x1200), then I'm back to the proper output.

If I try to launch Totem after I have reconfigured my monitors, I do not encounter the same problem. If I log out and log back in, the problem can be reproduced.

---

### Post by cfree220 on 2010-10-28
Update: When I changed the default config to use both monitors (ie I don't have to do it manually every time I start the computer), the problem went away.

It's still a bug, and I'd still like to fix it.

Also, when I log in I now get a libnotify bubble telling me that not all of the parameters of the x configuration could be loaded for reasons of resolution. Everything looks fine to me. Any ideas?

---

