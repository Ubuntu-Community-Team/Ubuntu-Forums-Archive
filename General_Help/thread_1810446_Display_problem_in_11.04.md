---
title: "Display problem in 11.04"
date: 2011-07-23
forum: General Help
---

### Post by One_Box on 2011-07-23
Recently updated to 11.04 (64bit) and using the recommended Nvidia display driver (using Gnome rather than Unity).

Started to get some empty windows opening instead of being filled with data.

Checked the display driver, it said it had been activated but not being used.

Deactivated it and restarted computer. 

I'm dual booting with Win7 64bit and the grub loader message appears as normal.

When I select the latest version of the kernel the HD operates and all I get is a blank screen!!

I've tried the previous kernel versions with the same result.

I know it's not a problem with the display adaptor as it works in Windows.

Can any one suggest a way forward, I don't want to lose important data in my home folder!!

Sorry to be thick, as you can see my knowledge of Linux is very limited.

Any help would be gratefully received

I

---

### Post by wildmanne39 on 2011-07-23
Hi, look at this link it should allow you to boot into ubuntu.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

That saying that the driver is not in use is just a bug, it really was in use if you activated it and you could see the unity desktop.

I also had the white windows and the problem was the nvidia driver I was using, I had to go back to the older 173 driver and everything works perfect.

---

### Post by One_Box on 2011-07-23
> **wildmanne39 said:**
> Hi, look at this link it should allow you to boot into ubuntu.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

That saying that the driver is not in use is just a bug, it really was in use if you activated it and you could see the unity desktop.

I also had the white windows and the problem was the nvidia driver I was using, I had to go back to the older 173 driver and everything works perfect.

Thanks for your help, I managed to boot to a command prompt but could not get the desktop up no matter what I did. A complete re-install cured the issue and I think I'll stay away from the Nvidia driver (I only use this machine for Folding@Home.)

---

### Post by wildmanne39 on 2011-07-23
Hi, your welcome! sorry you had to reinstall.

---

