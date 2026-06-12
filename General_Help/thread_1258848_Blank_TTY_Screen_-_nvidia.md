---
title: "Blank TTY Screen - nvidia"
date: 2009-09-05
forum: General Help
---

### Post by dognose2 on 2009-09-05
I'm using the Nvidia 180 driver (gforce 9500 gt) and get a blank TTY screen when doing CTL + ALT + F1  (actually black with blinking cursor) 

I've seen some posts in 2007 regarding a similar bug, but I'm running with the latest updates and that's suppose to be fixed.  

I'm guessing I messed up something when installing the driver, somehow disabling any framebuffer?  IDK.  I'm sorta scared to do anything because I don't have a command line to fall back on if I mess up xwindows.... So, I'm hoping to diagnose the problem correctly before fiddling with anything. 

Where would I start looking to clear up my configuration?

---

### Post by dognose2 on 2009-09-06
no one?

I should be on the lastest version.. Ubuntu 9.04

---

### Post by dognose2 on 2009-09-08
Trying to install the updated Nvidia driver gives me: 

sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run 

You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by dognose2 on 2009-09-08
duh. .ssh in  .   ok. .I was able to upgrade NVIDIA... but.. not the CTL + ALT + F1  yeilds a flashing screen with odd text.

---

