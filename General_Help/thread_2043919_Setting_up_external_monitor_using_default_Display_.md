---
title: "Setting up external monitor using default Display program (not Nvidia)"
date: 2012-08-17
forum: General Help
---

### Post by Linuxpal on 2012-08-17
Hello! Trying to mirror my laptop 13,3'' with my external benq 24'' monitor. Clicking the Display program detects my 24'' monitor, so 2 screens show up, but when trying to mirroring them, or using 24'' only, I just get a black screen. I've connected the power cable to the 24'' and HDMI-HDMI between my computer and the 24'', so everything should be set up. Why am I not seeing anything on my 24''? Any clue? Also, sometimes the 24'' says "cable not connected" (which I doubt, cause everything is set up correctly).

---

### Post by kemtnbkr on 2012-08-17
> **Linuxpal said:**
> Hello! Trying to mirror my laptop 13,3'' with my external benq 24'' monitor. Clicking the Display program detects my 24'' monitor, so 2 screens show up, but when trying to mirroring them, or using 24'' only, I just get a black screen. I've connected the power cable to the 24'' and HDMI-HDMI between my computer and the 24'', so everything should be set up. Why am I not seeing anything on my 24''? Any clue? Also, sometimes the 24'' says "cable not connected" (which I doubt, cause everything is set up correctly).

What desktop environment are you running?  I run lubuntu (LXDE on Openbox) so I don't remember exactly what vanilla Ubuntu has for monitor settings.

However, a very useful command for configuring multiple monitors is xrandr.

It can be a bit tricky to remember the syntax; myself, I just made a script for my laptop with HDMI-out so that when I connect my TV I can just run the script and everything gets set up properly.

Use the manpages or a google search to figure out how to use xrandr.

---

### Post by Linuxpal on 2012-08-18
> **kemtnbkr said:**
> What desktop environment are you running?  I run lubuntu (LXDE on Openbox) so I don't remember exactly what vanilla Ubuntu has for monitor settings.

However, a very useful command for configuring multiple monitors is xrandr.

It can be a bit tricky to remember the syntax; myself, I just made a script for my laptop with HDMI-out so that when I connect my TV I can just run the script and everything gets set up properly.

Use the manpages or a google search to figure out how to use xrandr.
I'm running Ubuntu, Gnome Shell or Unity (both installed). Never tried xrandr, would you be so kind and give me some links, what commands I need etc. I don't understand how Ubuntu can detect my screen but still not display anything on it!? Also that Disper program have a hdmi-hdmi setting, but that program is useless in my case. Sorry to ask, but what makes xrandr stand out from these other program? I'm using the monitor now on my windows computer and it worked like a charm... didn't have to do anything (maybe because i got nvidia installed on my windows pc?).

---

