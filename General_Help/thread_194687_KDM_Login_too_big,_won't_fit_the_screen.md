---
title: "KDM Login too big, won't fit the screen"
date: 2006-06-11
forum: General Help
---

### Post by Jucato on 2006-06-11
screwed up again! This time, I don't know where I went wrong.

As I was going about adding and removing some KDM Themes, I ended up with a KDM Login that was too big. No, the resolution wasn't too big. What I mean is that the not everything fits into one the whole screen anymore. Usually, the box where I would type in the username and password is at the middle, and some icons are at the bottom for the Sessions and System options. Now, the login box is off to the right, and half of the icons go below the limit of the screen. And the funny thing is, if I move my mouse to the limits of the screen (down, right, up, left), the login screen adjusts so that I could still reach the icons. 

Hope I'm being clear on that one. It's kinda hard to describe, and I can't seem to get screenshots to explain.

But it's still working in the same resolution (1024x768) except that the layout/placement of elements seems to be following a larger resolution (1280x1024 maybe?).

I'd appreciate any help. Thanks!

---

### Post by georgevn on 2006-06-12
i also have the same problem, my resolution is 1152*864 but the login screen seems to be 1280*1024.

---

### Post by Jucato on 2006-06-13
Hi! I was able to find the solution to my own problem :D
There's a line in my xorg.conf that looks like this:
> Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
  Monitor "AOC Spectrum"
  DefaultDepth 24
  SubSection "Display"
    depth 24
   **virtual 1024 768**
    modes "1024x768@60" "800x600@60" "800x600@72" "800x600@56" "640x480@72" "640x480@60"
  EndSubSection
EndSection

When I was having the login resolution trouble, that line was set to a higher resolution than what my monitor can support. Changing that to the right resolution solved it. I also deleted any reference to resolution higher than 1024x768 in my xorg.conf.

Hope that would help solve your problem, too.

---

### Post by georgevn on 2006-06-14
> 
Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
  Monitor "PHILIPS 107T"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    **virtual 1152 864**
    modes "1152x864@75" "1152x768@54" "1024x768@43" "1280x854" "1024x768@60" "1280x960@60" "1024x768@70" "1280x1024@60" "1024x768@75" "1400x1050@60" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection


Thank for your hint, that line initially was not in my file, so i add it in, and now my problem is solved

---

