---
title: "Firefox performance issues in 9.10"
date: 2009-12-20
forum: General Help
---

### Post by goaliefight on 2009-12-20
I am having a problem with karmic 9.10 and firefox. It will often take up %50-100% CPU for no good reason. Also, flash really isn't usable at all. If you go to a site like youtube it will lock up completely and must be killed.

This seems to be a common problem as I have been sifting through related posts for several days. Unfortunately I have not found a resolution.

My system is a Dell latitude e6400 with 2.5Ghz Core2 Duo with 4GB ram. I have had the same problem with both the 32-bit and 64-bit.

Any advice on a solution would be appreciated.

---

### Post by hansdown on 2009-12-20
Hi goaliefight.

Firefox does seem to use a lot of CPU.

Google chrome "may" work better.

[http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha)

Not sure of the best way to fix flash, though.

---

### Post by goaliefight on 2009-12-20
> **hansdown said:**
> Hi goaliefight.
Google chrome "may" work better.


This seems to be a common problem and 9.10 has been out for a couple of months, so I was hoping to find a way to Make Firefox usable because I have extensions and work applications that require FF.

---

### Post by lovinglinux on 2009-12-20
Have you tried to start Firefox in safe mode to see if the problem is caused by some extension?

```
firefox -safe-mode
```

Does the problems happens on every page or a particular page? There are some web sites with javascripts that can cause very high CPU usage.

Do you have NoScript and AdBlock Plus installed?

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

