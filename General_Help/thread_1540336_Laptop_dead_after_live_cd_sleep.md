---
title: "Laptop dead after live cd sleep"
date: 2010-07-27
forum: General Help
---

### Post by palz2015 on 2010-07-27
I shut the lid of my old toshiba tecra with the 10.04 LTS cd booted and I get a striped screen with grey and red stripes. WTF?!

---

### Post by marshmallow1304 on 2010-07-27
The laptop probably suspended to RAM and for some reason was unable to resume.  You can disable suspending when you close the lid in System->Preferences->Power Management.


This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502376") was the closest I could find.  There may be [a workaround]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502376/comments/25"), but I'm not sure as it refers to the proprietary NVIDIA driver, which can't be installed when working from a LiveCD anyway.

---

