---
title: "Radeon HD 2400 XT problems"
date: 2011-03-03
forum: General Help
---

### Post by whalogreg on 2011-03-03
I am running Ubuntu 10.10 on my desktop with a Radeon HD 2400 XT video card. The card has a DMS-59 output (for use with a split VGA or DVI cable) which I am connecting to my 1080p LCD television, via a VGA cable. There are no HDMI or other outputs on the card.

My problem is, some of the output resolutions that Ubuntu detects do not seem to apply properly. When I select 1366x768 (the highest 16:9 resolution available), 1360x768 etc, the display resolution is actually lower than the selected resolutions (two black bars of unused pixels, aprox 50px wide on each side of my screen). 

The odd thing is, my television says it's resolution is 1280x720 when my system is set to 1366x768. When I select a lower 16:9 resolution (1280x720) my display fits the screen perfectly, but my television says it is receiving a 1360x768 resolution.

This happens with the "out of the box" driver and with fglrx (and when applied via Ubuntu's monitor settings, and the ATI Catalyst Control Center).

This problem does not exist with my laptop connecting to my television via HDMI. The settings are consistent with actual output (1366x768).

Might this be a problem with the drivers, or with my television's VGA input/compatibility? Any ideas how I might be able to work around this? Or should I just be satisfied that my television is telling me that it's receiving a 1360x768 input and seems to look ok?

---

### Post by whalogreg on 2011-03-05
::bump::

---

### Post by whalogreg on 2011-03-08
Also, I've found that after I get my screen resolution working, after I reboot the resolution is STILL 1280x720, but my television displays "Invalid Format". Then I must switch to an actual monitor, change the resolution to one my television will recognize, unplug the vga cable and plug it back into my television, and click "detect monitors" and then re-set the resolution back to 1280x720 for it to display properly. This happens consistently.

---

### Post by whalogreg on 2011-03-09
anyone?

---

