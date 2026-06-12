---
title: "Trying to update video drivers - need to stop X server."
date: 2010-07-18
forum: General Help
---

### Post by WarKirby on 2010-07-18
Hello all.

Running Karmic 9.10

I'm trying to update the driver on my Nvidia 8800 GTS 512. Nvidia has a native linux driver for this. I've downloaded and attempted to run it, but it returns this error:

"You appear to be running an X server; please exit X before installing. For further details see..."

and it makes reference to this: [http://uk.download.nvidia.com/XFree86/Linux-x86/256.35/README/installdriver.html](http://uk.download.nvidia.com/XFree86/Linux-x86/256.35/README/installdriver.html)

So I'm attempting to stop the X server, though I don't understand what that is. Whoever came up with that name should feel bad. 

With a bit of poking around the internet, I found the "Booting to a different runlevel" section on this page: [http://uk.download.nvidia.com/XFree86/Linux-x86/256.35/README/newusertips.html](http://uk.download.nvidia.com/XFree86/Linux-x86/256.35/README/newusertips.html)

But the init command in console does nothing, and the file /etc/inittab is not there.

So how am I supposed to install this driver? all advice appreciated.

---

### Post by wojox on 2010-07-18
Follow this HowTo here: [HowTo: NViDIA Drivers in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1125400")

---

