---
title: "trying to edit .inf, can't change permissions"
date: 2010-05-03
forum: General Help
---

### Post by Mattevt on 2010-05-03
I'm trying to change the autoplay value in an .inf file that is embedded in my western digital MyBook; but I can't get past the read only property no matter what I try. Any advice?

---

### Post by bobcollard on 2010-05-03
> **Mattevt said:**
> I'm trying to change the autoplay value in an .inf file that is embedded in my western digital MyBook; but I can't get past the read only property no matter what I try. Any advice?
Usually you can get by using root in Terminal:
```
sudo gedit /yourdirectory/filename.inf
```Edit, Save file, close and exit Terminal.

---

### Post by polki@mac.com on 2010-05-04
Please use gksu instead of sudo for GUI apps.

---

