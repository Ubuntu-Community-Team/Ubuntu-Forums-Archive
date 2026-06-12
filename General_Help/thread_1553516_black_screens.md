---
title: "black screens"
date: 2010-08-15
forum: General Help
---

### Post by Someone uk on 2010-08-15
when i run some full screen applications i sometimes have this problem where the sound becomes a 5 second loop and the screen goes blank
how could i go about diagnosing and fixing this problem?

---

### Post by Rubi1200 on 2010-08-15
Hi,
couple of things:

1. what are your computer specs. such as RAM and graphics card?

2. what applications are you running that do this?

Go to Applications > Accessories > Terminal and run the program from there.

e.g. ```
firefox
``` Then do what ever you were doing and try and recreate the problem.

If any error messages come up you will see them in the terminal and can then either try and figure out what is going on or ask here again.

Hope this helps.

---

### Post by Someone uk on 2010-08-16
1. MSI GX700 laptop Core 2 duo T7500 4GB ram 512mb Geforce 8600m

2. just about everything, fullscreen video somtimes (only when ran fullscreen), native games (doom3), games in wine (mainly guild wars)

ok i just ran this and ran into the same problem whist playing doom3:```
doom3 >> doom3log.txt
```

---

### Post by Someone uk on 2010-08-18
anyone have any ideas?
due to the nature of the problem (forcing me to reboot) i can't use the terminal window to much avail and i find that sending the output to a text file delivers nothings out of the ordinary

any logs worth viewing (idk what most of them do)

---

### Post by Someone uk on 2010-08-22
nothing?
i have found i sometimes get them spontaneously

any ideas?

---

### Post by Someone uk on 2010-09-01
i installed cario dock and i somtimes get this problem when i boot ubuntu
could this be my graphics card drivers?

i have an nvidia 8600m GT 512mb driver version 172.14.22 (64bit)

i also found this in the Xorg.0.log, not sure if it's relevant
> Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3258]
1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a2ad4]
2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x47ceb4]
3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f82404e9000+0x53cf) [0x7f82404ee3cf]
4: /usr/bin/X (0x400000+0x6fcb7) [0x46fcb7]
5: /usr/bin/X (0x400000+0x11d1d3) [0x51d1d3]
6: /lib/libpthread.so.0 (0x7f8255ba8000+0xf8f0) [0x7f8255bb78f0]
7: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f8251533000+0x3c3bdb) [0x7f82518f6bdb]
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

---

### Post by Someone uk on 2010-09-08
update: tried a fresh install of ubuntu,
i have tried drivers 173, 195 and even downloaded and even installed 256.53 from the nvidia website
the problem happens spontainously but happens mostly when i try to run 3d games
i have 64 bit ubuntu
and i have no idea what other helpful infomation i can give

---

### Post by Someone uk on 2010-09-10
ok i think i have found the problem but have no idea on how to fix it
this is what i found in xorg.1.log
> 
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.
anyone actually reading this thread?

---

