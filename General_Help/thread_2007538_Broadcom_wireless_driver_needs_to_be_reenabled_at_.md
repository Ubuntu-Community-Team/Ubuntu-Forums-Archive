---
title: "Broadcom wireless driver needs to be reenabled at every reboot?"
date: 2012-06-20
forum: General Help
---

### Post by karasuman on 2012-06-20
So, I bought a new computer and promptly installed Lucid. Unfortunately, the wireless driver packaged with it doesn't actually work.  I did find a work-around, which included downloading a different driver and making it work (with a bunch of steps).

Unfortunately, I have to re-enable it every time I turn my computer off.  It's not really hard to do:

```
cd hybrid_wl
sudo modprobe lib80211
sudo modprobe cfg80211
sudo insmod wl.ko
```

There were some instructions on how to make this driver load at every boot, but they aren't working for me or I didn't understand them.  Can anyone help?

---

