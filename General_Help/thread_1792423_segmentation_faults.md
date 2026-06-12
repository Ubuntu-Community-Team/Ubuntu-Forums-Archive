---
title: "segmentation faults"
date: 2011-06-28
forum: General Help
---

### Post by nalle on 2011-06-28
I'm getting segmentation faults in just about all games. First I noticed this with wine when trying to run 3D games, then I tried games from the repos and it's the same. I figured it might have something to do with openGl. I'm running natty 64 bit, built in intel graphics card.

Compiz runs fine but unity doesn't. When I tried testing my 3d this is what I got:

```
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
Segmentation fault
```

but:
```
glxinfo | grep direct
direct rendering: Yes

```

My xorg.0.log says this:
```
...
Fatal server error:
[   598.935] xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call
...
```

 I have no idea how to fix this,any help would be appreciated :(

---

### Post by cbraxton on 2011-06-28
Check your hardware.

Just a few days ago I installed 11.04 on an Asus netbook. Installation went just fine, but shortly afterwards I found that I could not install or update anything as apt-get and dpkg were abending on segmentation faults.  After spending hours researching the issue, trying various fixes, and getting nowhere I finally decided to test system memory just in case. Memtest came up with numerous memory errors almost immediately. 

After replacement of the faulty hardware all is well.

---

### Post by nalle on 2011-07-02
I tried, but apparently there is a bug in memtest and I can't use it:
[https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839)

 I'll try to figure out a way to do the test from somewhere other then GRUB. Thanks for the tip!

---

### Post by nalle on 2011-07-02
Ok, I ran the test and there were no errors. I also checked the hard drive and it passed too. So it must be something else. Maybe I'll update my BIOS and see if that helps..

---

