---
title: "Floppy Drive not working"
date: 2011-11-08
forum: General Help
---

### Post by Seb71 on 2011-11-08
Ubuntu 11.10/Unity 2D

When I open Nautilus, in the left side-bar, under Devices, I can see that my Floppy Drive unit is listed. When I click on it, it does not open the floppy disc inside the Floppy Drive. No error message either.

I tested the drive with the same floppy disk - a boot floppy disk, from which I can boot that PC, so it is not a hardware problem.

---

### Post by plucky on 2011-11-08
> **Seb71 said:**
> Ubuntu 11.10/Unity 2D

When I open Nautilus, in the left side-bar, under Devices, I can see that my Floppy Drive unit is listed. When I click on it, it does not open the floppy disc inside the Floppy Drive. No error message either.

I tested the drive with the same floppy disk - a boot floppy disk, from which I can boot that PC, so it is not a hardware problem.

The floppy icon has been broken since 10.04. See [Bug Report](https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/441835)

This works

Open a terminal and after loading a floppy do ```
udisks --mount /dev/fd0
``` and then you should see the floppy icon on the Desktop and you should be able to access it through Nautilus File manager.

Good Luck

---

### Post by Seb71 on 2011-11-08
Thank you. The floppy is mounted with that command, the icon shows up on Desktop and I can access the floppy disc from there (but only from there).

---

