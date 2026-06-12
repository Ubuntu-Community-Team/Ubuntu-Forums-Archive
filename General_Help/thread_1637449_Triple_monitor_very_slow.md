---
title: "Triple monitor very slow"
date: 2010-12-04
forum: General Help
---

### Post by oxan on 2010-12-04
Hi,

I'm running Kubuntu 10.04 with a triple monitor setup on two videocards: one video card (nVidia 9500 GT) runs two screens, while the other one (nVidia GT 210) runs a single screen. I use Xinerama in the X11 configuration, see [xorg.conf]("http://pastebin.com/vQ2cTffg"). This is working great, except that after an hour (someimes two, sometimes directly) everything gets really slow: when I move my mouse to an icon on the desktop, it highlights after a second or two (not directly), when I move a window it leaves a trail of windows behind it, when I close a window the desktop shows after a second or two, when I type text in Konsole it appears after a really short but annoying delay, etc. When I log out and restart the X11 server everything is fast again, but after an hour it gets slow again. 

The CPU usage is ~10% according to the desktop widget (PhenomII X4 965, so that should be fast enough), so that shouldn't be the problem. However, when looking with htop, X is always using 20-50% of the CPU, which is a bit high. 

When I place back my old xorg.conf (with TwinView over 2 monitors and the third one not enabled), everything is working smoothly, even after 5 hours. In Windows the monitors are also working fine.

Anybody any idea how to solve this?

---

### Post by handheld-penguin on 2010-12-27
I'm having a similar issue, everything is just quite slow even from startup. I'm running a quad core with 3 monitors...CPU usage is only around 33% so I'm not sure why X is so slow.

---

