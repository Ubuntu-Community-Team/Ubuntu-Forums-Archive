---
title: "Intel i915 graphics issues - Mouse pointer disappears"
date: 2010-09-03
forum: General Help
---

### Post by psadza on 2010-09-03
I have had continued issues with my graphics: [http://ubuntuforums.org/showthread.php?p=9797795#post9797795](http://ubuntuforums.org/showthread.php?p=9797795#post9797795)

Now, after an update manager update, I have a new issue. My mouse cursor disappears when I use my external monitor beyond a given resolution. Also, my settings for the laptop monitor are incorrect (will not let me select the true laptop native resolution). I even had an instance when I had mirrored images, but saw the mouse pointer only on the laptop screen, but not on the external monitor.

I also recently did the suggestion to ```
gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"

```
Which had caused issues when I was previously running Ubuntu in dual boot with WIN XP. I am now on standalone Ubuntu 10.04. I reversed the grub edit, but the problem persists.

Currently, I have to keep my external monitor at a much lower resolution for mouse pointer to show up, or use the CTRL key to show mouse pointer location feature in higher resolutions. All other aspects of the higher resolution for the external monitor work well...just that my mouse cursor does not show up.

---

### Post by psadza on 2010-09-03
Seem to have a fix.

Detach external monitor cable.

Reset native resolution on laptop.

Attach external monitor cable.

Select new external monitor resolution and turn off laptop monitor.

Several error messages about virtual display, x server not supporting resolution, select small res, repeat...

Finally get good display for external monitor high res, but no mouse.

Hit APPLY on display setting again without making any changes. Mouse cursor reappears.

Is my issue a 1920 x 1200 external monitor, or the old laptop intel graphics chipset i915?

---

