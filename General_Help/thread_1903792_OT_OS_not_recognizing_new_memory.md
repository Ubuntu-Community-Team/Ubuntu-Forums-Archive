---
title: "OT: OS not recognizing new memory"
date: 2012-01-03
forum: General Help
---

### Post by jimbus on 2012-01-03
I don't think this is a Ubuntu thing, but wasn't sure where to properly address it... so please be patient :)

I had .5g of memory on a single stick and swapped in 2 1g sticks, but top still shows:

```
top - 09:31:53 up 2 days, 10:00,  0 users,  load average: 0.03, 0.19, 0.22
Tasks: 104 total,   1 running, 102 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.3%us,  1.7%sy,  0.0%ni, 89.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    [COLOR="Yellow"]442480k[/COLOR] total,   423148k used,    19332k free,    24252k buffers
Swap:   455676k total,    28192k used,   427484k free,   140916k cached
```

I'm reasonably sure I didn't swap sticks during the install and the machine is running, so at least one is registering... If you have any thoughts on how to debug this, or if there might be a configuration causing an issue, please help

The machine is an everex, $200 walmart special with a 1ghz via processor (Cyrix descendant). I've run Ubuntu 10.04 through current on it. I am now running Lubuntu 11.10

Thanks!

JimB

---

### Post by Azdour on 2012-01-03
Hi,

I usually go to (on Ubuntu 10.04): System | Administration | System Monitor and look on the System tab to see how much memory a machine has, otherwise post #5 on the following topic may help:

[http://ubuntuforums.org/showthread.php?t=1389253](http://ubuntuforums.org/showthread.php?t=1389253)

---

### Post by 2F4U on 2012-01-03
Does the BIOS recognize the new memory correct?

---

### Post by jimbus on 2012-01-16
Hrmm,

Apparently, I didn't buy what I thought... I reseated the two sticks, and, by the stickers, they were matching, and now I have 980992K of memory. 

I'm guessing they gave me a pair of .5g sticks instead of 1g like I asked. And when I installed them, only one of them seated right... and I should have been able to figure that out, but when the number was so graphically off of expectations, it overloaded my logic :)

Still, going from .5 to 1g makes it a bit perkier!

Thanks,

JimB

---

