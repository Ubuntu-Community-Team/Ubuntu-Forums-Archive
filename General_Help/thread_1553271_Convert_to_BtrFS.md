---
title: "Convert to BtrFS"
date: 2010-08-14
forum: General Help
---

### Post by conradin on 2010-08-14
Hi all,
I would like to convert my existing ext3 FS to a BtrFS (without re-installing) can anyone point me in the right direction?

If Re-installation is required, how do I install ubuntu with BtrFS?

---

### Post by snowpine on 2010-08-14
Btrfs is not yet supported by Ubuntu; perhaps with a fresh reinstall of 10.10 or 11.04 when the time comes. 

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

---

### Post by Blue Beard on 2010-08-22
> **conradin said:**
> Hi all,
I would like to convert my existing ext3 FS to a BtrFS (without re-installing) can anyone point me in the right direction?

If Re-installation is required, how do I install ubuntu with BtrFS?
Currently a /boot partition is needed to use btrfs.  This is being worked on by the Canonical Maverick Team.

The kernel.org wiki outlines the process to convert a non-root partition reasonably well.

There are stability issues --- so use with care.

---

