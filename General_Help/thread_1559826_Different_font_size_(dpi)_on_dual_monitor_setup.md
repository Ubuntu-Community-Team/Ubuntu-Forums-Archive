---
title: "Different font size (dpi?) on dual monitor setup"
date: 2010-08-24
forum: General Help
---

### Post by Aybara on 2010-08-24
I'm on 10.04 with a dual monitor setup. 15" laptop @ 1080p, and 24" monitor @ 1080p. The laptop has an ATI Radeon Mobile HD 5000 graphics card.

When I set the font size nicely on the 15" it is to big for my taste on the 24". Is there something clever I can do to get different font sizes on the two displays?

I googled setting different dpi on the two monitors, but didn't find out anything. Could it be done by running different X-sessions on the monitors?

---

### Post by Aybara on 2010-09-22
I think my initial Q is hard to solve. Plan B is to run separate x-sessions on the two monitors, and set a different DPI on the two displays. I can live with not being able to drag windows between monitors.

Q: How do I configure dual monitor with separate X-sessions for ATI graphics?

---

### Post by Aybara on 2010-09-23
To continue my rambling:

I got seperate X-sessions by running:

aticonfig --initial=dual-head --screen-layout=left

Then I tried setting DPI in xorg.conf like this:

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "DPI" "120 x 120"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
        Option      "DPI" "96 x 96"
EndSection

It didn't work though. fglrx sets (96,96) on both screens.

---

