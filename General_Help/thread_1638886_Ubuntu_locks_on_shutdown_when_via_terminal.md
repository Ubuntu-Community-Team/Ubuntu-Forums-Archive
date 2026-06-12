---
title: "Ubuntu locks on shutdown when via terminal"
date: 2010-12-06
forum: General Help
---

### Post by MrZarq on 2010-12-06
When I try shutting down Ubuntu (10.04) via the terminal (sudo shutdown now) it locks on the splash screen. I doesn't doe that when I shutdown with the button.

Anybody know how to solve this?

---

### Post by TeoBigusGeekus on 2010-12-06
The correct command is
```
sudo shutdown -h now
```
Without the -h option, shutdown doesn't power off the pc.

---

### Post by MrZarq on 2010-12-06
That worked. What a rookie mistake.

Thanks a lot.

---

