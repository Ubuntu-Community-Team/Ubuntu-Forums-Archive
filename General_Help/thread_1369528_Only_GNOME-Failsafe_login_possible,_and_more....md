---
title: "Only GNOME-Failsafe login possible, and more..."
date: 2010-01-01
forum: General Help
---

### Post by etienne@Rofti on 2010-01-01
Hi there!

After using my computer a few days ago, I tried to turn it on again yesterday, and I was unable to boot. After some Googling (on my mobile) and a few Grub bash commands, I was able to boot, but now I cannot log in. Neither normal Gnome nor XTerm work, and Failsafe is all that I can log into.

Above that, every time I log in, I get the following message:
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

More than that, I cannot run a command like:

```
sudo dpkg-reconfigure xserver-xorg
```

When I run the above command, I get the following answer:

> debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline


When attempting to boot up after the apparent crash, I did have to run **e2fsck** a few times.

I am using Ubuntu Karmic, without a regular connection to the internet. Any help would be much appreciated.

Thanks!

EDIT: I am also not able to apply any desktop effects. Is this because I am in failsafe mode?

---

### Post by etienne@Rofti on 2010-01-04
Bump?

Anyway, the result from the XKB commands given are as follows:

**xprop -root | grep XKB :**
> _XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "", ""


**gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd :**
>  layouts = [us]
 options = [Compose key	compose:rctrl]
 model = 


If these help anyone to help me solve any of my problems, I will give you a cookie!

Thanks in advance...

---

### Post by etienne@Rofti on 2010-01-19
Bump? The problem still persists...

---

### Post by candtalan on 2010-04-29
I am running  Ubuntu 9.10 on one of my machines, the graphics  did not work properly, th ecursor, for example had a blank square around it, but it was ok on failsafe gnome.

I discovered that visual effects were on, and when I turned them off, I could use normal gnome session. I had to use failsafe gnome initially to turn off the effcts though

System>Preferences>Appearance (visual efects, none)

hth

---

