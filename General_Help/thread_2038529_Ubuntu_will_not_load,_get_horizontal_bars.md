---
title: "Ubuntu will not load, get horizontal bars"
date: 2012-08-06
forum: General Help
---

### Post by kuntu on 2012-08-06
Hey guys,

I just downloaded and installed the alternative 64-bit Ubuntu 12.04. I had to download the alternative because it would not even start the liveCD or anything to allow me to install the OS graphically. 

Ubuntu is installed, but when it tries to load, this happens:
[http://i.imgur.com/K1E4H.jpg](http://i.imgur.com/K1E4H.jpg)

This is also what happened when I tried to install Ubuntu graphically (not with the alternative CD btw).

Hardware specs:
GeForce GTX 570 HD (which I suspect is the problem)
i-2500k
Asus P8P67 EVO mobo (Intel P67(B3) chipset)

This is also on a 7200rpm 500GB hard drive. Any help is appreciated.

PS: When I installed Ubuntu, I disconnected the rest of my internal hard drives (because a few had a similar size to the one I was installing it on and I didn't want to confuse it), with it one of them being the Windows 7 install I have on a 120GB SSD. One I get this issue resolved, what's the easiest way to get the dual boot to work? Right now, because of this lazy move by me, grub thinks Ubuntu is the only install on my rig.

---

### Post by kuntu on 2012-08-07
With the help of booting with the parameter "nomodeset" (referenced [here]("http://ubuntuforums.org/showthread.php?t=1613132%20on%20how%20to%20use%20this%20parameter")) I was able to get into the OS.

The resolution was very limited and the system was a bit sluggish. I tried installing the nvidia drivers manually because jockey did not work and it seemed they installed correctly. I rebooted and the resolution went to my native 1920x1200 and everything seemed fine..

After loading a YouTube video and trying to install Flash, Ubuntu locked up. Not too worrying, so I just turned off the computer and turned it back on.

I ended up getting the bars again, having to resort to the "nomodeset" parameter again to get in.

What gives, if nvidia's geforce drivers installed correctly? What should I look for, where, etc?

---

### Post by Gene_J on 2012-08-08
Try running the memtest from the live CD. This happened to me a couple of days ago and it turned out to be a bad stick of memory.

---

### Post by kuntu on 2012-08-08
> **Gene_J said:**
> Try running the memtest from the live CD. This happened to me a couple of days ago and it turned out to be a bad stick of memory.
Not to say it isn't it, I'll run the test in the morning, but I find it very unlikely.

Because of the fact that it ran fine after I installed the drivers, just after the second reboot it failed. It seems graphics related to me. The fact that the parameter 'nomodeset' eliminates the issue also reinforces that.

Plus I run Windows 7 fine for days on end with no issues. If my RAM was bad, I'd think I would experience BSOD or lock-ups.

---

