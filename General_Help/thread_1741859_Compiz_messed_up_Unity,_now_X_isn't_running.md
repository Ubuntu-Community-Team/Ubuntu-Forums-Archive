---
title: "Compiz messed up Unity, now X isn't running"
date: 2011-04-28
forum: General Help
---

### Post by Timsworth on 2011-04-28
Hi guys,
   I updated to 11.04 earlier today and everything was fine until I decided to get some effects back using compiz.  I disabled the desktop wall and enabled the desktop cube and instantly Unity crashed and I couldn't interact with anything.

I restarted and now I'm informed that X has had a problem and I'm in low-graphics mode.  Though the menu system, I try to restore X to its default settings, but I press OK and the same window with the same options keep popping up, so I'm not progressing.

I'm still able to interact with my computer via the many terminals, I just don't have any form of GUI.

I've tried reconfiguring xserver-xorg via 'sudo dpkg-reconfigure -phigh xserver-xorg' and I've tried reconfiguring all packages via 'sudo dpkg-reconfigure -phigh -a' but to no avail.

Any help or guidance would be greatly appreciated,

Cheers.

---

### Post by mörgæs on 2011-04-28
My advice is to stay with 10.10 at least a couple of months. Myself I am sticking to 10.10 until the last day of support.

---

### Post by Hedgehog1 on 2011-04-28
From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```


***The Hedge***

:KS

---

### Post by Timsworth on 2011-04-28
I tried unity --reset and I got something along the lines of the following as a result:

WARNING: no DISPLAY variable set, setting it to :0
Traceback (most recent call last):
  File "usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "usr/bin/unity", line 74, in reset_unity_compiz_profile
    except GError, e:
NameError : global name 'GError' is not defined

---

### Post by mc4man on 2011-04-28
There are several plugins that when you try to enable or disable will unset all the enabled plugins - you happened upon one of them
You actually could have slowly reenabled all that were needed or wanted even though compiz had crashed

Try running these 2 commands to reset your compiz profiles back to the defaults.
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1
```

If that works out then if still desiring to switch from wall to cube/rotate  there are better ways than the method you tried, let me know
(use rotate/cube here instead of wall, no issues

---

### Post by Timsworth on 2011-04-28
> **mc4man said:**
> There are several plugins that when you try to enable or disable will unset all the enabled plugins - you happened upon one of them
You actually could have slowly reenabled all that were needed or wanted even though compiz had crashed

Try running these 2 commands to reset your compiz profiles back to the defaults.
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1
```

If that works out then if still desiring to switch from wall to cube/rotate  there are better ways than the method you tried, let me know
(use rotate/cube here instead of wall, no issues

The code executes without problem but I still have the same issue.

---

### Post by Timsworth on 2011-04-29
bump

---

### Post by damianpeterson on 2011-04-29
Thank you Hedge, that worked for me and managed to unmess what I'd messed up.

---

### Post by Timsworth on 2011-04-30
continued bump

---

