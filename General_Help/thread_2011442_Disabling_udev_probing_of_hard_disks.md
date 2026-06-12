---
title: "Disabling udev probing of hard disks?"
date: 2012-06-27
forum: General Help
---

### Post by Inherited Allele on 2012-06-27
I have an an NFS booting volume that's working great. However when it boots it spends a long time on some systems probing for local hard disks, which it doesn't actually need to use - and this delays everything else, especially if the disk is slow to respond.

I know I can override udev rules to disable autoprobing/automounting, but I'm not sure what rules I'd want to write to do this.

To be clear: what I want is for udev to completely ignore local disks.

---

