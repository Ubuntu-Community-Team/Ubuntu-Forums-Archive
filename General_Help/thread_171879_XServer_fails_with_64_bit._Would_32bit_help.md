---
title: "XServer fails with 64 bit. Would 32bit help?"
date: 2006-05-07
forum: General Help
---

### Post by tonyweb on 2006-05-07
Good day friends,

I posted the following message in AMD64 forum ([http://ubuntuforums.org/showthread.php?t=171850):](http://ubuntuforums.org/showthread.php?t=171850):)

> Hi there,
I've used several distro in the past and now I was going to use ubuntu as my only distro and OS on my pc. My pc is an Athlon 64 3500+, with 1GB DDR2, 250GB 16M cache SATA2, and mobo ASUS A8N-VM CSM-UAYGZ.

I installed several times UBUNTU 64 Bit and it failed to load the Xserver all the times. My screen and integrated video card, both support the widescreen 1440x900 so I tried that and X failed.

So I tried all the resolutions, till the point that I selected only up to 1024x768. Nothing to do though.

As you can imagine this really disappointed me, I was expecting at least a VGA 16 colors Windows like, but nothing startx fails miserabily.

I tried sudo dpkg-reconfigure xserver-xorg but no joy.

Could you please help me? I don't want to use a different distro just because of this.


Many thanks,
Tony

PS: my monitor is a KDS 19" Widescreen.

I just realized that many many people in that forum are experiencing the same identical problem. I don't see this problem among 32 bit users.
So my question to you is: would installing Ubuntu x86 32bit resolve my problem?

I really want to become an ubuntu member, spread the world, be active part of the revolution, but this issues are putting me off a bit.

Thanks.
tony

---

### Post by DarkNemesis618 on 2006-05-08
Try checking the driver in xorg.conf.  I had the same problem.  I changed the driver from "nv" to "vesa" and that seemed to solve the problem.

---

