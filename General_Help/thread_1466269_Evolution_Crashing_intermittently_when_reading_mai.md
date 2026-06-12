---
title: "Evolution Crashing intermittently when reading mail"
date: 2010-04-30
forum: General Help
---

### Post by Psychobudgie on 2010-04-30
Had a couple of crashes with evolution when clicking on messages to read.

The errors reported from the log is below

kernel: [48544.183764] evolution[7455]: segfault at 4 ip 071afcb6 sp bfe8d320 error 4 in libglib-2.0.so.0.2400.0[7156000+c8000]

kernel: [48721.898121] evolution[7516]: segfault at 15 ip 00137980 sp bfc16f44 error 6 in libdbus-1.so.3.4.0[110000+37000]

Anyone getting similar problems or any suggestions what could be the source of the problem. It's been fine up to Lucid.

---

### Post by grapegrower on 2010-05-02
I've been having the same issue since I upgraded to 10.4 2 weeks ago.


evolution[27928] general protection ip:7fef3e597424 sp:7fff5c4fa090 error:0 in libdbus-1.so.3.4.0[7fef3e58c000+3d000]
evolution[28949]: segfault at 58d ip 00007fb84f202424 sp 00007fff0c88aca0 error 4 in libdbus-1.so.3.4.0[7fb84f1f7000+3d000]


It only happens once in a while and I don't seem to lose anything, it normally occurs right after I check for new messages and then click on a message to read it.


I'm going to reload now that 10.4 is finalized, I'll let you know if I still have the issues after my reload tomorrow.


Tim

---

