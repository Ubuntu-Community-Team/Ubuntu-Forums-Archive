---
title: "High CPU usage streaming video with Firefox"
date: 2012-04-30
forum: General Help
---

### Post by caffeinated blood on 2012-04-30
Firefox is running at an average 63% CPU when streaming video(YouTube). I have an nVidia graphics card and I'm not sure if this is the cause(GPU memory and/or proprietary driver) or something else. I don't see anything in the nVidia Control Panel settings I could adjust to help.

Reading previous threads on this issue I have not found a solution(disabled add-ons, created a default user in Firefox folder, etc...). Anyone else still experiencing this issue? By the way, I'm currently running Ubuntu 12.04.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
use flash video replacer (a firefox addon) and have it open a standalone player THIS WILL GET YOU HARDWARE ACCELERATION

high cpu usage is just what adobe flash does

you can also pause **most** (as in not all) videos and run this command (i suggest scrolling down hte page so the flash video is no longer on the visible part of the page)
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```

---

### Post by CosmoBeep on 2012-04-30
yeah i just went to youtube  and played a video and im getting 40-60 cpu usage.

---

### Post by brainwash on 2012-05-01
Hardware acceleration has been disabled in recent Flash Player versions for Linux.

So we are force to use software video rendering/decoding. :/

---

### Post by squilookle on 2012-05-01
Same issue in Chromium. It's annoying.

---

### Post by caffeinated blood on 2012-05-01
Okay, I added the 'FlashVideoReplacer' Firefox add-on and my CPU usage while streaming has been cut in half(down to an average 31%/Firefox). This still seems rather high usage doesn't it?

---

### Post by CosmoBeep on 2012-05-01
31% is still a bit high but its a lot better then 60%.I get  around 18-35% usage in windows.

---

### Post by SeijiSensei on 2012-05-01
> **brainwash said:**
> Hardware acceleration has been disabled in recent Flash Player versions for Linux.

So we are force to use software video rendering/decoding. :/

Is this to fix the [problem with blue faces]("https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091") on services that use Stage Video like YouTube?  I disabled HW acceleration manually (right-click on a video, then choose Settings).  Is it the case that it's now disabled by default as well?

---

### Post by brainwash on 2012-05-01
> **SeijiSensei said:**
> Is this to fix the [problem with blue faces]("https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091") on services that use Stage Video like YouTube?  I disabled HW acceleration manually (right-click on a video, then choose Settings).  Is it the case that it's now disabled by default as well?

The proprietary NVIDIA driver does offer hardware acceleration for Flash videos via the VDPAU API (libvdpau1, NVIDIA only). Not sure, why Adobe still supports this solution, most likely because it is "stable".

 **caffeinated blood**, did you test the various video output devices? I'm using mplayer to play  the Flash videos on YouTube and other sites. VA-API tends to be  unstable on my system and VDPAU is not supported (AMD/ATI GPU). OpenGL  works ok, but the CPU usage is kinda high. X11 does not offer scaling of  videos, so I'm using Xv (hardware scaling).

---

### Post by caffeinated blood on 2012-05-02
In reply to '**brainwash**': I just tried a youtube video on mplayer. My CPU usage dropped down to 20-30%(totem/xorg), but staying mostly in the low end of this percentage. At the moment this seems to be the way to go?

---

