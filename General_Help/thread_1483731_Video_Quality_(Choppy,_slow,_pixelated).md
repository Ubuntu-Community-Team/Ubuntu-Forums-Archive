---
title: "Video Quality (Choppy, slow, pixelated)"
date: 2010-05-14
forum: General Help
---

### Post by HolidayQueen on 2010-05-14
On my 3yr old tower, with a Radeon Xpress 200 card. I had to remove Ubuntu and install Crunchbang to get it to play video properly. (and trust me, i tried everything i could think of before proceeding with this option).

In Ubuntu, the video lags, gets choppy, and when i crop TV format videos to my screen's aspect ratio, a diagonal line flickers on the screen.

it's just gnawing at me. There isn't a huge diference between crunchbang which is based on debian, and ubuntu which is based on debian. So why does CB give me much better playback?

Comparing Xorg version numbers,

Crunchbang Statler:
xorg 1:7.5+6
xserver-xorg-video-ati 1:6.12.6-1
xserver-xorg-video-radeon 1:6.12.6-1

Ubuntu Lucid:
xorg 1:7.5+5
xserver-xorg-video-ati 1:6.13.0-1
xserver-xorg-video-radeon 1:6.13.0-1

The diferences here are not huge.

So what am i missing? what else could be different?

I like both distros, but installing certain software in CB is immensely more dificult and i miss PPA's lol.

---

### Post by NightwishFan on 2010-05-14
Press alt+f2 and run this command:
```
gstreamer-properties
```

You should get a dialog, go to the video section and change it from xv to x11. If that does not work change it back to xv.

---

### Post by ubunterooster on 2010-05-14
Did you have the proper drivers: system>administration>hardware drivers

---

### Post by HolidayQueen on 2010-05-14
> **NightwishFan said:**
> Press alt+f2 and run this command:
```
gstreamer-properties
```

You should get a dialog, go to the video section and change it from xv to x11. If that does not work change it back to xv.

Right now my tower has CB installed. However when Ubuntu was on, i tried every single output in VLC, the best was XV, but still had the diagonal line flicker.

> **ubunterooster said:**
> Did you have the proper drivers: system>administration>hardware drivers

My ati card is too old to still be supported by proprietary drivers.

---

