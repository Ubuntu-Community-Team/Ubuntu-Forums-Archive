---
title: "Run FSCK automatically"
date: 2009-11-09
forum: General Help
---

### Post by terciof on 2009-11-09
Hi!

I have a server machine that has no monitor and keyboard.

Sometimes this machine may be shutdown incorrectly.

And in those cases, it will ask to run FSCK manually, asking for root password and CTRL+D to restart.

Is there any way to force the FSCK automatically, without entering the root password?

There is no user in the machine and it's on another physical location.

Thanks!

Regards,

Tercio

---

### Post by Giblet5 on 2009-11-09
Yes, but you almost certainly don't want to do that.

That's an interactive process on purpose...

The fsck program is as incredibly powerful as it is incredibly stupid. It will roast your data at the drop of an unreferenced inode.

fsck should either be run with repairs disabled or interactively, and for your situation, that means interactively.

If it doesn't matter whether you lose data, then it doesn't matter whether the server is up, down, or upside down in a dumpster, because an automated run of fsck in repair mode will effectively destroy the server eventually.

Your implementation of this server is wrong (no remote console capability) and that is what you should fix.

Put the thing on a UPS. Run a serial cable to a modem and set up a serial console for all run levels so that you can dial in and fix it.

---

### Post by terciof on 2009-11-09
> **Giblet5 said:**
> Yes, but you almost certainly don't want to do that.

That's an interactive process on purpose...

The fsck program is as incredibly powerful as it is incredibly stupid. It will roast your data at the drop of an unreferenced inode.

fsck should either be run with repairs disabled or interactively, and for your situation, that means interactively.

If it doesn't matter whether you lose data, then it doesn't matter whether the server is up, down, or upside down in a dumpster, because an automated run of fsck in repair mode will effectively destroy the server eventually.

Your implementation of this server is wrong (no remote console capability) and that is what you should fix.

Put the thing on a UPS. Run a serial cable to a modem and set up a serial console for all run levels so that you can dial in and fix it.


I'll re-think my solution.. Thanks for your time!

---

