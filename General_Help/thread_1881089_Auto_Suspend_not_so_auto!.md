---
title: "Auto Suspend not so auto!"
date: 2011-11-14
forum: General Help
---

### Post by mindgernade on 2011-11-14
My Auto suspend use to work and just stopped working one day. I can hit suspend and it will work but not on its own. How can I troubleshoot and fix this?

Ubuntu 10.10 btw

---

### Post by froghopper on 2011-11-15
I had this problem after upgrading to 11.10, it would not suspend on idle. But running this in the command prompt and rebooting seems to have fixed it.
```
sudo update-initramfs -u
```

---

### Post by mindgernade on 2011-11-17
Still not working.

---

