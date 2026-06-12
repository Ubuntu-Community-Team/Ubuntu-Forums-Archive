---
title: "Nvidia driver not found with Kernel 2.6.31-20 (9.10)"
date: 2010-04-24
forum: General Help
---

### Post by carn1x on 2010-04-24
When I boot the upgraded kernel 2.6.31-20, Nvidia complains it can't find a driver installed, and the only way I can get to desktop is by running low graphics mode. 

If I choose to boot at 2.6.31-14 however I can get to the desktop no problem, Nvidia drivers run fine. 

I thought I might be able to run nvidia-installer --update however I need to /etc/init.d/gdm stop to do this, and when I do that, it doesn't connect to the nvidia server.

Is there a "proper" way to get round this problem, or do I just need to manually download the non-free driver from Nvidia site manually and then run the package from outside X?

Also, what's the point of 'nvidia-installer --update' if running it outside of X doesn't reach the nvidia server?

Thanks for any advice :)

---

