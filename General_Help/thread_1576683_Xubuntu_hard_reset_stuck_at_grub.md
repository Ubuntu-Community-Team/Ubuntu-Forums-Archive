---
title: "Xubuntu hard reset stuck at grub"
date: 2010-09-17
forum: General Help
---

### Post by sdwinder on 2010-09-17
I currently have a problem where when xubuntu is restarted using the power button, it will prompt the user with grub asking which selection to boot (xubuntu recovery or xubuntu) this feature itself is fine, but for some reason there is no timer, which means that unless you hit enter, it will always be stuck on the GRUB selection screen. I am wondering if there is any way to change this, is there anyway to enter a timer into the system so no matter what, after x seconds it will boot xubuntu?

---

### Post by andrewthomas on 2010-09-17
post the output of 

```
cat /etc/default/grub
```

---

