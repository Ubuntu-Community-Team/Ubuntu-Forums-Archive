---
title: "Segmentation Fault error?"
date: 2011-09-14
forum: General Help
---

### Post by infotron on 2011-09-14
Out of the blue I started getting "Segmentation Fault" errors while trying to process some files with GhostScript. I opened Synaptic and re-installed this package, but no change.

I opened sys-log and see this:

> kernel: [  166.175140] gs[1941]: segfault at 40 ip 00c788e1 sp bfed7ab0 error 4 in libgs.so.9.01[af8000+453000]
kernel: [  282.527975] gs[2019]: segfault at 40 ip 083428e1 sp bfee8de0 error 4 in libgs.so.9.01[81c2000+453000]
kernel: [  316.329986] gs[2040]: segfault at 40 ip 077dd8e1 sp bf8eeda0 error 4 in libgs.so.9.01[765d000+453000]
kernel: [  941.912510] gs[2323]: segfault at 40 ip 077598e1 sp bfa264b0 error 4 in libgs.so.9.01[75d9000+453000]
kernel: [  957.390037] gs[2334]: segfault at 40 ip 00e558e1 sp bfdaf5c0 error 4 in libgs.so.9.01[cd5000+453000]

What should I do now?

Should I remove GhostScript completely then re-install or it won't help?

---

