---
title: "MagicJack freezes system at login prompt"
date: 2010-08-26
forum: General Help
---

### Post by Slartifartfast on 2010-08-26
I have MagicJack working inside of an VMware XP guest no problem.  The only problem i have now is that my system freezes at the logon screen if the device is plugged in on reboot.

I tried disabling auto mount and auto play in "removeable devices and media" preferences.

I also added the following to my fstab. Still no luck.  Any ideas or am I missing something easy/obvious?  Thanks.


```
/dev/sde        /media/PHONE    auto    noauto  0       0
/dev/sr1        /media/magicJack        auto    noauto  0       0
/dev/sdd        /media/PHONE_   auto    noauto  0       0
```

Linux ben-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

---

