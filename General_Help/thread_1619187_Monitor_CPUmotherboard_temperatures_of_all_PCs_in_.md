---
title: "Monitor CPU/motherboard temperatures of all PCs in LAN?"
date: 2010-11-11
forum: General Help
---

### Post by maitchy on 2010-11-11
Is there software already that can be made to display the current temperature of each CPU (perhaps motherboard temperature and fans speeds too) of computers on the local area network, not just what lm-sensors will show for my own PC?  Otherwise, what do people think is the best way to implement such a thing myself (e.g. each PC has something like sensord periodically outputting information to syslog, which is set up to send those lines to a central logserver, and then make some application to present it nicely on the screen?

The main thing I want to do is to just see, from time to time, what the temperature is like on all the computers on hot days (they don't all have good ventilation) - maybe the next step would be to have something ring alarm bells if any of them are too hot, or are unusually hot for a long time... but to start with I'm happy just to see 'em all without having to go to where they are, plug in a screen, etc.... I don't even need a graph.

I'm talking about a mixture of Ubuntu and Fedora boxes, but it would be nice to monitor the Windows PCs too... they do have Cygwin installed, if that helps.

Thanks,
Mark

---

