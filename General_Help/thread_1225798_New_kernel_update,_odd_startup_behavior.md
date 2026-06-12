---
title: "New kernel update, odd startup behavior"
date: 2009-07-28
forum: General Help
---

### Post by QIII on 2009-07-28
After updating my Jaunty 64 bit machine just now with the latest kernel, I've encountered a strange behavior.

After selecting the new kernel from GRUB, I am presented with a message: "Unidentified video mode number".

I am given three choices:

Select a mode number
Press Space
Wait 30 seconds

Interestingly, the latter two start up as normal.

The first does not allow the number corresponding to my resolution and color depth, so I picked the closest fit.  The splash screen started, but was slightly misplaced on the screen.  Thereafter, the correct resolution was restored for the login screen.

None of the three choices caused any problem with resolution from that point on.

Has anyone else seen anything similar?

---

### Post by QIII on 2009-07-29
Sorry, folks.  Nothing to see here.

I went back and looked at the new menu.lst that was updated.

Removed the vga=xxxx bit from the end of the boot line.

---

