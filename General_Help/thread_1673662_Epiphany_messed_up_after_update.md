---
title: "Epiphany messed up after update"
date: 2011-01-22
forum: General Help
---

### Post by EvilBro on 2011-01-22
Today the update manager presented some updates and I allowed it to update. After it was finished, and I restarted the system, epiphany would not start anymore. When I start it from a terminal with sudo, it does start, but when I start it without sudo, it asks me to recover or restart and then segfaults. The message in messages is:

epiphany-browse[1946]: segfault at 0 ip 021d117c sp bfb13a50 error 4 in libc-2.12.1.so[21a0000+157000]

I tried reinstalling libc, but the reinstall had no effect.

Does anyone have any tips on what I might try to get things working again?

---

### Post by EvilBro on 2011-01-28
The file called 'cookies.sqlite' in ~/.gnome2/epiphany seemed to have caused the problem. I deleted it and now epiphany startup normally again.

---

