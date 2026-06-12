---
title: "TwinView and Fullscreen Games"
date: 2009-06-29
forum: General Help
---

### Post by Jinx-Wolf on 2009-06-29
I’ve been messing around with Dual Monitor options the past few days. I have to say I’m impressed at the improvement over the past few years, but it still needs a lot of work...

I’m currently trying to get a few games to run fullscreen on a single monitor, without it overlapping.
I would even be fine with running it in window mode, however the resolution options are limited to the current resolution of my two monitors put together.

I’ve looked around and found several solutions, but none of which work for me (mostly because my xorg.conf file looks slightly different from the solutions, and I can’t seem to get it to work)

Here’s the bottom of my xorg.conf:

```

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "1"
Option "TwinViewXineramaInfoOrder" "CRT-0"
Option "metamodes" "CRT-0: 1920x1080 +1280+0, CRT-1: 1280x1024 +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "CRT-1: 1280x1024 +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

```

I either need to be able to make it full screen on my 1920x1080 screen, or have more resolution options in the game so I can make it window mode without it still stretching across both screens.

I’ve finally given up and am asking for help.

---

### Post by t4thfavor on 2009-06-30
same boat, I just set my nvidia settings back to single monitor while gaming. Some games do it right, others dont.

---

