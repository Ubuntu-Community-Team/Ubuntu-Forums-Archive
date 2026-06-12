---
title: "ATI Radeon Screen Geometry Problem"
date: 2009-09-24
forum: General Help
---

### Post by Mike Eckman on 2009-09-24
I have a very perplexing problem that I have been battling for a week now and I am about ready to give up.

My problem is that in only 1280x720 mode, I get a 2" black bar along the left side of the screen going frop top to bottom.  The entire picture is shifted to the right off the right edge of the screen.  No amount of tweaking in the Settings menu of the TV can get the picture re-centered.

I am running an XBMC media center on Ubuntu 9.04 with an ATI Radeon 3450 Video card.  I am using the latest Catalyst 9.8 drivers.  My TV is a Sony 720p flat panel that supports 1280x720.  I can connect my laptop (Dell Studio 15") to my TV and put it in 1280x720 mode and this does not happen, nor does it happen in ANY other screen resolution.  I have tried 1280x768 and 1164x648 (or whatever the next down is).  The desktop is shifted to the right ONLY in 1280x720 mode.  It doesnt matter whether Im at the desktop or in XBMC, its the same.  None of the options in the Catalyst software can correct this.

This is extremely frustrating because I want to run my TV at its native resolution for optimal picture quality.  Instead I am forced to run at a scaled resolution, which techincally looks fine, but it still bothers me that I am not in the "best" resolution.

Not sure what you need from me to help you help me, but let me know if anyone has any ideas.

---

### Post by Mike Eckman on 2009-09-26
Still haven't solved my problem, but I have narrowed my problem down to the Catalyst drivers.  If I reload Ubuntu and do not load the Catalyst drivers, but instead stick with the proprietary third party ATI drivers, I can run 1280x720 without the screen geometry problem.

I am considering sticking with these drivers, but the problem now is that I do not have control over things like gamma and screen scaling which is nice for watching movies.  Ive found that when I watch movies using the default drivers, things are either too bright or too dark.  I can compensate with my TV's brightness and contrast settings, but then it screws up every other input I have, which is annoying.

In either case, my issue might just be something with my hardware combined with the ATI drivers...still, if someone has some suggestions, I'd be happy! :)

---

