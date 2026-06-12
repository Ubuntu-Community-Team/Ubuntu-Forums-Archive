---
title: "Shutdown -r works, Shutdown -P hangs"
date: 2010-07-11
forum: General Help
---

### Post by Eyeless Blond on 2010-07-11
...pretty much what it says in the title. For some reason, my Ubuntu install computer cannot shutdown, hibernate, or suspend. "Shutdown -P now" hangs; pressing Esc shows me it goes all the way to the "Power off" line and stops. Shutdown -r resets as normal.

I've been searching around, and I can already say that the "nomodeset" and "acpi=force" startup commands don't do anything. I've tried using both the open radeon driver and the closed fglrx one; again nothing helps. Any other ideas out there?

System details:
Running lucid 10.04. Running on a fresh install after failed upgrade (though I kept my /home partition; I might have to try a completely blank install, but I'd prefer not to)
Motherboard: MSI DKA790GX
Processor: AMD Athlon II X4 620
Video Card: HIS Radeon HD 4670 IceQ

---

### Post by Serpher on 2010-07-11
The shutdown command is really only when you need a timer. Change your runlevel using the init command.

**init 0** - Halt
**init 6** - Restart


Also did you install using wubi or did you boot the iso on startup?

---

### Post by Eyeless Blond on 2010-07-11
iso; I don't have Windows anywhere on this machine.

---

### Post by Eyeless Blond on 2010-07-13
Update: okay, so I've tried installing the newest proprietary drivers. They didn't help with my shutdown problem, but at least now I can use my dual monitors without things flaking out on me every time I get near the edges of the screen.

---

