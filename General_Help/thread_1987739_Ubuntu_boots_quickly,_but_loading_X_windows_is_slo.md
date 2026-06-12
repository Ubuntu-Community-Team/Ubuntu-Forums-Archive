---
title: "Ubuntu boots quickly, but loading X windows is slow"
date: 2012-05-26
forum: General Help
---

### Post by xaGrx on 2012-05-26
I've heard a lot about fast boot in Ubuntu 12.04. Unfortunately my experience is a bit different. My ubuntu start process could be described as following:

[LIST]
[*]from grub to noticeable mouse cursor ~30s + ~10s for desktop picture
[*]from desktop picture to unity panel ~35s
[*]then another ~45s for e.g. nautilus to be loaded
[/LIST]
All in all, I am not able to use my computer in less than two minutes, which is quite a lot, isn't it?

Note that dmesg log's last two rows are:
```

[   23.169677] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.064021] wlan0: no IPv6 routers present

```

Look at the time - 34s. What am I waiting for after that?

Maybe good to know: I am using the default nouveau driver instead of nvidia's. On Ubuntu 11.10 the boot took exactly the same time (I've made a new install to Ubuntu 12.04 though).

I know this question may be a bit too concrete, I would appreciate any information how to debug this as well, since I have no idea what's going on after the mentioned 34th second.

---

