---
title: "xserver does not start: &quot;undefined symbol: pixman_disable_out_of_bounds_workaround&quot;"
date: 2010-05-09
forum: General Help
---

### Post by tom.db on 2010-05-09
Hallo,

I installed UBUNTU 10.04 on a Dell Inspiron 1520 (Graphic card: NVIDIA GeForce 8400).
All worked fine but only some hours: after a few new start xserver does not start anymore.

During the boot, if the splash is disabled, gdm does not start and the system switchs automatically on the shell tty1.
If I press CTRL+ ALT + F7 I see the normal boot messeges before the gdm's start (I think...). The last two are:
> 
* Enabling additional executable binary formats binfmt-supports           [ OK ]
* Checking battery state...                                                                       [ OK ]

If I press CTRL+ ALT + F1 and log in and give the command

```
startx
```

I receive the following error message:
> 
/usr/bin/X: symbol  lookup error: /urs/binX: undefined symbol: pixman_disable_out_of_bounds_workaround

No log is written in /var/log/Xorg.0.log
The file /etc/X11/xorg.conf is not present.
Before this problem occourred the system worked fine. Immediatly before I didn't install anything and I didn't any administrative operations.
I already tried to reinstall, without results.
I had the same problem with debian too, so the issue can be related to my hardware.

cheers
tom.db

---

