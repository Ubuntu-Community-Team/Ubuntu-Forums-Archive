---
title: "Segfaults in notification-apple and upowerd"
date: 2010-09-29
forum: General Help
---

### Post by JoTaB on 2010-09-29
Hi!

I have set up a server to install ubuntu via PXE. This works really well and is unattended via a preseed file. The only problem i am having is that the shutdown, mail and volume button arent working. The menu is flashing rapidly when i click it, like it is two layers fighting over who will be on to. The username+status button crashes the session for indicator applet completely when i click it and i have to reload it.

This happens both on a virtual (virtualbox) and a physical machine. It does not happen when i install from a cd. Please help!

When checking the logs i find the following:

[PHP]
Sep 29 13:33:17 ubuntu kernel: [  186.011229] upowerd[13646]: segfault  at 14 ip 003d37f8 sp bfc13810 error 4 in  libdbus-1.so.3.4.0[3c5000+37000]
Sep 29 13:33:17 ubuntu kernel: [   186.143249] upowerd[15635]: segfault at 14 ip 001c17f8 sp bf8b1f70 error  4 in libdbus-1.so.3.4.0[1b3000+37000]
Sep 29 13:33:17 ubuntu  anacron[15689]: Anacron 2.3 started on 2010-09-29
Sep 29 13:33:17  ubuntu anacron[15689]: Normal exit (0 jobs run)
Sep 29 13:33:17  ubuntu kernel: [  186.227564] CPU0 attaching NULL sched-domain.
Sep  29 13:33:17 ubuntu kernel: [  186.227569] CPU1 attaching NULL  sched-domain.
Sep 29 13:33:17 ubuntu kernel: [  186.248111] CPU0  attaching sched-domain:
Sep 29 13:33:17 ubuntu kernel: [   186.248116]  domain 0: span 0-1 level MC
Sep 29 13:33:17 ubuntu  kernel: [  186.248120]   groups: 0 1
Sep 29 13:33:17 ubuntu kernel:  [  186.248127] CPU1 attaching sched-domain:
Sep 29 13:33:17 ubuntu  kernel: [  186.248129]  domain 0: span 0-1 level MC
Sep 29 13:33:17  ubuntu kernel: [  186.248132]   groups: 1 0
Sep 29 13:33:28 ubuntu  kernel: [  197.530393] indicator-apple[1578]: segfault at 2c ip 002adddf  sp bf9d6580 error 4 in libgtk-x11-2.0.so.0.2000.1[16c000+3cd000]
[/PHP]

---

### Post by JoTaB on 2010-09-29
Solved it!

In my preseed file i had the line below. When i removed it it works like a charm. NO idea why this causes the problem i was experiencing.. But now it works! :)

#d-i debian-installer/locale string sv_SE

---

