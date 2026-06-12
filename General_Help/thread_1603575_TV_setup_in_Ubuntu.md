---
title: "TV setup in Ubuntu"
date: 2010-10-22
forum: General Help
---

### Post by gramsyn on 2010-10-22
I have plugged an LG TV to my laptop using RGB cable. However Ubuntu recognise it as another brand. The result is that the image of TV is shown redish. How can I fix this? How can I properly install the TV?

Thanks everybody in advance for the help

---

### Post by efflandt on 2010-10-23
What video card do you have.  Reddish sounds like maybe an issue some people have had in 10.10 with some nvidia cards.

I am currently using a 32" LG HDTV as a monitor connected DVI to HDMI with my desktop (nVidia GT 220 w/nvidia 260.19.06 driver in 64-bit 10.10).  No problems there.

I have connected assorted laptops to it using VGA (15-pin RGB) with Intel and older ATI video using default drivers in 10.04 without any issues.

I just tried a laptop with Intel video in 64-bit 10.10 using VGA to LG HDTV with no issues.  Colors are fine.  I just need to figure out how to shift the 1920x1080 image slightly to the left by adjusting the modeline in a script with xrandr commands.  I use that script to switch to 1080p and turn my laptop display off, because when the laptop boots with the external display connected, X sets both my 1280x800 laptop display and the HDTV to 1024x768.

---

### Post by gramsyn on 2010-10-23
I don't know what video card I have. How can I identify it? I can find no such thing as hardware manager in Ubuntu.

Any ideas about how can I solve this problem? Maybe update the driver of video card or TV? I have no HDMI slot in my PC, so I have to use RGB

Thanks a lot

---

