---
title: "Box won't shut down properly"
date: 2006-06-18
forum: General Help
---

### Post by Maupertus on 2006-06-18
Hi guys,

I'm running Xubuntu 6.06 which runs without a hitch, but when I shut down my box it goes through the motions but when it gives the final message line (I don't remember what it is, but I bekieve it's "waiting to shutdown") it just hangs on that note.

Where can I look to solve this problem?

---

### Post by gabrielp on 2006-06-18
I have the same problem ,it is bug 43961 and is reported in launchpad
I hope it will be resolved ,upgrading of kernel did not solve the problem
Gabi

---

### Post by bryanlking on 2006-06-18
I don't know if this is related, or if it would even work in your case but some distros, ie: Mepis, append the kernel boot line in grub with the option **apm=power-off**, to assist on machines that have difficulty shutting completely down.  Someone correct me if I'm wrong.

Perhaps the next time you boot your system you could add that and see if it works. In any event it won't hurt.

BK

---

