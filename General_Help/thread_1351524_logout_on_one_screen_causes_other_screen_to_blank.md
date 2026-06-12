---
title: "logout on one screen causes other screen to blank"
date: 2009-12-10
forum: General Help
---

### Post by olithered on 2009-12-10
I've had a working multiseat configuration for some time (Fedora 8 and now Ubuntu 9.04), with two nvidia PCIe cards.

My computer has recently been upgraded and there is now a very annoying problem.

When I logout from one screen they both go blank. I can switch vt to find the new login screen, but the other screen (with programs still running) is completely inaccessible and I have to restart gdm to get both login screens back!

I have seen similar behaviour described in this bug (eg: c50):
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337019](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337019)

Any ideas?

---

### Post by olithered on 2010-01-16
Installing two new graphics cards and the 190.53 driver has fixed the problem!

Switch user even works properly too :-)

---

