---
title: "video playback does not work properly on totem (movie player) neither VLC"
date: 2010-07-12
forum: General Help
---

### Post by jm.mico on 2010-07-12
Hello community,

Since I upgraded to Lucid Lynx, playing videos with the default player do not work properly. I only see the content while moving the window, or in full screen mode, and in both ways, the picture is distorsioned and with strange colors.

Playing it with VLC does work properly ONLY IF I change the video output module to something different as default (X11 works, openGL also) but Linux Framebuffer does not.

The question:
Is there a way to change the "default" video mode that Totem (or Kaffeine) use?? I have not found anything on the net with this exact problem.

THanks ! :KS

Jm

---

### Post by jm.mico on 2010-08-02
hallo world?

I can not believe nobody else has this issue #?

How can someone change the default video engine for totem?????

Come on ...

Thnks,

Jm

---

### Post by no2498 on 2010-08-03
for the color in totem click edit preferences display  move some of the sliders then try the reset to defaults 

hope this helps some

smplayer is good for me if totem dont play well
put it in a terminal it tells you how to install it

---

### Post by WorMzy on 2010-08-03
You can change the default video output by running gstreamer-properties. Not sure that it'll help though, the only video problem I've encountered was solved by installing updated propriety graphics drivers through Hardware Drivers.

---

### Post by jm.mico on 2010-08-04
> **WorMzy said:**
> You can change the default video output by running gstreamer-properties. 

YESSSSSSSSS:D. That helped. I had to select in the video output, "X Window System (No Xv)", instead of "Autodetect". Now it works :)

If I select "X Window System ((X11/XShm/Xv)" it does not work (same behaviour as I described at my first post).

Do not know however why is this, my system has the intel GMA with i915 driver, and sometimes get the bug GPU Processor Hung, but I think that is another issue as to this one.

SOLVED!

---

### Post by jm.mico on 2010-08-04
By the way, thank you both for your answers!

People like you is what make "the linux" difference ;)

Jm

---

### Post by MikeFishcake on 2010-08-26
> **WorMzy said:**
> You can change the default video output by running gstreamer-properties. Not sure that it'll help though, the only video problem I've encountered was solved by installing updated propriety graphics drivers through Hardware Drivers.

I've been using Ubuntu for about 3 days now* and was having trouble playing my videos too - PC rebooting and was GPU hung message in the syslog (i didn't even know what/where syslog was until about 30 minutes ago). It's a combination of this thread and a few others that helped me to fix the problem.

You're all awesome. Thanks :)

 (* 3rd attempt at running Linux in 2 years - gave up and ran away screaming previously. 10.04 has totally changed my mind though :))

---

