---
title: "cpu freq starts in correct mode then switches"
date: 2011-07-27
forum: General Help
---

### Post by hypertyper on 2011-07-27
I'm running 11.04 on my laptop and I've figured out how to get the cpu freq indicator going. I've added the code to start my cpu on minimum frequency to rc.local. After boot the frequency is set correctly but soon after it changes to on demand.

How do I keep it from overriding my initial settings?

Thanks

---

### Post by mc4man on 2011-07-27
I've always found ondemand to be the best mode for most of the time, anyway - 
The ondemand script is set to sleep for 60 sec from some point during the boot, then run and set ondemand.

So you may  need to take that into consideration for whatever your looking for.

/etc/init.d/ondemand

(you can just adjust the script to suit most cases

---

