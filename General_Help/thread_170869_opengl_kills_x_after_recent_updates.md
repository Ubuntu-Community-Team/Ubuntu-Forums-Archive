---
title: "opengl kills x after recent updates"
date: 2006-05-05
forum: General Help
---

### Post by jrb114 on 2006-05-05
Hi,

Just today, I installed the latest kernel update and all the other xorg/xserver (forget which) updates. All fine.

Then, before I rebooted, I carried on working until we had a power cut. When the machine came back up (with the new kernel though, but also having to check root fs as it hadn't been checked in 30 mounts, etc) I saw the nvidia splash screen, no problems.

Logged in, carry on as normal... Start reading something, no activity for 5 minutes, screensaver (hence openGL) and X falls over and restarts, bringing me back to the login screen. This has happened over and over. Even asking at the terminal

```

glxinfo

```

kills X.

Has anyone else had this problem? I haven't yet tried reinstalling the nvidia drivers, but may have too. (And breezy is supposed to be "stable") :-(  

Thanks, will update when I'ved tried reinstalling nvidia.

J

---

### Post by tseliot on 2006-05-05
You need to reinstall the driver.

I'm trying to warn as many people as possible.

---

### Post by jrb114 on 2006-05-05
Thanks, 

Will set too shortly.

J

---

### Post by jrb114 on 2006-05-07
Your how-to worked perfectly. Thank you

[http://ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia+drivers)

---

### Post by rmaple on 2006-05-08
I've avoided installing these updates for fear that it would trash X, and I can't afford to fight it right now.  I'm running the ubuntu build of the nvidia drivers (nvidia-glx 1.0.767-0ubuntu25.1 and linux-restricted-modules for 2.6.12-10-k7 v 2.6.12.4-11.1) - not the latest and greatest, but they seem to work fine with my 6600gt board.  Do the new updates pushed last week (either kernel or Xserver) invalidate these drivers and require a new install from the nvidia sources?

Thanks

---

