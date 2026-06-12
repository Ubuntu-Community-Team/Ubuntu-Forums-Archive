---
title: "TV for a monitor"
date: 2009-10-24
forum: General Help
---

### Post by wlraider70 on 2009-10-24
I'm trying out my TV as monitor. 
It does display, but it cannot recognize the display type. it says unknown.
there are very few size option 1 wide screen and 2 standard. even worse the widescreen option doesn't work right,
its a wide TV and the top and bottom don't show up.



so is there anything i can do to improve the performance.
the tv is Polaroid.

---

### Post by Dark_Stang on 2009-10-24
Do you know what resolutions the TV can run at?

---

### Post by wlraider70 on 2009-10-24
1080i widescreen

would that be 1440x1080?

i can do "1280 x 720 (16:9)

---

### Post by dandnsmith on 2009-10-24
I've had some problems with using full width when using a 12:9 TV/Monitor via a VGA socket, but they don't appear the same when using DVI (same graphics card).

---

### Post by wlraider70 on 2009-10-24
I don't have DVI on either end. I am using VGA

however did simply going to DVI help you?

---

### Post by dandnsmith on 2009-10-24
I really don't know. I mainly discovered it because I have 2 PC's and the TV/monitor is switched between them. Interestingly, the same applies for WindowsXP (cannot use the full width on VGA).
I did wonder about the info that can be got about the display (some acronym reminiscent of EISA), for which I've seen postings about displays which don't give good feedback, so the automatic setting (used these days by Ubuntu) doesn't work. I have tried some playing about with manual setting via the xorg config file, but without much success.
The other thing I discovered about such setups was that using a KVM switch with VGA doesn't work (I think it's the same business with automatic settings not getting transmitted properly)

---

### Post by JBAlaska on 2009-10-24
You should be able to use 1920×1080, but since I have a progressive 1080, I may be wrong, If that does not work try 720p res 1280×720. Your graphics card will also have to support these resolutions and you may have an "OverScan" option in the Card's driver TV setup page to adjust your full screen mode.

---

### Post by wlraider70 on 2009-10-25
I don't THINK it should matter if its I or P. 
However i do have a cheap on board vga.
I ordered something new on ebay i hoping that will open up new resolutions. 

Regardless, i should not have the failure of the sizing. In widescreen i cant see either top menu or bottom menu.

---

### Post by Dark_Stang on 2009-10-25
1920 x 1080 should be the proper resolution for 1080p. 1440 x 1080 is for 1080i. I know it's a little weird but I don't feel like explaining it. Instead I will post 2 links.
[http://en.wikipedia.org/wiki/1080i](http://en.wikipedia.org/wiki/1080i)
[http://en.wikipedia.org/wiki/1080p](http://en.wikipedia.org/wiki/1080p)

The cable shouldn't matter much for resolution. Although for the image quality, here is a little math problem based on my understanding of the subject.
Display Port > HDMI > DVI > VGA > Serial > Hopes and dreams

Are you able to manually set the display settings for 1440 x 1080 and 60hz?

---

### Post by wlraider70 on 2009-10-25
thanks for the P and I info.

the best res. I can do is "1280 x 720 (16:9) 75 hrz, (no more or less on the hrz)

It appears that my computer doesn't recognize the 1080, it seems reasonable that my vid card doesn't support that.

---

### Post by Dark_Stang on 2009-10-25
> **wlraider70 said:**
> thanks for the P and I info.

the best res. I can do is "1280 x 720 (16:9) 75 hrz, (no more or less on the hrz)

It appears that my computer doesn't recognize the 1080, it seems reasonable that my vid card doesn't support that.
It is possible that your video card may not be able to push that high of a resolution. On the bright side, if this is a desktop you can pick up a fairly inexpensive video card that will if you're looking to do this as a long term solution.

---

### Post by cariboo on 2009-10-25
A lot of wide screen TV's have a native resolution of 1360X768 or there abouts. My TV is capable of doing 720i/p and 1080i, when my computer is connected to the VGA port, the best I can get is 1360X768. This is with Windows or Linux. I haven't tried the hdmi inputs yet though.

---

