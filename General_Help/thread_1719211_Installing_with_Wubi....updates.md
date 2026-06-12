---
title: "Installing with Wubi....updates??"
date: 2011-04-01
forum: General Help
---

### Post by Kal-El in SLO on 2011-04-01
I want to install Ubuntu via Wubi. Will updates be automatically installed during Ubuntu installation? I'm worried about the grub-pc and grub-common packages getting updated automatically, leading to possible boot problems. 

Thanks

---

### Post by Frogs Hair on 2011-04-01
No, you will receive update notifications after installation. I would recommend not installing proprietary drivers until after updates are installed . If you receive a message about grub during updates read the options carefully .

---

### Post by Frogs Hair on 2011-04-01
If you run into problems see this tread.[http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi)

---

### Post by Rubi1200 on 2011-04-01
> **Kal-El in SLO said:**
> I want to install Ubuntu via Wubi. Will updates be automatically installed during Ubuntu installation? I'm worried about the grub-pc and grub-common packages getting updated automatically, leading to possible boot problems. 

Thanks
You can prevent breakages on a fresh install by locking the grub-* packages. In the main post of the thread Frogs Hair linked to there is an explanation of how to do this (just after the Permanent Fix section).

---

### Post by Kal-El in SLO on 2011-04-02
Got it! Thanks

---

### Post by Rubi1200 on 2011-04-02
No problem, you are more than welcome :-)

---

