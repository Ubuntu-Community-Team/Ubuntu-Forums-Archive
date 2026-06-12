---
title: "Very Bad Compiz Performance with ATI 5870"
date: 2011-07-03
forum: General Help
---

### Post by Jforsyth on 2011-07-03
Hey guys,

I've recently installed Ubuntu (11.04) on my desktop computer. It has a Sapphire HD 5870 and an i7 920 processor. I am using the FGLRX drivers. 

General performance under Compiz is very bad. The computer is usable, but the interface is sluggish and unattractive. For example, if I move my cursor quickly down a drop-down menu, the system can't respond quickly enough to highlight each selection button smoothly. Wobbly windows looks downright terrible, with what appears to be a low frame-rate, tearing, and ghosting. 

Now, I get fantastic performance on my laptop, which has only a Core 2 Duo T6570 and Intel G45 Chipset graphics. I thought the problem may lie with my desktop's monitor, but when I connected my laptop to it the interface was just as smooth and responsive as it is on its own monitor. 

Does anyone know what could be the problem?

---

### Post by Jforsyth on 2011-07-03
So the problem was with the FGLRX drivers, apparently. The system appears to be fine if they are disabled.

---

### Post by lakerssuperman on 2011-07-10
If you are running the FGLRX drivers make sure you install the Compiz Settings Manager and disable the Compiz Vsync.  It does not play well with the FGLRX drivers.  Just turn on "Tear Free Deskop" in the FGLRX control panel and you will get a tear free vsynced desktop.

I will say that the there are some instances where there is still some lag, such as the last instant before a minimized window resumes it's position on the desktop, but for the most part it's a night and day difference.

Sadly, the VAAPI acceleration is still broken for Radeon owners no matter what settings are tweaked.

---

