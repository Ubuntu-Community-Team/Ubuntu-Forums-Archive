---
title: "Login Loop on Ubuntu 11.10 -  Not Caused by Upgrade"
date: 2011-10-19
forum: General Help
---

### Post by beardedman on 2011-10-19
I've been dealing with this issue since last night:

**Preface**
I upgraded my server to Ubuntu 11.10, everything worked fine *except* Desktop Sharing. So I tried installing packages other than Vino as a solution. I never did get the Desktop Sharing/VNC to work. But I did manage to screw things up even more.

After installing X11VNC I read that I needed to adjust one of the XServer or XServices files (I can't remember which one). When I tried to do so, Ubuntu told me that those files weren't there, but they were included in the tightVNC package. So I downloaded tightVNCServer and made the adjustments to the aforementioned file. 

Upon reboot, I am now caught in a login loop. My configuration was initially to auto login, but now I'm forced to type a password. 

**Abilities**
I can TTY[1-6] just fine
From the LightDM, I can login perfectly under Guest account only.

**Symptoms**
1. When at the login screen, I type in my password, the screen goes blank (as if its loading the desktop), but then returns me to the login screen. If I type my password in a second time, the textfield to type my password disappears and I'm stuck (and must forcefully shut down the computer).

2. When logged in via TTY[*] the command ```
startx
``` displays a ```
Fatal Server error: server is already active for display 0
``` followed shortly thereafter by ```
Invalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```

**Limitations**
Any recovery mode shell is read only

**What I've Tried Thus Far**
- Uninstall and re-install: xserver-xorg; xserver-xorg-core; ubunutu-desktop; lightdm; unity


There is more that I've tried from similar issues on different threads, but I honestly cannot remember at this point


**Misc**
ATI Onboard Graphics

Someone please help me out, I've googled to the point that I can no longer remember what an un-visited hyperlink looks like. :-({|=

Thanks for reading

---

### Post by mitchapalooza on 2011-10-19
I'm having the same problem. Although it was caused by a simple apt-get upgrade.

Bump for 4 hours.

---

### Post by beardedman on 2011-10-21
> **mitchapalooza said:**
> I'm having the same problem. Although it was caused by a simple apt-get upgrade.

Bump for 4 hours.

mitchapalooza - you should check out this thread: [http://ubuntuforums.org/showthread.php?t=1865355&highlight=login+loop](http://ubuntuforums.org/showthread.php?t=1865355&highlight=login+loop)

Long story short, it's a possibility that you have a program set to launch on start up and the upgrade got rid of the program

**Back on my issue for a moment**, I've attached my xsession-errors log. Will someone please help me interpret this?

---

