---
title: "nVidia problems in Jaunty?"
date: 2009-07-02
forum: General Help
---

### Post by sthompson1008 on 2009-07-02
I've been having a bit of a problem with my screen resolution as of late.

After my initial install of Jaunty and the restricted nVidia driver things were fine. My resolution was set to 1280x1024 which is normal for this monitor.

After an update and a restart though, I came to find that my resolution had been bumped down to 1024x768 and wouldnt change. The Display settings wouldnt let me change the resolution at all and neither would the nVidia X Server thing.

I tried a few things following other peoples instructions about editing xorg but nothing seemed to work.

Im using some crappy Yuraku monitor and i cant even find the h-v info for it.

Thanks.

---

### Post by synapsys on 2009-07-02
First, lets see what's in your xorg.conf

```
cat /etc/X11/xorg.conf
```

---

