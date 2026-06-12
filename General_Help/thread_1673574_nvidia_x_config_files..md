---
title: "nvidia x config files."
date: 2011-01-22
forum: General Help
---

### Post by soryu on 2011-01-22
where are they located ?
what file i cant find it.
thanks.

---

### Post by ajgreeny on 2011-01-22
Probably the file you mean is **/etc/X11/xorg.conf**.

---

### Post by soryu on 2011-01-22
yup.


where is that file?
how do i get to it?

i want to get rid of old config x files.

---

### Post by ajgreeny on 2011-01-23
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confbak
```will rename it but you can always restore it if you mess things up.

---

