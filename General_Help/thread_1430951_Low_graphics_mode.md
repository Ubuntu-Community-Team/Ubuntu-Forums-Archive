---
title: "Low graphics mode"
date: 2010-03-16
forum: General Help
---

### Post by WeaponsTheyFear on 2010-03-16
Hey guys,
I recently rebooted and now with every startup I've run into the low graphics mode issues.

To get this out of the way, I have an ATI Radeon HD4350 card.  I have my monitor setup via VGA, and I had a 50" setup via HDMI.

This all started I believe from extending desktops.  I used an app to send the TV to the bottom desktop and my monitor up top.

When I restarted, my monitor went black saying it couldnt support the video resolution and I couldnt see anything.

However, if I unplug the HDMI from the video card it would boot, but in low graphics mode.

I have tried dpkg-reconfigure xserver-xorg and even restored my old xorg.conf file from before i edited anything, but still not getting a decent looking display.

---

### Post by soltanis on 2010-03-16
That's really odd. Can you confirm that your video driver is still the one being loaded? Do you use proprietary drivers?

---

### Post by oldefoxx on 2010-03-16
I had one install of 9.10 that would drop to low resolution and be troublesome in other ways.  My final solution was just to go back to 9.04, and it holds up better. May have nothing to do with your problem, but who can say at this point.

---

