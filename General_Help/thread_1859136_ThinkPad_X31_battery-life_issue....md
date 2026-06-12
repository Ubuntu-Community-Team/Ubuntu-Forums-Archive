---
title: "ThinkPad X31 battery-life issue..."
date: 2011-10-13
forum: General Help
---

### Post by utnubuuser on 2011-10-13
Hello, 

Wondering if anyone out there has any insight into battery management on ThinkPads.  (I've read several threads about extending battery life etc, and my issue is of a different nature).

Specifically, my ThinkPad's battery is down to 67% of its original capacity.  At a full charge, I've got 29Wh of capacity on a battery designed to output 46Wh.

However, the laptop shuts down after only about a minute on battery power, even though the power-manager battery icon shows that the charge is ok for a while.

I've installed tp-smapi-dkms and checked the cycle count, and the output shows that the battery's been cycled 167 times. (Many of those would have been completely full to completely empty cycles too, because I've been living on a sail-boat all year with no on-board power.).

If anyone has had any experience with squeezing a bit more life out of their battery, I'd be interested in hearing about it.

Thanks

---

### Post by effenberg0x0 on 2011-10-13
Hey,

Consider powertop and jupiter. For some more info, read this thread:
[http://ubuntuforums.org/showthread.php?t=1855126&highlight=powertop+jupiter](http://ubuntuforums.org/showthread.php?t=1855126&highlight=powertop+jupiter)

Regards,
Effenberg

---

### Post by utnubuuser on 2011-10-15
thanks - jupiter looks interesting...

---

### Post by 2F4U on 2011-10-15
I am using a package named TLP to tweak power management. 

[https://launchpad.net/~linrunner/+archive/tlp]("https://launchpad.net/%7Elinrunner/+archive/tlp")

It is originally designed for ThinkPad laptops and combines some advanced settings for power management. Not all features work with a X31, for example, you will not be able to set battery charge thresholds.

---

