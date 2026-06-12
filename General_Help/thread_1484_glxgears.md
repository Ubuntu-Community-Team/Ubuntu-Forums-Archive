---
title: "glxgears"
date: 2004-10-21
forum: General Help
---

### Post by Neo40 on 2004-10-21
Hi,

When I type glxgears from a terminal, I get around 1000 FPS with a screen resolution 1024x768x85Hz. I have installed nvidia drivers. Is it normal or too small? My video card is a GeForce2 64 Mb and my cpu Athlon 1.2 Mhz.

Thanks.

---

### Post by pyx on 2004-10-21
Sounds pretty normal - i get about 1500 with an athlonXP 3.2 + GeForce4 64mb...

---

### Post by K6-III on 2004-10-21
I get about 6800fps with a GeforceFX 5900 Ultra and an Athlon 64 3200+ running on Ubuntu AMD64

---

### Post by jayclark on 2004-10-21
I do get low frames with glxgears in Ubuntu. Every other distro I would get 1000 fps-1500 fps. With Ubuntu its 500-700 fps. Dosen't seem to affect the games though.

---

### Post by flygmaskin on 2004-10-21
Hmm, when I tried glxgears in fedora core 2 I would get around 600fps. Now I get 300-12000 (changes all the time) fps on the same system (Athlon XP 2400+, 768mb ram, geforce fx 5200). Weird.

---

### Post by FLeiXiuS on 2004-10-21
I usually receive around 3000-4000.  I tested in Ubuntu and its around the same...

---

### Post by HungSquirrel on 2004-10-21
With a 1.4GHz Athlon OCed to 1.6GHz and a Radeon 9800 with fglrx I get 2500-3000 with the window up and 6000-7000 with it minimized.

---

### Post by kaput on 2004-10-27
First, glxgears scores are extremely unreliable. For those of you who have wildly varying scores, don't change the window size, make sure it's not covered by another app window (or minimized), and make sure your processor is mostly idle.

Also, if your score is lower in Ubuntu than other distros you've used, check your default screen depth. On my i852, X defaulted to 32-bit which causes a significantly "lower" score than 16-bit, though this type of test is obviously incredibly relative.

---

### Post by cseg on 2004-10-27
What's your screen depth?  This will impact your fps.

---

### Post by HiddenWolf on 2004-10-27
2997 - 7164 for me

Athlon 2200+
512mb RAM
ATI Radeon 9200se

Sounds like a terrible lot.

---

### Post by wazoo42 on 2004-11-01
I get about 4500 on a dual opteron 248 with 5700 ultra.  I was wondering though, why does my cpu0 usage jump to 100%?  Shouldn't all of this be handled by the vid card?  I didn't check glxgears before loading the nvidia driver so I don't have a comparison (it would have used software rendering with the nv driver, yes?).

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=wazoo42]I get about 4500 on a dual opteron 248 with 5700 ultra.  I was wondering though, why does my cpu0 usage jump to 100%?  Shouldn't all of this be handled by the vid card?  I didn't check glxgears before loading the nvidia driver so I don't have a comparison (it would have used software rendering with the nv driver, yes?).[/QUOTE]

Your FPS also depends on your Processor also.  If you have a faster processor your fps would obviously increase since the program your running can intake more data at once because your processor can handle it.

---

### Post by ynef on 2004-11-01
Besides checking that your nvidia module is running the way it's supposed to by checking the output of:

```
cat /proc/driver/nvidia/agp/card
cat /proc/driver/nvidia/agp/status
glxinfo | grep direct
```

...there's not much to do. If all of those are reporting expected values then you can safely assume that your card is running at its best performance. If not, it's time to start hunting for errors somewhere.

glxgears isn't the 3DMarks of linux... :wink:

---

### Post by wazoo42 on 2004-11-02
I just got my 6800gt today, now I get 12500fps in glxgears.   :-D

---

### Post by Hutch on 2004-11-02
1550 on an IBM Thinkpad T42 with a Radeon 9000 w/ 64MB. Default window size, system is running at 1024x768.

glxgears may not be a terribly accurate measure of video performance, but I appreciate everyone sharing the scores since I was wondering what some of the variations are.

---

### Post by markw on 2004-11-02
620, with integrated graphics and 256mb memory. Thats better than all other distros, partly because if have xf86 set up right.

---

### Post by mercurus on 2004-11-02
I get 890.6 fps ...

AMD Duron 700
384 MB SD RAM
GeForce 2 MX
nvidia-glx package installed and configured

Cheers
mercurus

---

### Post by ethana2 on 2008-01-09
> **ynef said:**
> glxgears isn't the 3DMarks of linux... :wink:

Requirements for linux graphical benchmark: OpenGL, GNU licensed, trivial to run, informative.

I say it fits the bill.  close all windows, see that CPU is idle and such.
Open a terminal, type glxgears.  Do not hit any keys, do not move the mouse.  Wait 30 seconds, switch back and hit control + c.  Look at the numbers.  The more constant they are, the better you did preventing interruptions.  A good number of the results should be within 1 fps of each other, depending on raw power.  On old cards, this is the case.  This number may not tell you everything, but it tells you a lot more than nothing.

If it isn't 'the 3DMarks of linux', please, tell us what is.

---

