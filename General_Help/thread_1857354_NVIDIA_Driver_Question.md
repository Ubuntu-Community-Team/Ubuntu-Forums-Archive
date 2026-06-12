---
title: "NVIDIA Driver Question"
date: 2011-10-10
forum: General Help
---

### Post by nankura on 2011-10-10
hey guys

Nvidia just stabilised recently there 285.05.09 drivers

Now this is mostly a curiousity question about a patch note

"Improved performance of the RENDER extension on Fermi-based GPUs."

Now im curious what this mean's and i wanted to ask about it. i have a nice nvidia GTX 460 1GB which im pretty sure is fermi. and for the past year ive had problems with any compositing manager that uses XRENDER

Like on XFCE i suffered screen tearing, and found out its a known bug with fermi nvidia gpu's because there inbuilt compositing manager doesnt call on opengl - this was from there bug report website

And doesnt call on opengl/vsync

The best compositing manager i ever used was the inbuilt E17 one, no problems, no screen tearing etc

But anything else. just bugs after bugs. compiz ofc works with the vsync fix. but causes resource issues and full screen bugs

So i was basically wondering if that patch note is anything to do with the nvidia compositing issue

---

### Post by LowSky on 2011-10-10
my GTX 460 works fine, no tearing issues here.

using the 280 driver currently

---

### Post by nankura on 2011-10-10
LowSky, could you do me a big favour mate and post your xorg config or pm me it.

Id love to match my XORG Config with another 460 GTX user. and see if this whole time i might have been missing something small

---

