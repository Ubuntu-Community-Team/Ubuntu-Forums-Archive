---
title: "kiba-dock segmentation fault"
date: 2009-07-20
forum: General Help
---

### Post by serious7 on 2009-07-20
when I run kiba-dock from terminal and try to add a seperator it just closes and the terminal reads this:

---------------------------
nicky@nicky-desktop:~$ kiba-dock
Segmentation fault
---------------------------------

I'm using 9.04 64-bit ubuntu. I followed this guide [http://ubuntuforums.org/showthread.php?p=7647282#post7647282](http://ubuntuforums.org/showthread.php?p=7647282#post7647282) but I installed everything in /usr/local/lib/ directory because I got this error just following the guide blatantly:

----------------------------------
nicky@nicky-desktop:~$ kiba-dock

** (kiba-dock:24874): WARNING **: Error (main.c @ line 252):
Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.
-------------------------------------

I deleted everything and installed it in that directory and I am finally able to START kiba-dock. But adding a seperator causes it to crash or shut down I think? Help i'm a noob in linux.

---

### Post by MasterPoulos89 on 2009-07-20
This thread should help you properly install the kiba-dock: 

[http://ubuntuforums.org/showthread.php?t=1203969&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=1203969&highlight=kiba-dock)

You should probably uninstall it first.

When Its done you will see kiba-dock in Applications\Accessories\Kiba-Dock

The guide you used seems to be correct so if it still doesn't work I don't know what to tell you......Maybe someone else does.

---

