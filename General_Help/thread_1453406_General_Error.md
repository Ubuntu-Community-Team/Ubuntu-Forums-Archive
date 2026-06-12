---
title: "General Error"
date: 2010-04-13
forum: General Help
---

### Post by joeknoodle on 2010-04-13
Ubuntu Karmic, Gnome, latest kernel, with all updates.

When trying to start my desktop now, I get the following error:

```

General error: 9c9-41f1-913f-38051bee47c3

```
Symptoms include a filesystem check that seems to stall out at inspecting the hard drive, and going into a shell look and not being able to "gdm" into Ubuntu.

I recently had a security update (on Mon 12 Apr 10) that I think may be related.

I've tried to do the "rescue mode" from Grub, as well as trying to use older kernels.

Any ideas?

---

### Post by Doctor Mike on 2010-04-13
> **joeknoodle said:**
> Ubuntu Karmic, Gnome, latest kernel, with all updates.

When trying to start my desktop now, I get the following error:

```

General error: 9c9-41f1-913f-38051bee47c3

```Symptoms include a filesystem check that seems to stall out at inspecting the hard drive, and going into a shell look and not being able to "gdm" into Ubuntu.

I recently had a security update (on Mon 12 Apr 10) that I think may be related.

I've tried to do the "rescue mode" from Grub, as well as trying to use older kernels.

Any ideas?
Boot from a live cd and run fsck:

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

