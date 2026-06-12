---
title: "How to set Windows as default boot option in GRUB2 ?"
date: 2010-04-03
forum: General Help
---

### Post by T-z3P on 2010-04-03
Hi . I managed to set up my laptop to dual-boot Windows XP SP3 and Ubuntu 10.04 . How do I set the Windows to be the default boot option at startup (GRUB2) ?

---

### Post by prodigy_ on 2010-04-03
```
sudo apt-get install startupmanager
```

Then in the system menu choose: ```
Administration/StartUp-Manager
```

---

### Post by T-z3P on 2010-04-03
Thank you .

---

### Post by warfacegod on 2010-04-03
In case Startup Manager doesn't work for you.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics")

---

