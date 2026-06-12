---
title: "Running any program in full screen"
date: 2010-05-11
forum: General Help
---

### Post by and_moe on 2010-05-11
Hi

I'm trying to run a program in full screen without any window chrome at all on Ubuntu 10.04. Is that possible?

Specifically, I'm trying to run the light control program Chamsys MagicQ (freely available at [http://download.magicq.co.uk](http://download.magicq.co.uk)). It runs just fine, but it is hardcoded to a size of 1024x768 inside the window chrome. This means that on my 1024x768 screen I loose maybe 50 pixels from the bottom of the program (see attached screenshot). This is bad, as the bottom contains some quite vital buttons.

However, if I could run it without any window chrome on top of the taskbars (perhaps on a separate desktop?), it would fit my screen perfectly. Any suggestions?

Thanks in advance,
Andreas Møgelmose

---

### Post by dcstar on 2010-05-11
> **and_moe said:**
> Hi

I'm trying to run a program in full screen without any window chrome at all on Ubuntu 10.04. Is that possible?

Specifically, I'm trying to run the light control program Chamsys MagicQ (freely available at [http://download.magicq.co.uk](http://download.magicq.co.uk)). It runs just fine, but it is hardcoded to a size of 1024x768 inside the window chrome. This means that on my 1024x768 screen I loose maybe 50 pixels from the bottom of the program (see attached screenshot). This is bad, as the bottom contains some quite vital buttons.

However, if I could run it without any window chrome on top of the taskbars (perhaps on a separate desktop?), it would fit my screen perfectly. Any suggestions?

Thanks in advance,
Andreas Møgelmose

You may want to investigate alternative window managers instead of the default:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
or
[http://ubuntuforums.org/showthread.php?t=934166](http://ubuntuforums.org/showthread.php?t=934166)
or
[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

---

### Post by Orange Kingdom on 2010-05-11
With CompizConfig manager (Window Rules)  you can run any window  in fullscreen.

---

### Post by and_moe on 2010-05-12
I've looked into the Compiz window rules, but unfortunately the neither the Fullscreen nor the Maximize attribute has any effect. It does catch the window, though, as for example Above works just fine.

I don't think I want to venture into other window manager if it can be avoided at all, since I also use the computer for other stuff and Gnome fits me just fine. But I suppose if all else fails, I could install something else and run the relevant sessions with that.

- Andreas

---

### Post by and_moe on 2010-05-12
Okay, just a short update: I've managed to remove the window border by setting the Decoration windows-field in Window Decorations in ccsm to ```
(any) & !(title=Microwindows)
```
Microwindows is the name of the windows I want to affect.

Now, I can make it be on top of the taskbars by setting name=gnome-panel to below in Window rules, but that affects all programs, so that is not optimal (yet still pretty good). So close now :-)

- Andresa

---

### Post by soundpartner on 2010-08-25
this have been solved with the new magicq. now it can run any resolutions and resizes to the windowsize

---

