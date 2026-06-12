---
title: "Does Ubuntu know when system has crashed?"
date: 2011-09-27
forum: General Help
---

### Post by Rebelli0us on 2011-09-27
I’d just opened gthumb, was cropping an image and my system just froze. My other most common crashes: opening any video file with Movie player or VLC randomly hangs the system, resume failure, random errors in apps, wii remote driver (wminput) in daemon mode, XBMC wiping out video system forcing a reset. I also get the impression that unhandled bad pointers **will** bring down Linux. 

My system hangs on average every **3 days**. On the same machine, my Windows 2000 can run for months. I’m hoping that Ubuntu logs its crashes and reports back to Canonical who fixes the problem!

---

### Post by JRV on 2011-09-27
ALT=>SySRq=>K will usually bring you back to the login screen.

---

### Post by Rebelli0us on 2011-09-27
> **JRV said:**
> ALT=>SySRq=>K will usually bring you back to the login screen.

Alt+PrintScr+K ?  Login means all apps killed?

---

### Post by JRV on 2011-09-30
> **Rebelli0us said:**
> Alt+PrintScr+K ?  Login means all apps killed?

Yes

---

### Post by 3rdalbum on 2011-09-30
This sounds like it could be caused by a bad graphics card, bad graphics driver, or bad RAM.

If you don't get any such problems in Windows, it's more likely to be the driver or the RAM. (Windows leaves much of your RAM unused for some silly reason - if the faulty spot is in that "never-used" section you'll never actually notice the problem on Windows. Until the rest of the RAM goes faulty, that is.

As for graphics driver problems, if possible use a different driver. If using the open-source ATI or Nvidia drivers, switch to the proprietary ones; or vice-versa. See if the problems still occur.

---

### Post by Rebelli0us on 2011-10-22
> **3rdalbum said:**
> This sounds like it could be caused by a bad graphics card, **bad graphics driver**, or bad RAM.

If you don't get any such problems in Windows, it's more likely to be the driver or the RAM. (Windows leaves much of your RAM unused for some silly reason - if the faulty spot is in that "never-used" section you'll never actually notice the problem on Windows. Until the rest of the RAM goes faulty, that is.

As for **graphics driver problems**, if possible use a different driver. If using the open-source ATI or Nvidia drivers, switch to the proprietary ones; or vice-versa. See if the problems still occur.


Thank you. I uninstalled the proprietary AMD video driver and the system freezing has stopped. I'm now at 10+ days uptime for the 1st time. Mobo is GIGABYTE GA-890GPA-UD3H and Compiz is also removed.

The wii remote driver (wminput) in daemon mode will still hang the system when reconnecting on resume from S3, but the random crashes have stopped.

---

