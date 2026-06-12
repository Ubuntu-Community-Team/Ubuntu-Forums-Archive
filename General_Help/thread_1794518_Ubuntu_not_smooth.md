---
title: "Ubuntu not smooth?"
date: 2011-07-01
forum: General Help
---

### Post by lwfx on 2011-07-01
First off I love Ubuntu and have been using it for some time, but it has always really bugged me how not smooth things are. I am not sure if I am doing something wrong or not, but compared to any windows machine it just doesn't seem as fluid. I have brand new hardware, have tested the os on several machines, tested nvidia and ati, tried many different drivers and still when dragging windows around I see lots of tearing and rugged movement.  Even simple things like the initial Ubuntu login screen where it 'fades' in, shows maybe 4-5 shades of gray and just doesnt feel smooth.  Using Inkscape is a tear fest and everything feels delayed.   Is this just how it is or do you think I'm screwing something up?

---

### Post by coffeecat on 2011-07-01
> **lwfx said:**
> I have brand new hardware, have tested the os on several machines, tested nvidia and ati, tried many different drivers and still when dragging windows around I see lots of tearing and rugged movement.

Welcome to the forum!

I don't think you have done anything wrong. I think you've been very unlucky with your choice of graphics cards. The only time I have ever seen anything like this was when trying out very old GPUs, or a few releases ago, trying the proprietary fglrx driver with a then newish but modest ATI graphics chipset.

You usually only see these sort of artefacts when using old GPUs or very new ones where the drivers do not yet properly support the new chipset. Specifically, which cards did you see this with and which drivers did you try, the open-source or proprietary, or both?

---

### Post by cottfcfan on 2011-07-01
Assuming your using 11.04. I found unticking "sync to vblank" in CCSM /Open GL. made things a lot smoother.

---

### Post by srisharan on 2011-07-01
I has kind of the same problem.When dragging windows the motion is not fluid.I think it has to do with the graphic cards not being supported properly(mine being Nvidia Geforce 105).I use maverick by the way.Any one has a fix like the above natty one for maverick?

---

