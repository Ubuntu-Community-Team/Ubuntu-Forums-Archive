---
title: "x11vnc XOpenDisplay failed"
date: 2011-11-24
forum: General Help
---

### Post by noodlesuk on 2011-11-24
Hi

Ubuntu newbie here, I've searched tghrough previous threads/Google and couldn't seem to find a definative solution, my issue is with x11vnc. I've installed and it worked ok until I logged out, when trying to start x11vnc via ssh I get the following error

24/11/2011 12:09:21 *** XOpenDisplay failed (:0)

I assume this is because no user is logged on? I've tried the suggestions under the **Continuously:** section of the x11vnc FAQ but to not avail. Any help much appreciated!

Cheers

---

### Post by maverickaddicted on 2011-11-24
These threads might help you - 

[http://ubuntuforums.org/showthread.php?t=1885994](http://ubuntuforums.org/showthread.php?t=1885994)
[http://brakertech.com/x11vnc-was-unable-to-open-the-x-display/](http://brakertech.com/x11vnc-was-unable-to-open-the-x-display/)
[http://ubuntuforums.org/showthread.php?t=1558680](http://ubuntuforums.org/showthread.php?t=1558680)
[http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html) (Q-1 - Building and Starting section)

---

### Post by noodlesuk on 2011-11-24
Thanks for the pointers, I've gone through the solutions, one thing they point towards is finding the MIT-MAGIC-COOKIE file, but the locations they suggest i.e \var\kdm \var\gdm etc don't seem to exists (Ubuntu 11.10)

Cheers

---

### Post by maverickaddicted on 2011-11-28
> **noodlesuk said:**
> Thanks for the pointers, I've gone through the solutions, one thing they point towards is finding the MIT-MAGIC-COOKIE file, but the locations they suggest i.e \var\kdm \var\gdm etc don't seem to exists (Ubuntu 11.10)

Cheers

It will be /var/lib/gdm or /var/lib/kdm, not /var/kdm or /var/gdm.

---

### Post by acey_zero on 2012-03-28
FYI, "-auth /var/run/lightdm/root/:0" was what finally worked for me on Mint 12 (I assume Ubuntu 11.10 would be the same).

---

