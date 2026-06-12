---
title: "fglrx packages for ATI Radeon mobility 7500"
date: 2005-03-12
forum: General Help
---

### Post by taniwha on 2005-03-12
Hi,
I am quite confused about which fglrx packages I should install.
what would be better for an ATI Radeon Mobility 7500 (32MB)?

Now, on Hoary preview,  I got:
fglrx-control
xorg-driver-fglrx

When I drag a window, I have a quite bad "shadowing" effect.

Missing anything important ?
Any settings?

Thanks in advance

---

### Post by CompShrink on 2005-03-13
I have the same card, and the package in synaptic only works for 8500 and up, which taking a look at ati's website seems to be the only ones they support...

I also tried "atitvout" with no success. It identified my card correctly, but could not perform any functions.

I'll tell you if I get mine working, please post here how you got yours working, if you do...

---

### Post by ivar on 2005-03-13
[QUOTE=taniwha]Hi,
I am quite confused about which fglrx packages I should install.
what would be better for an ATI Radeon Mobility 7500 (32MB)?
[/QUOTE]

bad news -
your fglrx troubles are over -  the Radeon Mobility 7500 is not supported by the fglrx driver.  see [http://www2.ati.com/drivers/linux/linux_8.8.25.html#172394](http://www2.ati.com/drivers/linux/linux_8.8.25.html#172394)

more bad news-
I don't know what to suggest to get 3D working, as I'm still stuck..  ](*,)  see my (currently unanswered) question at:
[http://ubuntuforums.org/showthread.php?t=18849](http://ubuntuforums.org/showthread.php?t=18849)

this post looks promising, but doesn't provide enough info:
[http://ubuntuforums.org/archive/index.php/t-4343.html](http://ubuntuforums.org/archive/index.php/t-4343.html)

if you figure anything out, please post back in this thread...

---

### Post by taniwha on 2005-03-13
Enter the following in the device section of your XFree config file...

Option "AGPMode" "4"
Option "AGPFastWrite" "True"
Option "EnablePageFlip" "True"

I did it, as suggested in one linked post.
It seems to me that there is an improvement in how the system handles the windows (the "dragging" effect).
I didn't try games such as quake, so I can't really say. But, at least, it does the job for normal use .

Hopefully, someone will come up with a better solution...

---

