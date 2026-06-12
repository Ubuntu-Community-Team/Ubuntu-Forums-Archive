---
title: "where do ubuntu livecd's store temporary files?"
date: 2009-12-14
forum: General Help
---

### Post by yawnmoth on 2009-12-14
[This URL](http://nerdnotes.org/2006/05/can-i-ssh-into-ubuntu-live-cd/) discusses installing SSH on an Ubuntu LiveCD.  My question is...  where will this install SSH?  MS-DOS used to have a driver that'd let you create a disk out of RAM.  Apparently Linux has something similar called tmpfs but if that's what's being used shouldn't I see it with 'sudo fdisk -l'?

---

### Post by dcstar on 2009-12-14
> **yawnmoth said:**
> [This URL](http://nerdnotes.org/2006/05/can-i-ssh-into-ubuntu-live-cd/) discusses installing SSH on an Ubuntu LiveCD.  My question is...  where will this install SSH?  MS-DOS used to have a driver that'd let you create a disk out of RAM.  Apparently Linux has something similar called tmpfs but if that's what's being used shouldn't I see it with 'sudo fdisk -l'?

a) Into RAM.

b) No.

c) mount will show you the temp filesystems.

---

### Post by yawnmoth on 2009-12-14
> **dcstar said:**
> a) Into RAM.

b) No.

c) mount will show you the temp filesystems.

The SSH binaries, upon installation, are stored at /usr/bin/.  I don't see /usr/ when running mount, however.  I see that /home/ubtuntu uses gvfs, but I don't see anything about /usr/.

If I were to create a whole new "directory" (or mount point or whatever) out of RAM, as presumably /usr/ is, how would I do it?

---

