---
title: "Save current xrandr configuration to xorg.conf?"
date: 2009-07-02
forum: General Help
---

### Post by Jeinhor on 2009-07-02
Hi,

I've had some problems getting the display on my TV working when in gnome. I "solved" it by booting up with my normal LCD monitor, and then plugged in the TV (using VGA port) and used the gnome-display-properties GUI to activate the TV and set correct resolution. I could then remove the LCD monitor (since this will be a HTPC).

But when I reboot, the settings are gone and I'm left with the same black screen.

Can I save the working settings from xrandr into xorg.conf somehow?

Thanks in advance!

---

### Post by Jeinhor on 2009-07-06
Well, I didn't find a way to save the configuration, but I found a way to run xrandr commands at startup. Just place the commands in /etc/gdm/Init/Default. That solved it for me.

---

### Post by caprilo on 2009-12-11
Great! It does work, at least in Debian testing. Thanks!

---

