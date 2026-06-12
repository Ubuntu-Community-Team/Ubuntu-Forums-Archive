---
title: "Display crashes, please help?"
date: 2010-04-04
forum: General Help
---

### Post by gypsyblue on 2010-04-04
Hi,

I'm having an odd problem. Every so often (every 45 minutes or so) while running Karmic Koala my display goes black, leaving only my cursor and an underscore in the top left corner visible. It's entirely unresponsive and requires a hard restart every time. This just started earlier today and I've had no problems until now.

I swapped to Ubuntu from Windows almost a year ago so I'm not a complete newbie, but I'm also not a programmer and definitely still learning my way around, so advice in simple language would really be appreciated. This problem is really frustrating.

Hardware specs: Lenovo Thinkpad T400 running Ubuntu 9.10 (dual-booting Vista Basic if it makes a difference), Intel Duo Core T9600 2.80 GHz, Intel Corp Mobile 4 Series Chipset Integrated Graphics (this is what it says when I look up the hardware info)

Any advice for how to deal with this problem? Any help would be REALLY appreciated. Please and thank you :)

---

### Post by gzarkadas on 2010-04-04
These stuff is usually hardware / drivers issues. Have you made any driver install before this behavior started to appear?

Open the log viewer (System|Administration| the icon with a magnifying glass in front of a printout), then select _syslog_ from the list to the left and scroll down the text trying to spot a section where such a hang occured (usually a little before a sequence of boot events). Then post it here, in order to pin down what's happening.

---

