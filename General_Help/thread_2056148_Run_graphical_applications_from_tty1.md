---
title: "Run graphical applications from tty1?"
date: 2012-09-10
forum: General Help
---

### Post by Kdar on 2012-09-10
I am connected to computer with serial port, which connects to tty1.

How can I run from there a graphical application that should be run on tty7? At the moment if I am trying to run bluetooth-sendto from tty1, it gives me "Cannot open display".

---

### Post by steeldriver on 2012-09-10
try

```
DISPLAY=:0 bluetooth-sendto
```

---

