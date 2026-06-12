---
title: "How do i stop disk check every time i boot up?"
date: 2010-12-19
forum: General Help
---

### Post by a quarter past seven on 2010-12-19
Every time i boot up i have to go through a disk check and then restart, how do i stop it from happening?

when the disk checks happening i press escape and it usually says its deleted inode something because it has zero Dtime or some thing similar and also a paragraph of repeated lines saying something like all system files need alsa base.cnfg it will be ignored in a future release then the disk check completes and it restarts and is fine then,

also sometimes it says dev/sda5 (my ubuntu partition) was not cleanly unmounted check forced

is their a way to stop this happening as it ends up taking ages just to login,

thanks for your help

---

### Post by Sef on 2010-12-19
A better question is why is this happening.  You could have a bad hard drive or other hardware problem, or maybe even a software problem. I would make sure that your data is back up off the hard drive, in case that is the problem.

---

### Post by searchfgold6789 on 2010-12-19
Did you let the check take place and fully complete?
In the disk's entry in /etc/fstab, make sure the two numbers next to it are "0 2" or "0 0".

---

### Post by a quarter past seven on 2010-12-20
yeah i usually let it finish, i have two installs of ubuntu and it never happens on my other install i have recently re partitoned my hard drive so maybe thats whats causing it

---

