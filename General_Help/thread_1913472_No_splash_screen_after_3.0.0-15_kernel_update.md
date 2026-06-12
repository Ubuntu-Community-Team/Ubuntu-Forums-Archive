---
title: "No splash screen after 3.0.0-15 kernel update"
date: 2012-01-22
forum: General Help
---

### Post by Quatrix on 2012-01-22
Today I updated to the 3.0.0-15 kernel, and afterward the Ubuntu splash screen no longer appears during startup and shutdown.  After the GRUB menu I get a black screen with a flashing cursor for several seconds, followed by a purplish screen with plain "Ubuntu 11.10" text, four dots underneath, and then some low-level boot messages.  The same thing happens when shutting down.

I checked the GRUB configuration, and the "ro quiet splash" options are still there.  The only difference I see between the updated configuration and an old backup is that "vt.handoff=7" has been added at the end.  The backup is from August, however, and the vt.handoff option might have been there for a while.

I don't see any other problems, and it seems to be only cosmetic, but I'm curious what's going on.  Any ideas?

---

### Post by bumeshrai on 2012-01-23
I have the same problem.

---

### Post by Quatrix on 2012-01-23
> **bumeshrai said:**
> I have the same problem.

Also after updating to 3.0.0-15?

---

### Post by Quatrix on 2012-02-18
To anyone who has this problem:

1. Do you have an NVIDIA video card?

2. Do you see the following line in /var/log/boot.log?

 * Starting load fallback graphics devices [fail]

---

### Post by trygvrad on 2012-02-27
[removed - my problem appears to be different]

---

