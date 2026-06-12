---
title: "Using ATI Radeon 200M with Ubuntu 10.04"
date: 2010-06-26
forum: General Help
---

### Post by IceRayn on 2010-06-26
Hello, I am trying to use a ATI Radeon 200M Series integrated graphics card with Ubuntu 10.04LTS edition. I am a semi-seasoned Linux user, using it on every system in my home other than my Mac. I am normally a Nvidia user, and I have found using ATI cards to be very difficult with Ubuntu in the past with family member's computers.

Currently, I am trying to run 10.04+XBMC on a Media Center system. The open source driver worked ok for regular use, but as soon as I tried to do anything with 3D acceleration needed, the application would segfault. I tried installing the proprietary driver, only to find that my card is not supported by this driver. When I attempted to move back to open source, I found that there is no driver running the card now.

I'm really hoping to use Linux on this system for it's stability and performance, but if I can't even use a 3D accelerated application (the main use for the system) then I'll try Windows, and see how that goes.

If any of you can think of a solution to the problem that would allow 3D acceleration on this card with any version of Linux, please reply.

Thanks,
IceRayn

---

### Post by Mark Phelps on 2010-06-27
> **IceRayn said:**
> If any of you can think of a solution to the problem that would allow 3D acceleration on this card with any version of Linux, please reply.

Thanks,
IceRayn
To have 3D acceleration, you would have to go back to Intrepid (8.10).  Nothing newer than that will support the older fglrx drivers, and the newer drivers won't work with your video chip/card.

---

