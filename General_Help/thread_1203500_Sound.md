---
title: "Sound"
date: 2009-07-03
forum: General Help
---

### Post by jet-san on 2009-07-03
Everytime I shut down my Ubuntu I can hear a "beep" from PC speaker(?).
Can I turn it off?

---

### Post by ~sHyLoCk~ on 2009-07-03
> **jet-san said:**
> Everytime I shut down my Ubuntu I can hear a "beep" from PC speaker(?).
Can I turn it off?

```
sudo gedit /etc/modprobe.d/blacklist.conf

```
add > blacklist pcspkr
reboot.

---

