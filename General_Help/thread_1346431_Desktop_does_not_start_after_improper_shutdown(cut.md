---
title: "Desktop does not start after improper shutdown(cut off power)"
date: 2009-12-05
forum: General Help
---

### Post by hofg on 2009-12-05
So I installed ubuntu 9.10 a few weeks ago and all was fine and dandy until cut off power while the computer was on and now the desktop freezes/does not start properly. There weren't any important processes running like updates and such. The loading icon comes up but then it skips the ubuntu screen and after that only background image and cursor come up. XP runs fine and I ran fsck from livecd but nothing seems to be wrong so I believe it's not a hardware problem. Also tried to run "fix broken packages" from recovery mode. So how do I fix this?!

---

### Post by jegerjensen on 2009-12-05
Do you see the login screen?  I believe you could choose a different session from there.  On hardy I have a "Failsafe GNOME" session.  That way you may get in as a first step to fix your problem.

If you have enabled automatic login, you can disable it by editing the file /etc/gdm.conf.  There is a setting AutomaticLoginEnable. Make sure it reads
```
AutomaticLoginEnable=false
```

---

### Post by hofg on 2009-12-05
> **jegerjensen said:**
> Do you see the login screen?  I believe you could choose a different session from there.  On hardy I have a "Failsafe GNOME" session.  That way you may get in as a first step to fix your problem.

If you have enabled automatic login, you can disable it by editing the file /etc/gdm.conf.  There is a setting AutomaticLoginEnable. Make sure it reads
```
AutomaticLoginEnable=false
```

I disabled autologin and now it freezes on the login screen I believe. I have yet to see the login screen of ubuntu 9.10 but i'm quite sure it is the login screen 8) There is just the "picture" and nothing else. Someone noted there is a rescue option on the livecd I shall try it next.

---

