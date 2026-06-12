---
title: "Bad resolution"
date: 2012-01-08
forum: General Help
---

### Post by Renewable on 2012-01-08
Hello, I just installed ubuntu on my new rig. I chose ubuntu because on the live disk, they had the resolution that i needed for my monitor - 1920x1200. I tried arch and windows beforehand but i couldnt get more than 1440x900 on arch and a really badly stretched one for windows. Well i installed it and started setting everything up. I installed the Nvidia driver as i am using a new Nvidia card (GeForce GT 430) and i need 3d acceleration, as a pose to nouveau which has bad 3d acceleration. Anyway, once i had installed the Nvidia driver and rebooted, I no longer had the option to chose 1920x1200, the highest is 1440x900, just like arch. I intend to stick with ubuntu now because i am one of the few people who likes the new unity desktop, but please could anyone help me out? :/ Thanks.

---

### Post by Renewable on 2012-01-08
By the way, changing the res on the nvidia settings jut gives me a black screen with a mouse, then reverts back to 1440x900 :/

---

### Post by Renewable on 2012-01-08
Bump :/

---

### Post by The Cog on 2012-01-08
It would probably help those who really know about this stuff if you could give more details. A few things that would probably be useful are:
* which version of Ubuntu are you using
* Are you using the drivers that come with Ubuntu, or have you downloaded drivers from nVidia
Can you post the output of these commands:
```
xrandr
lspci -v
```
For lspci, we only need the section on the VGA controller.

Since you say it is a new nVidia card, I am wondering if the drivers that Ubuntu ships with aren't recent enough. 

I know that 1920*1200 isn't a problem of itself, because that's the resolution I'm on (Xubuntu 11.04 and 11.10 using the drivers that come with the distro, and a nVidia GeForce 9400 GT). I haven't used the nvidia-settings program as far as I can remember - things just worked.

---

