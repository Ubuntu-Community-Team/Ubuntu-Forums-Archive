---
title: "mkinitrd-tools"
date: 2010-04-20
forum: General Help
---

### Post by CookieCutter on 2010-04-20
I found this guide for optimizing Ubuntu 9.10 here ([http://www.demonhades.org/phpBB3/viewtopic.php?f=242&t=3092&start=0](http://www.demonhades.org/phpBB3/viewtopic.php?f=242&t=3092&start=0)). I had no trouble for most of it but for this command:

```
sudo aptitude install build-essential kernel-package gcc libncurses5 libncurses5-dev wget make mkinitrd-tools
```

I had an error for mkinitrd-tools. After poking around Google, I discovered that mkinitrd-tools is apparently outdated. Only problem is that the kernel in the guide uses that command. What do I do?

---

### Post by CookieCutter on 2010-04-21
Bump

anyone?

---

### Post by klemes on 2010-04-21
Edit

---

### Post by klemes on 2010-04-21
If you have all the other packages in your post except this then proceed with the compiling of the kernel ,you do not need this package at least for a kernel targeted for a PC.But I don't think because this kernel is targeted for a PS3 anything would change...:).

---

