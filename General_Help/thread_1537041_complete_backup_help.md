---
title: "complete backup help?????"
date: 2010-07-23
forum: General Help
---

### Post by owners4life5 on 2010-07-23
hello,

i have what appears to be a very serious problem....

so i think two days ago, my lucid did updates and i reboot. when i.m starting up, i get a message about low graphics mode, fiddle with it a bit, and then look it up. (see more here: [http://ubuntuforums.org/showthread.php?t=1506463](http://ubuntuforums.org/showthread.php?t=1506463) )

anyhow, the problem is, is that i don.t know what to do. so my diagnosis is that i should backup all of my files, do a fresh install of lucid, then re-install all of my files again, since for some reason, it won.t boot now. 

i guess what i.m asking is this:

pertaining to my earlier problem, what is your suggestion on what i should do, and if it is to backup and do a fresh install, how do i do this?

anyhow, it.s been a long day and night and i.m going to get some very good rest this evening. it.s been a stressful day for this fourteen-year-old and linux has taught him many things today.... possibly too much.
so hopefully when i wake up, i see a reply, and i.ll go from there.

any help is greatly appreciated.
thank you very much

---

### Post by owners4life5 on 2010-07-23
boomp

---

### Post by linux18 on 2010-07-23
if your using the nvidia driver:


- boot into recovery mode 
- drop to a root prompt 
- type " telinit 3" and login
- type "nvidia-xconfig"
- then reboot, you should be good to go

---

### Post by owners4life5 on 2010-07-23
didn.t work... command not found

---

### Post by cbraxton on 2010-07-23
> **owners4life5 said:**
> didn.t work... command not found

If you have an /etc/X11/xorg.conf file you might try renaming it to something else and rebooting so that X will autoconfigure itself. They you can work on installing proprietary drivers, fiddling with resolution, etc. if needed.

---

### Post by owners4life5 on 2010-07-23
i tried... no go. i dont think 10.04 has one...

---

### Post by linux18 on 2010-07-23
I bump this thread

---

### Post by confused57 on 2010-07-23
> **owners4life5 said:**
> hello,

i have what appears to be a very serious problem....

so i think two days ago, my lucid did updates and i reboot. when i.m starting up, i get a message about low graphics mode, fiddle with it a bit, and then look it up. (see more here: [http://ubuntuforums.org/showthread.php?t=1506463](http://ubuntuforums.org/showthread.php?t=1506463) )

anyhow, the problem is, is that i don.t know what to do. so my diagnosis is that i should backup all of my files, do a fresh install of lucid, then re-install all of my files again, since for some reason, it won.t boot now. 

i guess what i.m asking is this:

pertaining to my earlier problem, what is your suggestion on what i should do, and if it is to backup and do a fresh install, how do i do this?

anyhow, it.s been a long day and night and i.m going to get some very good rest this evening. it.s been a stressful day for this fourteen-year-old and linux has taught him many things today.... possibly too much.
so hopefully when i wake up, i see a reply, and i.ll go from there.

any help is greatly appreciated.
thank you very much
I saw in your other thread that you have a Dell Mini 9, which may have gma500 graphics. You could see by opening a terminal & running:
```
lspci
```

I found this link that may be of help, if you have gma500 graphics:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

You'd need to boot into Ubuntu using "low graphics mode just for this session".  I don't really know if this is your problem, but might be worth a try?

Added:  Here's a post by oldfred that may be of interest:
[http://ubuntuforums.org/showpost.php?p=9586925&postcount=7](http://ubuntuforums.org/showpost.php?p=9586925&postcount=7)

---

### Post by owners4life5 on 2010-07-24
well i don.t see anything ab gma500... and i.ve already tried the one-session low graphics option... but no dice

---

### Post by confused57 on 2010-07-24
> **owners4life5 said:**
> well i don.t see anything ab gma500... and i.ve already tried the one-session low graphics option... but no dice
Which VGA graphics chip does it show?:
```
lspci | grep VGA
```

---

### Post by owners4life5 on 2010-07-24
> **confused57 said:**
> Which VGA graphics chip does it show?:
```
lspci | grep VGA
```

from recovery console:

```
root@brian-laptop:~# lspci | grep VGA
00:02.0 [COLOR="Red"]VGA [COLOR="Black"]compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)[/COLOR][/COLOR]
```

---

### Post by confused57 on 2010-07-24
Can you boot successfully into an older kernel and can you boot into low graphics mode, using the latest kernel?

If you decide to do a reinstall, here's a guide for what & how to back up your current install:
[http://ubuntuforums.org/showthread.php?t=701386](http://ubuntuforums.org/showthread.php?t=701386)

---

### Post by owners4life5 on 2010-10-06
i got this figured out. 

i just reinstalled, after completely backing up everything. so it.s all good.

marking as solved.

---

