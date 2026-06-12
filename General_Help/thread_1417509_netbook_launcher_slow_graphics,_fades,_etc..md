---
title: "netbook launcher slow graphics, fades, etc."
date: 2010-02-27
forum: General Help
---

### Post by langelgjm on 2010-02-27
Hi,

I just bought a used Acer Aspire One netbook and put UNR 9.04 on it. It works very well so far.

The "launcher" is very responsive when I use it on the netbook screen. However, if I attach an external monitor and use a dual-display setup (netbook at 1024x600, LCD at 1280x1024), the launcher becomes very sluggish. Fading effects take many seconds, icons no longer grow and shrink during mouseovers, clicking different categories takes about 10 seconds for the icons to change, etc.

Once I launch an application (e.g. Firefox or Terminal, etc.), the sluggishness goes away, the application is fast and runs fine. If I click back to the launcher, sluggishness returns.

I am guessing this is a graphics performance issue, but it's not obvious to me how to fix it. I have "no effects" selected in my Appearance/Effects tab. Is there anything else I can do to improve graphics performance of the launcher? Like disabling fade-in/out, etc.? Has anyone else had this issue?

The graphics card is a run-of-the-mill Intel 945 GME using shared system memory.

Thanks!

---

### Post by langelgjm on 2010-02-27
Solved!

Gave it another shot and figured out what was wrong.

According to [here]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"),

> Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled. This may matter if you like games and compiz desktop effects, or if you want Google Earth to display in better than geological time. Obviously the larger the virtual desktop, the more graphics memory is used. So for good performance with a shared graphics system such as Intel the Virtual should be no larger than necessary.

Sure enough, my xorg.conf Screen section has a Virtual line that was 2048 by 2136. I think this might have happened when I was dragging around the monitor arrangements.

I changed it back to 2048 by 2048, rebooted, and everything is working as it should!

---

