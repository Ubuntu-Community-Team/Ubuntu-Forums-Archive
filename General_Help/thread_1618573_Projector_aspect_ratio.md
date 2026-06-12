---
title: "Projector aspect ratio"
date: 2010-11-10
forum: General Help
---

### Post by superzanti on 2010-11-10
I have a projector, projecting an image from my computer onto a screen. I thought the projector had a horizontal size adjustment feature, but it doesn't. The problem is, the sides of the image hang over the edge of the screen. I want to output an image with black bars on the sides, so that the image fits on the screen. Is this possible?

Whenever I try to adjust the resolution of the projector, the projector fixes it. The native resolution is 1600x1200. When I output 1200x1200, it stretches that image to fit it's full projection area.

---

### Post by superzanti on 2010-11-11
So, If the projector is projecting the way I want it to, It would look like this:

XOOOOX
XOOOOX
XOOOOX
XOOOOX

X's being the black space, and O's being the projected space.

---

### Post by superzanti on 2010-11-12
SOLVED!

Alright, this took me about 3 hours to figure out, sadly.

If you open a terminal and type:
```
gtf width height refreshrate
```
If that doesn't work try:
```
cvt width height
```

It will return a result. In my case, I used 1024x768 (later I'll use 1600x1200) because that's the native resolution for my projector, at 60 hertz.
```
  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

```
You'll copy everything after Modeline.

Now, in terminal, open xorg.conf as root

Under the "monitor" or "device" section, whichever you want to add a letterbox, paste:
```
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
```
or whatever yours was.

You can check online to see what all of these values mean, It took me a while. The second number after "1024x768_60.00" is the one I changed to 786. I did this because I wanted a 1:1 ratio 786x786. The two numbers after that shift the horizontal position. Adding 100 to each of these will shift the image 100 pixels to the right (further away from the left). Once you have the values you want, save the xorg.conf, and restart the x-server. Now you should be able to select the 768x768 resolution, and have the letterbox!

---

