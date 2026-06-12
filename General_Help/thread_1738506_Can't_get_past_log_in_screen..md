---
title: "Can't get past log in screen."
date: 2011-04-24
forum: General Help
---

### Post by Fabled One on 2011-04-24
I had uninstalled pulseaudio and it's related libraries, then I rebooted, and now I can't log in.

Also, the log in screen looks different. Where it used to have the ubuntu logo, it now has a computer monitor icon.

Logging in from the command line works.

I tried reinstalling pulseaudio with ```
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter
```

but it did not help.

What happened?!

---

### Post by Krytarik on 2011-04-25
Check what has been removed along with them:
```
cat /var/log/apt/history.log
```
Maybe just reinstall "ubuntu-desktop" for a start:
```
sudo apt-get install ubuntu-desktop
```
Greetings.

---

### Post by Fabled One on 2011-04-26
Now I'm more screwed. The logs only showed removing some pulse audio stuff, installing java, and what I had been doing with video drivers.

I tried resetting the video drivers(with the same script that was working all week) and now I can't even see the log in screen at all.

I get no signal on my lcd, then black screen.

This is ridiculous, why does pulse audio affect this?

---

### Post by Krytarik on 2011-04-26
First, don't blame Pulseaudio for screwing yourself by fiddling with a video driver, also when you removed Pulseaudio related packages, there was definitely a warning about what else needs to be removed as a matter of dependency.

So, can you boot into "recovery mode"?

Also, what video driver did you try to reinstall?
Let me guess, a proprietary Nvidia/AMD driver, downloaded from either website, meant for a manual install (oh, I love these)?
What video card/chip do you have?

---

