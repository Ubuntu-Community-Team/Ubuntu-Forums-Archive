---
title: "Can I (and should I) update my Nvidia drivers?"
date: 2010-03-08
forum: General Help
---

### Post by tamccullough on 2010-03-08
I'm using a EVGA Geforce GTX 280 on my system.

Recently I've heard that a recent Nvidia driver can possibly kill cards. I'm assuming mainly on windows systems.

Anyways, about a month and a half ago, my BFG Geforce GTX 260 bit the dust while gaming. Apparently blowing out the memory I think. Atleast that was what I was told.

When I heard on another forum about there being a possible problem with drivers I thought I should get the new ones on the windows partition and also thought I could do the same here.

Currently the Nvidia drivers are loaded but they are an older version.

How often do new versions come out through Canonical?
Can I just type something into the terminal and get an updated version?


Also - would this also solve my little 64bit problem concerning my comp's problems with flash and Extra visual effects?

Thanks

---

### Post by LowSky on 2010-03-08
the 196 driver is the problem... more than likely your using the 185 (*current 9.10 driver included) driver on Linux and should be fine

---

### Post by tamccullough on 2010-03-10
Yup 185 is the one I have. 
OK than, I guess I should just wait until the next driver is released by ubuntu?

---

### Post by cascade9 on 2010-03-10
> **LowSky said:**
> the 196 driver is the problem... more than likely your using the 185 (*current 9.10 driver included) driver on Linux and should be fine

*sigh*

> [It started with the GeForce 196.75 WHQL driver]("http://www.dvhardware.net/article41520.html"), which was pulled last week. The driver &#8216;recall&#8217; has been extended to include versions 195.36.03 and 195.36.08 *nix drivers.[http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug](http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug)

Considering that is from a link you posted LowSky (and made threads about) I would really hope you would get it right. 

Its not just the 196 driver (which is WHQL and therefore windows only), its also the 195.xx linux drivers. 

Upgrading to 190.xx drivers should be fine. I'd actually get the 190.xx drivers if your still on 185.....just avoid the 195.xx drivers untill nvidia has fixed it. 

I would think that when nvidia fixes the problem, the 195.xx series drivers will move back into the the 'normal' nvidia linux downloads from here-

[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

There are still 195.xx drivers in beta. Not the series that are meant to be having problems (that is 195.36.xx series, the avaible beta drivers are 195.30) but I'd avoid the 195.xx series for now.

---

