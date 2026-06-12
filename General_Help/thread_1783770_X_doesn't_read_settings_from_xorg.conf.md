---
title: "X doesn't read settings from xorg.conf"
date: 2011-06-16
forum: General Help
---

### Post by scrooge on 2011-06-16
I'm running Kubuntu 11.04 on a laptop with dual monitor setup. I have Nvidia graphics card and I've successfully configured TwinView for the monitors. However, after saving the settings to xorg.conf (using the nvidia-settings application) X should use both monitors after boot, but only the main monitor is used. I first thought that X didn't read xorg.conf at all, but when I put some illegal statements into the file X wouldn't start and gave an error about the illegal statements. It is thus clear that X does read the file, but it just doesn't seem to use the settings in it. Does anybody have an idea why that might be?

Here is the contents of my xorg.conf file: [http://pastebin.com/spt1LDpz](http://pastebin.com/spt1LDpz)

---

### Post by scrooge on 2011-06-21
It turns out that the Screen section in my xorg.conf was overridden by another file in /usr/share/X11/xorg.conf.d/. when I removed that file TwinView starts on boot and works as intended.

---

