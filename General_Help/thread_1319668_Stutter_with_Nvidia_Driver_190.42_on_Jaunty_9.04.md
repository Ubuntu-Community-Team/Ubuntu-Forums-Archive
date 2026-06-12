---
title: "Stutter with Nvidia Driver 190.42 on Jaunty 9.04"
date: 2009-11-08
forum: General Help
---

### Post by efinidc on 2009-11-08
Hello,

I am having an issue with 9.04, an Nvidia 8400gs pci graphics card, and nvidia driver 190.42

The problem is that after upgrading to 180 or 190.42 the performance overall is poor. For example, when moving my mouse cursor it seems to jerk and stutter. If I watch any video, it will do the same as well. It is most noticable when I view a scrolling RSS feed across my screen.

This occurs only after I hook up my computer to a sharp lcd tv. It is being connected through a dvd to hdmi adapter. If I roll back to the default nv driver, everything works perfectly.

I have tried toggling several options through the nvidia settings such as turning off vsync blank and flipping. Under powermizer, it looks like there is no problem. It states maximum performance. My temperature is good as well, it is around 40C.

I also tried adding a modeline to my xorg.conf with gtf 1920 1080 60.

Thank You very much in advance

---

### Post by sojusnik on 2009-11-23
Maybe your problem is connected with this one:

[http://ubuntuforums.org/showthread.php?t=1309503&highlight=190.42+powermizer](http://ubuntuforums.org/showthread.php?t=1309503&highlight=190.42+powermizer)

---

