---
title: "How do I bypass the boot Menu Ubuntu 10.4"
date: 2010-04-26
forum: General Help
---

### Post by joelw135 on 2010-04-26
I upgraded my Ubuntu to 10.4 and when I boot it stops for 24 seconds at the boot menu then loads. This is the same menu you get on boot when you press Esc. How do I get Ubuntu to boot normal?

---

### Post by hopstah on 2010-04-27
I'm not sure how to disable it entirely, but a quick fix would be to edit your ```
/etc/default/grub
``` file and change the ```
GRUB_TIMEOUT
``` value to something shorter, like 5 seconds or so.  After you change that, be sure to run ```
sudo update-grub
```

---

### Post by joelw135 on 2010-04-27
> **hopstah said:**
> I'm not sure how to disable it entirely, but a quick fix would be to edit your ```
/etc/default/grub
``` file and change the ```
GRUB_TIMEOUT
``` value to something shorter, like 5 seconds or so.  After you change that, be sure to run ```
sudo update-grub
```

I have it working now, thanks.

---

