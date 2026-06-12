---
title: "User removed from sudoers"
date: 2010-01-09
forum: General Help
---

### Post by graabein on 2010-01-09
Hi! I managed without knowing to remove my user from the sudo users group. I did **usermod -G fuse <username>** and now I can't sudo anymore. How do I get back to the promised land?

I'm in a rut and I want out!

---

### Post by nothingspecial on 2010-01-09
Boot into a root recovery shell and type

```
adduser username admin
```

---

### Post by ibuclaw on 2010-01-09
> **graabein said:**
> Hi! I managed without knowing to remove my user from the sudo users group. I did **usermod -G fuse <username>** and now I can't sudo anymore. How do I get back to the promised land?

I'm in a rut and I want out!

FYI, you should have done:
```
usermod -G -a fuse <username>
```

The above post by nothingspecial will add you back onto admins.

But as soon as you get that control back, it's best just to readded everything in one batch again:
```
usermod -G adm,dialout,cdrom,audio,fuse,plugdev,admin -a <username>
```

Regards
Iain

---

### Post by graabein on 2010-01-09
Thanks guys. :D

---

