---
title: "Why is firefox so horriblly slow in karmic 64 bit?"
date: 2009-11-20
forum: General Help
---

### Post by bowens44 on 2009-11-20
I have tried all for a couple of weeks now to get firefox to preform adequately in karmic. I'm convinced it can't be done. It is painfully slow.

I have tested it with several sites, these sites take 8 to 10 seconds to load in firefox. In swiffox they load in under 3 seconds.Some of them so quickly that I don't have time to count to two!!

I wouldn't  be asking this question if I could get java to work
in swiftfox, I'd just be using swiftfox.  

I need the java so I have to stick with firefox for now. 

I have followed the various guides for speeding up firefox and nothing seems to work.

Is there a way to make firefox faster?

---

### Post by doixanh on 2009-11-20
try disabling IPv6 for firefox, as described [here]("http://en.opensuse.org/Disable_IPv6_for_Firefox").

---

### Post by judge jankum on 2009-11-20
Which version Firefox do you have? We had the same issue with 3.5 in Ubuntu and XP both...We dumped it for 3.0.10 and everything started working ok again...

---

### Post by bowens44 on 2009-11-20
> **doixanh said:**
> try disabling IPv6 for firefox, as described [here]("http://en.opensuse.org/Disable_IPv6_for_Firefox").

Thanks for the reply but I've already done that. I have also tried several other speed optimization tips in the several guides that are floating around. To me it looks like the problem is related to to DNS look up.

When looking up a site it takes as long as 5 seconds to resolve. The lookups in swiftfox are much much faster. I really don't understand why there is a such a huge difference.

---

### Post by lovinglinux on 2009-11-21
> **bowens44 said:**
> Thanks for the reply but I've already done that. I have also tried several other speed optimization tips in the several guides that are floating around. To me it looks like the problem is related to to DNS look up.

When looking up a site it takes as long as 5 seconds to resolve. The lookups in swiftfox are much much faster. I really don't understand why there is a such a huge difference.

Try [this](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/). Also take a look at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by pickett on 2009-11-21
swiftfox is actually a 32bit app even if you're on 64bit, so to get java to work you need to install the 32 bit version.

---

