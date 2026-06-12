---
title: "Oneiric hangs during boot"
date: 2012-02-12
forum: General Help
---

### Post by stefangr1 on 2012-02-12
During boot, my system hangs. The last messages that are shown are either:

Blocking file system - Stopping save kernel messages [  OK  ]
or Stopping Userspace bootsplash [  OK  ]

After that, there's just a blinking dash ( _ ) on the screen.

About ten lines before it hangs, it shows 
* Stopping automatic crash generation [fail]

Any ideas?

---

### Post by 2F4U on 2012-02-12
Since when do you have this problem and what happened before it appeared? Did you install new software, updates? Have you done a hard shutdown?

---

### Post by stefangr1 on 2012-02-13
> **2F4U said:**
> Since when do you have this problem and what happened before it appeared? Did you install new software, updates? Have you done a hard shutdown?

No, nothing of that. I did, however, have some problems regarding the NVIDIA 8400GS video card not too long ago. Suddenly, the screen went black entirely (even didn't show the bios messages). At that time I tried to solve those problems by removing the nvidia-current video driver (trough ssh), and then manually installing the driver provided on the NVIDIA website. I remember that a weird error emerged, that I haven't seen before, saying something like the operating system provided pre-install script could not be run. After that I reinstalled nvidia-current, rebooted, and found my system working again. After that, I have booted the system successfully at maybe about 8-10 times. So the two problems could be related.

I can still ssh into the system. Nothing unusual shows up in /var/log/syslog.

---

### Post by stefangr1 on 2012-02-16
I think my NVIDIA graphics card was broken. I had some problems previously that were also related to the graphics card (e.g. the system sometimes booting in low graphics mode, or even failing entirely (not even showing the bios). Reinstalling the video drivers did seem to solve that, as did doing a full reinstall. However, the problems always come back after a few days or weeks.

I now replaced it and did (again) a full reinstall.

Though the fact that it has been working flawless since the replacement doesn't necessarily imply a definite solution (previously reinstalling would also seem to solve things until the thing broke again),  I'm gradually starting to think that the problem may not have been due to os/driver issues. And even if it was, changing to a different GPU may solve things as well.

---

