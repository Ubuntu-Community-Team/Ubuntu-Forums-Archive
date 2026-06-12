---
title: "Ubuntu 10.10 random complete hang"
date: 2010-12-03
forum: General Help
---

### Post by TheRussMan on 2010-12-03
I'm using Ubuntu 10.10 with the 2.6.35-23-generic kernel and GNOME 2.32.0 and I keep getting random hangs.  I've disabled the screensaver and monitor going off so that I can see the time it hangs and checked through the main logs.  I can't see anything during the time of hangs, and when it's in a hung state i can do nothing and can't ping the IP from another machine on the network, therefore a hard reboot is required.

Any suggestions?  I can't believe that it can be a hardware problem because I previously (and actually still do have as a dual boot) had the x64 version of 10.10 installed and this was fine.  On the x86 version everything was fine for a period of a few weeks before these crashes started.  Since then I've installed the latest kernel which hasn't made a difference.

Does anyone have any suggestions before the missuses makes me put Windows back on :'(

---

### Post by TheRussMan on 2010-12-06
Sorry to bump this but I'm really struggling.  

I just left it running with GNOME System Monitor in the forground and when it had crashed there was nothing showing any process usage (apart from a couple for the sys mon), just a few processes like XORG polling with zero usage.

---

### Post by nickbrett on 2010-12-13
I might be suffering from the same issue. My laptop simply stops responding to input now and then. The only solution seams to be a hard reboot.

---

### Post by TheRussMan on 2010-12-13
I think I've worked out the problem I'm having.  It's caused by Ndiswrapper.  I've now uninstalled it and compiled my own wireless drivers and the computer hasn't crashed since.

Hope this helps.

---

### Post by jimfixx on 2011-05-14
Has anyone solved this issue?

I appear to be having the exact same problem on my machine, and I don't have Ndiswrapper installed..

---

### Post by syedwasi on 2011-09-30
hello,

Even myself having same problem without any solution inspite hard reseting system.
can any one got problem solve...

regds
wasi

---

