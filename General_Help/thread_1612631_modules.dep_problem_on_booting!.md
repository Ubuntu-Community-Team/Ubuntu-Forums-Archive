---
title: "modules.dep problem on booting!"
date: 2010-11-03
forum: General Help
---

### Post by Angus9046 on 2010-11-03
Hi everybody ^^
I just installed ubuntu, and everything went just good until i booted the system after the installation!
I get a message error that doesn't allow me to start working with linux.
The error is:

modprobe: FATAL: coult not load lib/modules/2.6.35-22-generic/modules.dep: No such file or directory.

modprobe: FATAL: coult not load lib/modules/2.6.35-22-generic/modules.dep: No such file or directory.

I found lots of topic for the problem, but the solutions were always adopted by terminal, modifying and reinstalling initramfs... my problem is that i can't open the terminal because the system just doesn't start up!
So, i can i solve my issue?
Anticipate thanks to everyone ^^

---

### Post by Lamez on 2010-11-03
On boot instead of choosing the normal kernel, choose the safe mode kernel, then drop to root shell. Then execute the commands they suggest. Also could you post a link I have the same problem, I would like to correct it. Thanks!

---

