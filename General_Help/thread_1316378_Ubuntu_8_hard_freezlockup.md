---
title: "Ubuntu 8 hard freez/lockup"
date: 2009-11-05
forum: General Help
---

### Post by wildbillnj1975 on 2009-11-05
My ubuntu 8 system started randomly locking up/freezing about a month ago.  No hardware changes or anything like that.  This was with the 2.6.24-24-386 kernel.  I switched to rt and added "acpi=off" in the boot setup, which seemed to resolve the issue, but it has started happening again, and worse now.  Have picked up the later kernels via apt, but it doesn't matter.  Even if I go back and pick the 24-rt kernel via grub it crashes more often - sometimes after an hour or less.  And this happens usually when the machine is mostly idle.  Already tried disabling the screen saver, that didn't resolve it.

The whole thing freezes up hard - mouse pointer doesn't move, click/keyboard do not do anything.  keyboard lights aren't flashing or anything like that - total catatonic mode.

The system isn't in heavy use.  I bounce files through it via FTP occasionally, and it's a fileserver for "my documents" on my MS PC & laptop so that I can just keep one copy of files on the server without setting up file sharing on the windows machines.

Any idea where I can start searching for something to tell what is going on?

---

### Post by wildbillnj1975 on 2009-11-10
BUMP!

Help, anybody?  At least a pointer for where to look for what's broken?

---

### Post by wildbillnj1975 on 2009-11-13
BUMP again!

Come one, somebody?  Does anybody even have a suggestion for where to LOOK?  It won't even stay up and running for an hour...

---

### Post by wildbillnj1975 on 2011-01-24
motherboard turned out to have blown capacitors.
but I replaced it and still get the problem.  Started a new thread.

---

