---
title: "one-time (so far) failure of X server to start - potential causes?"
date: 2009-12-24
forum: General Help
---

### Post by multanihl on 2009-12-24
I just installed Karmic 32-bit on an Acer X1300 (AMD Athlon X2-64, 3GB RAM, Integrated Nvidia 8200 Video) after I swapped out the factory hard drive for a 500GB Western Digital "green" drive, because for some reason the existing Vista install wouldn't let the partitioner set up for dual-boot.

*ahem* So anyway, installation was a breeze, I even got the video adapter working with restricted drivers no problem.  Everything has been working great, although I had to disable Compiz to stop a tearing issue with video playback (this solved the problem, thankfully).

The only curious thing is that, this morning, when I turned the machine on, after boot-up, I didn't get a login manager or display manager.  In other words, for some reason gdm didn't start on bootup.  I was able to start it from the console (sudo /etc/init.d/gdm start), and when I restarted it again I got my normal login screen.  To make sure, I did a couple more restarts, and each time so far it has been fine.

I guess I'm more curious than anything as to what caused me to boot to a console that one time -- does anybody out there have any ideas?  For the record, I checked the diagnostics on my (still pretty much brand-new) hard drive and it says all green.  Maybe was just a goof from the video driver?

---

