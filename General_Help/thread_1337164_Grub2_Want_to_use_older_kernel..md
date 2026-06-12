---
title: "Grub2 Want to use older kernel."
date: 2009-11-25
forum: General Help
---

### Post by gypsumwolf on 2009-11-25
I want to make the default entry my older kernel, not the newest one. How do I accomplish this?

---

### Post by philipp2084 on 2009-11-25
Have a look at [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

You want to change /etc/default/grub and look for the line: 

GRUB_DEFAULT=0

Also if you want grub to be displayed with the timer then comment out the following line: 

GRUB_HIDDEN_TIMEOUT=0


Before any of these changes take effect you have to update gurb: 

```
sudo update-grub
```

---

