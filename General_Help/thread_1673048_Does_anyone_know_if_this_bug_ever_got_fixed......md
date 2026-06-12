---
title: "Does anyone know if this bug ever got fixed....."
date: 2011-01-21
forum: General Help
---

### Post by adduds on 2011-01-21
[http://img299.imageshack.us/f/screenshoteg.jpg/](http://img299.imageshack.us/f/screenshoteg.jpg/)

---

### Post by earthmeLon on 2011-01-21
> **adduds said:**
> [http://img299.imageshack.us/f/screenshoteg.jpg/](http://img299.imageshack.us/f/screenshoteg.jpg/)

Not sure exactly what's going on but..!

You're using TwinView and have Cairo-Dock set up to use Xinerama.  If you have nvidia card, try using Xinerama.  I got Xinerama and cairo-dock working nicely last night, actually.

This worked for me.  Let me know if you have any more questions.

---

### Post by adduds on 2011-01-22
oh its just the problem is when scrolling over my shortcuts tab in my right monitor...the bubble pops up on the left monitor....

i have xvideo x server settings

how to i disable that... and enable xinerama...will i keep the nvidia driver settings so i can 3D stuff? 

ty for your help :)

---

### Post by earthmeLon on 2011-01-24
Open nvidia-settings and make sure that the window you want cairo-dock and popups to be within is set as screen 0 and that your second screen is set to screen 1.

---

