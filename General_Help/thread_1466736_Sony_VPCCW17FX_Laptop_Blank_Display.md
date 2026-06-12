---
title: "Sony VPCCW17FX Laptop Blank Display"
date: 2010-04-30
forum: General Help
---

### Post by lakerssuperman on 2010-04-30
Hello,

I have a Sony VPCCW17FX laptop.  It has a documented issue where the NVIDIA driver doesn't correctly read the EDID info from the screen.  I am running Kubuntu 9.10 but have also run Ubuntu 9.10 on it.  With both configurations the only way for the Nvidia driver to properly work was to force the use of an EDID file in the xorg.conf.  I am trying to do a fresh install of Kubuntu 10.04 on this laptop.  With 9.10 I could boot the livecd and it would show the desktop and I could install with the basic driver.  With 10.04 it loads the livecd and I can select from the livecd menu to run the live session.  However, once it begins to boot the screen goes black.  It isn't just not displaying, the screen is actually off and does not come back on.  The laptop continues to boot but the screen never returns.

I am unaware of how to go about fixing this.  Anyone have any suggestions on how to get the livecd to boot?  Thank you.

---

### Post by lakerssuperman on 2010-10-15
I just figured I'd give installing 10.10 a try on this laptop.  I had read that the new 260 NVIDIA Driver was supposed to fix the above issues.  Apparently not so.  Everything starts to load, Plymouth comes up and right after the loading animation disappears I am left with the screen keeping the purplish background color at which point it stops loading altogether.  I feel like I'm very close to having this working without having to use the EDID file hack.  Does anyone have any suggestions.  Again, this is Sony VPCCW17FX laptop with a NVIDIA G210m chip.

---

### Post by Quackers on 2010-10-16
See if posts 8 or 13 can help you here
[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

---

### Post by lakerssuperman on 2011-05-02
The latest Nvidia Drivers eliminate the video issues with this laptop.

---

