---
title: "Scroll Wheel"
date: 2006-02-04
forum: General Help
---

### Post by Mau on 2006-02-04
Hi everybody,
I was configuring my graphic driver yesterday trying to get my Radeon 9600 to work with 3D.  I first tried [this](http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+radeon+9600) tutorial, which just put my resolution to 1024x768.  I had a lot of trouble with this and it crashed my system numerous times.  At one time I completely crashed X.  I then went to install [another one](http://ubuntuforums.org/showthread.php?p=423589) and this one worked!  I was able to get it in the first try.

The problem is that my scroll wheel does not work any more.  I believe the problem may be have been with the first guide that I followed, because I believe I was completely reconfiguring X.

Is there any way to get this scroll wheel functionality back?  I have a USB Logitech mouse.

---

### Post by analyticalman on 2006-02-04
When you configure x using dpkg-reconfigure xserver-xorg you get an option to enable the scroll wheel - that might work

---

### Post by Mau on 2006-02-04
I just went through the whole tedious process again and this time I manually configured everything to get my scroll wheel to work.  I think I also solved a shut down problem I was having too in the process!

---

