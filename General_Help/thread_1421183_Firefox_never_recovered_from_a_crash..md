---
title: "Firefox never recovered from a crash."
date: 2010-03-03
forum: General Help
---

### Post by luisito on 2010-03-03
I was happily using firefox yesterday. At some point I tried to print a website as a PDF and firefox crashed. Ok, so I tried to restart and it didn't. I don't want to lose my settings, but I still tried with mv .mozilla mozilla-bak convinced that it would fix it. However it still did not. When I tried from the command prompt, it says
>~$ firefox
(firefox:4846): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault

If I try with sudo, same thing happens. When I remove .mozilla, it just gives four warnings before the segfault, but it still segfaults and does not start.

Right now I am using Google Chrome.

My system:
Ubuntu 9.10 x86_64
Firefox 3.5.8

---

### Post by luisito on 2010-03-03
It started working after a reboot. Don't ask me how or why.

---

### Post by ImperialXT on 2010-03-03
I would of just done sudo killall firefox-bin

---

