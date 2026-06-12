---
title: "Unable to use my Sanyo LCD's 1360x768 native resolution"
date: 2011-12-03
forum: General Help
---

### Post by wichid on 2011-12-03
Hi, I'm fairly new to Linux, my problem is this: I just got my wireless adapter working finally so I finally can use the internet in linux and update drivers and such to get everything working proper, so anyway I installed the nvidia drivers for my GT 430 and in Nvidia X Server Settings there is no option for 1360x768 resolution the closest i can get is 1280x720 which looks terrible on my tv. I've been searching online all day trying to figure this out and I either find similar unrelated issues or unsolved issues, So what do I need to do to get my screen resolution to 1360x768
Also another issue i have is with my sound, I get no sound output from my tv which is connected via HDMI, even when i run the sound test on it i dont hear anything but the main issue the the screen resolution, help would be greatly appreciated. :)

--Edit
Ive tried editing my xorg.conf file and everytime I try i get a blank screen also when i try to --addmode with xrandr i get: "failed to get size of gamma" what does that mean?

--Edit
I finally got 1360x768 added with xrandr but when i try to change the resolution with monito preferences i get a "could not set the configuration for CRTC 354" message, also if i try "xrandr --output default --mode 1360x768" i get:
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

---

### Post by wichid on 2011-12-04
60 views later I thought someone would try to help me by now... I've been doing nothing on my computer but trying to solve this problem for the past 2 days now, if anyone has any information that would help me please dont be shy

---

### Post by wichid on 2011-12-05
Ok, I finally Solved it. The problem is HDMI; HDMI is a TV-Out and therefore "Note: Modelines are ignored by NVIDIA, ATI and Intel drivers when using the TV-Out ability of these chipsets. Instead they use an internal and unmodifiable list of valid modes." applies to my output. I bought a VGA cable today and now I can get 1360x768 no problem.

---

