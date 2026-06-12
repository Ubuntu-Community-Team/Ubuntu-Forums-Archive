---
title: "Boot display doesn't fill the monitor screen"
date: 2010-07-15
forum: General Help
---

### Post by psycho5 on 2010-07-15
Hi,

I have an Nvidia card and I am using ubuntu 10.04.

Before installing the ubuntu nvidia restricted drivers, the boot screen with the ubuntu logo would cover the entire display area of the monitor. 

But now, after installing the Nvidia driver and fixing the display resolution of the boot screen with the Plymouth fix, the boot screen doesn't expand to fit the entirety of the monitor display area. How can I fix this? There is a good 2 inch off from either side of the display while booting.

---

### Post by dino99 on 2010-07-15
plymouth is still heavily bugged, you can remove it or only remove "splash" from boot line

---

### Post by darolu on 2010-07-15
> **dino99 said:**
> plymouth is still heavily bugged, **you can remove it** or only remove "splash" from boot line

According to [this thread](http://ubuntuforums.org/showthread.php?t=1469475) Removing plymouth is not recommended. Removing it would remove half the OS as it has a hard dependency on mountall. Removing the Themes would be the better option if a non-graphical boot is wanted.

[quote=psycho5]But now, after installing the Nvidia driver and fixing the display resolution of the boot screen with the Plymouth fix, the boot screen doesn't expand to fit the entirety of the monitor display area. How can I fix this? There is a good 2 inch off from either side of the display while booting.[/quote]

Sounds like you already tried but just in case: [This Thread](http://ubuntuforums.org/showthread.php?t=1469475) has a workaround that worked for me, I had a similar problem and following those steps fixed it; including the "etc/initramfs-tools/conf.d/splash" file step.

---

### Post by psycho5 on 2010-07-15
> 
Sounds like you already tried but just in case: [This Thread](http://ubuntuforums.org/showthread.php?t=1469475) has a workaround that worked for me, I had a similar problem and following those steps fixed it; including the "etc/initramfs-tools/conf.d/splash" file step.

Well, I have indeed tried all of that. Anyways, it's not a big issue, it's just that the entire boot looks alot more cleaner when it's nicely stretched out. Hopefully all these issues will be fixed in the next release? Who knows. *cross fingers*

---

