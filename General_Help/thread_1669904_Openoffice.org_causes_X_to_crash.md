---
title: "Openoffice.org causes X to crash"
date: 2011-01-18
forum: General Help
---

### Post by mwsherman on 2011-01-18
Hi everyone.

I'm using a ZaReason Terra HD netbook. I have not changed any of the default hardware, nor messed with any of the X or openoffice settings.

For almost as long as I've had the computer, I've been getting random X crashes. The screen goes to black, dumps some text, and I'm given a series of options of what to do (low-graphics mode, diagnostics, exit to terminal). From what I've gathered, this only happens when openoffice is running (it can be in the background, it does not have to be the active application). 

I really have no idea what to do or what is causing this. I've attached a log, and I will gladly attach whatever else might be useful. I've looked on the internet for help, and while I do see a lot of X and openoffice issues, they seem to be related to higher end hardware than I have.

I'm running Ubuntu 10.4, openoffice.org 3.2, and using an Intel Corporation N10 Family Integrated Graphics Controller .

Thanks in advance for any assistance. I'm not exactly a poweruser, so I appreciate any guidance I'm given.

Note: the attached log is a text file, but I made it a .doc because it barely exceeded the file size limit for .txt . 

-Mike

---

### Post by nerdy_kid on 2011-01-18
sounds similar to this maybe:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/555573](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/555573)

---

### Post by mwsherman on 2011-01-19
> **nerdy_kid said:**
> sounds similar to this maybe:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/555573](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/555573)

I think this is different...mine has nothing to do with suspend/hibernate, it just crashes randomly. I have issues only with openoffice, and there are no specific behaviors in openoffice that trigger it, at least that I can discern. I'm not sure there is a specific trigger I can reproduce, especially since it will crash with other applications active while openoffice is running in the background.

Also, I don't GPU-Hung errors in the log like these guys do.

Thanks for the information. Any other guesses? I don't want to submit a bug report until I'm sure there isn't a fix.

-Mike

---

### Post by nerdy_kid on 2011-01-20
I would try adding the x-swat ppa, and if that doesnt fix it then report a bug.

heres the ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Hagar Delest on 2011-01-21
I would first try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the vanilla version perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by corncob on 2011-01-21
Try changing your theme.  That fixed a problem I had with OOo one time.  They said OOo doesn't play well with some themes.

---

