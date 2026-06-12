---
title: "Compat-Wireless Aircrack Channel locked on -1"
date: 2010-10-27
forum: General Help
---

### Post by Hack.The.Pow. on 2010-10-27
Hello All!

Whenever I try to use aireplay I get the error message that 

```
mon0 is on channel -1, but the AP uses channel 6
```
(ap channel changes depending on ap)

I made sure to set my channel by using airmon
```
airmon-ng start wlan0 6
```

I found this thread that says I need to patch Compat-Wirless with a certain patch

[http://forum.aircrack-ng.org/index.php?topic=8646.0](http://forum.aircrack-ng.org/index.php?topic=8646.0)

However I can't figure out how to actually apply the patch.

I did a search for compat-wireless files and found three different folders.

compat-wireless-2.6.34
compat-wireless-2.6.34-staging
linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic

If anyone can tell me how to apply the patch that would be awesome.

---

### Post by trikster_x on 2010-10-28
[try this]("http://ubuntuforums.org/showthread.php?t=1598930")

---

### Post by Hack.The.Pow. on 2010-10-28
thanks!  worked like a charm.

I was just having trouble searching for the solution

---

### Post by sasagundul on 2010-11-28
thanks for the solution :D

---

