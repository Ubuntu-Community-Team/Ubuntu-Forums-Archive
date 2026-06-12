---
title: "Compiz won't automatically load on startup"
date: 2009-11-15
forum: General Help
---

### Post by PoHandle on 2009-11-15
After upgrading to 9.10 Karmic Koala, Compiz-Fusion will not load automatically upon startup.  It seems to just start in Metacity.  I have fusion-icon running at startup.  I have tried several suggestions found on Google and this forum, but none have helped.
To clarify, I have:
[LIST]
[*]Added 'compiz --replace' to my startup apps
[*]Edited the 'fusion-icon' entry to read 'fusion-icon -f'
[*]Updated Compiz
[*]Reinstalled Compiz
[*]Tried to use a script on startup to 'sleep 30' before 'fusion-icon -f'
[*]Tried a gnome-wm tweak.  I forget where I found it, but will post if I remember.
[*]Reinstalled the NVidia driver
[*]Removed both 'fusion-icon' and 'compiz --replace' from startup apps
[/LIST]

The only way I can start Compiz is to select it from my fusion-icon menu.  The menu already has Compiz checked, but if I click it anyway, it loads Compiz.  I am running Ubuntu 9.10 AMD64, I have a GeForce 9500 GT with the NVidia driver 185.18.36, and my Compiz version is 0.8.4-0.  If you need more info, just tell me.

And if I missed the solution in my searches, feel free to kick me in the butt and call me stupid. ;)

---

### Post by pelish on 2009-11-16
Hi, I have the same problem, except that I did a fresh install (same version of Ubuntu, Compiz and Nvidia drivers)

On fresh install I played with compizconfig settings manager for about a weak and startup worked fine. Then I remembered the Icon and when I installed it Compiz won't autostart.

So i think that Compiz Fusion Icon caused the autostart problem

---

### Post by PoHandle on 2009-11-17
I found some clues.... Silly me, I should have checked dmesg earlier.

This is what dmesg | grap 'compiz' prints:
```
compiz.real[2572]: segfault at 8 ip 00007fa7ef129583 sp 00007fff1720fe30 error 4 in libGLcore.so.185.18.36[7fa7ee637000+dda000]

```

This is apparently a known bug ( [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425160](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425160) ) with the NVidia driver.  I will try another driver and see if I get anywhere with that..

---

### Post by PoHandle on 2009-11-17
I've upgraded my NVidia driver from 185 to 190 from the NVidia website and still do not have Compiz load at startup.  The dmesg compiz.real error has changed to reflect the new driver version.

```
[   46.860065] compiz.real[2610]: segfault at 8 ip 00007fce265318d6 sp 00007fff79d242c0 error 4 in libGLcore.so.190.42[7fce2598c000+ecb000]

```

So I'm a bit lost now.  Has anyone found a solution/workaround for this problem?

---

### Post by pelish on 2009-11-20
After reading through forum and trying different startup commands, this one autostarts Compiz at startup on my sistem:

```
sleep 5 && compiz --replace
```

---

### Post by PoHandle on 2009-11-23
Thank you pelish!  This solution worked for me as well.  I suppose the compiz script I made wasn't loading properly at startup.

---

