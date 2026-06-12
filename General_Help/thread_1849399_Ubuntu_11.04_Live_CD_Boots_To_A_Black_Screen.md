---
title: "Ubuntu 11.04 Live CD Boots To A Black Screen"
date: 2011-09-24
forum: General Help
---

### Post by Tman5293 on 2011-09-24
So I have this older laptop that I'm trying to get running for a friend. So I told him that since his old Windows installation was broken beyond repair I would put Ubuntu on it. He had no problem with that.

My problem is that when I load up the live cd in order to install it, it just boots to a blank black screen. I'm not sure how to get past the blank screen. I've already tried the "nomodeset" option and that did not work for me. I have some older Ubuntu disks so I was trying to see if any of the older releases would boot up. It turns out that the newest release that will even boot is 9.10. Anything newer than that goes straight to the black screen.

The laptop is an older acer model. I'd say around 2007ish. I don't know a whole lot about the specs since I haven't able to successfully get an operating system running on it. Right now it has a 250GB hard drive with nothing on it and I know that it has an Intel Pentium Dual Core processor.

Any help with this would be greatly appreciated. It's really frustrating me right now.

---

### Post by ipatch on 2011-09-24
you might want to try to press the the tab key at the boot scree, then type "i915.modset=1"  This parameter has been getting video on my acer laptop.

---

### Post by Tman5293 on 2011-09-24
> **ipatch said:**
> you might want to try to press the the tab key at the boot scree, then type "i915.modset=1"  This parameter has been getting video on my acer laptop.

Thanks! This worked for me!

---

