---
title: "Help with grub2 and BrowserLinux"
date: 2012-02-02
forum: General Help
---

### Post by Perplexed Pat on 2012-02-02
I've installed BrowserLinux 501 on a separate partition to Ubuntu 10.10 and it wants me to edit menu.1st in grub. There isn't any menu.1st (grub2). Does anybody know how to do this/have any ideas?

---

### Post by BC59 on 2012-02-02
menu.lst (is lst not 1st) was used in grub and not in grub2.

---

### Post by snowpine on 2012-02-02
From Ubuntu, try:

```
sudo update-grub
```

This ought to detect other operating systems and add them to your GRUB menu (unless there is something special/weird about Browserlinux that would prevent this).

---

### Post by Perplexed Pat on 2012-02-05
Thanks. That seems to have done the trick. My BrowserLinux is now listed in Grub as "unknown Linux distribution" but I can live with that!

---

