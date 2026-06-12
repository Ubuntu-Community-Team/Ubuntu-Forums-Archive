---
title: "Can't change screen resolution, editing xorg.conf problematic"
date: 2010-08-10
forum: General Help
---

### Post by Bhundo on 2010-08-10
I'm very new to Ubuntu and have 9.04 running on a Sony Vaio, don't know what graphics card I have. My screen resolution doesn't have an option higher than 800x600, so everything looks super zoomed in. Other threads tell me to edit xorg.conf, which I did (probably incorrectly). The result was the computer had mega problems when I restarted it, and when it finally got back to the desktop it didn't give me any other options for screen resolution. Also it says I'm in low graphics mode.

---

### Post by dpol on 2010-08-13
You're on the right track.  Make sure that the vertical and horizontal synch in xorg.conf is exactly what the manufacturer of your monitor specifies.  Once you make that change and reboot, proper resolutions should be available to you in whatever GUI tool you're using to change your screen resolution.  

Be sure to back up your current xorg.conf before making any changes to it.  This way you could always revert to it if you run into problems.

---

