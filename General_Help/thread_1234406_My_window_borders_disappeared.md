---
title: "My window borders disappeared?"
date: 2009-08-07
forum: General Help
---

### Post by KinKiac on 2009-08-07
Ok, so I kinda screwed up one of my installations.  The good news is it is just my thumb drive installation.  Im using Jaunty.

Here's what happened:

First, installed onto thumb drive at work

Second, brought home, no internet, couldnt install video drivers, compiz doesnt work at home, np will get drivers later

Third, back at work, compiz working, had to use deb packages to install anything at work

Tried installing screensaver plugin from source, kept getting error saying "Compiz not installed"

So, I decided to re-install everything compiz, first by removing everything compiz in synaptic

After doing so I lost my window borders.  I manager to get to a connection where I could use apt-get and reinstalled compiz fine, but I still cant get window borders.  If I change my visual effects to none they come back but them compiz doesnt work, if I enable compiz I have no window borders.  

Any Ideas?

Thanks.

---

### Post by pastalavista on 2009-08-07
In CompizConfig Settings Manager go the 'Effects' menu and make sure 'Window Decoration' is checked.

If you installed a system on one computer, it likely won't work right on any other computer unless you Installed a 'persistent' version of the Live CD.

---

### Post by KinKiac on 2009-08-08
Actually window decorations is checked off.  Ive been through everything I can think of and nothing seems to make a difference.  I had no problems switching from one PC to another until I removed all the compiz features via synaptic, thats when the issue started.  

Interestingly enough it actually works on different PC's with different hardware.  I had considered doing a persistent install but all the tutorials I read involved using a casper rw loop file and even the largest setup only allowed for 4gig worth of changes.  I wanted more than that, I have a 16gig thumb drive and so have a lot of room to work with.  It works surprisingly well considering it was installed on a Lenovo Think Centre with a dual core and only onboard video(even compiz works, save for the window border issue, which happens even on the PC it was originally installed on) and my home PC which I have used it on as well is a pentium 4 with an nvidia card.

---

### Post by lnyitrai on 2009-08-10
I had similar problem: I use my monitor in custom resolution, and I used nvidia-settings set it up. Everything was fine so far. But when I saved xorg.conf and restarted X, my window decoration had gone.

Resolution is [here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159584"):
You need to add the following lines to **[COLOR=Red]all[/COLOR]** your Device sections in xorg.conf:
 ```
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
```

---

