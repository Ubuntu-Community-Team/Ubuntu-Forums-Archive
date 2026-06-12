---
title: "photoshop not working"
date: 2010-10-18
forum: General Help
---

### Post by kree8or on 2010-10-18
Hi,
I've installed photoshop cs2 on my kubuntu lappy. It loads fine, then I get a error message saying that I need administrator privileges . How do I run Photoshop?

---

### Post by Refalm on 2010-10-18
Try restarting the computer, then try again.

If that didn't work, do this in the terminal:
```
sudo sysctl -w vm.mmap_min_addr=0
```

---

