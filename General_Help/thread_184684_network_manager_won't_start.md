---
title: "network manager won't start"
date: 2006-05-30
forum: General Help
---

### Post by roots on 2006-05-30
hi there,

just switched from hoary to dapper, now i'm trying to get my IPW2200 to work with WPA. i read about network manager and installed it, but unfortunately it won't start!
the error message window i get when dapper starts is:

```
The NetworkManager applet could not find some required resources. It cannot continue.
```

any suggestions?


cheers,
roots

---

### Post by Clunsford on 2006-05-30
I got this same err about a month back... i just gave up on it, so... BUMP to see an answer

---

### Post by killmon on 2006-06-04
I am having the same problem. It started after trying to fix the firmware problem with my broadcom w/lan card. The card works, but the led does not show that is is working. And, now I get the error. I was just goingto leave it, but now I am having troubles downloading other apps --no net work manager...

Ah, and I wish I could give more help, but it is my first day using Linux.

Killmon- ](*,) bump-bump

---

### Post by Mr Fat Bat on 2006-06-05
How annoying!!

BUMP

---

### Post by roots on 2006-06-05
i found a solution in another thread on nm troubleshooting:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

good luck!


cheers,
roots

---

### Post by snowboard975 on 2007-01-21
> **roots said:**
> i found a solution in another thread on nm troubleshooting:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

good luck!


cheers,
roots


Thank you very much !! It solved my problem too!!!

---

