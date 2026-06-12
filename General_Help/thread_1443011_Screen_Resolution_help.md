---
title: "Screen Resolution help"
date: 2010-03-30
forum: General Help
---

### Post by mowque on 2010-03-30
I installed Ubuntu with Wubi and it works fine. (9.10). The only issue is my screen resolution is very low. 800X600. On windows it is much better. Can anyone help me? I did some digging and found a way to use Terminal to get some info and found this- 

xrandr- Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 

Does this mean I can't get any better then 800X600?

---

### Post by one-of-four on 2010-03-30
Question: are you using an NVIDIA card?
If so, it's not your max resolution it is an oddity of the NVIDIA drivers (I just went through all this so I understand where you're coming from). If it's NVIDIA I would try using this install guide to install the appropriate proprietary driver: [http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html](http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html)
It may be for an older version, but it still works in Ubuntu 9.10
Hope this helps!

---

