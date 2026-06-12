---
title: "Cairo Dock in a Strange Location"
date: 2010-10-03
forum: General Help
---

### Post by renno on 2010-10-03
Hi all,

Our baby loves the laptop and goes on pressing all buttons with all hands. We previously had cairo-dock configured nicely on the bottom of the screen with auto-hide option.

After she pressed buttons which we cannot figure out, the "bottom" location is now to the right side of the screen, and half the cannot be seen. So it is as if the whole dock was moved to the right (so that half of it is only showing) and then moved up to the middle of the screen.

I tried completely removing cairo-dock and then installing again, but that did not work. I am out of ideas, and am not expert in ubuntu.

Any help is appreciated,

Cheers,

---

### Post by sikander3786 on 2010-10-03
Right Click on the Dock, go to Cairo Dock > Configure. Hit Advanced at the bottom, now click Position and move the slider to '0' under Screen Offset (I don't remember the exact term). Click Apply and you'r done.

---

### Post by renno on 2010-10-03
Hi sikander3786,

Thank you very much for the prompt response. That solved the problem. It was really frustrating having the dock in that weird location.

Cheers,

---

### Post by sikander3786 on 2010-10-04
Nice.

Just a note, your Baby is going to become an Ubuntu Geek soon :-)

Another thing, whenever you want to remove a software alongwith all its configuration files, either mark the package for complete removal in Synaptic or put the --purge switch e.g,

```
sudo apt-get remove --purge cairo-dock
```

If you had done that and reinstalled, cairo-dock would have started in its default position after reinstall i.e, centered in the bottom. That would have removed all your icons/effects also.

Regards.

---

### Post by fabounet on 2010-10-05
no need to reinstall, just move the config files:
```
mv ~/.config/cairo-dock/current_theme ~/.config/cairo-dock/current_theme.bak
``` ;-)

---

### Post by sikander3786 on 2010-10-05
> **fabounet said:**
> no need to reinstall, just move the config files:
```
mv ~/.config/cairo-dock/current_theme ~/.config/cairo-dock/current_theme.bak
``` ;-)
I agree. But what about other software that you want to remove alongwith config files, e.g, samba or vlc or banshee? Instead of searching for the config files, just place the --purge and reinstall. Thats my point. :-)

---

