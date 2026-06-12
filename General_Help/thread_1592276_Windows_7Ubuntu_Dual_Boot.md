---
title: "Windows 7/Ubuntu Dual Boot"
date: 2010-10-10
forum: General Help
---

### Post by doji33 on 2010-10-10
This probably sounds really stupid, but I dual booted Ubuntu and Windows, and when I start my computer it goes directly to Ubuntu. How do I boot into Windows?

---

### Post by sikander3786 on 2010-10-10
If Windows 7 was detected, you should be presented with a Grub menu at start, opting you to select the OS you want to boot to.

Try

```
sudo update-grub
```

from terminal and post the output.

---

