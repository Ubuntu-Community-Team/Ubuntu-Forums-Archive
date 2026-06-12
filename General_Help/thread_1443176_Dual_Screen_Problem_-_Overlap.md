---
title: "Dual Screen Problem - Overlap"
date: 2010-03-30
forum: General Help
---

### Post by BraydenW on 2010-03-30
I'm using Ubuntu 10.04 (same problem occurs in 9.10).  What happens is when I extend the display with another monitor I get about 10 pixels of overlap.  The main screen looks fine, but on the left side of the screen to the right of my main display there is about 10 pixels of content being displayed from the main screen.  I'm having trouble turning the problem int words, so I took a screen shot here [http://www.flickr.com/photos/braydenw/4477043169/sizes/o/](http://www.flickr.com/photos/braydenw/4477043169/sizes/o/) .  Does anyone know how to fix this?  The screens are 2 different resolution and I'm using a Radeon Mobility 4550M graphics processor.

---

### Post by garolou on 2010-03-30
Ok, from the picture I get the impression that a window is overlapping a little.
Maximize that window and see what happens, sometimes we can be fooled in thinking a window is maximized when its not, and its dimensions are actually larger than the screen.

---

### Post by BraydenW on 2010-03-31
Yes, the windows is actually maximized.  And you can can see the problem a little bit even when a window isn't maximized.  You can see that the background image tiles a bit on the left hand side of the screen.

---

### Post by garolou on 2010-03-31
When I set up my dual set-up, compiz gave me some trouble cause I didn't have enough video memory to use the higher resolutions my monitor was capable of. Turn it off if not done already. Then using 'Display preferences', Detect monitors again and try different resolutions.
Have you modified the video configuration files (/etc/X11/xorg.conf)? If so, maybe reverting to defaults... run  'sudo dpkg-reconfigure xserver-xorg' in the console.

---

### Post by martingugino on 2010-04-22
Braden, I dont understand the screen shot that you posted.

---

### Post by scouser73 on 2010-04-22
> **martingugino said:**
> Braden, I dont understand the screen shot that you posted.

Brayden has two monitors, when he's using an application it's overlapping slightly onto the second monitor.

Brayden, I've been having this same problem when I'm using VLC and I've not seen a workaround as yet.

---

