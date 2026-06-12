---
title: "boot WITHOUT network or mounting /etc/fstab entries?"
date: 2010-09-10
forum: General Help
---

### Post by mathog on 2010-09-10
In Ubuntu 10.04, are there any boot options that will tell upstart NOT to start the network and NOT to mount everything in /etc/fstab?  "single" doesn't cut it, as both actions occur when this is on the command line.

Long story:
I just discovered that Ubuntu 10.04's "recovery mode" boot is a pale imitation of Mandriva's "failsafe".  The latter starts the bare minimum needed to get to a command prompt - it ignores the mounts in /etc/fstab and doesn't start the network.  Ubuntu's "recovery mode", on the other hand, does try to mount everything in /etc/fstab, which is a problem when one of those mounts contains a corrupted NTFS-3g partition, since the boot locks up shortly after the error message.  The only way I could get out of that mess was to boot another OS and repair the partition, then and only then would Ubuntu boot in "single" mode.

---

