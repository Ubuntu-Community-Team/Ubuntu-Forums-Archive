---
title: "Where do I see my Network driver?"
date: 2010-08-31
forum: General Help
---

### Post by Kajmak on 2010-08-31
How can I find out what my network driver is?

(I got it installed, just wondering where to see the name of it)

Thanks.

---

### Post by andrewthomas on 2010-08-31
```
 dmesg|grep eth0
```

---

### Post by nothingspecial on 2010-08-31
> **andrewthomas said:**
> ```
 dmesg|grep eth0
```


Unless it is a wireless interface

```
sudo lshw -C network
```

will tell you loads of network info

---

