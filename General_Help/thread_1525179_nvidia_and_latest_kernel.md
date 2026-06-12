---
title: "nvidia and latest kernel"
date: 2010-07-06
forum: General Help
---

### Post by MrGreen on 2010-07-06
Hi,

I am running kernel 2.6.32-23-generic-pae and since updating nvidia drivers do not work. I go into hardware drivers and activate but I get dropping to low resolution desktop or VGA not supported.

Reading ubuntu help did not shed any light nvidia module does not appear to be loading.

Can anyone help me how to fix or at least tell me what I am doing wrong?

Thanks

MrG

---

### Post by dino99 on 2010-07-06
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

---

### Post by MrGreen on 2010-07-06
Have no xorg.conf in /etc/X11

MrG

---

