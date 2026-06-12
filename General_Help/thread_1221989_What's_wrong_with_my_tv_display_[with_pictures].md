---
title: "What's wrong with my tv display? [with pictures]"
date: 2009-07-24
forum: General Help
---

### Post by GammaPoint on 2009-07-24
I've had this problem for months now and I'm not sure what the cause of it is. As you can see from the pictures my TV does not show the entire output of the videocard it seems (I have a black bar on the right side). This wasn't a problem when I was using Ubuntu 8.04 but has been an issue since then. Maybe it's a new nvidia driver or something?  Any suggestions would be greatly appreciated! 


Pictures here:

[Picture 1]("http://1.bp.blogspot.com/_-DwhYk8wmgw/SmnXUt_7NNI/AAAAAAAABdc/QtbJ7WClHDc/s1600-h/DSC02360.JPG") (full view of TV)
[Picture 2]("http://4.bp.blogspot.com/_-DwhYk8wmgw/SmnXcrNi_aI/AAAAAAAABdk/gOMFOfoMvbQ/s1600-h/DSC02361.JPG") (closeup of the right hand side)



I'm using the most recent version of Ubuntu and have a separate X session for the TV output.

---

### Post by ohzopants on 2009-07-24
Are you sure that you're using the TV's native resolution and refresh rate for that X screen.  I've had similar problems when those two values weren't correct.

The manual for your TV (or some googling) should tell you what the right resolution and refresh rate are.

---

### Post by GammaPoint on 2009-07-24
> **ohzopants said:**
> Are you sure that you're using the TV's native resolution and refresh rate for that X screen.

The TV is an LG 37LG30 and the resolution is 1366x768 the specs say online and my nvidia resolution is set to'auto', which it looks like it detects it to be 1360x768 so I guess that's right? Or should the numbers be exactly the same?

As for the refresh rate, I didn't see that in the nvidia-settings at all.

---

### Post by GammaPoint on 2009-07-24
Okay I fixed it. The problem was the nvidia driver version 180. I reverted back to revision 173 and the problem goes away. Also, just to test it conclusively I then put 180 back on to check that the problem reappears, and it does. So I guess I'll be using an older Nvidia driver for awhile...

---

