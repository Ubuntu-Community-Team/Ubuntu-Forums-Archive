---
title: "directory lockout due to mounted drives"
date: 2011-12-13
forum: General Help
---

### Post by samfraser on 2011-12-13
Hi, I'm on 11.10 and I have been using Ubunut on my Asus Eee netbook for some time now.

I've come up against this strange frustrating! Problem.  I have mounted drives to my NAS at home, if I put my netbook into hibernate, then move location, my home directory (where the NAS mount dir is located) is completely locked out!

When I list my mounted drives, they're still there...so I try to dismount them with umount however umount just hangs indefinitely!  I've tried the -f and -l options with umount as well.

The only way out of this problem is a reboot...which is crazy!

Any idea's chaps?

---

### Post by Mark Phelps on 2011-12-13
When you "move location", would that change the details of the mount commands?

My guess is that when the PC is hibernated, it saves the existing drive info, so that when it wakes up, it expects the same drives to be mounted the same way.

If that changes while hibernating, the mount commands will likely fail on awakening -- causing the problem you are having.

---

### Post by samfraser on 2012-01-09
I mount my nas which I have at home into a dir in my home directory.  I go to work, hibernate pc, when I get to work (no nas), my home directory is not accessible, from cli or file browser.  It just hangs when access is attempted.

Sure that fact that the mount point is no longer there would not lock out access to the entire directory?

---

