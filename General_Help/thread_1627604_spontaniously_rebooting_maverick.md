---
title: "spontaniously rebooting maverick?"
date: 2010-11-21
forum: General Help
---

### Post by Ashrael on 2010-11-21
Since I upgraded to 10.10 my system keeps rebooting spontaniously.... 
Haven't been able to find anything wrong with the system, other than the reboots. Anybody have a clue for me? Anything is welcome.

TIA!

---

### Post by Hippytaff on 2010-11-21
Have you looked at the logs?
```

cd /var/log

```

you can find them there or go to system -> administration -> log file viewer

:-)

---

### Post by Ashrael on 2010-11-22
have not been able to find the reason in the logs... I wouldnt know what at least half the stuff means there.... Any pointers are welcome!


TIA!

---

### Post by nunrgguy on 2010-11-22
It wouldn't happen to freeze before the reboot would it?

---

### Post by philinux on 2010-11-22
> **Ashrael said:**
> have not been able to find the reason in the logs... I wouldnt know what at least half the stuff means there.... Any pointers are welcome!


TIA!

You may have a hardware fault or high temps somewhere.

First thing to try is running the memtest from grub. It takes ages to run though.

Install lm-sensors and check your temps.

---

### Post by Ashrael on 2010-12-02
hi!

did check all the temps, no probs there..
And @nunrgguy: yes, it appears to freeze before reboot..
The only thing I found was this:

kernel: [ 2030.629800] NVRM: os_raise_smp_barrier(), invalid context!

it seems to be nvidia related... Could this be the reason it keeps rebooting? It reboots at variable intervals, and I have not been able to pinpoint an application that explains the behaviour...

Thinking of downgrading again to see if it stops the problems...have not have the time to look into it..

Will post when i did...


THX!

---

### Post by Ashrael on 2011-06-01
Finally got around to checking this machine out, and it seems one of the memory modules has at least a few bytes short of a picknick... So pulled the pair and now its working fine again. Just with half the RAM that is... :mad:

Thanks to all!

---

