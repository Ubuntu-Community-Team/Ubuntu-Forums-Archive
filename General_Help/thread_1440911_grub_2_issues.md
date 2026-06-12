---
title: "grub 2 issues"
date: 2010-03-28
forum: General Help
---

### Post by garma on 2010-03-28
i want grub 2 to load windows 7 by default after only 3 seconds it was easy to due with grub but since i updated to Ubuntu 9.1 64 bit from Ubuntu 9.0 32bit "it came with the new grub" anyways i was also wondering how to code it to add a boot in windows safe-mode option the reason for all this is i share this computer with my technophobia girlfriend and i am unfamiliar with the Linux commands as i am new to ubuntu and would eventually like to get away from microsoft

---

### Post by drs305 on 2010-03-28
This can still be done with StartUp-Manager. Install startupmanager via Synaptic or:
```
sudo apt-get install startupmanager
```

Then open it via the System, Administration, StartUp-Manager menu. You can set the default OS and timeout from the tabs in the app.

---

### Post by garma on 2010-03-28
thanks ill try it and get back to you.

---

### Post by garma on 2010-03-30
thank you that helped now lets see if i can find the kernal removal thread

---

### Post by drs305 on 2010-03-30
> **garma said:**
> thank you that helped now lets see if i can find the kernal removal thread

Post #2 that I wrote a few days ago covers how to install Ubuntu-Tweak, a great GUI app that will help uninstall older kernels.
[http://ubuntuforums.org/showthread.php?t=1441827]("http://ubuntuforums.org/showthread.php?t=1441827")

There is also information in this link. See the section on "Removing Older Kernels":
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

