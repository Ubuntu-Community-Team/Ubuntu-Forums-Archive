---
title: "Moved machine from Linux to Windows XP, now big disks show as 128gb"
date: 2009-08-05
forum: General Help
---

### Post by Underpants on 2009-08-05
I don't know if this is the right place for this, but:

I have a big workstation with a Promise TX2 IDE controller with 4x500gb hard drives attached.

This machine has had linux on it for a long time and the drives showed up just fine, as 500gb.

I have installed windows xp on this machine, with service pack 3, and now all 4 disks show as 128gb.

What is going on here?

---

### Post by shirilover on 2009-08-05
You probably need to enable 48-bit LBA support to see the full size of the drives.

See here -> [http://support.microsoft.com/kb/303013](http://support.microsoft.com/kb/303013)

---

