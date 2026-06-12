---
title: "Problem with Monitor Resolution at Login (Solved?)"
date: 2012-05-06
forum: General Help
---

### Post by Dulleo on 2012-05-06
So I just had a problem, but ended up solving it.  I'm wondering if my method is correct, and if so, if it can help others with similar problems.

My computer is a Sony Vaio C140G with on-board intel graphics.  Upon upgrading to one of the earlier versions of ubuntu that included the new splash screen, my monitor resolution would not apply correctly if I left the splash screen on.  The screen would actually start with a black screen and then white would bleed in from the edges in a very ugly manner, until the screen was completely white.  After being white it would come up in 1024x768 rather than my true resolution of 1280x800.

Rather than trying to figure out what was going on, I just removed splash from the grub config, and that seemed to work until we got to the last update of 12.04.  Now, even with splash disabled, my screen would not apply the default 1280x800 resolution, but would boot into a 1024 by 768, leaving two big black bars on the on the sides of my screen.  I was unable to get the machine to boot into 1280x800 with my old trick, so I had to find something new. 

I looked at the log file that was generated at boot and noticed that it said "[    88.441] (II) intel(0): Output LVDS1 has no monitor section", then it went through a series of attempts to find the best resolution - but never happened upon 1280 x 800.  

When I went to look for the xorg.conf file, that I had edited on occasion on older computers, I saw that it didn't exist anymore, there was only a fallback/failsafe file there.  Google told me that ubuntu now uses monitors.xml to set the resolution and then automatically configures the rest.  So on to the monitors.xml file I went.  In there I found that in the first configuration my desktop monitor (which I haven't been using lately) and "LVDS1" were shown. LVDS1 was the default, so I assumed this must be the screen built into my laptop.  Under LVDS1 there was no width or height configured, but this was configured for my other monitor.  The vendor, product, and serial were there but all blank or zero.  I had a second configuration in this file that did have my correct "LVDS1" screen width and all of the other business about rotation and shifting, etc.  So I just took the stuff from configuration 2 and pasted it into configuration 1. 

```
<width>1280</width><height>800</height><rate>60</rate><x>0</x><y>0</y><rotation>normal</rotation><reflect_x>no</reflect_x><reflect_y>no</reflect_y><primary>yes</primary>
```Then I rebooted, and surprise, surprise, it worked!  Was there a better way to achieve this result? And will this continue to work?

---

