---
title: "Multiple-monitors in 11.10"
date: 2011-12-19
forum: General Help
---

### Post by nikRbokR on 2011-12-19
I have a 23" Dell monitor that I just purchased. I've hooked it up to my laptop (with a 16" screen, I believe), but I'm only able to mirror the screens in Ubuntu. The resolution stays at 1366x768 for both screens.

Unchecking the "mirror" option and setting the resolution of the additional monitor to 1920x1080 results in both screens having the 1920x1080 resolution (with the smaller screen containing only a portion of the screen) and a continuation of the "mirror" mode.

Any ideas on how to fix this? It's really too bad it doesn't just work right out of the box...

---

### Post by thaelim on 2011-12-19
Can you post a screenshot of what the Display Settings dialog looks like when you have disabled Mirror mode?

---

### Post by nikRbokR on 2011-12-19
> **thaelim said:**
> Can you post a screenshot of what the Display Settings dialog looks like when you have disabled Mirror mode?

This is what it looks like:

[IMG]http://i1085.photobucket.com/albums/j421/nikRbokR/display_settings.png[/IMG]

Prior to this, I was getting an error when I unchecked the "Mirror" option. Something about how the resolutions wouldn't match. In the command window, I ran: ```
sudo amdcccle
``` and went into the Display Settings. I made it so that the two screens were extensions of each other. It asked to restart, and I did that. It didn't fix the problem, but I no longer get an error when I uncheck the mirror option.

---

### Post by nikRbokR on 2011-12-19
Well, it seems to have magically fixed itself. I was suddenly logged out of my session, and upon logging in again the desktops seem to be working. There is, however, no way of choosing which screen I want to be set as my "main" monitor.

---

### Post by CaptinGoogle on 2011-12-19
<duplicate removed>

---

### Post by CaptinGoogle on 2011-12-19
> **nikRbokR said:**
> Well, it seems to have magically fixed itself. I was suddenly logged out of my session, and upon logging in again the desktops seem to be working. There is, however, no way of choosing which screen I want to be set as my "main" monitor.
Do you have any proprietary drivers installed for your graphics card? If you do then there should be something like nVidia X Server Settings, say if you have an nVidia, then you should be able to have more control over monitor settings.

---

### Post by pwnage101 on 2011-12-19
For those of you who have this same problem, and it ***did not*** fix itself, I was able to fix it by executing xrandr during startup. Just learn how to use xrandr and figure out the correct command args to fix your specific problem.

In my case, this did the trick:
```
xrandr --output VGA-0 --pos 1600x0
```

I too was using an ATI card. (radeon open source drivers)

---

### Post by nikRbokR on 2011-12-21
> **CaptinGoogle said:**
> Do you have any proprietary drivers installed for your graphics card? If you do then there should be something like nVidia X Server Settings, say if you have an nVidia, then you should be able to have more control over monitor settings.

Yes, I have proprietary drivers for my ATI card.

I actually did change the settings in the Catalyst menu. It didn't seem to have any effect (until that random logging-out).

---

