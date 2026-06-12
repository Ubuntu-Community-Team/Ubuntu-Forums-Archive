---
title: "Chromium crashes everytime I run it"
date: 2012-06-06
forum: General Help
---

### Post by logos2501 on 2012-06-06
I have Ubuntu 10.04.  A few days ago Chromium crashed on me (I was looking at a picture on facebook).  Since then, every time I've tried to run it, it crashes after a few seconds.  I noticed that the applet is gone too.  I've tried uninstalling and reinstalling, but that didn't help.  When I try to run it from the terminal, it says "Segmentation fault" and nothing else.  Any ideas?  Thanks.

---

### Post by ron999 on 2012-06-06
> **logos2501 said:**
>  When I try to run it from the terminal, it says "Segmentation fault" and nothing else.  Any ideas?
Hi
The chromium profile folder is in:-
/home/user/.config/**chromium**

Maybe it's corrupted.

Try renaming the folder **chromiumOLD** so that chromium creates a new one when you run it.

---

### Post by logos2501 on 2012-06-06
That did it.  Thanks a lot!

---

