---
title: "NVidia 9600GS low graphics error"
date: 2009-11-20
forum: General Help
---

### Post by nintendo9freak on 2009-11-20
Hello,

I have an Asus laptop (M50VM-X1) running Ubuntu 9.04, and it comes with the NVidia 9600GS graphics card. I was trying to set visual effects to normal/extra, but I always get the Desktop effects could not be enabled error. I search online and came across two solutions: Go to System > Administrator > Hardware Drivers and enable NVidia accelerated graphics drvier v180 or to run xconfig (sudo nvidia -xconfig, i think). Now my issue is that, if I use the first method, Ubuntu takes a while to load then goes into low graphics mode with its positioning off. If I try the second method, everything will work fine for the first 2 or 3 boot ups, but after the 3rd boot up the same issue occurs. Can anybody please help me?

Thanks,
Hassaan

---

### Post by Giblet5 on 2009-11-20
Run ```
sudo nvidia-settings
```

Set it how you like it, then click "X Server Display Configuration" on the left. Now click "Save to X Configuration File" in the lower-right.

That should correct the low-res issues.

---

### Post by khelben1979 on 2009-11-20
I think that the problem might be related to your graphic drivers. Are you using an open source graphic driver or the one provided by nVidia?

```
nvidia-settings
```
to give us output on what graphics driver you're using.

---

### Post by Giblet5 on 2009-11-20
He [COLOR="Gray"](kind of)[/COLOR] said that he installed the 180 nvidia driver via System/Admin/Hardware.

---

### Post by khelben1979 on 2009-11-20
> **Giblet5 said:**
> He [COLOR="Gray"](kind of)[/COLOR] said that he installed the 180 nvidia driver via System/Admin/Hardware.

You're right! I was tired when I read it.

---

### Post by Giblet5 on 2009-11-20
> **khelben1979 said:**
> You're right! I was tired when I read it.

It's a ridiculously wealthy kind of tired though. ;)

---

### Post by nintendo9freak on 2009-11-20
Well the 180 nvidia driver did not work for me, so it's currently uninstalled. When I do nvidia-settings, a nvidia window pops up and tells me to do nvidia-xconfig, which I feel will bring the same issue up again.

---

### Post by nintendo9freak on 2009-11-20
OK, so I did nvidia-xconfig, and the issue came again when I restarted. Running nvidia-settings work properly, I think?

[Link NVIDIA Setting issue]("http://img97.imageshack.us/img97/1474/nvidiad.jpg")

---

### Post by khelben1979 on 2009-11-20
Perhaps you should try nVidia driver 177.80 to see if it works better? I looked at [this page]("http://www.nvnews.net/vbulletin/showthread.php?t=122130").

---

### Post by khelben1979 on 2009-11-20
> **Giblet5 said:**
> It's a ridiculously wealthy kind of tired though. ;)

Hmm.. everyone needs sleep.

---

### Post by nintendo9freak on 2009-11-20
I tried 1.77, and it worked! But it boot up looked similar to the boot up i was getting earlier, which only worked for a few boot ups. Hopefully it keeps up, if not I'll be back. =]

THANKS!

---

