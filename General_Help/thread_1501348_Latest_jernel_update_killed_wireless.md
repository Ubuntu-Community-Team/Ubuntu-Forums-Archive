---
title: "Latest jernel update killed wireless"
date: 2010-06-04
forum: General Help
---

### Post by llawwehttam on 2010-06-04
Using 9.10 as 10.04 cause problems for me.

Since I installed the updates this morning including the latest kernel my wireless cannot connect to my router.

```
 
 Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
 
```

I have the linux wireless backports installed and up to latest version.

Any help appreciated.

---

### Post by llawwehttam on 2010-06-04
All fixed.... phew.....

re-installed the backports and after a reboot its sprung back into life.

At least its working now

---

### Post by canadianwriterman on 2010-06-04
I have the same problem. The last update killed my wireless. What are the "wireless backports" you refer to?

---

### Post by llawwehttam on 2010-06-04
jack 1233 your posting in the wrong section, 2 your sig is advertising 3 your username looks identical to one made by a bot.

> **canadianwriterman said:**
> I have the same problem. The last  update killed my wireless. What are the "wireless backports" you refer  to?

backports are either bits of original linux code unedited by the ubuntu team or older bits of stable code.

Have a look at the wireless link in my sig. It works for most.

---

### Post by canadianwriterman on 2010-06-09
Installing linux-backports-modules-wireless-karmic-generic worked. Thanks llawwehttam.

---

### Post by llawwehttam on 2010-06-09
Glad that worked for you.

---

