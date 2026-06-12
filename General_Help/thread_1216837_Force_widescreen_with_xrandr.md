---
title: "Force widescreen with xrandr?"
date: 2009-07-18
forum: General Help
---

### Post by Chris_Bailey on 2009-07-18
So I've been working on getting a widescreen resolution working on and off now for about 2 months, still with no success. I have been able to display 1024x768 so far, leaving a few inches of black on either side of the picture. I added my desired resolution using xrandr and am able to see it listed but when I try to switch the output to it I get the error "screen cannot be larger than 1024x768". The exact same configuration has worked fine in all variations of Ubuntu prior to 9.04. I am using the latest Nvidia drivers for an older Nvidia Quadro 4 700 XGL coupled with a 26in RCA hdtv. The native resolution is 1368x768, and it has always operated at this resolution prior to the upgrade. I would really appreciate any assistance getting this working as I'm pretty tired of staring at a little square. =)

---

### Post by LightningCrash on 2009-07-18
what is the output of the command `xrandr`?


try `xrandr -s 0` from a terminal, too. I used to have to do that on ATI drivers to get a 2-screen Xinerama (@2560x1024) working properly.

---

### Post by aliozer on 2009-12-10
> **LightningCrash said:**
> what is the output of the command `xrandr`?


try `xrandr -s 0` from a terminal, too. I used to have to do that on ATI drivers to get a 2-screen Xinerama (@2560x1024) working properly.

I am having exactly the same problem. I will try your suggestion when I get home, but my guess is the results will not change. You can see the description of my problem and the xorg.conf file and the xrandr outputs at this and the following posts: [http://ubuntuforums.org/showthread.php?p=8470571#post8470571](http://ubuntuforums.org/showthread.php?p=8470571#post8470571) Any ideas?

Thanks,

Ali.

---

