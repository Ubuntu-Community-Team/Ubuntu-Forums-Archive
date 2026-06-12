---
title: "Installed Dapper, now everything graphical is slow"
date: 2006-06-28
forum: General Help
---

### Post by kdevil on 2006-06-28
I used to run Breezy on my laptop (Latitude X1), and it was working fine.  Then I upgraded it to Dapper via a fresh install, and now I have a problem: everything involving graphics is slow.
Zsnes is slow, the fade-in and fade-out you get for passwords and logging out is slow, xscreensaver (both 2D and 3D) and its fade effect are slow, the little wireframe thing you get when launching a program is slow....well, you get the idea.  The problem occurs whether I'm using GNOME or Xfce.

All of that was quick when using Breezy.  It's using the same driver (i810) that it did before, and a "dpkg-reconfigure xserver-xorg" didn't help, so I'm not sure what went wrong or how to get things back up to speed.

Any ideas on how to fix this?

---

### Post by kdevil on 2006-06-29
*crickets chirping*


Nobody?  Well, I got everything working anyway.

Incidently, another problem I was having was that when doing nothing my computer would report 10-20% CPU use, and after coming out of hibernation or standby would report 30-60%.  This was also fixed, and now when doing nothing it hovers around 1-4%, like it should.

How did I fix all that?  I was using kernel 2.6.15-25-686.  I am now using 2.6.15-25-386.  Yeah, that's all I had to do.

Problem solved :D

---

### Post by matthew on 2006-07-22
I discovered this as well. I believe the problem exists because both of the -686 kernels in the Ubuntu repos are compiled for SMP processors (rather than just the 686-smp kernel) and the Pentium M is a single core processor.

I switched back to the 386 kernel and all is well with me also.

---

### Post by SuperMike on 2006-07-22
You know, it just *might* be a module in your module section in /etc/X11/xorg.conf file is throwing your video driver for a loop. You could try commenting one of these at a time with #, rebooting, and seeing if one of those items was the reason why your video card slowed way down. Also, if you have "UseFB" or "UseFBDev" set to "true" or "false" in your device section, toggle it to the other value, reboot (easiest way to explain the way to reset X), and see if that doesn't fix you.

Note also that your BIOS might be at play here. I noticed that some motherboards have a setting called "Video DAC Snooping". Some video cards want this, while others do not. The sign that you're having trouble with this is if you see "faint multicolored snow trails" when you drag your mouse around the screen. On my home PC, I had this very case and had to toggle the Video DAC Snooping option in my BIOS setup.

---

### Post by kdevil on 2006-07-23
I think I actually tried commenting out modules before switching to the 386 kernel, and they either had no effect or made things even slower.

---

### Post by geos2 on 2006-07-24
I have the same problem on an x60s: it is definitely a problem with the 2.6.15.-26 kernel since under -23 everything is fine.

the symptoms seem to have to do with 2d screen redrawing, I think GL works fine...  desktop animations and xscreensaver are painfully choppy.  interestingly, under gnome you can't even type on my machine swithout painful lag, but under kde you can type (though animations are still choppy)

i'm going to try the taking out x.org modules and see but i think this is a kernel bug for the reason above... i've tired reporting it as a bug with no reply on launchpad...

---

### Post by geos2 on 2006-07-24
let me repeat: this isn't a problem with Pentium or SMP since the x60 is Core Duo...

I am going to try to report it as a bug again...

---

### Post by geos2 on 2006-07-24
reported as bug#53898

---

### Post by MarinaraOfDeath on 2006-07-24
Or you could just tell the person to save everything and press Ctrl+Alt+Backspace to restart X.

---

